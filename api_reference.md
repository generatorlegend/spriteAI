# SpriteAI API Reference

This document provides a comprehensive API reference for the SpriteAI library. It covers all public functions, their parameters, return values, and usage examples.

## Table of Contents

1. [Character Spritesheet Generation](#character-spritesheet-generation)
2. [Landscape Sprite Generation](#landscape-sprite-generation)
3. [Utility Functions](#utility-functions)

## Character Spritesheet Generation

### generateCharacterSpritesheet

Generates a character spritesheet based on the provided description and options.

#### Syntax

```javascript
async function generateCharacterSpritesheet(description, options = {})
```

#### Parameters

- `description` (string): A textual description of the character to generate.
- `options` (object, optional): Configuration options for the spritesheet generation.
  - `states` (array of strings, default: `['idle', 'walk', 'run', 'attack']`): Animation states to generate.
  - `framesPerState` (number, default: 6): Number of frames per animation state.
  - `size` (string, default: '1024x1024'): Output size of the spritesheet.
  - `style` (string, default: 'pixel-art'): Art style of the spritesheet.
  - `padding` (number, default: 1): Padding between sprites in the sheet.
  - `direction` (string, default: 'right'): Base direction of the character.
  - `save` (boolean, default: false): Whether to save the generated image to disk.

#### Return Value

The function returns an object with the following properties:

- `original` (string): URL of the originally generated image.
- `spritesheet` (string): Base64-encoded data URI of the processed spritesheet.
- `metadata` (object): Metadata about the generated spritesheet.
  - `states` (array): List of animation states.
  - `framesPerState` (number): Number of frames per state.
  - `totalFrames` (number): Total number of frames in the spritesheet.
  - `dimensions` (object): Width and height of the spritesheet.
  - `frameData` (object): Detailed information about each animation state.

#### Example Usage

```javascript
const spritesheet = await generateCharacterSpritesheet('A fierce warrior with a sword', {
  states: ['idle', 'attack', 'defend'],
  framesPerState: 8,
  size: '2048x2048',
  style: 'pixel-art',
  save: true
});

console.log(spritesheet.metadata);
```

## Landscape Sprite Generation

### generateLandscapeSprite

Generates a landscape sprite based on the provided description and options.

#### Syntax

```javascript
async function generateLandscapeSprite(description, options = {})
```

#### Parameters

- `description` (string): A textual description of the landscape to generate.
- `options` (object, optional): Configuration options for the landscape generation.
  - `size` (string, default: '1024x1024'): Output size of the sprite.
  - `style` (string, default: 'pixel-art'): Art style of the sprite.
  - `timeOfDay` (string, default: 'day'): Time of day setting (e.g., 'day', 'night', 'sunset', 'dawn').
  - `weather` (string, default: 'clear'): Weather conditions (e.g., 'clear', 'rainy', 'foggy', 'snowy').
  - `perspective` (string, default: 'side-scrolling'): Perspective of the landscape (e.g., 'side-scrolling', 'top-down', 'isometric').
  - `save` (boolean, default: false): Whether to save the generated image to disk.
  - `removeBackground` (boolean, optional): Whether to remove the background of the generated image.
  - `backgroundColor` (string, optional): Color to remove when `removeBackground` is true.
  - `colorThreshold` (number, optional): Threshold for color removal when `removeBackground` is true.

#### Return Value

The function returns an object with the following properties:

- `original` (string): URL of the originally generated image.
- `landscape` (string): Base64-encoded data URI of the processed landscape sprite.
- `metadata` (object): Metadata about the generated landscape sprite.
  - `description` (string): The original description used to generate the sprite.
  - `style` (string): The art style used.
  - `timeOfDay` (string): The time of day setting.
  - `weather` (string): The weather conditions.
  - `perspective` (string): The perspective used.
  - `dimensions` (object): Width and height of the sprite.

#### Example Usage

```javascript
const landscape = await generateLandscapeSprite('A lush forest with a winding river', {
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

## Utility Functions

### removeBackgroundColor

Removes a specified background color from an image.

#### Syntax

```javascript
async function removeBackgroundColor(inputPath, outputPath, targetColor, colorThreshold = 0, options = {})
```

#### Parameters

- `inputPath` (string): Path to the input image file.
- `outputPath` (string): Path where the processed image will be saved.
- `targetColor` (string): CSS color string of the background color to remove.
- `colorThreshold` (number, default: 0): Threshold for color matching.
- `options` (object, optional): Additional options for background removal.

#### Return Value

The function returns the result of the image processing operation.

#### Example Usage

```javascript
const result = await removeBackgroundColor(
  'input.png',
  'output.png',
  '#FFFFFF',
  0.1
);
console.log(result);
```

### fetchAvailableAnimationStates

Retrieves a list of available animation states for character spritesheets.

#### Syntax

```javascript
async function fetchAvailableAnimationStates()
```

#### Return Value

The function returns an array of strings representing available animation states.

#### Example Usage

```javascript
const states = await fetchAvailableAnimationStates();
console.log(states); // ['idle', 'walk', 'run', 'attack', 'jump', 'fall', 'hurt', 'die']
```

### fetchAvailableSpriteStyles

Retrieves a list of available sprite styles.

#### Syntax

```javascript
async function fetchAvailableSpriteStyles()
```

#### Return Value

The function returns an array of strings representing available sprite styles.

#### Example Usage

```javascript
const styles = await fetchAvailableSpriteStyles();
console.log(styles); // ['pixel-art', 'vector', '3d', 'hand-drawn', 'anime']
```

### generateEnvironmentSprites

Generates a tileset of environment sprites based on the provided description and options.

#### Syntax

```javascript
async function generateEnvironmentSprites(description, options = {})
```

#### Parameters

- `description` (string): A textual description of the environment to generate.
- `options` (object, optional): Configuration options for the environment generation.
  - `elements` (number, default: 4): Number of different elements to generate.
  - `size` (string, default: '1024x1024'): Output size of the tileset.
  - `style` (string, default: 'pixel-art'): Art style of the tileset.
  - `padding` (number, default: 1): Padding between elements in the tileset.
  - `theme` (string, default: 'fantasy'): Theme of the environment.
  - `save` (boolean, default: false): Whether to save the generated image to disk.

#### Return Value

The function returns an object with the following properties:

- `original` (string): URL of the originally generated image.
- `tileset` (string): Base64-encoded data URI of the processed tileset.
- `metadata` (object): Metadata about the generated environment tileset.
  - `elements` (number): Number of elements in the tileset.
  - `theme` (string): Theme of the environment.
  - `dimensions` (object): Width and height of the tileset.
  - `tileData` (object): Information about the tile arrangement.

#### Example Usage

```javascript
const environment = await generateEnvironmentSprites('A mystical forest', {
  elements: 6,
  size: '2048x2048',
  style: 'pixel-art',
  theme: 'fantasy',
  save: true
});

console.log(environment.metadata);
```

This concludes the API reference for the SpriteAI library. For any additional information or support, please refer to the official documentation or contact the library maintainers.