# SpriteAI API Reference

This document provides a comprehensive API reference for the SpriteAI library, covering all public functions, their parameters, return values, and usage examples.

## Table of Contents

1. [Character Sprite Generation](#character-sprite-generation)
2. [Landscape Sprite Generation](#landscape-sprite-generation)
3. [Environment Sprite Generation](#environment-sprite-generation)
4. [Utility Functions](#utility-functions)

## Character Sprite Generation

### generateCharacterSpritesheet

Generates a character spritesheet based on a given description and options.

```javascript
async function generateCharacterSpritesheet(description, options = {})
```

#### Parameters

- `description` (string): A description of the character to generate.
- `options` (object, optional): Configuration options for the spritesheet generation.
  - `states` (array of strings, default: `['idle', 'walk', 'run', 'attack']`): Animation states to generate.
  - `framesPerState` (number, default: 6): Number of frames per animation state.
  - `size` (string, default: '1024x1024'): Output size of the spritesheet.
  - `style` (string, default: 'pixel-art'): Art style of the character.
  - `padding` (number, default: 1): Padding between sprites.
  - `direction` (string, default: 'right'): Base direction of the character.
  - `save` (boolean, default: false): Whether to save the generated image to disk.

#### Returns

An object containing:
- `original` (string): URL of the original generated image.
- `spritesheet` (string): Base64-encoded string of the processed spritesheet.
- `metadata` (object): Metadata about the generated spritesheet, including states, dimensions, and frame data.

#### Example Usage

```javascript
const spriteAI = require('spriteai');

const characterSprite = await spriteAI.generateCharacterSpritesheet('a fierce warrior', {
  states: ['idle', 'walk', 'attack', 'die'],
  framesPerState: 8,
  size: '2048x2048',
  style: 'pixel-art',
  save: true
});

console.log(characterSprite.metadata);
```

## Landscape Sprite Generation

### generateLandscapeSprite

Generates a landscape sprite based on a given description and options.

```javascript
async function generateLandscapeSprite(description, options = {})
```

#### Parameters

- `description` (string): A description of the landscape to generate.
- `options` (object, optional): Configuration options for the landscape generation.
  - `size` (string, default: '1024x1024'): Output size of the sprite.
  - `style` (string, default: 'pixel-art'): Art style of the landscape.
  - `timeOfDay` (string, default: 'day'): Time of day setting (day, night, sunset, dawn).
  - `weather` (string, default: 'clear'): Weather conditions (clear, rainy, foggy, snowy).
  - `perspective` (string, default: 'side-scrolling'): Perspective of the landscape (side-scrolling, top-down, isometric).
  - `save` (boolean, default: false): Whether to save the generated image to disk.
  - `removeBackground` (boolean, optional): Whether to remove the background.
  - `backgroundColor` (string, optional): Background color to remove (if removeBackground is true).
  - `colorThreshold` (number, optional): Color threshold for background removal.

#### Returns

An object containing:
- `original` (string): URL of the original generated image.
- `landscape` (string): Base64-encoded string of the processed landscape sprite.
- `metadata` (object): Metadata about the generated landscape, including description, style, time of day, weather, perspective, and dimensions.

#### Example Usage

```javascript
const spriteAI = require('spriteai');

const landscapeSprite = await spriteAI.generateLandscapeSprite('a lush forest with a winding river', {
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

console.log(landscapeSprite.metadata);
```

## Environment Sprite Generation

### generateEnvironmentSprites

Generates a tileset of environment sprites based on a given description and options.

```javascript
async function generateEnvironmentSprites(description, options = {})
```

#### Parameters

- `description` (string): A description of the environment to generate.
- `options` (object, optional): Configuration options for the environment sprite generation.
  - `elements` (number, default: 4): Number of different elements to generate.
  - `size` (string, default: '1024x1024'): Output size of the tileset.
  - `style` (string, default: 'pixel-art'): Art style of the environment sprites.
  - `padding` (number, default: 1): Padding between sprites.
  - `theme` (string, default: 'fantasy'): Theme of the environment.
  - `save` (boolean, default: false): Whether to save the generated image to disk.

#### Returns

An object containing:
- `original` (string): URL of the original generated image.
- `tileset` (string): Base64-encoded string of the processed environment tileset.
- `metadata` (object): Metadata about the generated tileset, including number of elements, theme, dimensions, and tile data.

#### Example Usage

```javascript
const spriteAI = require('spriteai');

const environmentSprites = await spriteAI.generateEnvironmentSprites('desert oasis', {
  elements: 6,
  size: '2048x2048',
  style: 'pixel-art',
  theme: 'desert',
  save: true
});

console.log(environmentSprites.metadata);
```

## Utility Functions

### fetchAvailableAnimationStates

Retrieves a list of available animation states for character sprites.

```javascript
async function fetchAvailableAnimationStates()
```

#### Returns

An array of strings representing available animation states.

#### Example Usage

```javascript
const spriteAI = require('spriteai');

const availableStates = await spriteAI.fetchAvailableAnimationStates();
console.log(availableStates);
// Output: ['idle', 'walk', 'run', 'attack', 'jump', 'fall', 'hurt', 'die']
```

### fetchAvailableSpriteStyles

Retrieves a list of available sprite styles.

```javascript
async function fetchAvailableSpriteStyles()
```

#### Returns

An array of strings representing available sprite styles.

#### Example Usage

```javascript
const spriteAI = require('spriteai');

const availableStyles = await spriteAI.fetchAvailableSpriteStyles();
console.log(availableStyles);
// Output: ['pixel-art', 'vector', '3d', 'hand-drawn', 'anime']
```

### removeBackgroundColor

Removes a specified background color from an image.

```javascript
async function removeBackgroundColor(inputPath, outputPath, targetColor, colorThreshold = 0, options = {})
```

#### Parameters

- `inputPath` (string): Path to the input image file.
- `outputPath` (string): Path where the processed image will be saved.
- `targetColor` (string): CSS color string representing the background color to remove.
- `colorThreshold` (number, default: 0): Threshold for color matching.
- `options` (object, optional): Additional options for background removal.

#### Returns

A Promise that resolves when the background removal is complete.

#### Example Usage

```javascript
const spriteAI = require('spriteai');

await spriteAI.removeBackgroundColor(
  'input.png',
  'output.png',
  '#FFFFFF',
  0.1
);
console.log('Background removed successfully');
```

This API reference provides a comprehensive overview of the main functions available in the SpriteAI library. For more detailed information on specific use cases or advanced features, please refer to the individual function documentation or examples in the codebase.