# SpriteAI API Reference

This document provides a comprehensive API reference for SpriteAI, detailing all public functions, their parameters, return values, and usage examples.

## Table of Contents

1. [generateCharacterSpritesheet](#generatecharacterspritesheet)
2. [generateLandscapeSprite](#generatelandscapesprite)
3. [fetchAvailableAnimationStates](#fetchavailableanimationstates)
4. [fetchAvailableSpriteStyles](#fetchavailablespritestyles)
5. [generateEnvironmentSprites](#generateenvironmentsprites)

## generateCharacterSpritesheet

Generates a character spritesheet based on the provided description and options.

### Syntax

```javascript
async function generateCharacterSpritesheet(description, options = {})
```

### Parameters

- `description` (string): A detailed description of the character to generate.
- `options` (object, optional): Configuration options for the spritesheet generation.
  - `states` (array of strings, default: `['idle', 'walk', 'run', 'attack']`): Animation states to generate.
  - `framesPerState` (number, default: 6): Number of frames per animation state.
  - `size` (string, default: '1024x1024'): Output size of the spritesheet.
  - `style` (string, default: 'pixel-art'): Art style of the character.
  - `padding` (number, default: 1): Padding between sprites.
  - `direction` (string, default: 'right'): Base direction of the character.
  - `save` (boolean, default: false): Whether to save the generated image to disk.

### Return Value

Returns a Promise that resolves to an object with the following properties:

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
const spritesheet = await generateCharacterSpritesheet('A brave knight in shining armor', {
  states: ['idle', 'walk', 'attack', 'defend'],
  framesPerState: 8,
  size: '2048x2048',
  style: 'pixel-art',
  save: true
});

console.log(spritesheet.metadata);
```

## generateLandscapeSprite

Generates a landscape sprite based on the provided description and options.

### Syntax

```javascript
async function generateLandscapeSprite(description, options = {})
```

### Parameters

- `description` (string): A detailed description of the landscape to generate.
- `options` (object, optional): Configuration options for the landscape generation.
  - `size` (string, default: '1024x1024'): Output size of the sprite.
  - `style` (string, default: 'pixel-art'): Art style of the landscape.
  - `timeOfDay` (string, default: 'day'): Time of day setting (e.g., 'day', 'night', 'sunset', 'dawn').
  - `weather` (string, default: 'clear'): Weather conditions (e.g., 'clear', 'rainy', 'foggy', 'snowy').
  - `perspective` (string, default: 'side-scrolling'): Perspective of the landscape (e.g., 'side-scrolling', 'top-down', 'isometric').
  - `save` (boolean, default: false): Whether to save the generated image to disk.
  - `removeBackground` (boolean, optional): Whether to remove the background color.
  - `backgroundColor` (string, optional): Background color to remove (if removeBackground is true).
  - `colorThreshold` (number, optional): Color threshold for background removal.

### Return Value

Returns a Promise that resolves to an object with the following properties:

- `original` (string): URL of the original generated image.
- `landscape` (string): Base64-encoded data URL of the processed landscape sprite.
- `metadata` (object): Metadata about the generated landscape, including:
  - `description` (string): The original description used.
  - `style` (string): The art style used.
  - `timeOfDay` (string): The time of day setting.
  - `weather` (string): The weather conditions.
  - `perspective` (string): The perspective used.
  - `dimensions` (object): Width and height of the sprite.

### Example Usage

```javascript
const landscape = await generateLandscapeSprite('A lush forest with a flowing river', {
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
console.log(states); // ['idle', 'walk', 'run', 'attack', 'jump', 'fall', 'hurt', 'die']
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
console.log(styles); // ['pixel-art', 'vector', '3d', 'hand-drawn', 'anime']
```

## generateEnvironmentSprites

Generates a tileset of environment sprites based on the provided description and options.

### Syntax

```javascript
async function generateEnvironmentSprites(description, options = {})
```

### Parameters

- `description` (string): A detailed description of the environment to generate.
- `options` (object, optional): Configuration options for the environment sprite generation.
  - `elements` (number, default: 4): Number of different elements to generate.
  - `size` (string, default: '1024x1024'): Output size of the tileset.
  - `style` (string, default: 'pixel-art'): Art style of the environment sprites.
  - `padding` (number, default: 1): Padding between sprite elements.
  - `theme` (string, default: 'fantasy'): Theme of the environment.
  - `save` (boolean, default: false): Whether to save the generated image to disk.

### Return Value

Returns a Promise that resolves to an object with the following properties:

- `original` (string): URL of the original generated image.
- `tileset` (string): Base64-encoded data URL of the processed environment tileset.
- `metadata` (object): Metadata about the generated environment sprites, including:
  - `elements` (number): Number of distinct environment pieces.
  - `theme` (string): The theme used for generation.
  - `dimensions` (object): Width and height of the tileset.
  - `tileData` (object): Information about the tile arrangement, including rows, columns, and total tiles.

### Example Usage

```javascript
const environmentSprites = await generateEnvironmentSprites('A mystical forest with ancient ruins', {
  elements: 6,
  size: '2048x2048',
  style: 'pixel-art',
  theme: 'fantasy',
  save: true
});

console.log(environmentSprites.metadata);
```

This concludes the API reference for SpriteAI. For more detailed information on using these functions in your projects, please refer to the usage guides and examples in the main documentation.