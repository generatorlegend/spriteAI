Here's the new documentation page content for troubleshooting.md:

<response>
---
title: Troubleshooting SpriteAI
description: A guide to common issues and solutions when using SpriteAI
---

# Troubleshooting SpriteAI

This guide addresses common issues you might encounter while using SpriteAI, along with step-by-step solutions and explanations.

## Table of Contents

1. [Error Messages](#error-messages)
   - [OpenAI API Error](#openai-api-error)
   - [File System Errors](#file-system-errors)
2. [Unexpected Results](#unexpected-results)
   - [Inconsistent Sprite Sizes](#inconsistent-sprite-sizes)
   - [Incorrect Animation States](#incorrect-animation-states)
3. [Performance Issues](#performance-issues)
   - [Slow Generation Times](#slow-generation-times)
4. [Image Processing Problems](#image-processing-problems)
   - [Background Removal Issues](#background-removal-issues)

## Error Messages

### OpenAI API Error

**Problem**: You receive an error related to the OpenAI API, such as authentication issues or rate limiting.

**Solution**:

1. Check your OpenAI API key:
   - Ensure you've set the `OPENAI_API_KEY` environment variable correctly.
   - Verify that your API key is valid and has not expired.

2. Handle rate limiting:
   - If you're hitting rate limits, implement exponential backoff in your requests.
   - Consider upgrading your OpenAI plan for higher rate limits.

Example of implementing exponential backoff:

```javascript
const exponentialBackoff = async (fn, maxRetries = 5) => {
  for (let i = 0; i < maxRetries; i++) {
    try {
      return await fn();
    } catch (error) {
      if (error.response && error.response.status === 429) {
        const delay = Math.pow(2, i) * 1000;
        await new Promise(resolve => setTimeout(resolve, delay));
      } else {
        throw error;
      }
    }
  }
  throw new Error('Max retries reached');
};

// Usage
const response = await exponentialBackoff(() => openAiObject.images.generate({
  model: "dall-e-3",
  prompt: prompt,
  size: size,
  n: 1
}));
```

### File System Errors

**Problem**: Errors occur when saving or reading files, such as "ENOENT: no such file or directory".

**Solution**:

1. Check file paths:
   - Ensure you're using the correct path separators for your operating system (`path.sep`).
   - Use `path.join()` for constructing file paths to ensure cross-platform compatibility.

2. Verify directory existence:
   - Before saving files, check if the directory exists and create it if necessary.

Example:

```javascript
import fs from 'fs';
import path from 'path';

const saveSprite = async (buffer, filename) => {
  const dir = path.join(process.cwd(), 'assets');
  if (!fs.existsSync(dir)) {
    fs.mkdirSync(dir, { recursive: true });
  }
  const filePath = path.join(dir, filename);
  await fs.promises.writeFile(filePath, buffer);
};
```

## Unexpected Results

### Inconsistent Sprite Sizes

**Problem**: Generated sprites have inconsistent sizes across different animation states.

**Solution**:

1. Adjust the prompt:
   - Emphasize the need for consistent character size in your DALL-E prompt.
   - Example: "Ensure the character maintains a consistent size across all animation frames."

2. Post-processing:
   - Implement a post-processing step to normalize sprite sizes.

Example of size normalization:

```javascript
import sharp from 'sharp';

const normalizeSpriteSizes = async (spritesheet, targetSize) => {
  const image = sharp(spritesheet);
  const metadata = await image.metadata();
  const { width, height } = metadata;

  const normalizedSpritesheet = await image
    .resize(width, height, {
      fit: 'contain',
      background: { r: 0, g: 0, b: 0, alpha: 0 }
    })
    .toBuffer();

  return normalizedSpritesheet;
};
```

### Incorrect Animation States

**Problem**: Generated spritesheets contain incorrect or missing animation states.

**Solution**:

1. Verify input parameters:
   - Double-check that you're passing the correct `states` array to `generateCharacterSpritesheet`.

2. Enhance prompt specificity:
   - Make your DALL-E prompt more explicit about required animation states.

3. Implement validation:
   - Add a validation step to ensure all requested states are present in the generated spritesheet.

Example validation function:

```javascript
const validateAnimationStates = (metadata, requestedStates) => {
  const missingStates = requestedStates.filter(state => !metadata.frameData[state]);
  if (missingStates.length > 0) {
    throw new Error(`Missing animation states: ${missingStates.join(', ')}`);
  }
};
```

## Performance Issues

### Slow Generation Times

**Problem**: Sprite generation is taking longer than expected.

**Solution**:

1. Optimize API calls:
   - Minimize the number of API calls by generating multiple sprites in a single request when possible.

2. Implement caching:
   - Cache generated sprites to avoid redundant API calls for identical requests.

3. Use smaller image sizes:
   - Start with smaller image sizes and scale up if necessary.

Example caching implementation:

```javascript
import NodeCache from 'node-cache';

const spriteCache = new NodeCache({ stdTTL: 3600 }); // Cache for 1 hour

export const generateCharacterSpritesheet = async function(description, options = {}) {
  const cacheKey = JSON.stringify({ description, options });
  const cachedResult = spriteCache.get(cacheKey);

  if (cachedResult) {
    return cachedResult;
  }

  // Existing sprite generation code...

  spriteCache.set(cacheKey, result);
  return result;
};
```

## Image Processing Problems

### Background Removal Issues

**Problem**: The `removeBackgroundColor` function is not effectively removing the background or is removing parts of the sprite.

**Solution**:

1. Adjust color threshold:
   - Experiment with different `colorThreshold` values to find the optimal balance.

2. Use advanced image processing:
   - Consider implementing more sophisticated background removal techniques, such as edge detection or machine learning-based segmentation.

3. Manual touchups:
   - Provide guidance on manual post-processing for complex cases.

Example of adjusting color threshold:

```javascript
const removeBackgroundWithThreshold = async (inputPath, outputPath, targetColor, colorThreshold = 0.1) => {
  await removeBackgroundColor(inputPath, outputPath, targetColor, colorThreshold);
  
  // Check result and adjust threshold if needed
  const result = await Jimp.read(outputPath);
  const transparentPixels = countTransparentPixels(result);
  
  if (transparentPixels / (result.bitmap.width * result.bitmap.height) < 0.1) {
    // If less than 10% of pixels are transparent, try a higher threshold
    return removeBackgroundWithThreshold(inputPath, outputPath, targetColor, colorThreshold + 0.05);
  }
  
  return result;
};

const countTransparentPixels = (image) => {
  let count = 0;
  image.scan(0, 0, image.bitmap.width, image.bitmap.height, (x, y, idx) => {
    if (image.bitmap.data[idx + 3] === 0) count++;
  });
  return count;
};
```

By following these troubleshooting steps, you should be able to resolve most common issues encountered when using SpriteAI. If you continue to experience problems, please reach out to our support team for further assistance.
</response>---
title: Troubleshooting SpriteAI
description: A guide to common issues and solutions when using SpriteAI
---

# Troubleshooting SpriteAI

This guide addresses common issues you might encounter while using SpriteAI, along with step-by-step solutions and explanations.

## Table of Contents

1. [Error Messages](#error-messages)
   - [OpenAI API Error](#openai-api-error)
   - [File System Errors](#file-system-errors)
2. [Unexpected Results](#unexpected-results)
   - [Inconsistent Sprite Sizes](#inconsistent-sprite-sizes)
   - [Incorrect Animation States](#incorrect-animation-states)
3. [Performance Issues](#performance-issues)
   - [Slow Generation Times](#slow-generation-times)
4. [Image Processing Problems](#image-processing-problems)
   - [Background Removal Issues](#background-removal-issues)

## Error Messages

### OpenAI API Error

**Problem**: You receive an error related to the OpenAI API, such as authentication issues or rate limiting.

**Solution**:

1. Check your OpenAI API key:
   - Ensure you've set the `OPENAI_API_KEY` environment variable correctly.
   - Verify that your API key is valid and has not expired.

2. Handle rate limiting:
   - If you're hitting rate limits, implement exponential backoff in your requests.
   - Consider upgrading your OpenAI plan for higher rate limits.

Example of implementing exponential backoff:

```javascript
const exponentialBackoff = async (fn, maxRetries = 5) => {
  for (let i = 0; i < maxRetries; i++) {
    try {
      return await fn();
    } catch (error) {
      if (error.response && error.response.status === 429) {
        const delay = Math.pow(2, i) * 1000;
        await new Promise(resolve => setTimeout(resolve, delay));
      } else {
        throw error;
      }
    }
  }
  throw new Error('Max retries reached');
};

// Usage
const response = await exponentialBackoff(() => openAiObject.images.generate({
  model: "dall-e-3",
  prompt: prompt,
  size: size,
  n: 1
}));
```

### File System Errors

**Problem**: Errors occur when saving or reading files, such as "ENOENT: no such file or directory".

**Solution**:

1. Check file paths:
   - Ensure you're using the correct path separators for your operating system (`path.sep`).
   - Use `path.join()` for constructing file paths to ensure cross-platform compatibility.

2. Verify directory existence:
   - Before saving files, check if the directory exists and create it if necessary.

Example:

```javascript
import fs from 'fs';
import path from 'path';

const saveSprite = async (buffer, filename) => {
  const dir = path.join(process.cwd(), 'assets');
  if (!fs.existsSync(dir)) {
    fs.mkdirSync(dir, { recursive: true });
  }
  const filePath = path.join(dir, filename);
  await fs.promises.writeFile(filePath, buffer);
};
```

## Unexpected Results

### Inconsistent Sprite Sizes

**Problem**: Generated sprites have inconsistent sizes across different animation states.

**Solution**:

1. Adjust the prompt:
   - Emphasize the need for consistent character size in your DALL-E prompt.
   - Example: "Ensure the character maintains a consistent size across all animation frames."

2. Post-processing:
   - Implement a post-processing step to normalize sprite sizes.

Example of size normalization:

```javascript
import sharp from 'sharp';

const normalizeSpriteSizes = async (spritesheet, targetSize) => {
  const image = sharp(spritesheet);
  const metadata = await image.metadata();
  const { width, height } = metadata;

  const normalizedSpritesheet = await image
    .resize(width, height, {
      fit: 'contain',
      background: { r: 0, g: 0, b: 0, alpha: 0 }
    })
    .toBuffer();

  return normalizedSpritesheet;
};
```

### Incorrect Animation States

**Problem**: Generated spritesheets contain incorrect or missing animation states.

**Solution**:

1. Verify input parameters:
   - Double-check that you're passing the correct `states` array to `generateCharacterSpritesheet`.

2. Enhance prompt specificity:
   - Make your DALL-E prompt more explicit about required animation states.

3. Implement validation:
   - Add a validation step to ensure all requested states are present in the generated spritesheet.

Example validation function:

```javascript
const validateAnimationStates = (metadata, requestedStates) => {
  const missingStates = requestedStates.filter(state => !metadata.frameData[state]);
  if (missingStates.length > 0) {
    throw new Error(`Missing animation states: ${missingStates.join(', ')}`);
  }
};
```

## Performance Issues

### Slow Generation Times

**Problem**: Sprite generation is taking longer than expected.

**Solution**:

1. Optimize API calls:
   - Minimize the number of API calls by generating multiple sprites in a single request when possible.

2. Implement caching:
   - Cache generated sprites to avoid redundant API calls for identical requests.

3. Use smaller image sizes:
   - Start with smaller image sizes and scale up if necessary.

Example caching implementation:

```javascript
import NodeCache from 'node-cache';

const spriteCache = new NodeCache({ stdTTL: 3600 }); // Cache for 1 hour

export const generateCharacterSpritesheet = async function(description, options = {}) {
  const cacheKey = JSON.stringify({ description, options });
  const cachedResult = spriteCache.get(cacheKey);

  if (cachedResult) {
    return cachedResult;
  }

  // Existing sprite generation code...

  spriteCache.set(cacheKey, result);
  return result;
};
```

## Image Processing Problems

### Background Removal Issues

**Problem**: The `removeBackgroundColor` function is not effectively removing the background or is removing parts of the sprite.

**Solution**:

1. Adjust color threshold:
   - Experiment with different `colorThreshold` values to find the optimal balance.

2. Use advanced image processing:
   - Consider implementing more sophisticated background removal techniques, such as edge detection or machine learning-based segmentation.

3. Manual touchups:
   - Provide guidance on manual post-processing for complex cases.

Example of adjusting color threshold:

```javascript
const removeBackgroundWithThreshold = async (inputPath, outputPath, targetColor, colorThreshold = 0.1) => {
  await removeBackgroundColor(inputPath, outputPath, targetColor, colorThreshold);
  
  // Check result and adjust threshold if needed
  const result = await Jimp.read(outputPath);
  const transparentPixels = countTransparentPixels(result);
  
  if (transparentPixels / (result.bitmap.width * result.bitmap.height) < 0.1) {
    // If less than 10% of pixels are transparent, try a higher threshold
    return removeBackgroundWithThreshold(inputPath, outputPath, targetColor, colorThreshold + 0.05);
  }
  
  return result;
};

const countTransparentPixels = (image) => {
  let count = 0;
  image.scan(0, 0, image.bitmap.width, image.bitmap.height, (x, y, idx) => {
    if (image.bitmap.data[idx + 3] === 0) count++;
  });
  return count;
};
```

By following these troubleshooting steps, you should be able to resolve most common issues encountered when using SpriteAI. If you continue to experience problems, please reach out to our support team for further assistance.