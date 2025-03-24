Here's the new documentation page content for the troubleshooting guide:

<response>
# Troubleshooting Guide for SpriteAI

This guide addresses common issues that users might encounter when using the SpriteAI library. It covers problems related to image generation, background removal, API usage, and integration with game engines. For each issue, we provide solutions and workarounds.

## Image Generation Issues

### 1. Low-quality or Inconsistent Sprites

**Problem**: Generated sprites have low quality or inconsistent styles across frames.

**Solution**:
- Ensure your prompt is detailed and specific about the desired style and consistency.
- Try adjusting the `style` parameter in the options (e.g., 'pixel-art', 'vector', '3d', 'hand-drawn', 'anime').
- Experiment with different `size` settings to get higher resolution outputs.

Example:
```javascript
const result = await generateCharacterSpritesheet('medieval knight', {
  style: 'pixel-art',
  size: '1024x1024',
  framesPerState: 8 // Increase frames for smoother animations
});
```

### 2. Missing Animation States

**Problem**: Some expected animation states are missing from the generated spritesheet.

**Solution**:
- Explicitly specify all desired states in the `states` option.
- Use the `fetchAvailableAnimationStates()` function to see all supported states.

Example:
```javascript
const availableStates = await fetchAvailableAnimationStates();
const result = await generateCharacterSpritesheet('elf archer', {
  states: ['idle', 'walk', 'run', 'attack', 'jump'] // Specify all needed states
});
```

## Background Removal Issues

### 1. Incomplete Background Removal

**Problem**: The background is not fully removed, leaving artifacts around the sprite.

**Solution**:
- Adjust the `colorThreshold` parameter when using `removeBackgroundColor()`.
- Ensure the background color in the original image is consistent.

Example:
```javascript
await removeBackgroundColor(
  inputPath,
  outputPath,
  '#FFFFFF', // Target background color
  0.1 // Increase threshold for more aggressive removal
);
```

### 2. Unintended Transparency in Sprites

**Problem**: Parts of the sprite become transparent during background removal.

**Solution**:
- Decrease the `colorThreshold` to be more conservative in color matching.
- If possible, generate sprites with a background color that contrasts more with the sprite.

## API Usage Issues

### 1. API Rate Limiting

**Problem**: Encountering rate limit errors when making multiple requests.

**Solution**:
- Implement proper error handling and retry logic with exponential backoff.
- Consider batching requests or using a queue system for large-scale sprite generation.

Example error handling:
```javascript
const generateWithRetry = async (description, options, maxRetries = 3) => {
  for (let i = 0; i < maxRetries; i++) {
    try {
      return await generateCharacterSpritesheet(description, options);
    } catch (error) {
      if (error.response && error.response.status === 429) {
        // Rate limited, wait before retrying
        await new Promise(resolve => setTimeout(resolve, 1000 * Math.pow(2, i)));
      } else {
        throw error; // Rethrow if it's not a rate limit error
      }
    }
  }
  throw new Error('Max retries reached');
};
```

### 2. Unexpected API Responses

**Problem**: Receiving unexpected or error responses from the API.

**Solution**:
- Ensure you're using the latest version of the SpriteAI library.
- Check your API key and authentication setup.
- Verify that your requests are properly formatted.

## Game Engine Integration Issues

### 1. Incorrect Sprite Dimensions

**Problem**: Sprites don't fit correctly in your game engine's rendering system.

**Solution**:
- Use the metadata returned by the generation functions to properly size and position sprites.
- Adjust the `size` option when generating sprites to match your game's requirements.

Example of using metadata:
```javascript
const result = await generateCharacterSpritesheet('warrior');
const { width, height } = result.metadata.dimensions;
// Use width and height to set up your game sprite
```

### 2. Animation Timing Issues

**Problem**: Animations don't play smoothly or are out of sync.

**Solution**:
- Use the `frameData` from the metadata to set up your animation frames correctly.
- Adjust the `framesPerState` option to get smoother or more detailed animations.

Example:
```javascript
const result = await generateCharacterSpritesheet('mage', {
  framesPerState: 8 // Increase for smoother animations
});

// Set up animations using frameData
Object.entries(result.metadata.frameData).forEach(([state, data]) => {
  setUpAnimation(state, data.startFrame, data.endFrame);
});
```

## General Troubleshooting Tips

1. **Check Console Logs**: Always monitor your console for any error messages or warnings that might provide clues to issues.

2. **Update Dependencies**: Ensure you're using the latest version of SpriteAI and its dependencies.

3. **Validate Input Data**: Double-check that all input parameters (descriptions, options) are correctly formatted and contain valid values.

4. **Test with Simplified Requests**: If encountering issues, try simplifying your requests (e.g., fewer states, simpler descriptions) to isolate the problem.

5. **Review Examples**: Refer to the example usage in the documentation to ensure you're using the library as intended.

If you continue to experience issues after trying these solutions, please open an issue on our GitHub repository with a detailed description of the problem, including any error messages and a minimal reproducible example.
</response># Troubleshooting Guide for SpriteAI

