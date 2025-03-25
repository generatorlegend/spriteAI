# SpriteAI SDK Usage Guide

## Introduction

The SpriteAI SDK provides powerful tools for generating game assets programmatically. This guide will walk you through the main functions of the SDK and how to integrate them into your game development workflow.

## Installation

To use the SpriteAI SDK, first install it via npm:

```bash
npm install spriteai-sdk
```

Then, import the necessary functions in your project:

```javascript
import { 
  generateCharacterSpritesheet, 
  fetchAvailableAnimationStates, 
  fetchAvailableSpriteStyles, 
  generateEnvironmentSprites 
} from 'spriteai-sdk';
```

## Generating Character Spritesheets

The `generateCharacterSpritesheet` function allows you to create character spritesheets based on a description. Here's how to use it:

```javascript
const characterDescription = "A brave knight in shining armor";
const options = {
  states: ['idle', 'walk', 'run', 'attack'],
  framesPerState: 6,
  size: '1024x1024',
  style: 'pixel-art',
  direction: 'right'
};

const result = await generateCharacterSpritesheet(characterDescription, options);

console.log(result.spritesheet); // Base64 encoded spritesheet
console.log(result.metadata); // Metadata about the generated spritesheet
```

### Options

- `states`: Array of animation states (default: ['idle', 'walk', 'run', 'attack'])
- `framesPerState`: Number of frames per animation state (default: 6)
- `size`: Size of the output image (default: '1024x1024')
- `style`: Art style of the spritesheet (default: 'pixel-art')
- `padding`: Padding between frames (default: 1)
- `direction`: Direction the character faces (default: 'right')

## Fetching Available Animation States

To get a list of available animation states:

```javascript
const states = await fetchAvailableAnimationStates();
console.log(states); // ['idle', 'walk', 'run', 'attack', 'jump', 'fall', 'hurt', 'die']
```

## Fetching Available Sprite Styles

To get a list of available sprite styles:

```javascript
const styles = await fetchAvailableSpriteStyles();
console.log(styles); // ['pixel-art', 'vector', '3d', 'hand-drawn', 'anime']
```

## Generating Environment Sprites

The `generateEnvironmentSprites` function creates environmental assets for your game:

```javascript
const environmentDescription = "A lush forest with ancient ruins";
const options = {
  elements: 4,
  size: '1024x1024',
  style: 'pixel-art',
  theme: 'fantasy'
};

const result = await generateEnvironmentSprites(environmentDescription, options);

console.log(result.tileset); // Base64 encoded tileset
console.log(result.metadata); // Metadata about the generated tileset
```

### Options

- `elements`: Number of distinct environment pieces (default: 4)
- `size`: Size of the output image (default: '1024x1024')
- `style`: Art style of the tileset (default: 'pixel-art')
- `padding`: Padding between elements (default: 1)
- `theme`: Theme of the environment (default: 'fantasy')

## Integration Tips

1. Use `fetchAvailableAnimationStates` to dynamically populate UI options for character animations.
2. Combine `generateCharacterSpritesheet` and `generateEnvironmentSprites` to create cohesive game worlds.
3. Utilize the metadata returned by generation functions to correctly slice and use the spritesheets in your game engine.

## Error Handling

All SDK functions are asynchronous and may throw errors. Always use try-catch blocks or .catch() methods when calling these functions:

```javascript
try {
  const result = await generateCharacterSpritesheet(description, options);
  // Handle successful result
} catch (error) {
  console.error("Error generating spritesheet:", error);
  // Handle error (e.g., show user-friendly message, retry, etc.)
}
```

## Conclusion

The SpriteAI SDK provides a powerful set of tools for generating game assets programmatically. By leveraging these functions, you can streamline your asset creation process and focus more on game design and development.

For more detailed information on each function, refer to the SDK's API documentation.