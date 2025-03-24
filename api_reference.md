# SpriteAI API Reference

This document provides a comprehensive API reference for the SpriteAI module. It includes detailed information on public functions, their parameters, return values, and usage examples.

## Table of Contents

1. [generateCharacterSpritesheet](#generatecharacterspritesheet)
2. [generateLandscapeSprite](#generatelandscapesprite)
3. [fetchAvailableAnimationStates](#fetchavailableanimationstates)
4. [fetchAvailableSpriteStyles](#fetchavailablespritestyles)
5. [generateEnvironmentSprites](#generateenvironmentsprites)

## generateCharacterSpritesheet

Generates a character spritesheet based on a given description.

### Parameters

- `description` (string): A description of the character to generate.
- `options` (object, optional): Configuration options for the spritesheet generation.
  - `states` (array of strings, default: `['idle', 'walk', 'run', 'attack']`): Animation states to generate.
  - `framesPerState` (number, default: 6): Number of frames per animation state.
  - `size` (string, default: '1024x1024'): Output size of the spritesheet.
  - `style` (string, default: 'pixel-art'): Art style of the spritesheet.
  - `padding` (number, default: 1): Padding between sprites.
  - `direction` (string, default: 'right'): Base direction of the character.
  - `save` (boolean): Whether to save the generated image to disk.

### Return Value

Returns an object with the following properties:

- `original` (string): URL of the original generated image.
- `spritesheet` (string): Base64-encoded data URL of the processed spritesheet.
- `metadata` (object): Metadata about the generated spritesheet, including:
  - `states` (array): List of animation states.
  - `framesPerState` (number): Number of frames per state.
  - `totalFrames` (number): Total number of frames in the spritesheet.
  - `dimensions` (object): Width and height of the spritesheet.
  - `frameData` (object): Detailed information about each animation state's frames.

### Usage Example

```javascript
const sprite = require('spriteAI');

const characterSprite = await sprite.generateCharacterSpritesheet('a medieval knight in armor', {
  states: ['idle', 'walk', 'attack'],
  framesPerState: 4,
  size: '512x512',
  style: 'pixel-art',
  save: true
});

console.log(characterSprite.metadata);
```

## generateLandscapeSprite

Generates a landscape sprite based on a given description.

### Parameters

- `description` (string): A description of the landscape to generate.
- `options` (object, optional): Configuration options for the landscape generation.
  - `size` (string, default: '1024x1024'): Output size of the sprite.
  - `style` (string, default: 'pixel-art'): Art style of the sprite.
  - `timeOfDay` (string, default: 'day'): Time of day setting (e.g., 'day', 'night', 'sunset', 'dawn').
  - `weather` (string, default: 'clear'): Weather conditions (e.g., 'clear', 'rainy', 'foggy', 'snowy').
  - `perspective` (string, default: 'side-scrolling'): Perspective of the landscape (e.g., 'side-scrolling', 'top-down', 'isometric').
  - `save` (boolean, default: false): Whether to save the generated image to disk.
  - `removeBackground` (boolean): Whether to remove the background from the generated image.
  - `backgroundColor` (string): Background color to remove (if removeBackground is true).
  - `colorThreshold` (number): Threshold for background color removal (if removeBackground is true).

### Return Value

Returns an object with the following properties:

- `original` (string): URL of the original generated image.
- `landscape` (string): Base64-encoded data URL of the processed landscape sprite.
- `metadata` (object): Metadata about the generated landscape, including:
  - `description` (string): The original description used to generate the sprite.
  - `style` (string): The art style used.
  - `timeOfDay` (string): The time of day setting.
  - `weather` (string): The weather conditions.
  - `perspective` (string): The perspective used.
  - `dimensions` (object): Width and height of the sprite.

### Usage Example

```javascript
const sprite = require('spriteAI');

const landscapeSprite = await sprite.generateLandscapeSprite('a lush forest with a winding river', {
  size: '512x512',
  style: 'pixel-art',
  timeOfDay: 'sunset',
  weather: 'clear',
  perspective: 'side-scrolling',
  save: true,
  removeBackground: true,
  backgroundColor: '#FFFFFF',
  colorThreshold: 0.1
});

console.log(landscapeSprite.metadata);
```

## fetchAvailableAnimationStates

Retrieves a list of available animation states for character sprites.

### Parameters

None

### Return Value

Returns an array of strings representing available animation states.

### Usage Example

```javascript
const sprite = require('spriteAI');

const animationStates = await sprite.fetchAvailableAnimationStates();
console.log(animationStates);
// Output: ['idle', 'walk', 'run', 'attack', 'jump', 'fall', 'hurt', 'die']
```

## fetchAvailableSpriteStyles

Retrieves a list of available sprite styles.

### Parameters

None

### Return Value

Returns an array of strings representing available sprite styles.

### Usage Example

```javascript
const sprite = require('spriteAI');

const spriteStyles = await sprite.fetchAvailableSpriteStyles();
console.log(spriteStyles);
// Output: ['pixel-art', 'vector', '3d', 'hand-drawn', 'anime']
```

## generateEnvironmentSprites

Generates a set of environment sprites based on a given description.

### Parameters

- `description` (string): A description of the environment to generate.
- `options` (object, optional): Configuration options for the environment sprites generation.
  - `elements` (number, default: 4): Number of different elements to generate.
  - `size` (string, default: '1024x1024'): Output size of the tileset.
  - `style` (string, default: 'pixel-art'): Art style of the sprites.
  - `padding` (number, default: 1): Padding between sprites.
  - `theme` (string, default: 'fantasy'): Theme of the environment.
  - `save` (boolean): Whether to save the generated image to disk.

### Return Value

Returns an object with the following properties:

- `original` (string): URL of the original generated image.
- `tileset` (string): Base64-encoded data URL of the processed environment tileset.
- `metadata` (object): Metadata about the generated environment sprites, including:
  - `elements` (number): Number of different elements generated.
  - `theme` (string): The theme of the environment.
  - `dimensions` (object): Width and height of the tileset.
  - `tileData` (object): Information about the tileset layout.

### Usage Example

```javascript
const sprite = require('spriteAI');

const environmentSprites = await sprite.generateEnvironmentSprites('a mystical forest', {
  elements: 6,
  size: '512x512',
  style: 'pixel-art',
  theme: 'fantasy',
  save: true
});

console.log(environmentSprites.metadata);
```

This API reference provides a comprehensive overview of the main functions available in the SpriteAI module. For more detailed information or advanced usage, please refer to the specific function documentation or contact the development team.