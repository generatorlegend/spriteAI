<response>

# SpriteAI API Reference

## Table of Contents

1. [Introduction](#introduction)
2. [Character Spritesheet Generation](#character-spritesheet-generation)
3. [Landscape Sprite Generation](#landscape-sprite-generation)
4. [Environment Sprites Generation](#environment-sprites-generation)
5. [Utility Functions](#utility-functions)

## Introduction

SpriteAI is a powerful library for generating game assets using AI. This API reference provides detailed information about the main functions and utilities available in the SpriteAI library.

## Character Spritesheet Generation

### generateCharacterSpritesheet

Generates a character spritesheet based on a given description and options.

```javascript
async function generateCharacterSpritesheet(description, options = {})
```

#### Parameters:

- `description` (string): A text description of the character to generate.
- `options` (object, optional): Configuration options for the spritesheet generation.
  - `states` (array of strings): Animation states to generate. Default: `['idle', 'walk', 'run', 'attack']`
  - `framesPerState` (number): Number of frames per animation state. Default: `6`
  - `size` (string): Output size of the spritesheet. Default: `'1024x1024'`
  - `style` (string): Art style of the sprite. Default: `'pixel-art'`
  - `padding` (number): Padding between sprites. Default: `1`
  - `direction` (string): Base direction of the character. Default: `'right'`
  - `save` (boolean): Whether to save the generated image to disk. Default: `false`

#### Returns:

An object containing:
- `original` (string): URL of the original generated image.
- `spritesheet` (string): Base64-encoded data URL of the processed spritesheet.
- `metadata` (object): Metadata about the generated spritesheet, including:
  - `states` (array): List of animation states.
  - `framesPerState` (number): Number of frames per state.
  - `totalFrames` (number): Total number of frames in the spritesheet.
  - `dimensions` (object): Width and height of the spritesheet.
  - `frameData` (object): Detailed information about each animation state's frames.

#### Example Usage:

```javascript
const result = await generateCharacterSpritesheet('a medieval knight in armor', {
  states: ['idle', 'walk', 'attack'],
  framesPerState: 4,
  size: '512x512',
  style: 'pixel-art',
  direction: 'left',
  save: true
});

console.log(result.metadata);
// Use result.spritesheet for rendering in your game
```

## Landscape Sprite Generation

### generateLandscapeSprite

Generates a landscape sprite based on a given description and options.

```javascript
async function generateLandscapeSprite(description, options = {})
```

#### Parameters:

- `description` (string): A text description of the landscape to generate.
- `options` (object, optional): Configuration options for the landscape generation.
  - `size` (string): Output size of the sprite. Default: `'1024x1024'`
  - `style` (string): Art style of the sprite. Default: `'pixel-art'`
  - `timeOfDay` (string): Time of day setting. Default: `'day'`
  - `weather` (string): Weather conditions. Default: `'clear'`
  - `perspective` (string): Perspective of the landscape. Default: `'side-scrolling'`
  - `save` (boolean): Whether to save the generated image to disk. Default: `false`
  - `removeBackground` (boolean): Whether to remove the background. Default: `false`
  - `backgroundColor` (string): Background color to remove (if removeBackground is true). Default: `'#FFFFFF'`
  - `colorThreshold` (number): Threshold for background color removal. Default: `0.1`

#### Returns:

An object containing:
- `original` (string): URL of the original generated image.
- `landscape` (string): Base64-encoded data URL of the processed landscape sprite.
- `metadata` (object): Metadata about the generated landscape, including:
  - `description` (string): Original description used for generation.
  - `style` (string): Art style of the sprite.
  - `timeOfDay` (string): Time of day setting.
  - `weather` (string): Weather conditions.
  - `perspective` (string): Perspective of the landscape.
  - `dimensions` (object): Width and height of the sprite.

#### Example Usage:

```javascript
const result = await generateLandscapeSprite('a mystical forest with glowing mushrooms', {
  size: '512x512',
  style: 'pixel-art',
  timeOfDay: 'night',
  weather: 'foggy',
  perspective: 'side-scrolling',
  removeBackground: true,
  save: true
});

console.log(result.metadata);
// Use result.landscape for rendering in your game
```

## Environment Sprites Generation

### generateEnvironmentSprites

Generates a set of environment sprites based on a given description and options.

```javascript
async function generateEnvironmentSprites(description, options = {})
```

#### Parameters:

- `description` (string): A text description of the environment to generate.
- `options` (object, optional): Configuration options for the environment sprites generation.
  - `elements` (number): Number of different elements to generate. Default: `4`
  - `size` (string): Output size of the tileset. Default: `'1024x1024'`
  - `style` (string): Art style of the sprites. Default: `'pixel-art'`
  - `padding` (number): Padding between sprites. Default: `1`
  - `theme` (string): Theme of the environment. Default: `'fantasy'`
  - `save` (boolean): Whether to save the generated image to disk. Default: `false`

#### Returns:

An object containing:
- `original` (string): URL of the original generated image.
- `tileset` (string): Base64-encoded data URL of the processed environment tileset.
- `metadata` (object): Metadata about the generated environment sprites, including:
  - `elements` (number): Number of different elements generated.
  - `theme` (string): Theme of the environment.
  - `dimensions` (object): Width and height of the tileset.
  - `tileData` (object): Information about the tileset layout.

#### Example Usage:

```javascript
const result = await generateEnvironmentSprites('ancient ruins in a jungle', {
  elements: 6,
  size: '512x512',
  style: 'pixel-art',
  theme: 'adventure',
  save: true
});

console.log(result.metadata);
// Use result.tileset for rendering in your game
```

## Utility Functions

### fetchAvailableAnimationStates

Retrieves a list of available animation states for character spritesheets.

```javascript
async function fetchAvailableAnimationStates()
```

#### Returns:

An array of strings representing available animation states.

#### Example Usage:

```javascript
const states = await fetchAvailableAnimationStates();
console.log(states); // ['idle', 'walk', 'run', 'attack', 'jump', 'fall', 'hurt', 'die']
```

### fetchAvailableSpriteStyles

Retrieves a list of available sprite styles.

```javascript
async function fetchAvailableSpriteStyles()
```

#### Returns:

An array of strings representing available sprite styles.

#### Example Usage:

```javascript
const styles = await fetchAvailableSpriteStyles();
console.log(styles); // ['pixel-art', 'vector', '3d', 'hand-drawn', 'anime']
```

### removeBackgroundColor

Removes a specified background color from an image.

```javascript
async function removeBackgroundColor(inputPath, outputPath, targetColor, colorThreshold = 0, options = {})
```

#### Parameters:

- `inputPath` (string): Path to the input image file.
- `outputPath` (string): Path where the processed image will be saved.
- `targetColor` (string): CSS color string of the background color to remove.
- `colorThreshold` (number, optional): Threshold for color matching. Default: `0`
- `options` (object, optional): Additional options for background removal.

#### Returns:

A promise that resolves when the background removal is complete.

#### Example Usage:

```javascript
await removeBackgroundColor('input.png', 'output.png', '#FFFFFF', 0.1);
console.log('Background removed successfully');
```

This concludes the API reference for the SpriteAI library. For more detailed information on usage and best practices, please refer to the main documentation and examples.

</response># SpriteAI API Reference

## Table of Contents

1. [Introduction](#introduction)
2. [Character Spritesheet Generation](#character-spritesheet-generation)
3. [Landscape Sprite Generation](#landscape-sprite-generation)
4. [Environment Sprites Generation](#environment-sprites-generation)
5. [Utility Functions](#utility-functions)

## Introduction

SpriteAI is a powerful library for generating game assets using AI. This API reference provides detailed information about the main functions and utilities available in the SpriteAI library.

## Character Spritesheet Generation

### generateCharacterSpritesheet

Generates a character spritesheet based on a given description and options.

```javascript
async function generateCharacterSpritesheet(description, options = {})
```

#### Parameters:

- `description` (string): A text description of the character to generate.
- `options` (object, optional): Configuration options for the spritesheet generation.
  - `states` (array of strings): Animation states to generate. Default: `['idle', 'walk', 'run', 'attack']`
  - `framesPerState` (number): Number of frames per animation state. Default: `6`
  - `size` (string): Output size of the spritesheet. Default: `'1024x1024'`
  - `style` (string): Art style of the sprite. Default: `'pixel-art'`
  - `padding` (number): Padding between sprites. Default: `1`
  - `direction` (string): Base direction of the character. Default: `'right'`
  - `save` (boolean): Whether to save the generated image to disk. Default: `false`

#### Returns:

An object containing:
- `original` (string): URL of the original generated image.
- `spritesheet` (string): Base64-encoded data URL of the processed spritesheet.
- `metadata` (object): Metadata about the generated spritesheet, including:
  - `states` (array): List of animation states.
  - `framesPerState` (number): Number of frames per state.
  - `totalFrames` (number): Total number of frames in the spritesheet.
  - `dimensions` (object): Width and height of the spritesheet.
  - `frameData` (object): Detailed information about each animation state's frames.

#### Example Usage:

```javascript
const result = await generateCharacterSpritesheet('a medieval knight in armor', {
  states: ['idle', 'walk', 'attack'],
  framesPerState: 4,
  size: '512x512',
  style: 'pixel-art',
  direction: 'left',
  save: true
});

console.log(result.metadata);
// Use result.spritesheet for rendering in your game
```

## Landscape Sprite Generation

### generateLandscapeSprite

Generates a landscape sprite based on a given description and options.

```javascript
async function generateLandscapeSprite(description, options = {})
```

#### Parameters:

- `description` (string): A text description of the landscape to generate.
- `options` (object, optional): Configuration options for the landscape generation.
  - `size` (string): Output size of the sprite. Default: `'1024x1024'`
  - `style` (string): Art style of the sprite. Default: `'pixel-art'`
  - `timeOfDay` (string): Time of day setting. Default: `'day'`
  - `weather` (string): Weather conditions. Default: `'clear'`
  - `perspective` (string): Perspective of the landscape. Default: `'side-scrolling'`
  - `save` (boolean): Whether to save the generated image to disk. Default: `false`
  - `removeBackground` (boolean): Whether to remove the background. Default: `false`
  - `backgroundColor` (string): Background color to remove (if removeBackground is true). Default: `'#FFFFFF'`
  - `colorThreshold` (number): Threshold for background color removal. Default: `0.1`

#### Returns:

An object containing:
- `original` (string): URL of the original generated image.
- `landscape` (string): Base64-encoded data URL of the processed landscape sprite.
- `metadata` (object): Metadata about the generated landscape, including:
  - `description` (string): Original description used for generation.
  - `style` (string): Art style of the sprite.
  - `timeOfDay` (string): Time of day setting.
  - `weather` (string): Weather conditions.
  - `perspective` (string): Perspective of the landscape.
  - `dimensions` (object): Width and height of the sprite.

#### Example Usage:

```javascript
const result = await generateLandscapeSprite('a mystical forest with glowing mushrooms', {
  size: '512x512',
  style: 'pixel-art',
  timeOfDay: 'night',
  weather: 'foggy',
  perspective: 'side-scrolling',
  removeBackground: true,
  save: true
});

console.log(result.metadata);
// Use result.landscape for rendering in your game
```

## Environment Sprites Generation

### generateEnvironmentSprites

Generates a set of environment sprites based on a given description and options.

```javascript
async function generateEnvironmentSprites(description, options = {})
```

#### Parameters:

- `description` (string): A text description of the environment to generate.
- `options` (object, optional): Configuration options for the environment sprites generation.
  - `elements` (number): Number of different elements to generate. Default: `4`
  - `size` (string): Output size of the tileset. Default: `'1024x1024'`
  - `style` (string): Art style of the sprites. Default: `'pixel-art'`
  - `padding` (number): Padding between sprites. Default: `1`
  - `theme` (string): Theme of the environment. Default: `'fantasy'`
  - `save` (boolean): Whether to save the generated image to disk. Default: `false`

#### Returns:

An object containing:
- `original` (string): URL of the original generated image.
- `tileset` (string): Base64-encoded data URL of the processed environment tileset.
- `metadata` (object): Metadata about the generated environment sprites, including:
  - `elements` (number): Number of different elements generated.
  - `theme` (string): Theme of the environment.
  - `dimensions` (object): Width and height of the tileset.
  - `tileData` (object): Information about the tileset layout.

#### Example Usage:

```javascript
const result = await generateEnvironmentSprites('ancient ruins in a jungle', {
  elements: 6,
  size: '512x512',
  style: 'pixel-art',
  theme: 'adventure',
  save: true
});

console.log(result.metadata);
// Use result.tileset for rendering in your game
```

## Utility Functions

### fetchAvailableAnimationStates

Retrieves a list of available animation states for character spritesheets.

```javascript
async function fetchAvailableAnimationStates()
```

#### Returns:

An array of strings representing available animation states.

#### Example Usage:

```javascript
const states = await fetchAvailableAnimationStates();
console.log(states); // ['idle', 'walk', 'run', 'attack', 'jump', 'fall', 'hurt', 'die']
```

### fetchAvailableSpriteStyles

Retrieves a list of available sprite styles.

```javascript
async function fetchAvailableSpriteStyles()
```

#### Returns:

An array of strings representing available sprite styles.

#### Example Usage:

```javascript
const styles = await fetchAvailableSpriteStyles();
console.log(styles); // ['pixel-art', 'vector', '3d', 'hand-drawn', 'anime']
```

### removeBackgroundColor

Removes a specified background color from an image.

```javascript
async function removeBackgroundColor(inputPath, outputPath, targetColor, colorThreshold = 0, options = {})
```

#### Parameters:

- `inputPath` (string): Path to the input image file.
- `outputPath` (string): Path where the processed image will be saved.
- `targetColor` (string): CSS color string of the background color to remove.
- `colorThreshold` (number, optional): Threshold for color matching. Default: `0`
- `options` (object, optional): Additional options for background removal.

#### Returns:

A promise that resolves when the background removal is complete.

#### Example Usage:

```javascript
await removeBackgroundColor('input.png', 'output.png', '#FFFFFF', 0.1);
console.log('Background removed successfully');
```

This concludes the API reference for the SpriteAI library. For more detailed information on usage and best practices, please refer to the main documentation and examples.