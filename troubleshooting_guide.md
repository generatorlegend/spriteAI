# Troubleshooting Guide for SpriteAI

This guide addresses common issues you might encounter when using the SpriteAI library and provides solutions for problems related to image generation, background removal, and API interactions. It also includes debug tips and explains how to interpret error messages.

## Table of Contents
1. [Image Generation Issues](#image-generation-issues)
2. [Background Removal Problems](#background-removal-problems)
3. [API Interaction Errors](#api-interaction-errors)
4. [Debug Tips](#debug-tips)
5. [Interpreting Error Messages](#interpreting-error-messages)

## Image Generation Issues

### Problem: Generated images are not in the expected style
If the generated images don't match the requested style (e.g., pixel-art, vector, 3D), try the following:

1. Double-check the `style` parameter in your function call:

```javascript
const result = await generateCharacterSpritesheet(description, {
  style: 'pixel-art', // Make sure this matches your desired style
  // ... other options
});
```

2. Ensure that the `description` provided is clear and specific about the desired style.

3. If the issue persists, try using different style keywords or elaborating on the style in the description.

### Problem: Inconsistent character size across frames
If you notice that the character size varies across different frames:

1. Emphasize consistency in your description, e.g., "Ensure consistent character size across all frames."

2. Adjust the `framesPerState` option to a lower number, which may help maintain consistency:

```javascript
const result = await generateCharacterSpritesheet(description, {
  framesPerState: 4, // Try a lower number
  // ... other options
});
```

## Background Removal Problems

### Problem: Background is not fully removed
If the background is not completely removed when using the `removeBackgroundColor` function:

1. Adjust the `colorThreshold` parameter to be more lenient:

```javascript
await removeBackgroundColor(
  inputPath,
  outputPath,
  '#FFFFFF', // Target color (white in this case)
  0.2 // Increase this value for more lenient color matching
);
```

2. Ensure that the `targetColor` parameter matches the background color of your image exactly.

3. If the background has slight variations, you may need to process the image multiple times with different target colors.

## API Interaction Errors

### Problem: OpenAI API key not recognized
If you encounter an error related to the OpenAI API key:

1. Make sure you have set the `OPENAI_API_KEY` environment variable correctly.

2. Verify that your API key is valid and has not expired.

3. Check if you have the necessary permissions and quota for image generation.

### Problem: Exceeded rate limits
If you're hitting rate limits with the OpenAI API:

1. Implement exponential backoff and retry logic in your code:

```javascript
const axios = require('axios');
const axiosRetry = require('axios-retry');

axiosRetry(axios, {
  retries: 3,
  retryDelay: axiosRetry.exponentialDelay,
  retryCondition: (error) => {
    return error.response.status === 429;
  },
});
```

2. Consider upgrading your API plan if you frequently hit rate limits.

## Debug Tips

1. Enable verbose logging:
   Add console.log statements at key points in your code to track the flow and identify where issues occur.

2. Use try-catch blocks:
   Wrap API calls and image processing functions in try-catch blocks to catch and log specific errors:

```javascript
try {
  const result = await generateCharacterSpritesheet(description, options);
  console.log('Spritesheet generated successfully:', result);
} catch (error) {
  console.error('Error generating spritesheet:', error);
}
```

3. Check intermediate results:
   For functions like `removeBackgroundColor`, save intermediate images to disk for inspection:

```javascript
await sharp(intermediateBuffer).toFile('debug_intermediate.png');
```

## Interpreting Error Messages

Common error messages and their meanings:

1. "Invalid API key": Your OpenAI API key is not set correctly or has expired.
2. "Quota exceeded": You have reached your usage limit for the OpenAI API.
3. "Content policy violation": The generated image content violates OpenAI's content policy.
4. "ENOENT: no such file or directory": The specified input or output file path is incorrect.
5. "Unable to read input image": The input image file is corrupted or in an unsupported format.

When encountering these errors, review the corresponding section of this troubleshooting guide for potential solutions. If the issue persists, consult the OpenAI API documentation or reach out to their support team for further assistance.

Remember to always keep your SpriteAI library and dependencies up to date, as newer versions may include bug fixes and performance improvements that could resolve some issues automatically.