<response>

# Troubleshooting Guide for SpriteAI

This guide addresses common issues you might encounter when using SpriteAI, along with potential solutions and workarounds.

## Table of Contents
1. [Image Generation Failures](#image-generation-failures)
2. [Unexpected Results](#unexpected-results)
3. [Integration Problems](#integration-problems)
4. [Performance Issues](#performance-issues)

## Image Generation Failures

### API Key Issues
**Problem**: The API returns an authentication error.
**Solution**: 
- Ensure you've set up your OpenAI API key correctly.
- Check if your API key has expired or has been revoked.
- Verify that you're using the correct API key for the environment (development/production).

### Network Errors
**Problem**: The API call fails due to network issues.
**Solution**:
- Check your internet connection.
- Verify that you can access the OpenAI API from your current network.
- Implement retry logic for transient network issues:

```javascript
const MAX_RETRIES = 3;
const RETRY_DELAY = 1000; // 1 second

async function apiCallWithRetry(apiFunction, ...args) {
  for (let i = 0; i < MAX_RETRIES; i++) {
    try {
      return await apiFunction(...args);
    } catch (error) {
      if (i === MAX_RETRIES - 1) throw error;
      await new Promise(resolve => setTimeout(resolve, RETRY_DELAY));
    }
  }
}

// Usage
const result = await apiCallWithRetry(openAiObject.images.generate, {
  model: "dall-e-3",
  prompt: prompt,
  size: size,
  n: 1
});
```

## Unexpected Results

### Inconsistent Character Sizes
**Problem**: Generated character sprites have inconsistent sizes across frames.
**Solution**:
- Adjust the prompt to emphasize consistent character size.
- Post-process the generated images to normalize character sizes.

### Incorrect Animation States
**Problem**: The generated spritesheet doesn't match the requested animation states.
**Solution**:
- Double-check that you're using valid animation states from `fetchAvailableAnimationStates()`.
- Ensure the `states` array in your options matches the desired animations.
- If the issue persists, try simplifying your description or reducing the number of states.

## Integration Problems

### Module Import Issues
**Problem**: Unable to import SpriteAI functions.
**Solution**:
- Verify that you've installed the SpriteAI package correctly.
- Ensure you're using the correct import syntax:

```javascript
import { generateCharacterSpritesheet, generateEnvironmentSprites } from 'spriteai';
```

### File Saving Errors
**Problem**: Generated images fail to save.
**Solution**:
- Check if the `assets` directory exists in your project root.
- Ensure your application has write permissions for the target directory.
- Use a try-catch block to handle potential file system errors:

```javascript
try {
  const result = await generateCharacterSpritesheet('wizard', { save: true });
  console.log('Spritesheet saved successfully');
} catch (error) {
  console.error('Failed to save spritesheet:', error);
}
```

## Performance Issues

### Slow Generation Times
**Problem**: Image generation takes too long.
**Solution**:
- Consider using smaller image sizes for faster generation.
- Implement caching for frequently used sprites.
- Use a loading indicator in your UI to improve user experience during generation.

### High Memory Usage
**Problem**: The application consumes excessive memory when generating multiple sprites.
**Solution**:
- Implement a queue system for batch sprite generation to limit concurrent API calls.
- Dispose of large objects (like image buffers) after use.
- Consider using streams for large file operations instead of loading entire files into memory.

Remember, if you encounter persistent issues not covered in this guide, please refer to the OpenAI API documentation or reach out to our support team for further assistance.

</response>