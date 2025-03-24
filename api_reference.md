<response>

# SpriteAI API Reference

This document provides a comprehensive API reference for the SpriteAI module, covering both the main `index.js` file and the SDK version in `spriteAI/index.js`.

## Table of Contents

1. [generateCharacterSpritesheet](#generatecharacterspritesheet)
2. [generateLandscapeSprite](#generatelandscapesprite)
3. [fetchAvailableAnimationStates](#fetchavailableanimationstates)
4. [fetchAvailableSpriteStyles](#fetchavailablespritestyles)
5. [generateEnvironmentSprites](#generateenvironmentsprites)
6. [removeBackgroundColor](#removebackgroundcolor)

---

## generateCharacterSpritesheet

Generates a character spritesheet based on a given description and options.

### Function Signature

```javascript
async function generateCharacterSpritesheet(description, options = {})
```

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
- `spritesheet` (string): Base64-encoded string of the processed spritesheet.
- `metadata` (object): Metadata about the generated spritesheet, including:
  - `states` (array): List of animation states.
  - `framesPerState` (number): Number of frames per state.
  - `totalFrames` (number): Total number of frames in the spritesheet.
  - `dimensions` (object): Width and height of the spritesheet.
  - `frameData` (object): Detailed information about each animation state's frames.

### Example Usage

```javascript
const characterSprite = await generateCharacterSpritesheet('a cute robot', {
  states: ['idle', 'walk', 'jump'],
  framesPerState: 8,
  size: '2048x2048',
  style: 'pixel-art',
  direction: 'left',
  save: true
});

console.log(characterSprite.metadata);
```

---

## generateLandscapeSprite

Generates a landscape sprite based on a given description and options.

### Function Signature

```javascript
async function generateLandscapeSprite(description, options = {})
```

### Parameters

- `description` (string): A description of the landscape to generate.
- `options` (object, optional): Configuration options for the landscape generation.
  - `size` (string, default: '1024x1024'): Output size of the sprite.
  - `style` (string, default: 'pixel-art'): Art style of the sprite.
  - `timeOfDay` (string, default: 'day'): Time of day setting (e.g., 'day', 'night', 'sunset', 'dawn').
  - `weather` (string, default: 'clear'): Weather conditions (e.g., 'clear', 'rainy', 'foggy', 'snowy').
  - `perspective` (string, default: 'side-scrolling'): Perspective of the landscape (e.g., 'side-scrolling', 'top-down', 'isometric').
  - `save` (boolean, default: false): Whether to save the generated image to disk.
  - `removeBackground` (boolean): Whether to remove the background of the generated image.
  - `backgroundColor` (string): The background color to remove (if removeBackground is true).
  - `colorThreshold` (number): The color threshold for background removal (if removeBackground is true).

### Return Value

Returns an object with the following properties:

- `original` (string): URL of the original generated image.
- `landscape` (string): Base64-encoded string of the processed landscape sprite.
- `metadata` (object): Metadata about the generated landscape, including:
  - `description` (string): The original description used to generate the sprite.
  - `style` (string): The art style used.
  - `timeOfDay` (string): The time of day setting.
  - `weather` (string): The weather conditions.
  - `perspective` (string): The perspective used.
  - `dimensions` (object): Width and height of the sprite.

### Example Usage

```javascript
const landscapeSprite = await generateLandscapeSprite('a lush forest with a river', {
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

---

## fetchAvailableAnimationStates

Fetches the available animation states for character spritesheets.

### Function Signature

```javascript
async function fetchAvailableAnimationStates()
```

### Return Value

Returns an array of strings representing the available animation states.

### Example Usage

```javascript
const states = await fetchAvailableAnimationStates();
console.log(states); // ['idle', 'walk', 'run', 'attack', 'jump', 'fall', 'hurt', 'die']
```

---

## fetchAvailableSpriteStyles

Fetches the available sprite styles for generation.

### Function Signature

```javascript
async function fetchAvailableSpriteStyles()
```

### Return Value

Returns an array of strings representing the available sprite styles.

### Example Usage

```javascript
const styles = await fetchAvailableSpriteStyles();
console.log(styles); // ['pixel-art', 'vector', '3d', 'hand-drawn', 'anime']
```

---

## generateEnvironmentSprites

Generates a set of environment sprites based on a given description and options.

### Function Signature

```javascript
async function generateEnvironmentSprites(description, options = {})
```

### Parameters

- `description` (string): A description of the environment to generate.
- `options` (object, optional): Configuration options for the environment sprite generation.
  - `elements` (number, default: 4): Number of different elements to generate.
  - `size` (string, default: '1024x1024'): Output size of the tileset.
  - `style` (string, default: 'pixel-art'): Art style of the sprites.
  - `padding` (number, default: 1): Padding between sprites.
  - `theme` (string, default: 'fantasy'): Theme of the environment.
  - `save` (boolean): Whether to save the generated image to disk.

### Return Value

Returns an object with the following properties:

- `original` (string): URL of the original generated image.
- `tileset` (string): Base64-encoded string of the processed environment tileset.
- `metadata` (object): Metadata about the generated environment sprites, including:
  - `elements` (number): Number of different elements generated.
  - `theme` (string): The theme used for generation.
  - `dimensions` (object): Width and height of the tileset.
  - `tileData` (object): Information about the tile arrangement.

### Example Usage

```javascript
const environmentSprites = await generateEnvironmentSprites('medieval castle', {
  elements: 6,
  size: '2048x2048',
  style: 'pixel-art',
  theme: 'medieval',
  save: true
});

console.log(environmentSprites.metadata);
```

---

## removeBackgroundColor

Removes a specified background color from an image.

### Function Signature

```javascript
async function removeBackgroundColor(inputPath, outputPath, targetColor, colorThreshold = 0, options = {})
```

### Parameters

- `inputPath` (string): Path to the input image file.
- `outputPath` (string): Path where the processed image will be saved.
- `targetColor` (string): The color to be removed (e.g., '#FFFFFF' for white).
- `colorThreshold` (number, default: 0): Tolerance for color matching.
- `options` (object, optional): Additional options for background removal.

### Return Value

Returns the result of the image processing operation.

### Example Usage

```javascript
const result = await removeBackgroundColor(
  'input.png',
  'output.png',
  '#FFFFFF',
  0.1
);
console.log('Background removal complete:', result);
```

</response># SpriteAI API Reference

This document provides a comprehensive API reference for the SpriteAI module, covering both the main `index.js` file and the SDK version in `spriteAI/index.js`.

## Table of Contents

1. [generateCharacterSpritesheet](#generatecharacterspritesheet)
2. [generateLandscapeSprite](#generatelandscapesprite)
3. [fetchAvailableAnimationStates](#fetchavailableanimationstates)
4. [fetchAvailableSpriteStyles](#fetchavailablespritestyles)
5. [generateEnvironmentSprites](#generateenvironmentsprites)
6. [removeBackgroundColor](#removebackgroundcolor)

---

## generateCharacterSpritesheet

Generates a character spritesheet based on a given description and options.

### Function Signature

```javascript
async function generateCharacterSpritesheet(description, options = {})
```

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
- `spritesheet` (string): Base64-encoded string of the processed spritesheet.
- `metadata` (object): Metadata about the generated spritesheet, including:
  - `states` (array): List of animation states.
  - `framesPerState` (number): Number of frames per state.
  - `totalFrames` (number): Total number of frames in the spritesheet.
  - `dimensions` (object): Width and height of the spritesheet.
  - `frameData` (object): Detailed information about each animation state's frames.

### Example Usage

```javascript
const characterSprite = await generateCharacterSpritesheet('a cute robot', {
  states: ['idle', 'walk', 'jump'],
  framesPerState: 8,
  size: '2048x2048',
  style: 'pixel-art',
  direction: 'left',
  save: true
});

console.log(characterSprite.metadata);
```

---

## generateLandscapeSprite

Generates a landscape sprite based on a given description and options.

### Function Signature

```javascript
async function generateLandscapeSprite(description, options = {})
```

### Parameters

- `description` (string): A description of the landscape to generate.
- `options` (object, optional): Configuration options for the landscape generation.
  - `size` (string, default: '1024x1024'): Output size of the sprite.
  - `style` (string, default: 'pixel-art'): Art style of the sprite.
  - `timeOfDay` (string, default: 'day'): Time of day setting (e.g., 'day', 'night', 'sunset', 'dawn').
  - `weather` (string, default: 'clear'): Weather conditions (e.g., 'clear', 'rainy', 'foggy', 'snowy').
  - `perspective` (string, default: 'side-scrolling'): Perspective of the landscape (e.g., 'side-scrolling', 'top-down', 'isometric').
  - `save` (boolean, default: false): Whether to save the generated image to disk.
  - `removeBackground` (boolean): Whether to remove the background of the generated image.
  - `backgroundColor` (string): The background color to remove (if removeBackground is true).
  - `colorThreshold` (number): The color threshold for background removal (if removeBackground is true).

### Return Value

Returns an object with the following properties:

- `original` (string): URL of the original generated image.
- `landscape` (string): Base64-encoded string of the processed landscape sprite.
- `metadata` (object): Metadata about the generated landscape, including:
  - `description` (string): The original description used to generate the sprite.
  - `style` (string): The art style used.
  - `timeOfDay` (string): The time of day setting.
  - `weather` (string): The weather conditions.
  - `perspective` (string): The perspective used.
  - `dimensions` (object): Width and height of the sprite.

### Example Usage

```javascript
const landscapeSprite = await generateLandscapeSprite('a lush forest with a river', {
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

---

## fetchAvailableAnimationStates

Fetches the available animation states for character spritesheets.

### Function Signature

```javascript
async function fetchAvailableAnimationStates()
```

### Return Value

Returns an array of strings representing the available animation states.

### Example Usage

```javascript
const states = await fetchAvailableAnimationStates();
console.log(states); // ['idle', 'walk', 'run', 'attack', 'jump', 'fall', 'hurt', 'die']
```

---

## fetchAvailableSpriteStyles

Fetches the available sprite styles for generation.

### Function Signature

```javascript
async function fetchAvailableSpriteStyles()
```

### Return Value

Returns an array of strings representing the available sprite styles.

### Example Usage

```javascript
const styles = await fetchAvailableSpriteStyles();
console.log(styles); // ['pixel-art', 'vector', '3d', 'hand-drawn', 'anime']
```

---

## generateEnvironmentSprites

Generates a set of environment sprites based on a given description and options.

### Function Signature

```javascript
async function generateEnvironmentSprites(description, options = {})
```

### Parameters

- `description` (string): A description of the environment to generate.
- `options` (object, optional): Configuration options for the environment sprite generation.
  - `elements` (number, default: 4): Number of different elements to generate.
  - `size` (string, default: '1024x1024'): Output size of the tileset.
  - `style` (string, default: 'pixel-art'): Art style of the sprites.
  - `padding` (number, default: 1): Padding between sprites.
  - `theme` (string, default: 'fantasy'): Theme of the environment.
  - `save` (boolean): Whether to save the generated image to disk.

### Return Value

Returns an object with the following properties:

- `original` (string): URL of the original generated image.
- `tileset` (string): Base64-encoded string of the processed environment tileset.
- `metadata` (object): Metadata about the generated environment sprites, including:
  - `elements` (number): Number of different elements generated.
  - `theme` (string): The theme used for generation.
  - `dimensions` (object): Width and height of the tileset.
  - `tileData` (object): Information about the tile arrangement.

### Example Usage

```javascript
const environmentSprites = await generateEnvironmentSprites('medieval castle', {
  elements: 6,
  size: '2048x2048',
  style: 'pixel-art',
  theme: 'medieval',
  save: true
});

console.log(environmentSprites.metadata);
```

---

## removeBackgroundColor

Removes a specified background color from an image.

### Function Signature

```javascript
async function removeBackgroundColor(inputPath, outputPath, targetColor, colorThreshold = 0, options = {})
```

### Parameters

- `inputPath` (string): Path to the input image file.
- `outputPath` (string): Path where the processed image will be saved.
- `targetColor` (string): The color to be removed (e.g., '#FFFFFF' for white).
- `colorThreshold` (number, default: 0): Tolerance for color matching.
- `options` (object, optional): Additional options for background removal.

### Return Value

Returns the result of the image processing operation.

### Example Usage

```javascript
const result = await removeBackgroundColor(
  'input.png',
  'output.png',
  '#FFFFFF',
  0.1
);
console.log('Background removal complete:', result);
```