Here's the new documentation page content for troubleshooting.md:

<response>
---
title: Troubleshooting SpriteAI
description: A guide to common issues and solutions when using the SpriteAI library
---

# Troubleshooting SpriteAI

This guide addresses common issues you might encounter when using the SpriteAI library and provides solutions to help you resolve them quickly.

## Table of Contents

1. [Image Generation Issues](#image-generation-issues)
2. [API Usage Problems](#api-usage-problems)
3. [Integration Challenges](#integration-challenges)

## Image Generation Issues

### No Images Generated

**Problem**: The `generateCharacterSpritesheet` or `generateLandscapeSprite` function is not producing any images.

**Solution**:

1. Check your OpenAI API key:
   - Ensure you have set up your OpenAI API key correctly.
   - Verify that the API key has the necessary permissions for image generation.

2. Examine the prompt:
   - Make sure your description is clear and specific.
   - Avoid using terms that might violate content policies.

Example of a good prompt:

```javascript
const description = "A brave knight in shining armor";
const options = {
  style: 'pixel-art',
  states: ['idle', 'walk', 'attack']
};

const result = await generateCharacterSpritesheet(description, options);
```

### Poor Quality Images

**Problem**: The generated images are low quality or don't match the expected style.

**Solution**:

1. Adjust the `size` option:
   - Increase the size for higher resolution images (e.g., '1024x1024').

2. Refine the `style` option:
   - Be more specific with the style description (e.g., '16-bit pixel-art').

3. Iterate on the prompt:
   - Add more details to guide the AI in generating the desired outcome.

Example of improved options:

```javascript
const options = {
  size: '1024x1024',
  style: '16-bit pixel-art with vibrant colors',
  states: ['idle', 'walk', 'run', 'attack']
};
```

## API Usage Problems

### Rate Limiting

**Problem**: You're encountering rate limit errors when making multiple requests.

**Solution**:

1. Implement request throttling:
   - Add delays between requests to stay within rate limits.

2. Use a queue system:
   - Implement a queue to manage multiple requests over time.

Example of basic throttling:

```javascript
const delay = (ms) => new Promise(resolve => setTimeout(resolve, ms));

async function generateMultipleSprites(descriptions) {
  const results = [];
  for (const desc of descriptions) {
    const result = await generateCharacterSpritesheet(desc);
    results.push(result);
    await delay(1000); // Wait 1 second between requests
  }
  return results;
}
```

### Unexpected Errors

**Problem**: You're getting unexpected errors or exceptions when calling SpriteAI functions.

**Solution**:

1. Check for required dependencies:
   - Ensure all required packages (OpenAI, axios, sharp, Jimp) are installed.

2. Verify function parameters:
   - Double-check that you're passing the correct parameters to functions.

3. Implement error handling:
   - Wrap API calls in try-catch blocks to handle and log errors.

Example of error handling:

```javascript
try {
  const result = await generateCharacterSpritesheet(description, options);
  // Process the result
} catch (error) {
  console.error("Error generating spritesheet:", error.message);
  // Handle the error appropriately
}
```

## Integration Challenges

### Incorrect File Paths

**Problem**: Generated images are not being saved in the expected location.

**Solution**:

1. Use absolute paths:
   - Provide full file paths when saving images.

2. Check directory permissions:
   - Ensure your application has write permissions for the target directory.

Example of using absolute paths:

```javascript
const path = require('path');

const options = {
  save: true,
  outputPath: path.join(__dirname, 'assets', 'generated_sprites')
};

await generateCharacterSpritesheet(description, options);
```

### Incompatible Image Formats

**Problem**: Generated images are not compatible with your game engine or other tools.

**Solution**:

1. Convert images to the required format:
   - Use the `sharp` library to convert images to your needed format.

2. Adjust image parameters:
   - Modify color depth, compression, or other parameters as needed.

Example of image conversion:

```javascript
const sharp = require('sharp');

async function convertToGameFormat(inputBuffer) {
  return await sharp(inputBuffer)
    .png({ palette: true, quality: 100 })
    .toBuffer();
}

const result = await generateCharacterSpritesheet(description, options);
const gameReadyBuffer = await convertToGameFormat(result.spritesheet);
```

By following these troubleshooting steps, you should be able to resolve most common issues encountered when using the SpriteAI library. If you continue to experience problems, please check the GitHub repository for known issues or open a new issue with a detailed description of your problem.
</response>---
title: Troubleshooting SpriteAI
description: A guide to common issues and solutions when using the SpriteAI library
---

# Troubleshooting SpriteAI

This guide addresses common issues you might encounter when using the SpriteAI library and provides solutions to help you resolve them quickly.

## Table of Contents

1. [Image Generation Issues](#image-generation-issues)
2. [API Usage Problems](#api-usage-problems)
3. [Integration Challenges](#integration-challenges)

## Image Generation Issues

### No Images Generated

**Problem**: The `generateCharacterSpritesheet` or `generateLandscapeSprite` function is not producing any images.

**Solution**:

1. Check your OpenAI API key:
   - Ensure you have set up your OpenAI API key correctly.
   - Verify that the API key has the necessary permissions for image generation.

2. Examine the prompt:
   - Make sure your description is clear and specific.
   - Avoid using terms that might violate content policies.

Example of a good prompt:

```javascript
const description = "A brave knight in shining armor";
const options = {
  style: 'pixel-art',
  states: ['idle', 'walk', 'attack']
};

const result = await generateCharacterSpritesheet(description, options);
```

### Poor Quality Images

**Problem**: The generated images are low quality or don't match the expected style.

**Solution**:

1. Adjust the `size` option:
   - Increase the size for higher resolution images (e.g., '1024x1024').

2. Refine the `style` option:
   - Be more specific with the style description (e.g., '16-bit pixel-art').

3. Iterate on the prompt:
   - Add more details to guide the AI in generating the desired outcome.

Example of improved options:

```javascript
const options = {
  size: '1024x1024',
  style: '16-bit pixel-art with vibrant colors',
  states: ['idle', 'walk', 'run', 'attack']
};
```

## API Usage Problems

### Rate Limiting

**Problem**: You're encountering rate limit errors when making multiple requests.

**Solution**:

1. Implement request throttling:
   - Add delays between requests to stay within rate limits.

2. Use a queue system:
   - Implement a queue to manage multiple requests over time.

Example of basic throttling:

```javascript
const delay = (ms) => new Promise(resolve => setTimeout(resolve, ms));

async function generateMultipleSprites(descriptions) {
  const results = [];
  for (const desc of descriptions) {
    const result = await generateCharacterSpritesheet(desc);
    results.push(result);
    await delay(1000); // Wait 1 second between requests
  }
  return results;
}
```

### Unexpected Errors

**Problem**: You're getting unexpected errors or exceptions when calling SpriteAI functions.

**Solution**:

1. Check for required dependencies:
   - Ensure all required packages (OpenAI, axios, sharp, Jimp) are installed.

2. Verify function parameters:
   - Double-check that you're passing the correct parameters to functions.

3. Implement error handling:
   - Wrap API calls in try-catch blocks to handle and log errors.

Example of error handling:

```javascript
try {
  const result = await generateCharacterSpritesheet(description, options);
  // Process the result
} catch (error) {
  console.error("Error generating spritesheet:", error.message);
  // Handle the error appropriately
}
```

## Integration Challenges

### Incorrect File Paths

**Problem**: Generated images are not being saved in the expected location.

**Solution**:

1. Use absolute paths:
   - Provide full file paths when saving images.

2. Check directory permissions:
   - Ensure your application has write permissions for the target directory.

Example of using absolute paths:

```javascript
const path = require('path');

const options = {
  save: true,
  outputPath: path.join(__dirname, 'assets', 'generated_sprites')
};

await generateCharacterSpritesheet(description, options);
```

### Incompatible Image Formats

**Problem**: Generated images are not compatible with your game engine or other tools.

**Solution**:

1. Convert images to the required format:
   - Use the `sharp` library to convert images to your needed format.

2. Adjust image parameters:
   - Modify color depth, compression, or other parameters as needed.

Example of image conversion:

```javascript
const sharp = require('sharp');

async function convertToGameFormat(inputBuffer) {
  return await sharp(inputBuffer)
    .png({ palette: true, quality: 100 })
    .toBuffer();
}

const result = await generateCharacterSpritesheet(description, options);
const gameReadyBuffer = await convertToGameFormat(result.spritesheet);
```

By following these troubleshooting steps, you should be able to resolve most common issues encountered when using the SpriteAI library. If you continue to experience problems, please check the GitHub repository for known issues or open a new issue with a detailed description of your problem.