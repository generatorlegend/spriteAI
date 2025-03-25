# SpriteAI API Reference

This document provides a comprehensive reference for the SpriteAI API, detailing all public functions, their parameters, return values, and usage examples.

## Table of Contents

1. [generateCharacterSpritesheet](#generatecharacterspritesheet)
2. [generateLandscapeSprite](#generatelandscapesprite)
3. [fetchAvailableAnimationStates](#fetchavailableanimationstates)
4. [fetchAvailableSpriteStyles](#fetchavailablespritestyles)
5. [generateEnvironmentSprites](#generateenvironmentsprites)

## generateCharacterSpritesheet

Generates a character spritesheet based on a given description and options.

### Syntax

```javascript
async function generateCharacterSpritesheet(description, options = {})
```

### Parameters

- `description` (string): A textual description of the character to generate.
- `options` (object, optional): Configuration options for the spritesheet generation.
  - `states` (array of strings, default: `['idle', 'walk', 'run', 'attack']`): Animation states to generate.
  - `framesPerState` (number, default: 6): Number of frames per animation state.
  - `size` (string, default: '1024x1024'): Output size of the spritesheet.
  - `style` (string, default: 'pixel-art'): Art style of the character.
  - `padding` (number, default: 1): Padding between sprites in the sheet.
  - `direction` (string, default: 'right'): Base direction of the character.
  - `save` (boolean, default: false): Whether to save the generated image to disk.

### Return Value

Returns a Promise that resolves to an object containing:

- `original` (string): URL of the original generated image.
- `spritesheet` (string): Base64-encoded data URL of the processed spritesheet.
- `metadata` (object): Metadata about the generated spritesheet, including:
  - `states` (array): List of animation states.
  - `framesPerState` (number): Number of frames per state.
  - `totalFrames` (number): Total number of frames in the spritesheet.
  - `dimensions` (object): Width and height of the spritesheet.
  - `frameData` (object): Detailed information about each animation state's frames.

### Example Usage

```javascript
const sprite = await generateCharacterSpritesheet('a medieval knight in armor', {
  states: ['idle', 'walk', 'attack'],
  framesPerState: 8,
  size: '2048x2048',
  style: 'pixel-art',
  save: true
});

console.log(sprite.metadata);
// Use sprite.spritesheet for rendering in your game
```

## generateLandscapeSprite

Generates a landscape sprite based on a given description and options.

### Syntax

```javascript
async function generateLandscapeSprite(description, options = {})
```

### Parameters

- `description` (string): A textual description of the landscape to generate.
- `options` (object, optional): Configuration options for the landscape generation.
  - `size` (string, default: '1024x1024'): Output size of the sprite.
  - `style` (string, default: 'pixel-art'): Art style of the landscape.
  - `timeOfDay` (string, default: 'day'): Time of day setting (e.g., 'day', 'night', 'sunset', 'dawn').
  - `weather` (string, default: 'clear'): Weather conditions (e.g., 'clear', 'rainy', 'foggy', 'snowy').
  - `perspective` (string, default: 'side-scrolling'): Perspective of the landscape (e.g., 'side-scrolling', 'top-down', 'isometric').
  - `save` (boolean, default: false): Whether to save the generated image to disk.
  - `removeBackground` (boolean, optional): Whether to remove the background color.
  - `backgroundColor` (string, optional): Background color to remove (if removeBackground is true).
  - `colorThreshold` (number, optional): Threshold for background color removal.

### Return Value

Returns a Promise that resolves to an object containing:

- `original` (string): URL of the original generated image.
- `landscape` (string): Base64-encoded data URL of the processed landscape sprite.
- `metadata` (object): Metadata about the generated landscape, including:
  - `description` (string): The original description.
  - `style` (string): The art style used.
  - `timeOfDay` (string): The time of day setting.
  - `weather` (string): The weather conditions.
  - `perspective` (string): The perspective used.
  - `dimensions` (object): Width and height of the sprite.

### Example Usage

```javascript
const landscape = await generateLandscapeSprite('a lush forest with a winding river', {
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

console.log(landscape.metadata);
// Use landscape.landscape for rendering in your game
```

## fetchAvailableAnimationStates

Retrieves a list of available animation states for character spritesheets.

### Syntax

```javascript
async function fetchAvailableAnimationStates()
```

### Return Value

Returns a Promise that resolves to an array of strings representing available animation states.

### Example Usage

```javascript
const states = await fetchAvailableAnimationStates();
console.log(states);
// Output: ['idle', 'walk', 'run', 'attack', 'jump', 'fall', 'hurt', 'die']
```

## fetchAvailableSpriteStyles

Retrieves a list of available sprite styles.

### Syntax

```javascript
async function fetchAvailableSpriteStyles()
```

### Return Value

Returns a Promise that resolves to an array of strings representing available sprite styles.

### Example Usage

```javascript
const styles = await fetchAvailableSpriteStyles();
console.log(styles);
// Output: ['pixel-art', 'vector', '3d', 'hand-drawn', 'anime']
```

## generateEnvironmentSprites

Generates a tileset of environment sprites based on a given description and options.

### Syntax

```javascript
async function generateEnvironmentSprites(description, options = {})
```

### Parameters

- `description` (string): A textual description of the environment to generate.
- `options` (object, optional): Configuration options for the environment generation.
  - `elements` (number, default: 4): Number of distinct environment elements to generate.
  - `size` (string, default: '1024x1024'): Output size of the tileset.
  - `style` (string, default: 'pixel-art'): Art style of the environment.
  - `padding` (number, default: 1): Padding between tiles in the set.
  - `theme` (string, default: 'fantasy'): Theme of the environment.
  - `save` (boolean, default: false): Whether to save the generated image to disk.

### Return Value

Returns a Promise that resolves to an object containing:

- `original` (string): URL of the original generated image.
- `tileset` (string): Base64-encoded data URL of the processed environment tileset.
- `metadata` (object): Metadata about the generated environment, including:
  - `elements` (number): Number of distinct environment elements.
  - `theme` (string): The theme of the environment.
  - `dimensions` (object): Width and height of the tileset.
  - `tileData` (object): Information about the tile arrangement.

### Example Usage

```javascript
const environment = await generateEnvironmentSprites('a medieval castle interior', {
  elements: 6,
  size: '2048x2048',
  style: 'pixel-art',
  theme: 'medieval',
  save: true
});

console.log(environment.metadata);
// Use environment.tileset for rendering in your game
```

This API reference provides developers with comprehensive information on how to use the SpriteAI module to generate various game assets programmatically. Each function is documented with its parameters, return values, and example usage to facilitate easy integration into game development workflows.