# Troubleshooting Guide for SpriteAI

This guide addresses common issues you might encounter when using the SpriteAI library and provides step-by-step solutions to resolve them.

## Table of Contents
1. [Image Generation Issues](#image-generation-issues)
2. [Background Removal Problems](#background-removal-problems)
3. [API Usage Errors](#api-usage-errors)
4. [Game Engine Integration Challenges](#game-engine-integration-challenges)
5. [Error Message Interpretation](#error-message-interpretation)

## Image Generation Issues

### Problem: Sprites are not generating or are incomplete

1. Check your OpenAI API key:
   - Ensure your API key is correctly set and has the necessary permissions.
   - Verify the API key is properly loaded in your environment variables.

2. Validate your prompt:
   - Make sure your description is clear and specific.
   - Avoid using terms that might violate content policies.

3. Check network connectivity:
   - Ensure you have a stable internet connection.
   - Try running a simple API test to confirm connectivity.

### Problem: Generated sprites are low quality or inconsistent

1. Adjust the size parameter:
   - Increase the size (e.g., from '1024x1024' to '2048x2048') for higher resolution.
   ```javascript
   const result = await generateCharacterSpritesheet(description, { size: '2048x2048' });
   ```

2. Refine your prompt:
   - Be more specific about the style and details you want.
   - Use descriptive adjectives to guide the AI.

3. Increase the number of iterations:
   - Generate multiple sprites and select the best one.
   ```javascript
   const options = { iterations: 3 };
   const results = await generateSprite(description, options);
   ```

## Background Removal Problems

### Problem: Background is not fully removed

1. Adjust the color threshold:
   - Increase the threshold to remove more similar colors.
   ```javascript
   await removeBackgroundColor(inputPath, outputPath, '#FFFFFF', 0.2);
   ```

2. Specify the correct background color:
   - Ensure you're targeting the right color for removal.
   - Use a color picker tool to get the exact color code.

3. Pre-process the image:
   - Use image editing software to increase contrast before processing.

### Problem: Important parts of the sprite are being removed

1. Decrease the color threshold:
   - Lower the threshold to be more selective in color removal.
   ```javascript
   await removeBackgroundColor(inputPath, outputPath, '#FFFFFF', 0.05);
   ```

2. Use a more specific target color:
   - Instead of removing all white, target a specific shade.

3. Manually touch up the sprite:
   - For complex cases, use image editing software for final adjustments.

## API Usage Errors

### Problem: Rate limiting errors

1. Implement exponential backoff:
   - Add retry logic with increasing delays between attempts.
   ```javascript
   const axios = require('axios');
   const axiosRetry = require('axios-retry');

   axiosRetry(axios, {
     retries: 3,
     retryDelay: axiosRetry.exponentialDelay
   });
   ```

2. Check your API usage limits:
   - Review your OpenAI account for current usage and limits.
   - Consider upgrading your plan if necessary.

3. Optimize your requests:
   - Batch multiple sprite generations when possible.
   - Cache frequently used sprites to reduce API calls.

### Problem: Authentication errors

1. Verify your API key:
   - Double-check that you're using the correct API key.
   - Ensure the key has not expired or been revoked.

2. Check API key permissions:
   - Confirm the key has the necessary scopes for image generation.

3. Update your authentication method:
   - If using an old authentication method, update to the latest recommended approach.

## Game Engine Integration Challenges

### Problem: Sprites not rendering correctly in the game engine

1. Check image format compatibility:
   - Ensure your game engine supports the generated image format.
   - Convert sprites to a compatible format if necessary.
   ```javascript
   const sharp = require('sharp');
   await sharp(spriteBuffer).toFormat('png').toFile('sprite.png');
   ```

2. Verify sprite dimensions:
   - Confirm the sprite dimensions match your game engine's requirements.
   - Resize sprites if needed using the `sharp` library.

3. Implement proper sprite loading:
   - Use the correct method to load sprites in your game engine.
   - Ensure the file path is correct and accessible.

### Problem: Animation states not working as expected

1. Review the generated metadata:
   - Check the `frameData` in the returned metadata for correct animation information.

2. Adjust animation parameters:
   - Modify the `framesPerState` or `states` options to match your needs.
   ```javascript
   const options = {
     states: ['idle', 'walk', 'run', 'jump'],
     framesPerState: 8
   };
   const result = await generateCharacterSpritesheet(description, options);
   ```

3. Implement correct sprite sheet parsing:
   - Ensure your game engine is correctly interpreting the sprite sheet structure.
   - Use the metadata to inform your animation setup.

## Error Message Interpretation

### "Invalid API key provided"
- **Cause**: The API key is incorrect or not set properly.
- **Solution**: Double-check your API key and ensure it's correctly set in your environment variables or configuration file.

### "You exceeded your current quota, please check your plan and billing details"
- **Cause**: You've hit your API usage limit.
- **Solution**: Review your OpenAI account, upgrade your plan if necessary, or optimize your API usage.

### "Error: Input file is missing"
- **Cause**: The specified input file for background removal doesn't exist.
- **Solution**: Check the file path and ensure the file exists in the specified location.

### "Error: ENOENT: no such file or directory, open 'path/to/file'"
- **Cause**: The system cannot find the specified file or directory.
- **Solution**: Verify the file path, check for typos, and ensure the directory structure is correct.

### "Image processing error: TypeError: Cannot read property 'bitmap' of undefined"
- **Cause**: The image couldn't be loaded or processed by Jimp.
- **Solution**: Check the image file format and integrity. Try using a different image processing library like Sharp for better compatibility.

If you encounter any issues not covered in this guide, please refer to the API documentation or reach out to our support team for further assistance.