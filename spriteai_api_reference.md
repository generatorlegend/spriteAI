<response>

# SpriteAI API Reference

This document provides a comprehensive API reference for SpriteAI's public functions. It includes detailed descriptions of the main functions, their parameters, return values, and usage examples.

## Table of Contents

1. [generateCharacterSpritesheet](#generatecharacterspritesheet)
2. [generateLandscapeSprite](#generatelandscapesprite)
3. [fetchAvailableAnimationStates](#fetchavailableanimationstates)
4. [fetchAvailableSpriteStyles](#fetchavailablespritestyles)
5. [generateEnvironmentSprites](#generateenvironmentsprites)

## generateCharacterSpritesheet

Generates a character spritesheet based on a given description and options.

### Parameters

- `description` (string): A description of the character to generate.
- `options` (object, optional): An object containing additional options for spritesheet generation.
  - `states` (array of strings, default: `['idle', 'walk', 'run', 'attack']`): Animation states to generate.
  - `framesPerState` (number, default: 6): Number of frames per animation state.
  - `size` (string, default: '1024x1024'): Output size of the spritesheet.
  - `style` (string, default: 'pixel-art'): Art style of the spritesheet.
  - `padding` (number, default: 1): Padding between sprites.
  - `direction` (string, default: 'right'): Base direction of the character.
  - `save` (boolean, default: false): Whether to save the generated image to disk.

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

### Example Usage

```javascript
import { generateCharacterSpritesheet } from 'spriteAI';

const character = await generateCharacterSpritesheet('a brave knight in shining armor', {
  states: ['idle', 'walk', 'attack', 'defend'],
  framesPerState: 8,
  size: '2048x2048',
  style: 'pixel-art',
  direction: 'left',
  save: true
});

console.log(character.metadata);
// Use character.spritesheet for rendering in your game
```

## generateLandscapeSprite

Generates a landscape sprite based on a given description and options.

### Parameters

- `description` (string): A description of the landscape to generate.
- `options` (object, optional): An object containing additional options for landscape generation.
  - `size` (string, default: '1024x1024'): Output size of the landscape sprite.
  - `style` (string, default: 'pixel-art'): Art style of the landscape.
  - `timeOfDay` (string, default: 'day'): Time of day setting (day, night, sunset, dawn).
  - `weather` (string, default: 'clear'): Weather conditions (clear, rainy, foggy, snowy).
  - `perspective` (string, default: 'side-scrolling'): Perspective of the landscape (side-scrolling, top-down, isometric).
  - `save` (boolean, default: false): Whether to save the generated image to disk.
  - `removeBackground` (boolean, optional): Whether to remove the background of the generated image.
  - `backgroundColor` (string, optional): Color to be removed if removeBackground is true.
  - `colorThreshold` (number, optional): Threshold for color removal if removeBackground is true.

### Return Value

Returns an object with the following properties:

- `original` (string): URL of the original generated image.
- `landscape` (string): Base64-encoded data URL of the processed landscape sprite.
- `metadata` (object): Metadata about the generated landscape, including:
  - `description` (string): The original description used.
  - `style` (string): The art style used.
  - `timeOfDay` (string): The time of day setting.
  - `weather` (string): The weather conditions.
  - `perspective` (string): The perspective used.
  - `dimensions` (object): Width and height of the landscape sprite.

### Example Usage

```javascript
import { generateLandscapeSprite } from 'spriteAI';

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

Retrieves a list of available animation states for character sprites.

### Parameters

None

### Return Value

Returns a Promise that resolves to an array of strings representing available animation states.

### Example Usage

```javascript
import { fetchAvailableAnimationStates } from 'spriteAI';

const states = await fetchAvailableAnimationStates();
console.log(states);
// Output: ['idle', 'walk', 'run', 'attack', 'jump', 'fall', 'hurt', 'die']
```

## fetchAvailableSpriteStyles

Retrieves a list of available sprite styles.

### Parameters

None

### Return Value

Returns a Promise that resolves to an array of strings representing available sprite styles.

### Example Usage

```javascript
import { fetchAvailableSpriteStyles } from 'spriteAI';

const styles = await fetchAvailableSpriteStyles();
console.log(styles);
// Output: ['pixel-art', 'vector', '3d', 'hand-drawn', 'anime']
```

## generateEnvironmentSprites

Generates a tileset of environment sprites based on a given description and options.

### Parameters

- `description` (string): A description of the environment to generate.
- `options` (object, optional): An object containing additional options for environment sprite generation.
  - `elements` (number, default: 4): Number of different elements to generate.
  - `size` (string, default: '1024x1024'): Output size of the tileset.
  - `style` (string, default: 'pixel-art'): Art style of the environment sprites.
  - `padding` (number, default: 1): Padding between sprite elements.
  - `theme` (string, default: 'fantasy'): Theme of the environment.
  - `save` (boolean, default: false): Whether to save the generated image to disk.

### Return Value

Returns an object with the following properties:

- `original` (string): URL of the original generated image.
- `tileset` (string): Base64-encoded data URL of the processed environment tileset.
- `metadata` (object): Metadata about the generated environment sprites, including:
  - `elements` (number): Number of different elements generated.
  - `theme` (string): The theme used for generation.
  - `dimensions` (object): Width and height of the tileset.
  - `tileData` (object): Information about the tile arrangement, including rows, columns, and total tiles.

### Example Usage

```javascript
import { generateEnvironmentSprites } from 'spriteAI';

const environment = await generateEnvironmentSprites('a magical forest with ancient ruins', {
  elements: 6,
  size: '2048x2048',
  style: 'pixel-art',
  theme: 'fantasy',
  save: true
});

console.log(environment.metadata);
// Use environment.tileset for rendering in your game
```

This API reference provides developers with the necessary information to utilize the SpriteAI library effectively in their projects. Each function is documented with its parameters, return values, and example usage to facilitate easy integration and understanding of the library's capabilities.

</response>