This guide addresses common issues that users might encounter when using the SpriteAI library. It covers problems related to image generation, background removal, API usage, and integration with game engines. For each issue, we provide solutions and workarounds.

## Image Generation Issues

### 1. Low-quality or Inconsistent Sprites

**Problem**: Generated sprites have low quality or inconsistent styles across frames.

**Solution**:
- Ensure your prompt is detailed and specific about the desired style and consistency.
- Try adjusting the `style` parameter in the options (e.g., 'pixel-art', 'vector', '3d', 'hand-drawn', 'anime').
- Experiment with different `size` settings to get higher resolution outputs.

Example:
```javascript
const result = await generateCharacterSpritesheet('medieval knight', {
  style: 'pixel-art',
  size: '1024x1024',
  framesPerState: 8 // Increase frames for smoother animations
});
```

### 2. Missing Animation States

**Problem**: Some expected animation states are missing from the generated spritesheet.

**Solution**:
- Explicitly specify all desired states in the `states` option.
- Use the `fetchAvailableAnimationStates()` function to see all supported states.

Example:
```javascript
const availableStates = await fetchAvailableAnimationStates();
const result = await generateCharacterSpritesheet('elf archer', {
  states: ['idle', 'walk', 'run', 'attack', 'jump'] // Specify all needed states
});
```

## Background Removal Issues

### 1. Incomplete Background Removal

**Problem**: The background is not fully removed, leaving artifacts around the sprite.

**Solution**:
- Adjust the `colorThreshold` parameter when using `removeBackgroundColor()`.
- Ensure the background color in the original image is consistent.

Example:
```javascript
await removeBackgroundColor(
  inputPath,
  outputPath,
  '#FFFFFF', // Target background color
  0.1 // Increase threshold for more aggressive removal
);
```

### 2. Unintended Transparency in Sprites

**Problem**: Parts of the sprite become transparent during background removal.

**Solution**:
- Decrease the `colorThreshold` to be more conservative in color matching.
- If possible, generate sprites with a background color that contrasts more with the sprite.

## API Usage Issues

### 1. API Rate Limiting

**Problem**: Encountering rate limit errors when making multiple requests.

**Solution**:
- Implement proper error handling and retry logic with exponential backoff.
- Consider batching requests or using a queue system for large-scale sprite generation.

Example error handling:
```javascript
const generateWithRetry = async (description, options, maxRetries = 3) => {
  for (let i = 0; i < maxRetries; i++) {
    try {
      return await generateCharacterSpritesheet(description, options);
    } catch (error) {
      if (error.response && error.response.status === 429) {
        // Rate limited, wait before retrying
        await new Promise(resolve => setTimeout(resolve, 1000 * Math.pow(2, i)));
      } else {
        throw error; // Rethrow if it's not a rate limit error
      }
    }
  }
  throw new Error('Max retries reached');
};
```

### 2. Unexpected API Responses

**Problem**: Receiving unexpected or error responses from the API.

**Solution**:
- Ensure you're using the latest version of the SpriteAI library.
- Check your API key and authentication setup.
- Verify that your requests are properly formatted.

## Game Engine Integration Issues

### 1. Incorrect Sprite Dimensions

**Problem**: Sprites don't fit correctly in your game engine's rendering system.

**Solution**:
- Use the metadata returned by the generation functions to properly size and position sprites.
- Adjust the `size` option when generating sprites to match your game's requirements.

Example of using metadata:
```javascript
const result = await generateCharacterSpritesheet('warrior');
const { width, height } = result.metadata.dimensions;
// Use width and height to set up your game sprite
```

### 2. Animation Timing Issues

**Problem**: Animations don't play smoothly or are out of sync.

**Solution**:
- Use the `frameData` from the metadata to set up your animation frames correctly.
- Adjust the `framesPerState` option to get smoother or more detailed animations.

Example:
```javascript
const result = await generateCharacterSpritesheet('mage', {
  framesPerState: 8 // Increase for smoother animations
});

// Set up animations using frameData
Object.entries(result.metadata.frameData).forEach(([state, data]) => {
  setUpAnimation(state, data.startFrame, data.endFrame);
});
```

## General Troubleshooting Tips

1. **Check Console Logs**: Always monitor your console for any error messages or warnings that might provide clues to issues.

2. **Update Dependencies**: Ensure you're using the latest version of SpriteAI and its dependencies.

3. **Validate Input Data**: Double-check that all input parameters (descriptions, options) are correctly formatted and contain valid values.

4. **Test with Simplified Requests**: If encountering issues, try simplifying your requests (e.g., fewer states, simpler descriptions) to isolate the problem.

5. **Review Examples**: Refer to the example usage in the documentation to ensure you're using the library as intended.

If you continue to experience issues after trying these solutions, please open an issue on our GitHub repository with a detailed description of the problem, including any error messages and a minimal reproducible example.