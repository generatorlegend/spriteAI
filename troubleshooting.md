# Troubleshooting Guide for SpriteAI

This guide addresses common issues you might encounter when using the SpriteAI library. Follow the steps below to resolve problems related to image generation, background removal, API interactions, and integration with game engines.

## Table of Contents

1. [Image Generation Issues](#image-generation-issues)
2. [Background Removal Problems](#background-removal-problems)
3. [API Interaction Errors](#api-interaction-errors)
4. [Game Engine Integration Challenges](#game-engine-integration-challenges)

## Image Generation Issues

### Problem: Generated images are low quality or don't match the description

1. Check your prompt:
   - Ensure your description is detailed and specific.
   - Use clear, concise language to describe the desired output.

2. Verify size parameters:
   - Make sure you're using an appropriate size (e.g., '1024x1024').
   - Example:
     ```javascript
     const options = {
       size: '1024x1024',
       // other options...
     };
     ```

3. Adjust style settings:
   - Try different style options like 'pixel-art', 'vector', or '3d'.
   - Example:
     ```javascript
     const options = {
       style: 'pixel-art',
       // other options...
     };
     ```

4. Increase the number of iterations:
   - Generate multiple images and select the best one.
   - Example:
     ```javascript
     const options = {
       iterations: 3,
       // other options...
     };
     ```

## Background Removal Problems

### Problem: Background isn't fully removed or important parts of the sprite are missing

1. Adjust color threshold:
   - Increase the `colorThreshold` value for more aggressive removal.
   - Decrease it for more conservative removal.
   - Example:
     ```javascript
     await removeBackgroundColor(
       inputPath,
       outputPath,
       '#FFFFFF',
       0.1 // Adjust this value
     );
     ```

2. Specify the correct background color:
   - Ensure you're using the exact color of the background you want to remove.
   - Example:
     ```javascript
     await removeBackgroundColor(
       inputPath,
       outputPath,
       '#FFFFFF', // Use the correct color code
       0.1
     );
     ```

3. Pre-process the image:
   - Use image editing software to increase contrast between the sprite and background before processing.

## API Interaction Errors

### Problem: API calls fail or timeout

1. Check your API key:
   - Ensure your OpenAI API key is correctly set and has sufficient credits.

2. Verify network connection:
   - Check your internet connection and firewall settings.

3. Handle rate limits:
   - Implement exponential backoff for retries.
   - Example:
     ```javascript
     async function callWithRetry(apiFunction, maxRetries = 3) {
       for (let i = 0; i < maxRetries; i++) {
         try {
           return await apiFunction();
         } catch (error) {
           if (i === maxRetries - 1) throw error;
           await new Promise(res => setTimeout(res, 2 ** i * 1000));
         }
       }
     }

     // Usage
     await callWithRetry(() => openAiObject.images.generate({...}));
     ```

4. Check API response for error messages:
   - Log and handle errors returned by the API.
   - Example:
     ```javascript
     try {
       const response = await openAiObject.images.generate({...});
     } catch (error) {
       console.error('API Error:', error.response?.data?.error || error.message);
       // Handle the error appropriately
     }
     ```

## Game Engine Integration Challenges

### Problem: Sprites don't display correctly in the game engine

1. Check image format compatibility:
   - Ensure your game engine supports the generated image format (PNG).

2. Verify spritesheet metadata:
   - Use the metadata returned by `generateCharacterSpritesheet` to correctly slice the spritesheet.
   - Example:
     ```javascript
     const result = await generateCharacterSpritesheet('character description', options);
     console.log(result.metadata);
     // Use this metadata to set up your sprite animations
     ```

3. Adjust sprite scaling:
   - If sprites appear too large or small, scale them appropriately in your game engine.

4. Handle transparency:
   - Ensure your game engine is correctly interpreting the alpha channel for transparency.

### Problem: Animation states are not working as expected

1. Verify animation state names:
   - Ensure you're using the correct state names as defined in your options.
   - Example:
     ```javascript
     const options = {
       states: ['idle', 'walk', 'run', 'attack'],
       // other options...
     };
     ```

2. Check frame count:
   - Make sure the `framesPerState` option matches the actual number of frames in each animation state.

3. Use the correct row for each animation state:
   - The `frameData` in the metadata provides the correct row for each state.
   - Example:
     ```javascript
     const result = await generateCharacterSpritesheet('character description', options);
     const idleRowIndex = result.metadata.frameData.idle.row;
     // Use idleRowIndex to set up the idle animation in your game engine
     ```

By following this troubleshooting guide, you should be able to resolve most common issues encountered when using the SpriteAI library. If you continue to experience problems, please check the library's documentation for updates or contact support for further assistance.