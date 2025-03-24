# SpriteAI API Reference

This document provides a comprehensive reference for the SpriteAI library, detailing all exported functions, their parameters, return values, and usage examples.

## Table of Contents

1. [generateCharacterSpritesheet](#generatecharacterspritesheet)
2. [generateLandscapeSprite](#generatelandscapesprite)
3. [fetchAvailableAnimationStates](#fetchavailableanimationstates)
4. [fetchAvailableSpriteStyles](#fetchavailablespritestyles)
5. [generateEnvironmentSprites](#generateenvironmentsprites)

## generateCharacterSpritesheet

Generates a character spritesheet with multiple animation states.

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

### Returns

An object containing:
- `original` (string): URL of the original generated image.
- `spritesheet` (string): Base64-encoded data URL of the processed spritesheet.
- `metadata` (object): Metadata about the generated spritesheet, including states, frame counts, and dimensions.

### Example

```javascript
import { generateCharacterSpritesheet } from 'spriteAI';

const result = await generateCharacterSpritesheet('a cute robot', {
  states: ['idle', 'walk', 'jump'],
  framesPerState: 8,
  size: '2048x2048',
  style: 'pixel-art',
  save: true
});

console.log(result.metadata);
// Use result.spritesheet in your game engine
```

## generateLandscapeSprite

Generates a landscape sprite for game backgrounds.

### Parameters

- `description` (string): A description of the landscape to generate.
- `options` (object, optional): Configuration options for the landscape generation.
  - `size` (string, default: '1024x1024'): Output size of the sprite.
  - `style` (string, default: 'pixel-art'): Art style of the landscape.
  - `timeOfDay` (string, default: 'day'): Time of day setting (e.g., 'day', 'night', 'sunset', 'dawn').
  - `weather` (string, default: 'clear'): Weather conditions (e.g., 'clear', 'rainy', 'foggy', 'snowy').
  - `perspective` (string, default: 'side-scrolling'): Perspective of the landscape (e.g., 'side-scrolling', 'top-down', 'isometric').
  - `save` (boolean, default: false): Whether to save the generated image to disk.
  - `removeBackground` (boolean, optional): Whether to remove the background.
  - `backgroundColor` (string, optional): Background color to remove if `removeBackground` is true.
  - `colorThreshold` (number, optional): Threshold for background color removal.

### Returns

An object containing:
- `original` (string): URL of the original generated image.
- `landscape` (string): Base64-encoded data URL of the processed landscape sprite.
- `metadata` (object): Metadata about the generated landscape, including description, style, and dimensions.

### Example

```javascript
import { generateLandscapeSprite } from 'spriteAI';

const result = await generateLandscapeSprite('a lush forest with a river', {
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
// Use result.landscape in your game engine
```

## fetchAvailableAnimationStates

Retrieves a list of available animation states for character spritesheets.

### Parameters

None

### Returns

An array of strings representing available animation states.

### Example

```javascript
import { fetchAvailableAnimationStates } from 'spriteAI';

const states = await fetchAvailableAnimationStates();
console.log(states);
// Output: ['idle', 'walk', 'run', 'attack', 'jump', 'fall', 'hurt', 'die']
```

## fetchAvailableSpriteStyles

Retrieves a list of available sprite styles for character and landscape generation.

### Parameters

None

### Returns

An array of strings representing available sprite styles.

### Example

```javascript
import { fetchAvailableSpriteStyles } from 'spriteAI';

const styles = await fetchAvailableSpriteStyles();
console.log(styles);
// Output: ['pixel-art', 'vector', '3d', 'hand-drawn', 'anime']
```

## generateEnvironmentSprites

Generates a tileset of environment sprites for game backgrounds.

### Parameters

- `description` (string): A description of the environment to generate.
- `options` (object, optional): Configuration options for the environment generation.
  - `elements` (number, default: 4): Number of distinct environment pieces to generate.
  - `size` (string, default: '1024x1024'): Output size of the tileset.
  - `style` (string, default: 'pixel-art'): Art style of the environment.
  - `padding` (number, default: 1): Padding between sprites.
  - `theme` (string, default: 'fantasy'): Theme of the environment.
  - `save` (boolean, default: false): Whether to save the generated image to disk.

### Returns

An object containing:
- `original` (string): URL of the original generated image.
- `tileset` (string): Base64-encoded data URL of the processed environment tileset.
- `metadata` (object): Metadata about the generated tileset, including number of elements, theme, and dimensions.

### Example

```javascript
import { generateEnvironmentSprites } from 'spriteAI';

const result = await generateEnvironmentSprites('a desert oasis', {
  elements: 6,
  size: '2048x2048',
  style: 'pixel-art',
  theme: 'desert',
  save: true
});

console.log(result.metadata);
// Use result.tileset in your game engine
```

This API reference provides a comprehensive overview of the SpriteAI library's capabilities for generating game assets programmatically. Developers can use these functions to create character spritesheets, landscape backgrounds, and environment tilesets for their games, with a high degree of customization and control over the output.