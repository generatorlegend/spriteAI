# SpriteAI API Reference

This document provides a detailed API reference for the SpriteAI library, including all public functions, their parameters, return values, and usage examples.

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

- `description` (string): A description of the character to generate.
- `options` (object, optional): Configuration options for the spritesheet generation.
  - `states` (array of strings, default: `['idle', 'walk', 'run', 'attack']`): Animation states to generate.
  - `framesPerState` (number, default: 6): Number of frames per animation state.
  - `size` (string, default: '1024x1024'): Output size of the spritesheet.
  - `style` (string, default: 'pixel-art'): Art style of the character.
  - `padding` (number, default: 1): Padding between sprites.
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
  - `frameData` (object): Detailed information about each animation state.

### Example Usage

```javascript
const spriteAI = require('spriteai');

async function generateCharacter() {
  const result = await spriteAI.generateCharacterSpritesheet('a medieval knight in armor', {
    states: ['idle', 'walk', 'attack', 'defend'],
    framesPerState: 8,
    size: '2048x2048',
    style: 'pixel-art',
    save: true
  });

  console.log(result.metadata);
  // Use result.spritesheet for further processing or display
}

generateCharacter();
```

## generateLandscapeSprite

Generates a landscape sprite based on the provided description and options.

### Syntax

```javascript
async function generateLandscapeSprite(description, options = {})
```

### Parameters

- `description` (string): A description of the landscape to generate.
- `options` (object, optional): Configuration options for the landscape generation.
  - `size` (string, default: '1024x1024'): Output size of the sprite.
  - `style` (string, default: 'pixel-art'): Art style of the landscape.
  - `timeOfDay` (string, default: 'day'): Time of day setting (e.g., 'day', 'night', 'sunset', 'dawn').
  - `weather` (string, default: 'clear'): Weather conditions (e.g., 'clear', 'rainy', 'foggy', 'snowy').
  - `perspective` (string, default: 'side-scrolling'): Perspective of the landscape (e.g., 'side-scrolling', 'top-down', 'isometric').
  - `save` (boolean, default: false): Whether to save the generated image to disk.
  - `removeBackground` (boolean, optional): Whether to remove the background color.
  - `backgroundColor` (string, optional): Background color to remove (if removeBackground is true).
  - `colorThreshold` (number, optional): Threshold for color removal (if removeBackground is true).

### Return Value

Returns a Promise that resolves to an object containing:

- `original` (string): URL of the original generated image.
- `landscape` (string): Base64-encoded data URL of the processed landscape sprite.
- `metadata` (object): Metadata about the generated landscape, including:
  - `description` (string): Original description used for generation.
  - `style` (string): Art style used.
  - `timeOfDay` (string): Time of day setting.
  - `weather` (string): Weather conditions.
  - `perspective` (string): Perspective used.
  - `dimensions` (object): Width and height of the sprite.

### Example Usage

```javascript
const spriteAI = require('spriteai');

async function generateLandscape() {
  const result = await spriteAI.generateLandscapeSprite('a lush forest with a winding river', {
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
  // Use result.landscape for further processing or display
}

generateLandscape();
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
const spriteAI = require('spriteai');

async function getAnimationStates() {
  const states = await spriteAI.fetchAvailableAnimationStates();
  console.log('Available animation states:', states);
}

getAnimationStates();
```

## fetchAvailableSpriteStyles

Retrieves a list of available sprite styles for generation.

### Syntax

```javascript
async function fetchAvailableSpriteStyles()
```

### Return Value

Returns a Promise that resolves to an array of strings representing available sprite styles.

### Example Usage

```javascript
const spriteAI = require('spriteai');

async function getSpriteStyles() {
  const styles = await spriteAI.fetchAvailableSpriteStyles();
  console.log('Available sprite styles:', styles);
}

getSpriteStyles();
```

## generateEnvironmentSprites

Generates a tileset of environment sprites based on the provided description and options.

### Syntax

```javascript
async function generateEnvironmentSprites(description, options = {})
```

### Parameters

- `description` (string): A description of the environment to generate.
- `options` (object, optional): Configuration options for the environment generation.
  - `elements` (number, default: 4): Number of different elements to generate.
  - `size` (string, default: '1024x1024'): Output size of the tileset.
  - `style` (string, default: 'pixel-art'): Art style of the environment.
  - `padding` (number, default: 1): Padding between elements.
  - `theme` (string, default: 'fantasy'): Theme of the environment.
  - `save` (boolean, default: false): Whether to save the generated image to disk.

### Return Value

Returns a Promise that resolves to an object containing:

- `original` (string): URL of the original generated image.
- `tileset` (string): Base64-encoded data URL of the processed environment tileset.
- `metadata` (object): Metadata about the generated environment, including:
  - `elements` (number): Number of elements generated.
  - `theme` (string): Theme of the environment.
  - `dimensions` (object): Width and height of the tileset.
  - `tileData` (object): Information about the tile arrangement.

### Example Usage

```javascript
const spriteAI = require('spriteai');

async function generateEnvironment() {
  const result = await spriteAI.generateEnvironmentSprites('a desert oasis', {
    elements: 6,
    size: '2048x2048',
    style: 'pixel-art',
    theme: 'desert',
    save: true
  });

  console.log(result.metadata);
  // Use result.tileset for further processing or display
}

generateEnvironment();
```

This API reference provides a comprehensive overview of the main functions available in the SpriteAI library. Each function is documented with its syntax, parameters, return values, and example usage to help developers integrate and utilize the library effectively in their projects.