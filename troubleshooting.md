---
title: Troubleshooting Guide
description: Common issues and solutions when using SpriteAI
---

# Troubleshooting Guide

This guide covers common issues you might encounter when using SpriteAI and provides step-by-step solutions to help you resolve them. If you're experiencing problems with image generation, background removal, or API interactions, you'll find helpful information here.

## Table of Contents

1. [Image Generation Issues](#image-generation-issues)
2. [Background Removal Problems](#background-removal-problems)
3. [API Interaction Errors](#api-interaction-errors)
4. [Unexpected Results](#unexpected-results)

## Image Generation Issues

### Error: Unable to generate image

If you encounter an error stating that the image couldn't be generated, try the following steps:

1. Check your OpenAI API key to ensure it's valid and has the necessary permissions.
2. Verify that you have sufficient credits in your OpenAI account.
3. Make sure your prompt adheres to OpenAI's content policy.
4. Try simplifying your prompt or breaking it into smaller requests.

Example of a valid API key configuration:

```javascript
const openAiObject = new OpenAI({
  apiKey: 'your-api-key-here'
});
```

### Low-quality or inconsistent sprites

If the generated sprites are of low quality or inconsistent:

1. Ensure you're using the correct `size` parameter (e.g., '1024x1024' for higher resolution).
2. Be more specific in your description, including details about style and character features.
3. Experiment with different `style` options, such as 'pixel-art' or 'vector'.

Example of generating a high-quality character spritesheet:

```javascript
const result = await generateCharacterSpritesheet("A medieval knight in full armor", {
  size: '1024x1024',
  style: 'pixel-art',
  states: ['idle', 'walk', 'attack'],
  framesPerState: 8
});
```

## Background Removal Problems

### Incomplete background removal

If the background isn't being removed completely:

1. Adjust the `colorThreshold` parameter to be more lenient.
2. Ensure the `backgroundColor` parameter matches the actual background color of your image.
3. For complex backgrounds, consider using a more advanced image processing library or service.

Example of background removal with adjusted parameters:

```javascript
await removeBackgroundColor(
  'input.png',
  'output.png',
  '#FFFFFF',
  0.2  // Increased color threshold
);
```

### Unintended transparency in sprites

If parts of your sprites are becoming transparent unintentionally:

1. Decrease the `colorThreshold` to be more strict about color matching.
2. Use a more specific `backgroundColor` that closely matches the background without affecting the sprite.

## API Interaction Errors

### Rate limiting errors

If you're encountering rate limiting errors:

1. Implement proper error handling and retry logic in your code.
2. Consider using a queueing system for large batch operations.
3. Check your OpenAI plan and consider upgrading if you need higher rate limits.

Example of error handling for rate limiting:

```javascript
try {
  const response = await openAiObject.images.generate({
    // ... parameters ...
  });
} catch (error) {
  if (error.response && error.response.status === 429) {
    console.log('Rate limit reached. Retrying after a delay...');
    // Implement retry logic here
  } else {
    console.error('An error occurred:', error);
  }
}
```

### Network-related issues

For network-related problems:

1. Check your internet connection.
2. Verify that you can reach the OpenAI API endpoints.
3. Implement proper timeout handling in your requests.

## Unexpected Results

### Misaligned or incorrect animation frames

If your animation frames are misaligned or incorrect:

1. Double-check the `states` and `framesPerState` parameters in your `generateCharacterSpritesheet` call.
2. Verify that the generated spritesheet matches the expected layout.
3. Use the `metadata` returned by the function to correctly interpret the spritesheet.

Example of using metadata to interpret the spritesheet:

```javascript
const result = await generateCharacterSpritesheet("A running cat", {
  states: ['idle', 'run'],
  framesPerState: 4
});

console.log(result.metadata.frameData);
// This will show you the exact layout of frames in the spritesheet
```

### Unexpected environment elements

If your environment sprites contain unexpected elements:

1. Be more specific in your `description` when calling `generateEnvironmentSprites`.
2. Adjust the `elements` parameter to control the number of distinct environment pieces.
3. Use the `theme` parameter to better guide the style and type of elements generated.

Example of generating specific environment sprites:

```javascript
const result = await generateEnvironmentSprites("Forest with ancient ruins", {
  elements: 6,
  theme: 'fantasy',
  style: 'pixel-art'
});
```

By following this troubleshooting guide, you should be able to resolve most common issues encountered when using SpriteAI. If you continue to experience problems, please reach out to our support team or consult the API documentation for more detailed information.