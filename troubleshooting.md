---
title: Troubleshooting Guide
description: Common issues and solutions for the SpriteAI library
---

# Troubleshooting Guide

This guide addresses common issues you might encounter when using the SpriteAI library and provides solutions to help you resolve them.

## Image Generation Issues

### Problem: Generated images are not in the expected style

If the generated images don't match the requested style (e.g., pixel art, vector, 3D), try the following:

1. Double-check the `style` parameter in your options object:

```javascript
const options = {
  style: 'pixel-art', // Make sure this matches your desired style
  // ... other options
};
```

2. Be more specific in your description, emphasizing the desired style:

```javascript
const description = "A pixel art warrior with a large sword and shield";
```

### Problem: Inconsistent character size across frames

If you notice that the character size varies between frames in a spritesheet:

1. Ensure you're using the latest version of the library.
2. Try adjusting the `framesPerState` option to a lower number:

```javascript
const options = {
  framesPerState: 4, // Reduced from the default 6
  // ... other options
};
```

3. If the issue persists, consider generating separate spritesheets for each animation state and combining them manually.

## Background Removal Issues

### Problem: Background not fully removed

If the `removeBackgroundColor` function isn't effectively removing the background:

1. Adjust the `colorThreshold` parameter:

```javascript
await removeBackgroundColor(
  inputPath,
  outputPath,
  '#FFFFFF', // Target color (white in this case)
  0.1 // Increase this value for more aggressive removal
);
```

2. Ensure the background color in your image closely matches the `targetColor` parameter.

3. If dealing with complex backgrounds, consider using a more advanced image processing library or service for background removal.

## API Usage Issues

### Problem: OpenAI API key not recognized

If you're encountering authentication errors:

1. Verify that you've set the OpenAI API key correctly:

```javascript
import OpenAI from "openai";

const openAiObject = new OpenAI({
  apiKey: process.env.OPENAI_API_KEY,
});
```

2. Ensure the environment variable is properly set in your development environment or deployment platform.

3. Check that your API key has the necessary permissions for image generation.

### Problem: Exceeding API rate limits

If you're hitting rate limits with the OpenAI API:

1. Implement proper error handling and retry logic:

```javascript
try {
  const response = await openAiObject.images.generate({
    // ... options
  });
} catch (error) {
  if (error.response && error.response.status === 429) {
    console.log("Rate limit exceeded. Retrying in 60 seconds...");
    await new Promise(resolve => setTimeout(resolve, 60000));
    // Retry the request
  } else {
    throw error;
  }
}
```

2. Consider implementing a queue system for large batch operations to manage API calls more effectively.

## File System Issues

### Problem: Unable to save generated images

If you're having trouble saving generated images:

1. Ensure you have write permissions for the target directory:

```javascript
const currentWorkingDirectory = process.cwd();
const assetsDir = path.join(currentWorkingDirectory, 'assets');

// Create assets directory if it doesn't exist
if (!fs.existsSync(assetsDir)) {
  fs.mkdirSync(assetsDir, { recursive: true });
}
```

2. Verify that the file path is constructed correctly for your operating system:

```javascript
const filename = path.join(assetsDir, `${description.replace(/\s+/g, '_')}_spritesheet.png`);
```

3. Handle potential file system errors:

```javascript
try {
  await sharp(spritesheet).toFile(filename);
} catch (error) {
  console.error("Error saving file:", error);
  // Implement appropriate error handling
}
```

## Performance Optimization

### Problem: Slow generation times for complex spritesheets

If generating large or complex spritesheets is taking too long:

1. Consider breaking down the generation process into smaller batches:

```javascript
const generateBatch = async (states, startIndex, batchSize) => {
  const batchStates = states.slice(startIndex, startIndex + batchSize);
  // Generate spritesheet for this batch
  // ...
};

const allStates = ['idle', 'walk', 'run', 'attack', 'jump', 'fall', 'hurt', 'die'];
const batchSize = 3;

for (let i = 0; i < allStates.length; i += batchSize) {
  await generateBatch(allStates, i, batchSize);
}
```

2. Implement caching mechanisms for frequently used sprites or elements.

3. If possible, use lower resolution settings for initial prototyping and increase resolution for final assets.

By following this troubleshooting guide, you should be able to resolve most common issues encountered when using the SpriteAI library. If you continue to experience problems, please check the library's GitHub repository for known issues or to report new ones.