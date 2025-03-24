<response>

# Landscape Sprite Generation Guide

This guide provides a comprehensive overview of generating landscape sprites using SpriteAI. Learn how to create detailed game backgrounds with various customization options.

## Table of Contents
1. [Introduction](#introduction)
2. [Basic Usage](#basic-usage)
3. [Customization Options](#customization-options)
   - [Size](#size)
   - [Style](#style)
   - [Time of Day](#time-of-day)
   - [Weather Conditions](#weather-conditions)
   - [Perspective](#perspective)
4. [Advanced Features](#advanced-features)
   - [Background Removal](#background-removal)
   - [Saving Generated Images](#saving-generated-images)
5. [Tips for Creating Cohesive Game Backgrounds](#tips-for-creating-cohesive-game-backgrounds)
6. [Integrating Landscape Sprites into Your Project](#integrating-landscape-sprites-into-your-project)

## Introduction

SpriteAI's `generateLandscapeSprite` function allows you to create custom landscape sprites for your game backgrounds. This powerful tool uses AI to generate high-quality, pixel-art style landscapes based on your descriptions and specifications.

## Basic Usage

To generate a landscape sprite, use the `generateLandscapeSprite` function:

```javascript
import { generateLandscapeSprite } from 'spriteai';

const result = await generateLandscapeSprite('lush forest with a winding river');
```

This will create a default landscape sprite based on your description.

## Customization Options

### Size

Specify the output size of your landscape sprite:

```javascript
const options = { size: '1024x1024' };
const result = await generateLandscapeSprite('mountain range with snow-capped peaks', options);
```

Default size is 1024x1024 pixels.

### Style

Set the art style for your landscape:

```javascript
const options = { style: 'pixel-art' };
const result = await generateLandscapeSprite('desert oasis with palm trees', options);
```

Default style is 'pixel-art'.

### Time of Day

Control the lighting and atmosphere by setting the time of day:

```javascript
const options = { timeOfDay: 'sunset' };
const result = await generateLandscapeSprite('cityscape with tall skyscrapers', options);
```

Available options:
- 'day' (default)
- 'night'
- 'sunset'
- 'dawn'

### Weather Conditions

Add weather effects to your landscape:

```javascript
const options = { weather: 'rainy' };
const result = await generateLandscapeSprite('tropical beach with crashing waves', options);
```

Available options:
- 'clear' (default)
- 'rainy'
- 'foggy'
- 'snowy'

### Perspective

Choose the viewing angle for your landscape:

```javascript
const options = { perspective: 'isometric' };
const result = await generateLandscapeSprite('medieval village with thatched roofs', options);
```

Available options:
- 'side-scrolling' (default)
- 'top-down'
- 'isometric'

## Advanced Features

### Background Removal

Remove the white background from your generated sprite:

```javascript
const options = {
  removeBackground: true,
  backgroundColor: '#FFFFFF',
  colorThreshold: 0.1
};
const result = await generateLandscapeSprite('alien planet with strange vegetation', options);
```

### Saving Generated Images

Automatically save the generated image to your project's assets folder:

```javascript
const options = { save: true };
const result = await generateLandscapeSprite('underwater coral reef', options);
```

## Tips for Creating Cohesive Game Backgrounds

1. Maintain a consistent style across all your landscapes.
2. Use a coherent color palette that matches your game's theme.
3. Consider the time of day and weather conditions to create atmosphere.
4. Ensure your landscapes work well with your chosen perspective.
5. Add depth by including foreground, midground, and background elements.
6. Create variations of the same landscape for different times of day or weather conditions.

## Integrating Landscape Sprites into Your Project

After generating your landscape sprite, you can access it in two formats:

1. Original URL:
```javascript
const originalUrl = result.original;
```

2. Base64-encoded data URL:
```javascript
const base64Image = result.landscape;
```

You can use these in your game engine or framework of choice. For example, in a web-based game using Phaser:

```javascript
function preload() {
  this.load.image('background', result.landscape);
}

function create() {
  this.add.image(0, 0, 'background').setOrigin(0);
}
```

Remember to adjust the image according to your game's scaling and resolution requirements.

By leveraging SpriteAI's landscape sprite generation capabilities, you can create rich, detailed game backgrounds that enhance the overall aesthetic and atmosphere of your game.

</response># Landscape Sprite Generation Guide

This guide provides a comprehensive overview of generating landscape sprites using SpriteAI. Learn how to create detailed game backgrounds with various customization options.

## Table of Contents
1. [Introduction](#introduction)
2. [Basic Usage](#basic-usage)
3. [Customization Options](#customization-options)
   - [Size](#size)
   - [Style](#style)
   - [Time of Day](#time-of-day)
   - [Weather Conditions](#weather-conditions)
   - [Perspective](#perspective)
4. [Advanced Features](#advanced-features)
   - [Background Removal](#background-removal)
   - [Saving Generated Images](#saving-generated-images)
5. [Tips for Creating Cohesive Game Backgrounds](#tips-for-creating-cohesive-game-backgrounds)
6. [Integrating Landscape Sprites into Your Project](#integrating-landscape-sprites-into-your-project)

## Introduction

SpriteAI's `generateLandscapeSprite` function allows you to create custom landscape sprites for your game backgrounds. This powerful tool uses AI to generate high-quality, pixel-art style landscapes based on your descriptions and specifications.

## Basic Usage

To generate a landscape sprite, use the `generateLandscapeSprite` function:

```javascript
import { generateLandscapeSprite } from 'spriteai';

const result = await generateLandscapeSprite('lush forest with a winding river');
```

This will create a default landscape sprite based on your description.

## Customization Options

### Size

Specify the output size of your landscape sprite:

```javascript
const options = { size: '1024x1024' };
const result = await generateLandscapeSprite('mountain range with snow-capped peaks', options);
```

Default size is 1024x1024 pixels.

### Style

Set the art style for your landscape:

```javascript
const options = { style: 'pixel-art' };
const result = await generateLandscapeSprite('desert oasis with palm trees', options);
```

Default style is 'pixel-art'.

### Time of Day

Control the lighting and atmosphere by setting the time of day:

```javascript
const options = { timeOfDay: 'sunset' };
const result = await generateLandscapeSprite('cityscape with tall skyscrapers', options);
```

Available options:
- 'day' (default)
- 'night'
- 'sunset'
- 'dawn'

### Weather Conditions

Add weather effects to your landscape:

```javascript
const options = { weather: 'rainy' };
const result = await generateLandscapeSprite('tropical beach with crashing waves', options);
```

Available options:
- 'clear' (default)
- 'rainy'
- 'foggy'
- 'snowy'

### Perspective

Choose the viewing angle for your landscape:

```javascript
const options = { perspective: 'isometric' };
const result = await generateLandscapeSprite('medieval village with thatched roofs', options);
```

Available options:
- 'side-scrolling' (default)
- 'top-down'
- 'isometric'

## Advanced Features

### Background Removal

Remove the white background from your generated sprite:

```javascript
const options = {
  removeBackground: true,
  backgroundColor: '#FFFFFF',
  colorThreshold: 0.1
};
const result = await generateLandscapeSprite('alien planet with strange vegetation', options);
```

### Saving Generated Images

Automatically save the generated image to your project's assets folder:

```javascript
const options = { save: true };
const result = await generateLandscapeSprite('underwater coral reef', options);
```

## Tips for Creating Cohesive Game Backgrounds

1. Maintain a consistent style across all your landscapes.
2. Use a coherent color palette that matches your game's theme.
3. Consider the time of day and weather conditions to create atmosphere.
4. Ensure your landscapes work well with your chosen perspective.
5. Add depth by including foreground, midground, and background elements.
6. Create variations of the same landscape for different times of day or weather conditions.

## Integrating Landscape Sprites into Your Project

After generating your landscape sprite, you can access it in two formats:

1. Original URL:
```javascript
const originalUrl = result.original;
```

2. Base64-encoded data URL:
```javascript
const base64Image = result.landscape;
```

You can use these in your game engine or framework of choice. For example, in a web-based game using Phaser:

```javascript
function preload() {
  this.load.image('background', result.landscape);
}

function create() {
  this.add.image(0, 0, 'background').setOrigin(0);
}
```

Remember to adjust the image according to your game's scaling and resolution requirements.

By leveraging SpriteAI's landscape sprite generation capabilities, you can create rich, detailed game backgrounds that enhance the overall aesthetic and atmosphere of your game.