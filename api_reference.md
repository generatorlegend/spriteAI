<response>

# SpriteAI API Reference

## Table of Contents
1. [generateCharacterSpritesheet](#generatecharacterspritesheet)
2. [generateLandscapeSprite](#generatelandscapesprite)
3. [fetchAvailableAnimationStates](#fetchavailableanimationstates)
4. [fetchAvailableSpriteStyles](#fetchavailablespritestyles)
5. [generateEnvironmentSprites](#generateenvironmentsprites)
6. [removeBackgroundColor](#removebackgroundcolor)

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
  - `save` (boolean): Whether to save the generated image to disk.

### Returns

An object containing:
- `original` (string): URL of the original generated image.
- `spritesheet` (string): Base64-encoded data URL of the processed spritesheet.
- `metadata` (object): Metadata about the generated spritesheet.

### Example Usage

```javascript
import { generateCharacterSpritesheet } from 'spriteAI';

const result = await generateCharacterSpritesheet('a medieval knight', {
  states: ['idle', 'walk', 'attack', 'die'],
  framesPerState: 8,
  size: '2048x2048',
  style: 'pixel-art',
  save: true
});

console.log(result.metadata);
```

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
  - `save` (boolean, default: false): Whether to save the generated image to disk.
  - `removeBackground` (boolean): Whether to remove the background from the generated image.
  - `backgroundColor` (string): Target color to remove when removing background.
  - `colorThreshold` (number): Threshold for color removal when removing background.

### Returns

An object containing:
- `original` (string): URL of the original generated image.
- `landscape` (string): Base64-encoded data URL of the processed landscape sprite.
- `metadata` (object): Metadata about the generated landscape.

### Example Usage

```javascript
import { generateLandscapeSprite } from 'spriteAI';

const result = await generateLandscapeSprite('a lush forest with a cascading waterfall', {
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

## fetchAvailableAnimationStates

Retrieves a list of available animation states for character spritesheets.

### Parameters

None

### Returns

An array of strings representing available animation states.

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

### Returns

An array of strings representing available sprite styles.

### Example Usage

```javascript
import { fetchAvailableSpriteStyles } from 'spriteAI';

const styles = await fetchAvailableSpriteStyles();
console.log(styles);
// Output: ['pixel-art', 'vector', '3d', 'hand-drawn', 'anime']
```

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
  - `save` (boolean): Whether to save the generated image to disk.

### Returns

An object containing:
- `original` (string): URL of the original generated image.
- `tileset` (string): Base64-encoded data URL of the processed tileset.
- `metadata` (object): Metadata about the generated environment sprites.

### Example Usage

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
```

## removeBackgroundColor

Removes a specified background color from an image.

### Parameters

- `inputPath` (string): Path to the input image file.
- `outputPath` (string): Path where the processed image will be saved.
- `targetColor` (string): CSS color string representing the color to be removed.
- `colorThreshold` (number, default: 0): Threshold for color matching.
- `options` (object, optional): Additional options for background removal.

### Returns

A Promise that resolves when the background removal is complete.

### Example Usage

```javascript
import { removeBackgroundColor } from 'spriteAI';

await removeBackgroundColor(
  'input.png',
  'output.png',
  '#FFFFFF',
  0.1
);

console.log('Background removed successfully');
```

</response># SpriteAI API Reference

## Table of Contents
1. [generateCharacterSpritesheet](#generatecharacterspritesheet)
2. [generateLandscapeSprite](#generatelandscapesprite)
3. [fetchAvailableAnimationStates](#fetchavailableanimationstates)
4. [fetchAvailableSpriteStyles](#fetchavailablespritestyles)
5. [generateEnvironmentSprites](#generateenvironmentsprites)
6. [removeBackgroundColor](#removebackgroundcolor)

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
  - `save` (boolean): Whether to save the generated image to disk.

### Returns

An object containing:
- `original` (string): URL of the original generated image.
- `spritesheet` (string): Base64-encoded data URL of the processed spritesheet.
- `metadata` (object): Metadata about the generated spritesheet.

### Example Usage

```javascript
import { generateCharacterSpritesheet } from 'spriteAI';

const result = await generateCharacterSpritesheet('a medieval knight', {
  states: ['idle', 'walk', 'attack', 'die'],
  framesPerState: 8,
  size: '2048x2048',
  style: 'pixel-art',
  save: true
});

console.log(result.metadata);
```

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
  - `save` (boolean, default: false): Whether to save the generated image to disk.
  - `removeBackground` (boolean): Whether to remove the background from the generated image.
  - `backgroundColor` (string): Target color to remove when removing background.
  - `colorThreshold` (number): Threshold for color removal when removing background.

### Returns

An object containing:
- `original` (string): URL of the original generated image.
- `landscape` (string): Base64-encoded data URL of the processed landscape sprite.
- `metadata` (object): Metadata about the generated landscape.

### Example Usage

```javascript
import { generateLandscapeSprite } from 'spriteAI';

const result = await generateLandscapeSprite('a lush forest with a cascading waterfall', {
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

## fetchAvailableAnimationStates

Retrieves a list of available animation states for character spritesheets.

### Parameters

None

### Returns

An array of strings representing available animation states.

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

### Returns

An array of strings representing available sprite styles.

### Example Usage

```javascript
import { fetchAvailableSpriteStyles } from 'spriteAI';

const styles = await fetchAvailableSpriteStyles();
console.log(styles);
// Output: ['pixel-art', 'vector', '3d', 'hand-drawn', 'anime']
```

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
  - `save` (boolean): Whether to save the generated image to disk.

### Returns

An object containing:
- `original` (string): URL of the original generated image.
- `tileset` (string): Base64-encoded data URL of the processed tileset.
- `metadata` (object): Metadata about the generated environment sprites.

### Example Usage

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
```

## removeBackgroundColor

Removes a specified background color from an image.

### Parameters

- `inputPath` (string): Path to the input image file.
- `outputPath` (string): Path where the processed image will be saved.
- `targetColor` (string): CSS color string representing the color to be removed.
- `colorThreshold` (number, default: 0): Threshold for color matching.
- `options` (object, optional): Additional options for background removal.

### Returns

A Promise that resolves when the background removal is complete.

### Example Usage

```javascript
import { removeBackgroundColor } from 'spriteAI';

await removeBackgroundColor(
  'input.png',
  'output.png',
  '#FFFFFF',
  0.1
);

console.log('Background removed successfully');
```