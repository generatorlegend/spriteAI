# Getting Started with SpriteAI

## Introduction

SpriteAI is a powerful library that allows you to generate character spritesheets and landscape sprites using AI. This guide will walk you through the process of setting up and using SpriteAI in your projects.

## Installation

To get started with SpriteAI, you'll need to install it along with its dependencies. Make sure you have Node.js installed on your system, then follow these steps:

1. Create a new directory for your project and navigate to it:

```bash
mkdir my-spriteai-project
cd my-spriteai-project
```

2. Initialize a new Node.js project:

```bash
npm init -y
```

3. Install SpriteAI and its dependencies:

```bash
npm install spriteai openai axios sharp jimp
```

## Basic Usage

### Generating Character Spritesheets

To generate a character spritesheet, you can use the `generateCharacterSpritesheet` function. Here's a basic example:

```javascript
import { generateCharacterSpritesheet } from 'spriteai';

async function createCharacterSprite() {
  const result = await generateCharacterSpritesheet('a cute robot');
  console.log(result);
}

createCharacterSprite();
```

This will generate a spritesheet with default animation states (idle, walk, run, attack) for a cute robot character.

### Generating Landscape Sprites

To create a landscape sprite, use the `generateLandscapeSprite` function:

```javascript
import { generateLandscapeSprite } from 'spriteai';

async function createLandscapeSprite() {
  const result = await generateLandscapeSprite('a lush forest with a waterfall');
  console.log(result);
}

createLandscapeSprite();
```

This will generate a landscape sprite of a lush forest with a waterfall.

## Advanced Options

Both `generateCharacterSpritesheet` and `generateLandscapeSprite` functions accept an options object as a second parameter, allowing you to customize various aspects of the generated sprites.

### Character Spritesheet Options

- `states`: An array of animation states (default: ['idle', 'walk', 'run', 'attack'])
- `framesPerState`: Number of frames per animation state (default: 6)
- `size`: Output size of the spritesheet (default: '1024x1024')
- `style`: Art style of the sprite (default: 'pixel-art')
- `padding`: Padding between sprites (default: 1)
- `direction`: Base direction of the character (default: 'right')
- `save`: Whether to save the generated image (default: false)

Example with custom options:

```javascript
const options = {
  states: ['idle', 'walk', 'jump'],
  framesPerState: 8,
  size: '2048x2048',
  style: 'vector',
  save: true
};

const result = await generateCharacterSpritesheet('a heroic knight', options);
```

### Landscape Sprite Options

- `size`: Output size of the sprite (default: '1024x1024')
- `style`: Art style of the sprite (default: 'pixel-art')
- `timeOfDay`: Time of day setting (default: 'day')
- `weather`: Weather conditions (default: 'clear')
- `perspective`: Perspective of the landscape (default: 'side-scrolling')
- `save`: Whether to save the generated image (default: false)
- `removeBackground`: Whether to remove the background (default: false)
- `backgroundColor`: Background color to remove (if removeBackground is true)
- `colorThreshold`: Threshold for background color removal (if removeBackground is true)

Example with custom options:

```javascript
const options = {
  size: '2048x2048',
  style: 'hand-drawn',
  timeOfDay: 'sunset',
  weather: 'rainy',
  perspective: 'isometric',
  save: true,
  removeBackground: true,
  backgroundColor: '#FFFFFF',
  colorThreshold: 0.1
};

const result = await generateLandscapeSprite('a mystical floating island', options);
```

## Fetching Available Options

SpriteAI provides functions to fetch available animation states and sprite styles:

```javascript
import { fetchAvailableAnimationStates, fetchAvailableSpriteStyles } from 'spriteai';

async function getOptions() {
  const states = await fetchAvailableAnimationStates();
  console.log('Available animation states:', states);

  const styles = await fetchAvailableSpriteStyles();
  console.log('Available sprite styles:', styles);
}

getOptions();
```

## Conclusion

This guide covered the basics of setting up and using SpriteAI to generate character spritesheets and landscape sprites. Experiment with different descriptions and options to create unique and exciting game assets for your projects!

For more detailed information on each function and its capabilities, refer to the API documentation.