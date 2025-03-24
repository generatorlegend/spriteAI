# Troubleshooting Guide for SpriteAI

This guide addresses common issues you might encounter when using the SpriteAI library and provides step-by-step solutions to help you resolve them.

## Table of Contents

1. [Image Generation Issues](#image-generation-issues)
2. [Background Removal Problems](#background-removal-problems)
3. [File Saving Errors](#file-saving-errors)
4. [Game Engine Integration Challenges](#game-engine-integration-challenges)
5. [Error Message Interpretation](#error-message-interpretation)

## Image Generation Issues

### Problem: No image generated

If you're not getting any image output from the `generateCharacterSpritesheet` or `generateEnvironmentSprites` functions, try the following:

1. Check your OpenAI API key:
   ```javascript
   const openai = new OpenAI();
   console.log(openai.apiKey); // Should print your API key
   ```

2. Ensure you have sufficient API credits.

3. Verify your network connection.

4. Check for any error messages in the console.

### Problem: Low-quality or incorrect images

If the generated images don't meet your expectations:

1. Refine your prompt:
   ```javascript
   const description = "A detailed, pixel-art warrior with a large sword and shield";
   ```

2. Adjust the `style` option:
   ```javascript
   const options = {
     style: 'pixel-art', // Try different styles like 'vector', '3d', 'hand-drawn'
   };
   ```

3. Increase the image size:
   ```javascript
   const options = {
     size: '1024x1024', // Larger size for more details
   };
   ```

## Background Removal Problems

### Problem: Background not fully removed

If the `removeBackgroundColor` function isn't effectively removing the background:

1. Adjust the `colorThreshold`:
   ```javascript
   await removeBackgroundColor(inputPath, outputPath, '#FFFFFF', 0.1);
   ```

2. Ensure the background color is correctly specified:
   ```javascript
   const targetColor = '#FFFFFF'; // Use the exact color code of the background
   ```

3. Check if the input image has a consistent background color.

## File Saving Errors

### Problem: Unable to save generated images

If you're encountering issues when trying to save generated images:

1. Check file permissions:
   ```javascript
   const fs = require('fs');
   fs.access('path/to/save/directory', fs.constants.W_OK, (err) => {
     if (err) {
       console.error('Directory is not writable');
     } else {
       console.log('Directory is writable');
     }
   });
   ```

2. Ensure the save path is correct:
   ```javascript
   const path = require('path');
   const savePath = path.join(process.cwd(), 'assets', 'generated_image.png');
   console.log('Save path:', savePath);
   ```

3. Verify that the `assets` directory exists:
   ```javascript
   const fs = require('fs');
   const path = require('path');
   const assetsDir = path.join(process.cwd(), 'assets');
   if (!fs.existsSync(assetsDir)) {
     fs.mkdirSync(assetsDir, { recursive: true });
   }
   ```

## Game Engine Integration Challenges

### Problem: Incorrect sprite dimensions in game engine

If the generated sprites don't fit correctly in your game engine:

1. Check the `metadata` returned by the generation functions:
   ```javascript
   const result = await generateCharacterSpritesheet(description, options);
   console.log(result.metadata);
   ```

2. Ensure you're using the correct frame dimensions:
   ```javascript
   const { frameWidth, frameHeight } = result.metadata.dimensions;
   // Use frameWidth and frameHeight to set up your sprite in the game engine
   ```

3. Verify that your game engine's sprite import settings match the generated sprite's properties.

## Error Message Interpretation

### OpenAI API Errors

- `"Error: Request failed with status code 401"`: Check your API key and ensure it's correctly set.
- `"Error: Rate limit reached for requests"`: You've hit the API rate limit. Wait a bit before trying again or upgrade your plan.
- `"Error: You exceeded your current quota"`: You're out of API credits. Check your usage on the OpenAI dashboard.

### File System Errors

- `"ENOENT: no such file or directory"`: The specified file or directory doesn't exist. Check your file paths.
- `"EACCES: permission denied"`: You don't have the necessary permissions. Check file/directory permissions.

### Image Processing Errors

- `"Error: Input buffer contains unsupported image format"`: Ensure you're working with supported image formats (PNG, JPEG).
- `"Error: Image file is truncated"`: The image file is incomplete or corrupted. Try regenerating or reuploading the image.

If you encounter any errors not covered here, please check the official OpenAI API documentation or file an issue on the SpriteAI GitHub repository for further assistance.