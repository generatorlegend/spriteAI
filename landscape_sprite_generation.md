<response>

# Landscape Sprite Generation with SpriteAI

This guide provides a comprehensive overview of generating landscape sprites using the SpriteAI library. We'll focus on the `generateLandscapeSprite` function, its parameters, and options for customizing the output.

## Table of Contents

1. [Introduction](#introduction)
2. [Function Overview](#function-overview)
3. [Parameters](#parameters)
4. [Options](#options)
5. [Usage Examples](#usage-examples)
6. [Output](#output)
7. [Advanced Customization](#advanced-customization)

## Introduction

The `generateLandscapeSprite` function allows you to create pixel art landscape scenes for use in games or other visual applications. It uses AI-powered image generation to produce high-quality, customizable landscape sprites based on your descriptions and preferences.

## Function Overview

```javascript
async function generateLandscapeSprite(description, options = {})
```

This asynchronous function takes a landscape description and an optional options object to generate a customized landscape sprite.

## Parameters

1. `description` (string): A detailed description of the landscape you want to generate.
2. `options` (object): An optional object containing customization parameters.

## Options

The `options` object can include the following properties:

- `size` (string): Output size of the image. Default: '1024x1024'
- `style` (string): Art style of the landscape. Default: 'pixel-art'
- `timeOfDay` (string): Time setting for the scene. Options: 'day', 'night', 'sunset', 'dawn'. Default: 'day'
- `weather` (string): Weather conditions. Options: 'clear', 'rainy', 'foggy', 'snowy'. Default: 'clear'
- `perspective` (string): Viewing angle of the landscape. Options: 'side-scrolling', 'top-down', 'isometric'. Default: 'side-scrolling'
- `save` (boolean): Whether to save the generated image to the local file system. Default: false
- `removeBackground` (boolean): Option to remove the white background. Default: false
- `backgroundColor` (string): The background color to remove if `removeBackground` is true. Default: '#FFFFFF'
- `colorThreshold` (number): Threshold for background color removal. Default: 0.1

## Usage Examples

### Basic Usage

```javascript
import { generateLandscapeSprite } from 'spriteai';

const basicLandscape = await generateLandscapeSprite('A lush forest with a winding river');
```

### Customized Landscape

```javascript
const mountainScene = await generateLandscapeSprite('Snow-capped mountains with a clear lake', {
  size: '2048x1024',
  timeOfDay: 'sunset',
  weather: 'clear',
  perspective: 'side-scrolling',
  save: true
});
```

### Night Scene with Weather

```javascript
const nightCityscape = await generateLandscapeSprite('Futuristic city skyline', {
  timeOfDay: 'night',
  weather: 'rainy',
  style: 'pixel-art',
  perspective: 'isometric'
});
```

## Output

The function returns an object with the following properties:

- `original` (string): URL of the original generated image.
- `landscape` (string): Base64-encoded data URL of the processed landscape image.
- `metadata` (object): Contains information about the generated landscape:
  - `description` (string): The input description.
  - `style` (string): The art style used.
  - `timeOfDay` (string): The time of day setting.
  - `weather` (string): The weather conditions.
  - `perspective` (string): The perspective used.
  - `dimensions` (object): Width and height of the image.

## Advanced Customization

### Removing Background

To remove the white background from the generated sprite:

```javascript
const transparentLandscape = await generateLandscapeSprite('Desert oasis', {
  removeBackground: true,
  backgroundColor: '#FFFFFF',
  colorThreshold: 0.15
});
```

### Saving to File System

When `save` is set to `true`, the image will be saved in the `assets` directory of your project:

```javascript
const savedLandscape = await generateLandscapeSprite('Tropical beach at dawn', {
  save: true,
  timeOfDay: 'dawn'
});
```

The file will be named based on the description, with spaces replaced by underscores, e.g., `Tropical_beach_at_dawn_landscape.png`.

By leveraging these options and examples, you can generate a wide variety of landscape sprites for your game development needs using SpriteAI.

</response># Landscape Sprite Generation with SpriteAI

This guide provides a comprehensive overview of generating landscape sprites using the SpriteAI library. We'll focus on the `generateLandscapeSprite` function, its parameters, and options for customizing the output.

## Table of Contents

1. [Introduction](#introduction)
2. [Function Overview](#function-overview)
3. [Parameters](#parameters)
4. [Options](#options)
5. [Usage Examples](#usage-examples)
6. [Output](#output)
7. [Advanced Customization](#advanced-customization)

## Introduction

The `generateLandscapeSprite` function allows you to create pixel art landscape scenes for use in games or other visual applications. It uses AI-powered image generation to produce high-quality, customizable landscape sprites based on your descriptions and preferences.

## Function Overview

```javascript
async function generateLandscapeSprite(description, options = {})
```

This asynchronous function takes a landscape description and an optional options object to generate a customized landscape sprite.

## Parameters

1. `description` (string): A detailed description of the landscape you want to generate.
2. `options` (object): An optional object containing customization parameters.

## Options

The `options` object can include the following properties:

- `size` (string): Output size of the image. Default: '1024x1024'
- `style` (string): Art style of the landscape. Default: 'pixel-art'
- `timeOfDay` (string): Time setting for the scene. Options: 'day', 'night', 'sunset', 'dawn'. Default: 'day'
- `weather` (string): Weather conditions. Options: 'clear', 'rainy', 'foggy', 'snowy'. Default: 'clear'
- `perspective` (string): Viewing angle of the landscape. Options: 'side-scrolling', 'top-down', 'isometric'. Default: 'side-scrolling'
- `save` (boolean): Whether to save the generated image to the local file system. Default: false
- `removeBackground` (boolean): Option to remove the white background. Default: false
- `backgroundColor` (string): The background color to remove if `removeBackground` is true. Default: '#FFFFFF'
- `colorThreshold` (number): Threshold for background color removal. Default: 0.1

## Usage Examples

### Basic Usage

```javascript
import { generateLandscapeSprite } from 'spriteai';

const basicLandscape = await generateLandscapeSprite('A lush forest with a winding river');
```

### Customized Landscape

```javascript
const mountainScene = await generateLandscapeSprite('Snow-capped mountains with a clear lake', {
  size: '2048x1024',
  timeOfDay: 'sunset',
  weather: 'clear',
  perspective: 'side-scrolling',
  save: true
});
```

### Night Scene with Weather

```javascript
const nightCityscape = await generateLandscapeSprite('Futuristic city skyline', {
  timeOfDay: 'night',
  weather: 'rainy',
  style: 'pixel-art',
  perspective: 'isometric'
});
```

## Output

The function returns an object with the following properties:

- `original` (string): URL of the original generated image.
- `landscape` (string): Base64-encoded data URL of the processed landscape image.
- `metadata` (object): Contains information about the generated landscape:
  - `description` (string): The input description.
  - `style` (string): The art style used.
  - `timeOfDay` (string): The time of day setting.
  - `weather` (string): The weather conditions.
  - `perspective` (string): The perspective used.
  - `dimensions` (object): Width and height of the image.

## Advanced Customization

### Removing Background

To remove the white background from the generated sprite:

```javascript
const transparentLandscape = await generateLandscapeSprite('Desert oasis', {
  removeBackground: true,
  backgroundColor: '#FFFFFF',
  colorThreshold: 0.15
});
```

### Saving to File System

When `save` is set to `true`, the image will be saved in the `assets` directory of your project:

```javascript
const savedLandscape = await generateLandscapeSprite('Tropical beach at dawn', {
  save: true,
  timeOfDay: 'dawn'
});
```

The file will be named based on the description, with spaces replaced by underscores, e.g., `Tropical_beach_at_dawn_landscape.png`.

By leveraging these options and examples, you can generate a wide variety of landscape sprites for your game development needs using SpriteAI.