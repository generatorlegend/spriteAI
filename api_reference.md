# SpriteAI API Reference

This document provides a comprehensive API reference for the SpriteAI library. The library offers functions for generating character spritesheets, landscape sprites, and various utility functions for image processing.

## Table of Contents

1. [Sprite Generation](#sprite-generation)
   - [generateCharacterSpritesheet](#generatecharacterspritesheet)
   - [generateLandscapeSprite](#generatelandscapesprite)
   - [generateEnvironmentSprites](#generateenvironmentsprites)
2. [Utility Functions](#utility-functions)
   - [removeBackgroundColor](#removebackgroundcolor)
   - [fetchAvailableAnimationStates](#fetchavailableanimationstates)
   - [fetchAvailableSpriteStyles](#fetchavailablespritestyles)

## Sprite Generation

### generateCharacterSpritesheet

Generates a character spritesheet based on a given description and options.

**Syntax:**

```javascript
async function generateCharacterSpritesheet(description, options = {})
```

**Parameters:**

- `description` (string): A description of the character to generate.
- `options` (object, optional): Configuration options for the spritesheet generation.
  - `states` (array of strings, default: `['idle', 'walk', 'run', 'attack']`): Animation states to generate.
  - `framesPerState` (number, default: 6): Number of frames per animation state.
  - `size` (string, default: '1024x1024'): Output size of the spritesheet.
  - `style` (string, default: 'pixel-art'): Art style of the spritesheet.
  - `padding` (number, default: 1): Padding between sprites.
  - `direction` (string, default: 'right'): Base direction of the character.
  - `save` (boolean): Whether to save the generated image to disk.

**Returns:**

An object containing:
- `original` (string): URL of the original generated image.
- `spritesheet` (string): Base64-encoded PNG data of the processed spritesheet.
- `metadata` (object): Metadata about the generated spritesheet, including states, frame data, and dimensions.

**Example:**

```javascript
const result = await generateCharacterSpritesheet('a medieval knight', {
  states: ['idle', 'walk', 'attack'],
  framesPerState: 8,
  size: '2048x2048',
  style: 'pixel-art',
  save: true
});

console.log(result.metadata);
```

### generateLandscapeSprite

Generates a landscape sprite based on a given description and options.

**Syntax:**

```javascript
async function generateLandscapeSprite(description, options = {})
```

**Parameters:**

- `description` (string): A description of the landscape to generate.
- `options` (object, optional): Configuration options for the landscape generation.
  - `size` (string, default: '1024x1024'): Output size of the sprite.
  - `style` (string, default: 'pixel-art'): Art style of the sprite.
  - `timeOfDay` (string, default: 'day'): Time of day setting (e.g., 'day', 'night', 'sunset', 'dawn').
  - `weather` (string, default: 'clear'): Weather conditions (e.g., 'clear', 'rainy', 'foggy', 'snowy').
  - `perspective` (string, default: 'side-scrolling'): Perspective of the landscape (e.g., 'side-scrolling', 'top-down', 'isometric').
  - `save` (boolean, default: false): Whether to save the generated image to disk.
  - `removeBackground` (boolean): Whether to remove the background from the generated image.
  - `backgroundColor` (string): The background color to remove (if removeBackground is true).
  - `colorThreshold` (number): The color threshold for background removal (if removeBackground is true).

**Returns:**

An object containing:
- `original` (string): URL of the original generated image.
- `landscape` (string): Base64-encoded PNG data of the processed landscape sprite.
- `metadata` (object): Metadata about the generated landscape, including description, style, time of day, weather, perspective, and dimensions.

**Example:**

```javascript
const result = await generateLandscapeSprite('a lush forest with a winding river', {
  size: '2048x1024',
  style: 'pixel-art',
  timeOfDay: 'sunset',
  weather: 'clear',
  perspective: 'side-scrolling',
  save: true,
  removeBackground: true,
  backgroundColor: '#FFFFFF',
  colorThreshold: 0.1
});

console.log(result.metadata);
```

### generateEnvironmentSprites

Generates a set of environment sprites based on a given description and options.

**Syntax:**

```javascript
async function generateEnvironmentSprites(description, options = {})
```

**Parameters:**

- `description` (string): A description of the environment to generate.
- `options` (object, optional): Configuration options for the environment sprite generation.
  - `elements` (number, default: 4): Number of different elements to generate.
  - `size` (string, default: '1024x1024'): Output size of the tileset.
  - `style` (string, default: 'pixel-art'): Art style of the sprites.
  - `padding` (number, default: 1): Padding between elements.
  - `theme` (string, default: 'fantasy'): Theme of the environment.
  - `save` (boolean): Whether to save the generated image to disk.

**Returns:**

An object containing:
- `original` (string): URL of the original generated image.
- `tileset` (string): Base64-encoded PNG data of the processed environment tileset.
- `metadata` (object): Metadata about the generated environment sprites, including number of elements, theme, dimensions, and tile data.

**Example:**

```javascript
const result = await generateEnvironmentSprites('a desert oasis', {
  elements: 6,
  size: '2048x2048',
  style: 'pixel-art',
  theme: 'desert',
  save: true
});

console.log(result.metadata);
```

## Utility Functions

### removeBackgroundColor

Removes a specified background color from an image.

**Syntax:**

```javascript
async function removeBackgroundColor(inputPath, outputPath, targetColor, colorThreshold = 0, options = {})
```

**Parameters:**

- `inputPath` (string): Path to the input image file.
- `outputPath` (string): Path where the processed image will be saved.
- `targetColor` (string): The color to be removed (e.g., '#FFFFFF' for white).
- `colorThreshold` (number, default: 0): Tolerance for color matching.
- `options` (object, optional): Additional options for background removal.

**Returns:**

A promise that resolves when the background removal is complete.

**Example:**

```javascript
await removeBackgroundColor('input.png', 'output.png', '#FFFFFF', 0.1);
```

### fetchAvailableAnimationStates

Retrieves a list of available animation states for character sprites.

**Syntax:**

```javascript
async function fetchAvailableAnimationStates()
```

**Returns:**

An array of strings representing available animation states.

**Example:**

```javascript
const states = await fetchAvailableAnimationStates();
console.log(states); // ['idle', 'walk', 'run', 'attack', 'jump', 'fall', 'hurt', 'die']
```

### fetchAvailableSpriteStyles

Retrieves a list of available sprite styles.

**Syntax:**

```javascript
async function fetchAvailableSpriteStyles()
```

**Returns:**

An array of strings representing available sprite styles.

**Example:**

```javascript
const styles = await fetchAvailableSpriteStyles();
console.log(styles); // ['pixel-art', 'vector', '3d', 'hand-drawn', 'anime']
```

This API reference provides a comprehensive overview of the main functions available in the SpriteAI library. For more detailed information on implementation or advanced usage, please refer to the source code or contact the library maintainers.