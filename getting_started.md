# Getting Started with SpriteAI

Welcome to SpriteAI, a powerful library for generating game-ready sprites and assets using AI. This guide will walk you through the installation process and demonstrate how to use the main features of SpriteAI.

## Installation

To get started with SpriteAI, you'll need to have Node.js installed on your system. Then, follow these steps:

1. Create a new directory for your project and navigate to it:

```bash
mkdir spriteai-project
cd spriteai-project
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

SpriteAI allows you to generate character spritesheets with various animation states. Here's a basic example:

```javascript
import { generateCharacterSpritesheet } from 'spriteai';

async function createCharacterSprite() {
  const result = await generateCharacterSpritesheet('a medieval knight in armor', {
    states: ['idle', 'walk', 'attack'],
    framesPerState: 4,
    size: '512x512',
    style: 'pixel-art',
    save: true
  });

  console.log('Character spritesheet generated:', result.spritesheet);
  console.log('Metadata:', result.metadata);
}

createCharacterSprite();
```

This will generate a pixel-art spritesheet of a medieval knight with idle, walk, and attack animations.

### Creating Landscape Sprites

You can also generate landscape sprites for game backgrounds:

```javascript
import { generateLandscapeSprite } from 'spriteai';

async function createLandscapeSprite() {
  const result = await generateLandscapeSprite('a lush forest with a winding river', {
    size: '1024x512',
    style: 'pixel-art',
    timeOfDay: 'sunset',
    weather: 'clear',
    perspective: 'side-scrolling',
    save: true
  });

  console.log('Landscape sprite generated:', result.landscape);
  console.log('Metadata:', result.metadata);
}

createLandscapeSprite();
```

This will create a pixel-art landscape of a forest with a river at sunset, suitable for a side-scrolling game.

## Advanced Features

### Customizing Animation States

SpriteAI provides flexibility in defining animation states for character spritesheets. You can fetch available animation states:

```javascript
import { fetchAvailableAnimationStates } from 'spriteai';

async function getAnimationStates() {
  const states = await fetchAvailableAnimationStates();
  console.log('Available animation states:', states);
}

getAnimationStates();
```

### Exploring Sprite Styles

You can also check available sprite styles:

```javascript
import { fetchAvailableSpriteStyles } from 'spriteai';

async function getSpriteStyles() {
  const styles = await fetchAvailableSpriteStyles();
  console.log('Available sprite styles:', styles);
}

getSpriteStyles();
```

### Generating Environment Sprites

For creating game environments, you can use the `generateEnvironmentSprites` function:

```javascript
import { generateEnvironmentSprites } from 'spriteai';

async function createEnvironmentSprites() {
  const result = await generateEnvironmentSprites('desert oasis', {
    elements: 6,
    size: '1024x1024',
    style: 'pixel-art',
    theme: 'fantasy',
    save: true
  });

  console.log('Environment tileset generated:', result.tileset);
  console.log('Metadata:', result.metadata);
}

createEnvironmentSprites();
```

This will generate a tileset of fantasy-themed desert oasis elements in pixel-art style.

## Next Steps

- Explore the API documentation for detailed information on each function and its options.
- Check out the examples directory for more complex usage scenarios.
- Join our community forum to share your creations and get help from other developers.

Happy sprite generating with SpriteAI!