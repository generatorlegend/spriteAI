# SpriteAI API Reference

## Table of Contents
1. [Introduction](#introduction)
2. [generateCharacterSpritesheet](#generatecharacterspritesheet)
3. [generateLandscapeSprite](#generatelandscapesprite)
4. [fetchAvailableAnimationStates](#fetchavailableanimationstates)
5. [fetchAvailableSpriteStyles](#fetchavailablespritestyles)
6. [generateEnvironmentSprites](#generateenvironmentsprites)

## Introduction

SpriteAI is a powerful library for generating game assets using AI. This API reference provides detailed information on the available functions, their parameters, return values, and usage examples.

## generateCharacterSpritesheet

Generates a character spritesheet with multiple animation states.

### Syntax

```javascript
async function generateCharacterSpritesheet(description, options = {})
```

### Parameters

- `description` (string): A description of the character to generate.
- `options` (object, optional): Customization options for the spritesheet.
  - `states` (array of strings, default: `['idle', 'walk', 'run', 'attack']`): Animation states to generate.
  - `framesPerState` (number, default: 6): Number of frames per animation state.
  - `size` (string, default: '1024x1024'): Output size of the spritesheet.
  - `style` (string, default: 'pixel-art'): Art style of the character.
  - `padding` (number, default: 1): Padding between sprites.
  - `direction` (string, default: 'right'): Base direction of the character.
  - `save` (boolean, default: false): Whether to save the generated image to disk.

### Return Value

An object containing:
- `original` (string): URL of the original generated image.
- `spritesheet` (string): Base64-encoded PNG data of the processed spritesheet.
- `metadata` (object): Detailed information about the generated spritesheet.

### Example Usage

```javascript
const result = await generateCharacterSpritesheet('a brave knight with shining armor', {
  states: ['idle', 'walk', 'attack', 'defend'],
  framesPerState: 8,
  size: '2048x2048',
  style: 'pixel-art',
  direction: 'left',
  save: true
});

console.log(result.metadata);
// Use result.spritesheet for rendering in your game
```

## generateLandscapeSprite

Generates a landscape sprite for use as a game background.

### Syntax

```javascript
async function generateLandscapeSprite(description, options = {})
```

### Parameters

- `description` (string): A description of the landscape to generate.
- `options` (object, optional): Customization options for the landscape sprite.
  - `size` (string, default: '1024x1024'): Output size of the sprite.
  - `style` (string, default: 'pixel-art'): Art style of the landscape.
  - `timeOfDay` (string, default: 'day'): Time of day setting (day, night, sunset, dawn).
  - `weather` (string, default: 'clear'): Weather conditions (clear, rainy, foggy, snowy).
  - `perspective` (string, default: 'side-scrolling'): Perspective of the landscape (side-scrolling, top-down, isometric).
  - `save` (boolean, default: false): Whether to save the generated image to disk.
  - `removeBackground` (boolean, optional): Whether to remove the background.
  - `backgroundColor` (string, optional): Background color to remove (if removeBackground is true).
  - `colorThreshold` (number, optional): Threshold for background color removal.

### Return Value

An object containing:
- `original` (string): URL of the original generated image.
- `landscape` (string): Base64-encoded PNG data of the processed landscape sprite.
- `metadata` (object): Detailed information about the generated landscape.

### Example Usage

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
// Use result.landscape for rendering in your game
```

## fetchAvailableAnimationStates

Retrieves a list of available animation states for character spritesheets.

### Syntax

```javascript
async function fetchAvailableAnimationStates()
```

### Return Value

An array of strings representing available animation states.

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

An array of strings representing available sprite styles.

### Example Usage

```javascript
const styles = await fetchAvailableSpriteStyles();
console.log(styles);
// Output: ['pixel-art', 'vector', '3d', 'hand-drawn', 'anime']
```

## generateEnvironmentSprites

Generates a tileset of environment sprites.

### Syntax

```javascript
async function generateEnvironmentSprites(description, options = {})
```

### Parameters

- `description` (string): A description of the environment to generate.
- `options` (object, optional): Customization options for the environment sprites.
  - `elements` (number, default: 4): Number of different elements to generate.
  - `size` (string, default: '1024x1024'): Output size of the tileset.
  - `style` (string, default: 'pixel-art'): Art style of the environment sprites.
  - `padding` (number, default: 1): Padding between sprites.
  - `theme` (string, default: 'fantasy'): Theme of the environment.
  - `save` (boolean, default: false): Whether to save the generated image to disk.

### Return Value

An object containing:
- `original` (string): URL of the original generated image.
- `tileset` (string): Base64-encoded PNG data of the processed environment tileset.
- `metadata` (object): Detailed information about the generated environment sprites.

### Example Usage

```javascript
const result = await generateEnvironmentSprites('a desert oasis', {
  elements: 6,
  size: '2048x2048',
  style: 'pixel-art',
  theme: 'desert',
  save: true
});

console.log(result.metadata);
// Use result.tileset for rendering in your game
```

This API reference provides a comprehensive overview of the main functions available in the SpriteAI library. Use these functions to generate character spritesheets, landscape sprites, and environment tilesets for your game development needs. Customize the output by adjusting the provided options to achieve the desired results.