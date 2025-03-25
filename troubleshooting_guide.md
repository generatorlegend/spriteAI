# Troubleshooting Guide for SpriteAI Library

This guide addresses common issues users might encounter when using the SpriteAI library. We'll cover installation problems, API usage errors, and image processing challenges, providing step-by-step solutions and explanations for each issue.

## Table of Contents

1. [Installation Problems](#installation-problems)
2. [API Usage Errors](#api-usage-errors)
3. [Image Processing Challenges](#image-processing-challenges)

## Installation Problems

### Issue: Unable to install the SpriteAI library

If you're having trouble installing the SpriteAI library, try the following steps:

1. Ensure you have the latest version of Node.js installed.
2. Clear your npm cache:
   ```
   npm cache clean --force
   ```
3. Try installing the library again:
   ```
   npm install spriteai
   ```

If the issue persists, check your network connection and firewall settings.

## API Usage Errors

### Issue: Invalid API Key

If you receive an error related to an invalid API key, follow these steps:

1. Double-check that you've set the correct API key in your environment variables or configuration file.
2. Ensure the API key has the necessary permissions for the operations you're trying to perform.
3. If using environment variables, make sure they're properly loaded in your application.

Example of setting the API key:

```javascript
import OpenAI from "openai";

const openAiObject = new OpenAI({
  apiKey: process.env.OPENAI_API_KEY
});
```

### Issue: Incorrect Function Parameters

If you're encountering errors related to function parameters, review the following:

1. Check the function signature in the documentation.
2. Ensure all required parameters are provided.
3. Verify that the parameter types match the expected types.

Example of correct usage for `generateCharacterSpritesheet`:

```javascript
const result = await generateCharacterSpritesheet("A medieval knight", {
  states: ['idle', 'walk', 'attack'],
  framesPerState: 4,
  size: '1024x1024',
  style: 'pixel-art'
});
```

## Image Processing Challenges

### Issue: White Background Not Removed

If the white background is not being removed as expected in the `removeBackgroundColor` function:

1. Ensure you're passing the correct color value for the background:

   ```javascript
   await removeBackgroundColor(
     inputPath,
     outputPath,
     '#FFFFFF', // White color
     0.1 // Color threshold
   );
   ```

2. Adjust the `colorThreshold` parameter. A higher value will be more lenient in color matching:

   ```javascript
   await removeBackgroundColor(
     inputPath,
     outputPath,
     '#FFFFFF',
     0.2 // Increased threshold for more lenient color matching
   );
   ```

3. If the issue persists, check the input image format and ensure it's compatible with the Jimp library.

### Issue: Incorrect Sprite Dimensions

If the generated sprite dimensions are incorrect:

1. Verify that you're providing the correct `size` option in the `generateCharacterSpritesheet` or `generateLandscapeSprite` functions:

   ```javascript
   const result = await generateCharacterSpritesheet("A medieval knight", {
     size: '1024x1024' // Ensure this matches your desired output size
   });
   ```

2. Check that the number of states and frames per state are correctly set, as these affect the final spritesheet layout:

   ```javascript
   const result = await generateCharacterSpritesheet("A medieval knight", {
     states: ['idle', 'walk', 'run', 'attack'],
     framesPerState: 6
   });
   ```

3. If using custom image processing, ensure that any resizing or cropping operations are correctly implemented.

## Additional Troubleshooting Tips

- Always check the console for detailed error messages, which can provide insights into the root cause of issues.
- Keep your SpriteAI library and dependencies up to date to benefit from the latest bug fixes and improvements.
- If you encounter persistent issues, review the test files (`removeBackground.test.js` and `sprite.test.js`) for examples of correct usage and expected behavior.

If you continue to experience problems after trying these solutions, please open an issue on the SpriteAI GitHub repository with a detailed description of the problem and steps to reproduce it.