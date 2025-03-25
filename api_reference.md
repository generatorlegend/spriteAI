# SpriteAI API Reference

## Table of Contents
1. [Introduction](#introduction)
2. [Installation](#installation)
3. [API Functions](#api-functions)
   - [generateCharacterSpritesheet](#generatecharacterspritesheet)
   - [generateLandscapeSprite](#generatelandscapesprite)
   - [fetchAvailableAnimationStates](#fetchavailableanimationstates)
   - [fetchAvailableSpriteStyles](#fetchavailablespritestyles)
   - [generateEnvironmentSprites](#generateenvironmentsprites)
4. [Utility Functions](#utility-functions)
   - [removeBackgroundColor](#removebackgroundcolor)
5. [Error Handling](#error-handling)
6. [Best Practices](#best-practices)

## Introduction

SpriteAI is a powerful library that leverages AI to generate game assets, including character spritesheets, landscapes, and environment sprites. This API reference provides detailed information on how to use the SpriteAI library in your projects.

## Installation

To install SpriteAI, use npm:

```bash
npm install spriteai
```

Then, import the functions you need in your project:

```javascript
import { generateCharacterSpritesheet, generateLandscapeSprite } from 'spriteai';
```

## API Functions

### generateCharacterSpritesheet

Generates a character spritesheet based on a given description.

#### Syntax

```javascript
async function generateCharacterSpritesheet(description, options = {})
```

#### Parameters

- `description` (string): A detailed description of the character.
- `options` (object, optional): Configuration options for the spritesheet generation.
  - `states` (array of strings, default: `['idle', 'walk', 'run', 'attack']`): Animation states to generate.
  - `framesPerState` (number, default: 6): Number of frames per animation state.
  - `size` (string, default: '1024x1024'): Output size of the spritesheet.
  - `style` (string, default: 'pixel-art'): Art style of the spritesheet.
  - `padding` (number, default: 1): Padding between sprites.
  - `direction` (string, default: 'right'): Base direction of the character.
  - `save` (boolean): Whether to save the generated image to disk.

#### Returns

- An object containing:
  - `original` (string): URL of the original generated image.
  - `spritesheet` (string): Base64-encoded PNG data of the processed spritesheet.
  - `metadata` (object): Detailed information about the generated spritesheet.

#### Example

```javascript
const result = await generateCharacterSpritesheet('A brave knight in shining armor', {
  states: ['idle', 'walk', 'attack'],
  framesPerState: 8,
  size: '2048x2048',
  style: 'pixel-art',
  save: true
});

console.log(result.metadata);
```

### generateLandscapeSprite

Generates a landscape sprite based on a given description.

#### Syntax

```javascript
async function generateLandscapeSprite(description, options = {})
```

#### Parameters

- `description` (string): A detailed description of the landscape.
- `options` (object, optional): Configuration options for the landscape generation.
  - `size` (string, default: '1024x1024'): Output size of the sprite.
  - `style` (string, default: 'pixel-art'): Art style of the sprite.
  - `timeOfDay` (string, default: 'day'): Time of day setting (e.g., 'day', 'night', 'sunset', 'dawn').
  - `weather` (string, default: 'clear'): Weather conditions (e.g., 'clear', 'rainy', 'foggy', 'snowy').
  - `perspective` (string, default: 'side-scrolling'): Perspective of the landscape (e.g., 'side-scrolling', 'top-down', 'isometric').
  - `save` (boolean, default: false): Whether to save the generated image to disk.
  - `removeBackground` (boolean): Whether to remove the background of the generated image.
  - `backgroundColor` (string): The background color to remove (if removeBackground is true).
  - `colorThreshold` (number): Threshold for color removal (if removeBackground is true).

#### Returns

- An object containing:
  - `original` (string): URL of the original generated image.
  - `landscape` (string): Base64-encoded PNG data of the processed landscape sprite.
  - `metadata` (object): Detailed information about the generated landscape.

#### Example

```javascript
const result = await generateLandscapeSprite('A lush forest with a winding river', {
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

### fetchAvailableAnimationStates

Retrieves a list of available animation states for character spritesheets.

#### Syntax

```javascript
async function fetchAvailableAnimationStates()
```

#### Returns

- An array of strings representing available animation states.

#### Example

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

#### Returns

- An array of strings representing available sprite styles.

#### Example

```javascript
const styles = await fetchAvailableSpriteStyles();
console.log(styles); // ['pixel-art', 'vector', '3d', 'hand-drawn', 'anime']
```

### generateEnvironmentSprites

Generates a set of environment sprites based on a given description.

#### Syntax

```javascript
async function generateEnvironmentSprites(description, options = {})
```

#### Parameters

- `description` (string): A detailed description of the environment.
- `options` (object, optional): Configuration options for the environment sprites generation.
  - `elements` (number, default: 4): Number of different elements to generate.
  - `size` (string, default: '1024x1024'): Output size of the tileset.
  - `style` (string, default: 'pixel-art'): Art style of the sprites.
  - `padding` (number, default: 1): Padding between elements.
  - `theme` (string, default: 'fantasy'): Theme of the environment.
  - `save` (boolean): Whether to save the generated image to disk.

#### Returns

- An object containing:
  - `original` (string): URL of the original generated image.
  - `tileset` (string): Base64-encoded PNG data of the processed environment tileset.
  - `metadata` (object): Detailed information about the generated environment sprites.

#### Example

```javascript
const result = await generateEnvironmentSprites('A medieval village', {
  elements: 6,
  size: '2048x2048',
  style: 'pixel-art',
  theme: 'medieval',
  save: true
});

console.log(result.metadata);
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
- `targetColor` (string): The color to be removed (e.g., '#FFFFFF').
- `colorThreshold` (number, default: 0): Threshold for color matching.
- `options` (object, optional): Additional options for background removal.

#### Returns

- A promise that resolves when the background removal is complete.

#### Example

```javascript
await removeBackgroundColor('input.png', 'output.png', '#FFFFFF', 0.1);
```

## Error Handling

SpriteAI functions use async/await and will throw errors when issues occur. It's recommended to use try-catch blocks when calling these functions:

```javascript
try {
  const result = await generateCharacterSpritesheet('A brave knight');
  // Process the result
} catch (error) {
  console.error('Error generating character spritesheet:', error);
}
```

Common errors include:
- Network issues when connecting to the AI service
- Invalid input parameters
- File system errors when saving images

## Best Practices

1. **Descriptive Inputs**: Provide detailed descriptions for better AI-generated results.
2. **Error Handling**: Always implement proper error handling to manage potential issues.
3. **Resource Management**: Be mindful of API usage limits and implement rate limiting if necessary.
4. **Caching**: Consider caching generated assets to improve performance and reduce API calls.
5. **Image Optimization**: Post-process generated images to optimize file sizes for web or mobile use.
6. **Consistent Styling**: Use consistent style options across related sprites for a cohesive look.
7. **Validate Inputs**: Check and sanitize user inputs before passing them to the API functions.
8. **Testing**: Implement unit tests for your integration with SpriteAI to ensure reliability.

By following these guidelines and leveraging the powerful features of SpriteAI, you can efficiently generate high-quality game assets for your projects.