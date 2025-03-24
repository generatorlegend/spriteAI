# SpriteAI API Reference

## Table of Contents
1. [Introduction](#introduction)
2. [Character Sprite Generation](#character-sprite-generation)
   - [generateCharacterSpritesheet](#generatecharacterspritesheet)
3. [Landscape Sprite Generation](#landscape-sprite-generation)
   - [generateLandscapeSprite](#generatelandscapesprite)
4. [Utility Functions](#utility-functions)
   - [removeBackgroundColor](#removebackgroundcolor)
5. [Types](#types)

## Introduction

SpriteAI is a powerful library for generating game assets using AI. This API reference provides detailed information about the main functions available in the SpriteAI module.

## Character Sprite Generation

### generateCharacterSpritesheet

Generates a character spritesheet based on a description and optional parameters.

```javascript
async function generateCharacterSpritesheet(description, options = {})
```

#### Parameters

- `description` (string): A detailed description of the character to generate.
- `options` (object): Optional configuration for the spritesheet generation.
  - `states` (array of strings): Animation states to generate. Default: `['idle', 'walk', 'run', 'attack']`
  - `framesPerState` (number): Number of frames per animation state. Default: `6`
  - `size` (string): Output size of the spritesheet. Default: `'1024x1024'`
  - `style` (string): Art style for the character. Default: `'pixel-art'`
  - `padding` (number): Padding between sprites. Default: `1`
  - `direction` (string): Base direction of the character. Default: `'right'`
  - `save` (boolean): Whether to save the generated image to disk. Default: `false`

#### Returns

An object containing:
- `original` (string): URL of the original generated image.
- `spritesheet` (string): Base64-encoded PNG data of the processed spritesheet.
- `metadata` (object): Detailed information about the generated spritesheet.

#### Example Usage

```javascript
const result = await generateCharacterSpritesheet('A brave knight with shining armor', {
  states: ['idle', 'walk', 'attack'],
  framesPerState: 4,
  size: '512x512',
  style: 'pixel-art',
  save: true
});

console.log(result.metadata);
```

## Landscape Sprite Generation

### generateLandscapeSprite

Generates a landscape sprite based on a description and optional parameters.

```javascript
async function generateLandscapeSprite(description, options = {})
```

#### Parameters

- `description` (string): A detailed description of the landscape to generate.
- `options` (object): Optional configuration for the landscape generation.
  - `size` (string): Output size of the sprite. Default: `'1024x1024'`
  - `style` (string): Art style for the landscape. Default: `'pixel-art'`
  - `timeOfDay` (string): Time of day setting. Default: `'day'`
  - `weather` (string): Weather conditions. Default: `'clear'`
  - `perspective` (string): Perspective of the landscape. Default: `'side-scrolling'`
  - `save` (boolean): Whether to save the generated image to disk. Default: `false`
  - `removeBackground` (boolean): Whether to remove the background. Default: `false`
  - `backgroundColor` (string): Background color to remove (if removeBackground is true). Default: `'#FFFFFF'`
  - `colorThreshold` (number): Threshold for background color removal. Default: `0.1`

#### Returns

An object containing:
- `original` (string): URL of the original generated image.
- `landscape` (string): Base64-encoded PNG data of the processed landscape sprite.
- `metadata` (object): Detailed information about the generated landscape.

#### Example Usage

```javascript
const result = await generateLandscapeSprite('A lush forest with a winding river', {
  size: '512x512',
  style: 'pixel-art',
  timeOfDay: 'sunset',
  weather: 'clear',
  perspective: 'side-scrolling',
  save: true,
  removeBackground: true
});

console.log(result.metadata);
```

## Utility Functions

### removeBackgroundColor

Removes a specified background color from an image.

```javascript
async function removeBackgroundColor(inputPath, outputPath, targetColor, colorThreshold = 0, options = {})
```

#### Parameters

- `inputPath` (string): Path to the input image file.
- `outputPath` (string): Path where the processed image will be saved.
- `targetColor` (string): CSS color string of the background color to remove.
- `colorThreshold` (number): Threshold for color matching. Default: `0`
- `options` (object): Additional options (currently unused).

#### Returns

The result of the image processing operation.

#### Example Usage

```javascript
const result = await removeBackgroundColor(
  'input.png',
  'output.png',
  '#FFFFFF',
  0.1
);
console.log('Background removed:', result);
```

## Types

### SpriteSheetMetadata

```typescript
interface SpriteSheetMetadata {
  states: string[];
  framesPerState: number;
  totalFrames: number;
  dimensions: {
    width: string;
    height: string;
  };
  frameData: {
    [state: string]: {
      row: number;
      frames: number;
      startFrame: number;
      endFrame: number;
    };
  };
}
```

### LandscapeMetadata

```typescript
interface LandscapeMetadata {
  description: string;
  style: string;
  timeOfDay: string;
  weather: string;
  perspective: string;
  dimensions: {
    width: string;
    height: string;
  };
}
```