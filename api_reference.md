<response>

# SpriteAI API Reference

This document provides a comprehensive API reference for the SpriteAI module. It covers all public functions, their parameters, return values, and example usage for both the main `index.js` and additional SDK functions in `spriteAI/index.js`.

## Table of Contents

1. [generateCharacterSpritesheet](#generatecharacterspritesheet)
2. [generateLandscapeSprite](#generatelandscapesprite)
3. [fetchAvailableAnimationStates](#fetchavailableanimationstates)
4. [fetchAvailableSpriteStyles](#fetchavailablespritestyles)
5. [generateEnvironmentSprites](#generateenvironmentsprites)
6. [removeBackgroundColor](#removebackgroundcolor)

---

## generateCharacterSpritesheet

Generates a character spritesheet based on the provided description and options.

### Parameters

- `description` (string): A description of the character to generate.
- `options` (object, optional): Configuration options for the spritesheet generation.
  - `states` (array of strings, default: `['idle', 'walk', 'run', 'attack']`): Animation states to generate.
  - `framesPerState` (number, default: 6): Number of frames per animation state.
  - `size` (string, default: '1024x1024'): Output size of the spritesheet.
  - `style` (string, default: 'pixel-art'): Art style of the spritesheet.
  - `padding` (number, default: 1): Padding between sprites.
  - `direction` (string, default: 'right'): Base direction of the character.
  - `save` (boolean): Whether to save the generated image to the filesystem.

### Returns

An object containing:
- `original` (string): URL of the original generated image.
- `spritesheet` (string): Base64-encoded spritesheet image.
- `metadata` (object): Metadata about the generated spritesheet.

### Example Usage

```javascript
import { generateCharacterSpritesheet } from './spriteAI';

const result = await generateCharacterSpritesheet('a medieval knight', {
  states: ['idle', 'walk', 'attack'],
  framesPerState: 8,
  size: '2048x2048',
  style: 'pixel-art',
  save: true
});

console.log(result.metadata);
```

---

## generateLandscapeSprite

Generates a landscape sprite based on the provided description and options.

### Parameters

- `description` (string): A description of the landscape to generate.
- `options` (object, optional): Configuration options for the landscape generation.
  - `size` (string, default: '1024x1024'): Output size of the sprite.
  - `style` (string, default: 'pixel-art'): Art style of the sprite.
  - `timeOfDay` (string, default: 'day'): Time of day setting (day, night, sunset, dawn).
  - `weather` (string, default: 'clear'): Weather conditions (clear, rainy, foggy, snowy).
  - `perspective` (string, default: 'side-scrolling'): Perspective of the landscape (side-scrolling, top-down, isometric).
  - `save` (boolean, default: false): Whether to save the generated image to the filesystem.
  - `removeBackground` (boolean): Whether to remove the background of the generated image.
  - `backgroundColor` (string): Background color to remove (if removeBackground is true).
  - `colorThreshold` (number): Threshold for color removal (if removeBackground is true).

### Returns

An object containing:
- `original` (string): URL of the original generated image.
- `landscape` (string): Base64-encoded landscape image.
- `metadata` (object): Metadata about the generated landscape.

### Example Usage

```javascript
import { generateLandscapeSprite } from './spriteAI';

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
```

---

## fetchAvailableAnimationStates

Retrieves a list of available animation states for character spritesheets.

### Parameters

None

### Returns

An array of strings representing available animation states.

### Example Usage

```javascript
import { fetchAvailableAnimationStates } from './spriteAI';

const states = await fetchAvailableAnimationStates();
console.log(states);
// Output: ['idle', 'walk', 'run', 'attack', 'jump', 'fall', 'hurt', 'die']
```

---

## fetchAvailableSpriteStyles

Retrieves a list of available sprite styles.

### Parameters

None

### Returns

An array of strings representing available sprite styles.

### Example Usage

```javascript
import { fetchAvailableSpriteStyles } from './spriteAI';

const styles = await fetchAvailableSpriteStyles();
console.log(styles);
// Output: ['pixel-art', 'vector', '3d', 'hand-drawn', 'anime']
```

---

## generateEnvironmentSprites

Generates a tileset of environment sprites based on the provided description and options.

### Parameters

- `description` (string): A description of the environment to generate.
- `options` (object, optional): Configuration options for the environment generation.
  - `elements` (number, default: 4): Number of different elements to generate.
  - `size` (string, default: '1024x1024'): Output size of the tileset.
  - `style` (string, default: 'pixel-art'): Art style of the sprites.
  - `padding` (number, default: 1): Padding between sprites.
  - `theme` (string, default: 'fantasy'): Theme of the environment.
  - `save` (boolean): Whether to save the generated image to the filesystem.

### Returns

An object containing:
- `original` (string): URL of the original generated image.
- `tileset` (string): Base64-encoded tileset image.
- `metadata` (object): Metadata about the generated environment sprites.

### Example Usage

```javascript
import { generateEnvironmentSprites } from './spriteAI';

const result = await generateEnvironmentSprites('a desert oasis', {
  elements: 6,
  size: '2048x2048',
  style: 'pixel-art',
  theme: 'desert',
  save: true
});

console.log(result.metadata);
```

---

## removeBackgroundColor

Removes a specified background color from an image.

### Parameters

- `inputPath` (string): Path to the input image file.
- `outputPath` (string): Path where the processed image will be saved.
- `targetColor` (string): CSS color string of the background color to remove.
- `colorThreshold` (number, default: 0): Threshold for color matching.
- `options` (object, optional): Additional options for background removal.

### Returns

A promise that resolves when the background removal is complete.

### Example Usage

```javascript
import { removeBackgroundColor } from './spriteAI';

await removeBackgroundColor(
  'input_image.png',
  'output_image.png',
  '#FFFFFF',
  0.1
);

console.log('Background removed successfully');
```

---

This API reference provides a comprehensive overview of the main functions available in the SpriteAI module. For any additional information or specific use cases, please refer to the individual function documentation or consult the SpriteAI development team.

</response># SpriteAI API Reference

This document provides a comprehensive API reference for the SpriteAI module. It covers all public functions, their parameters, return values, and example usage for both the main `index.js` and additional SDK functions in `spriteAI/index.js`.

## Table of Contents

1. [generateCharacterSpritesheet](#generatecharacterspritesheet)
2. [generateLandscapeSprite](#generatelandscapesprite)
3. [fetchAvailableAnimationStates](#fetchavailableanimationstates)
4. [fetchAvailableSpriteStyles](#fetchavailablespritestyles)
5. [generateEnvironmentSprites](#generateenvironmentsprites)
6. [removeBackgroundColor](#removebackgroundcolor)

---

## generateCharacterSpritesheet

Generates a character spritesheet based on the provided description and options.

### Parameters

- `description` (string): A description of the character to generate.
- `options` (object, optional): Configuration options for the spritesheet generation.
  - `states` (array of strings, default: `['idle', 'walk', 'run', 'attack']`): Animation states to generate.
  - `framesPerState` (number, default: 6): Number of frames per animation state.
  - `size` (string, default: '1024x1024'): Output size of the spritesheet.
  - `style` (string, default: 'pixel-art'): Art style of the spritesheet.
  - `padding` (number, default: 1): Padding between sprites.
  - `direction` (string, default: 'right'): Base direction of the character.
  - `save` (boolean): Whether to save the generated image to the filesystem.

### Returns

An object containing:
- `original` (string): URL of the original generated image.
- `spritesheet` (string): Base64-encoded spritesheet image.
- `metadata` (object): Metadata about the generated spritesheet.

### Example Usage

```javascript
import { generateCharacterSpritesheet } from './spriteAI';

const result = await generateCharacterSpritesheet('a medieval knight', {
  states: ['idle', 'walk', 'attack'],
  framesPerState: 8,
  size: '2048x2048',
  style: 'pixel-art',
  save: true
});

console.log(result.metadata);
```

---

## generateLandscapeSprite

Generates a landscape sprite based on the provided description and options.

### Parameters

- `description` (string): A description of the landscape to generate.
- `options` (object, optional): Configuration options for the landscape generation.
  - `size` (string, default: '1024x1024'): Output size of the sprite.
  - `style` (string, default: 'pixel-art'): Art style of the sprite.
  - `timeOfDay` (string, default: 'day'): Time of day setting (day, night, sunset, dawn).
  - `weather` (string, default: 'clear'): Weather conditions (clear, rainy, foggy, snowy).
  - `perspective` (string, default: 'side-scrolling'): Perspective of the landscape (side-scrolling, top-down, isometric).
  - `save` (boolean, default: false): Whether to save the generated image to the filesystem.
  - `removeBackground` (boolean): Whether to remove the background of the generated image.
  - `backgroundColor` (string): Background color to remove (if removeBackground is true).
  - `colorThreshold` (number): Threshold for color removal (if removeBackground is true).

### Returns

An object containing:
- `original` (string): URL of the original generated image.
- `landscape` (string): Base64-encoded landscape image.
- `metadata` (object): Metadata about the generated landscape.

### Example Usage

```javascript
import { generateLandscapeSprite } from './spriteAI';

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
```

---

## fetchAvailableAnimationStates

Retrieves a list of available animation states for character spritesheets.

### Parameters

None

### Returns

An array of strings representing available animation states.

### Example Usage

```javascript
import { fetchAvailableAnimationStates } from './spriteAI';

const states = await fetchAvailableAnimationStates();
console.log(states);
// Output: ['idle', 'walk', 'run', 'attack', 'jump', 'fall', 'hurt', 'die']
```

---

## fetchAvailableSpriteStyles

Retrieves a list of available sprite styles.

### Parameters

None

### Returns

An array of strings representing available sprite styles.

### Example Usage

```javascript
import { fetchAvailableSpriteStyles } from './spriteAI';

const styles = await fetchAvailableSpriteStyles();
console.log(styles);
// Output: ['pixel-art', 'vector', '3d', 'hand-drawn', 'anime']
```

---

## generateEnvironmentSprites

Generates a tileset of environment sprites based on the provided description and options.

### Parameters

- `description` (string): A description of the environment to generate.
- `options` (object, optional): Configuration options for the environment generation.
  - `elements` (number, default: 4): Number of different elements to generate.
  - `size` (string, default: '1024x1024'): Output size of the tileset.
  - `style` (string, default: 'pixel-art'): Art style of the sprites.
  - `padding` (number, default: 1): Padding between sprites.
  - `theme` (string, default: 'fantasy'): Theme of the environment.
  - `save` (boolean): Whether to save the generated image to the filesystem.

### Returns

An object containing:
- `original` (string): URL of the original generated image.
- `tileset` (string): Base64-encoded tileset image.
- `metadata` (object): Metadata about the generated environment sprites.

### Example Usage

```javascript
import { generateEnvironmentSprites } from './spriteAI';

const result = await generateEnvironmentSprites('a desert oasis', {
  elements: 6,
  size: '2048x2048',
  style: 'pixel-art',
  theme: 'desert',
  save: true
});

console.log(result.metadata);
```

---

## removeBackgroundColor

Removes a specified background color from an image.

### Parameters

- `inputPath` (string): Path to the input image file.
- `outputPath` (string): Path where the processed image will be saved.
- `targetColor` (string): CSS color string of the background color to remove.
- `colorThreshold` (number, default: 0): Threshold for color matching.
- `options` (object, optional): Additional options for background removal.

### Returns

A promise that resolves when the background removal is complete.

### Example Usage

```javascript
import { removeBackgroundColor } from './spriteAI';

await removeBackgroundColor(
  'input_image.png',
  'output_image.png',
  '#FFFFFF',
  0.1
);

console.log('Background removed successfully');
```

---

This API reference provides a comprehensive overview of the main functions available in the SpriteAI module. For any additional information or specific use cases, please refer to the individual function documentation or consult the SpriteAI development team.