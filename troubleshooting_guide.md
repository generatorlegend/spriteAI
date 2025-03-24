# Troubleshooting Guide for SpriteAI Library

This guide addresses common issues users might encounter when using the SpriteAI library, including problems with image generation, background removal, and SDK usage. Here you'll find solutions and workarounds for each issue.

## Table of Contents

1. [Image Generation Issues](#image-generation-issues)
2. [Background Removal Problems](#background-removal-problems)
3. [SDK Usage Difficulties](#sdk-usage-difficulties)
4. [Performance Concerns](#performance-concerns)

## Image Generation Issues

### DALL-E API Connection Errors

**Problem**: Unable to connect to the DALL-E API when generating images.

**Solution**:
1. Check your internet connection.
2. Verify that your OpenAI API key is correct and has the necessary permissions.
3. Ensure you're not exceeding API rate limits.

**Code example**:
```javascript
const openAiObject = new OpenAI({
  apiKey: 'your-api-key-here'
});
```

### Unexpected Image Results

**Problem**: Generated images don't match the provided description.

**Solution**:
1. Refine your prompt to be more specific and detailed.
2. Adjust the `style` parameter to better match your desired output.
3. Try breaking down complex requests into simpler components.

**Example**:
```javascript
const result = await generateCharacterSpritesheet("a fierce dragon", {
  style: "pixel-art",
  states: ["idle", "attack", "fly"],
  framesPerState: 8
});
```

## Background Removal Problems

### Incomplete Background Removal

**Problem**: Background color not fully removed from sprites.

**Solution**:
1. Adjust the `colorThreshold` parameter in the `removeBackgroundColor` function.
2. Ensure the `targetColor` matches the background color exactly.

**Code example**:
```javascript
await removeBackgroundColor(
  inputPath,
  outputPath,
  '#FFFFFF',  // Exact background color
  0.1  // Adjust this threshold as needed
);
```

### Unintended Transparency

**Problem**: Parts of the sprite become transparent unexpectedly.

**Solution**:
1. Decrease the `colorThreshold` to make the color matching more strict.
2. Use a more unique background color in the original image to avoid confusion with sprite colors.

## SDK Usage Difficulties

### Incorrect Function Parameters

**Problem**: Errors when calling SDK functions with incorrect parameters.

**Solution**:
1. Refer to the function documentation for correct parameter usage.
2. Use TypeScript or JSDoc for better type checking and autocompletion.

**Example**:
```javascript
// Correct usage
const spritesheet = await generateCharacterSpritesheet("a heroic knight", {
  states: ["idle", "walk", "attack"],
  framesPerState: 6,
  size: "1024x1024"
});

// Incorrect usage (will throw an error)
const spritesheet = await generateCharacterSpritesheet();
```

### Handling Asynchronous Operations

**Problem**: Difficulty managing asynchronous function calls.

**Solution**:
1. Use `async/await` syntax for cleaner asynchronous code.
2. Implement proper error handling with try/catch blocks.

**Example**:
```javascript
async function generateGameAssets() {
  try {
    const character = await generateCharacterSpritesheet("player character");
    const environment = await generateEnvironmentSprites("forest background");
    return { character, environment };
  } catch (error) {
    console.error("Asset generation failed:", error);
    throw error;
  }
}
```

## Performance Concerns

### Slow Image Generation

**Problem**: Image generation takes longer than expected.

**Solution**:
1. Optimize your prompts to be more concise and specific.
2. Consider caching frequently used sprites.
3. Implement a loading indicator in your application to improve user experience during generation.

### High Memory Usage

**Problem**: The application consumes a lot of memory when processing large spritesheets.

**Solution**:
1. Process images in smaller batches if possible.
2. Implement streaming for large file operations instead of loading entire files into memory.
3. Consider using worker threads for heavy image processing tasks in Node.js environments.

**Example of using worker threads**:
```javascript
const { Worker, isMainThread, parentPort } = require('worker_threads');

if (isMainThread) {
  const worker = new Worker(__filename);
  worker.on('message', (result) => {
    console.log('Processed spritesheet:', result);
  });
  worker.postMessage('Generate large spritesheet');
} else {
  parentPort.on('message', async (message) => {
    const result = await generateCharacterSpritesheet("large character set", {
      states: ["idle", "walk", "run", "jump", "attack"],
      framesPerState: 10,
      size: "2048x2048"
    });
    parentPort.postMessage(result);
  });
}
```

By following this troubleshooting guide, you should be able to resolve most common issues encountered when using the SpriteAI library. If you continue to experience problems, please reach out to our support team or consult the API documentation for more detailed information.