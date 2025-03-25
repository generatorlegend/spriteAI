# SpriteAI API Reference

This document provides a comprehensive API reference for the SpriteAI library. The library offers functions for generating character spritesheets, landscape sprites, and environment sprites using AI-powered image generation.

## Table of Contents

1. [Character Generation](#character-generation)
   - [generateCharacterSpritesheet](#generatecharacterspritesheet)
2. [Landscape Generation](#landscape-generation)
   - [generateLandscapeSprite](#generatelandscapesprite)
3. [Environment Generation](#environment-generation)
   - [generateEnvironmentSprites](#generateenvironmentsprites)
4. [Utility Functions](#utility-functions)
   - [fetchAvailableAnimationStates](#fetchavailableanimationstates)
   - [fetchAvailableSpriteStyles](#fetchavailablespritestyles)

## Character Generation

### generateCharacterSpritesheet

Generates a character spritesheet with multiple animation states.

```javascript
async function generateCharacterSpritesheet(description, options = {})
```

#### Parameters

- `description` (string): A detailed description of the character to generate.
- `options` (object, optional): Configuration options for the spritesheet generation.
  - `states` (array of strings, default: ['idle', 'walk', 'run', 'attack']): Animation states to generate.
  - `framesPerState` (number, default: 6): Number of frames per animation state.
  - `size` (string, default: '1024x1024'): Output size of the spritesheet.
  - `style` (string, default: 'pixel-art'): Art style of the character.
  - `padding` (number, default: 1): Padding between sprites.
  - `direction` (string, default: 'right'): Base direction of the character.
  - `save` (boolean, default: false): Whether to save the generated image to disk.

#### Returns

An object containing:
- `original` (string): URL of the original generated image.
- `spritesheet` (string): Base64-encoded PNG data of the processed spritesheet.
- `metadata` (object): Metadata about the generated spritesheet, including:
  - `states` (array): List of animation states.
  - `framesPerState` (number): Number of frames per state.
  - `totalFrames` (number): Total number of frames in the spritesheet.
  - `dimensions` (object): Width and height of the spritesheet.
  - `frameData` (object): Detailed information about each animation state's frames.

#### Example Usage

```javascript
const spritesheet = await generateCharacterSpritesheet("a medieval knight in armor", {
  states: ['idle', 'walk', 'attack'],
  framesPerState: 8,
  size: '1024x1024',
  style: 'pixel-art',
  save: true
});

console.log(spritesheet.metadata);
```

## Landscape Generation

### generateLandscapeSprite

Generates a landscape sprite suitable for game backgrounds.

```javascript
async function generateLandscapeSprite(description, options = {})
```

#### Parameters

- `description` (string): A detailed description of the landscape to generate.
- `options` (object, optional): Configuration options for the landscape generation.
  - `size` (string, default: '1024x1024'): Output size of the sprite.
  - `style` (string, default: 'pixel-art'): Art style of the landscape.
  - `timeOfDay` (string, default: 'day'): Time of day setting (day, night, sunset, dawn).
  - `weather` (string, default: 'clear'): Weather conditions (clear, rainy, foggy, snowy).
  - `perspective` (string, default: 'side-scrolling'): Perspective of the landscape (side-scrolling, top-down, isometric).
  - `save` (boolean, default: false): Whether to save the generated image to disk.
  - `removeBackground` (boolean, optional): Whether to remove the background color.
  - `backgroundColor` (string, optional): Target background color to remove (if removeBackground is true).
  - `colorThreshold` (number, optional): Color threshold for background removal (if removeBackground is true).

#### Returns

An object containing:
- `original` (string): URL of the original generated image.
- `landscape` (string): Base64-encoded PNG data of the processed landscape sprite.
- `metadata` (object): Metadata about the generated landscape, including:
  - `description` (string): The original description.
  - `style` (string): The art style used.
  - `timeOfDay` (string): The time of day setting.
  - `weather` (string): The weather conditions.
  - `perspective` (string): The perspective of the landscape.
  - `dimensions` (object): Width and height of the sprite.

#### Example Usage

```javascript
const landscape = await generateLandscapeSprite("a lush forest with a winding river", {
  style: 'pixel-art',
  timeOfDay: 'sunset',
  weather: 'clear',
  perspective: 'side-scrolling',
  save: true,
  removeBackground: true,
  backgroundColor: '#FFFFFF'
});

console.log(landscape.metadata);
```

## Environment Generation

### generateEnvironmentSprites

Generates a tileset of environment sprites suitable for game environments.

```javascript
async function generateEnvironmentSprites(description, options = {})
```

#### Parameters

- `description` (string): A detailed description of the environment to generate.
- `options` (object, optional): Configuration options for the environment generation.
  - `elements` (number, default: 4): Number of different elements to generate.
  - `size` (string, default: '1024x1024'): Output size of the tileset.
  - `style` (string, default: 'pixel-art'): Art style of the environment sprites.
  - `padding` (number, default: 1): Padding between sprites.
  - `theme` (string, default: 'fantasy'): Theme of the environment.
  - `save` (boolean, default: false): Whether to save the generated image to disk.

#### Returns

An object containing:
- `original` (string): URL of the original generated image.
- `tileset` (string): Base64-encoded PNG data of the processed environment tileset.
- `metadata` (object): Metadata about the generated environment, including:
  - `elements` (number): Number of distinct environment pieces.
  - `theme` (string): The theme of the environment.
  - `dimensions` (object): Width and height of the tileset.
  - `tileData` (object): Information about the tileset layout.

#### Example Usage

```javascript
const environment = await generateEnvironmentSprites("desert oasis", {
  elements: 6,
  style: 'pixel-art',
  theme: 'desert',
  save: true
});

console.log(environment.metadata);
```

## Utility Functions

### fetchAvailableAnimationStates

Retrieves a list of available animation states for character spritesheets.

```javascript
async function fetchAvailableAnimationStates()
```

#### Returns

An array of strings representing available animation states.

#### Example Usage

```javascript
const states = await fetchAvailableAnimationStates();
console.log(states);
// Output: ['idle', 'walk', 'run', 'attack', 'jump', 'fall', 'hurt', 'die']
```

### fetchAvailableSpriteStyles

Retrieves a list of available sprite styles for character and environment generation.

```javascript
async function fetchAvailableSpriteStyles()
```

#### Returns

An array of strings representing available sprite styles.

#### Example Usage

```javascript
const styles = await fetchAvailableSpriteStyles();
console.log(styles);
// Output: ['pixel-art', 'vector', '3d', 'hand-drawn', 'anime']
```