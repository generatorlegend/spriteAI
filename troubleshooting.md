# Troubleshooting Guide for SpriteAI

This guide addresses common issues that users might encounter when using SpriteAI, including problems related to image generation, background removal, API interactions, and integration into game development workflows. Follow the solutions and workarounds provided to resolve these issues.

## Image Generation Issues

### 1. Low-Quality or Unexpected Results

**Problem**: The generated sprites or landscapes don't meet your quality expectations or deviate significantly from the description.

**Solution**:
- Refine your prompt by being more specific and detailed in your description.
- Experiment with different style options (e.g., 'pixel-art', 'vector', '3d', 'hand-drawn', 'anime').
- Adjust the `size` parameter to generate larger images for more detail.

Example:
```javascript
const result = await generateCharacterSpritesheet("A tall, muscular warrior with golden armor and a large sword", {
  style: "pixel-art",
  size: "1024x1024"
});
```

### 2. Missing Animation States

**Problem**: Some expected animation states are missing from the generated spritesheet.

**Solution**:
- Explicitly specify the desired states in the `states` option.
- Check the available animation states using the `fetchAvailableAnimationStates` function.

Example:
```javascript
const availableStates = await fetchAvailableAnimationStates();
console.log("Available states:", availableStates);

const result = await generateCharacterSpritesheet("A nimble elf archer", {
  states: ['idle', 'walk', 'run', 'attack', 'jump']
});
```

## Background Removal Issues

### 1. Inconsistent Background Removal

**Problem**: The background removal process leaves artifacts or removes parts of the sprite.

**Solution**:
- Adjust the `colorThreshold` parameter in the `removeBackgroundColor` function.
- Ensure the background color in the original image is consistent.

Example:
```javascript
await removeBackgroundColor(
  inputPath, 
  outputPath, 
  '#FFFFFF', // Target color (white)
  0.1 // Adjust this threshold value
);
```

### 2. Unexpected Transparency in Sprites

**Problem**: Parts of the sprite become transparent when they shouldn't.

**Solution**:
- Check if the sprite's colors are too similar to the background color.
- Increase the `colorThreshold` slightly to preserve more of the original image.

## API Interaction Issues

### 1. API Rate Limiting

**Problem**: You encounter rate limiting errors when making multiple requests.

**Solution**:
- Implement a delay between API calls using a sleep function.
- Consider batching requests or using a queue system for large-scale sprite generation.

Example:
```javascript
const sleep = (ms) => new Promise(resolve => setTimeout(resolve, ms));

async function generateMultipleSprites(descriptions) {
  for (const desc of descriptions) {
    await generateCharacterSpritesheet(desc);
    await sleep(1000); // Wait 1 second between requests
  }
}
```

### 2. Authentication Errors

**Problem**: You're encountering authentication errors when trying to use SpriteAI.

**Solution**:
- Ensure your OpenAI API key is correctly set in your environment variables.
- Check that your API key has the necessary permissions for image generation.

## Integration into Game Development Workflows

### 1. Incorrect Sprite Dimensions

**Problem**: The generated sprites don't fit your game's required dimensions.

**Solution**:
- Use the `size` option to specify the exact dimensions you need.
- Implement a post-processing step to resize or crop the sprites as needed.

Example:
```javascript
const result = await generateCharacterSpritesheet("A small goblin", {
  size: "512x512" // Adjust to your game's required size
});

// Post-processing example (using sharp)
const processedSprite = await sharp(Buffer.from(result.spritesheet.split(',')[1], 'base64'))
  .resize(256, 256)
  .toBuffer();
```

### 2. Inconsistent Style Across Multiple Generations

**Problem**: Sprites generated in separate calls have inconsistent styles.

**Solution**:
- Always specify the `style` option explicitly in your function calls.
- Consider generating related sprites in a single batch when possible.

Example:
```javascript
const characterTypes = ['warrior', 'mage', 'archer'];
const sprites = await Promise.all(characterTypes.map(type => 
  generateCharacterSpritesheet(`A ${type} character`, {
    style: 'pixel-art', // Consistent style across all generations
    size: '1024x1024'
  })
));
```

## General Troubleshooting Tips

1. **Check Your Inputs**: Always verify that your function inputs (descriptions, options) are correct and properly formatted.

2. **Logging and Debugging**: Use console.log statements to track the progress of your sprite generation and identify where issues occur.

3. **Update Dependencies**: Ensure you're using the latest version of SpriteAI and its dependencies.

4. **Error Handling**: Implement proper error handling in your code to catch and log any issues that may arise during sprite generation.

Example:
```javascript
try {
  const result = await generateCharacterSpritesheet("A character description");
  console.log("Sprite generated successfully:", result.metadata);
} catch (error) {
  console.error("Error generating sprite:", error.message);
}
```

5. **Community Support**: If you encounter persistent issues, reach out to the SpriteAI community or support channels for assistance.

By following this troubleshooting guide, you should be able to resolve most common issues encountered when using SpriteAI. Remember to always refer to the latest documentation and keep your environment up-to-date for the best experience.