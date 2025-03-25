# Getting Started with SpriteAI

Welcome to SpriteAI! This guide will help you get up and running with our powerful sprite generation tool. SpriteAI allows you to easily create character spritesheets and landscape sprites for your game development projects.

## Installation

To install SpriteAI, make sure you have Node.js installed on your system. Then, follow these steps:

1. Create a new directory for your project:
   ```
   mkdir my-spriteai-project
   cd my-spriteai-project
   ```

2. Initialize a new Node.js project:
   ```
   npm init -y
   ```

3. Install SpriteAI and its dependencies:
   ```
   npm install spriteai axios jimp openai sharp
   ```

## Basic Usage

### Generating Character Spritesheets

To generate a character spritesheet, use the `generateCharacterSpritesheet` function. Here's a basic example:

```javascript
import { generateCharacterSpritesheet } from 'spriteai';

async function createCharacter() {
  const result = await generateCharacterSpritesheet('a cute robot', {
    states: ['idle', 'walk', 'run'],
    framesPerState: 4,
    size: '512x512',
    style: 'pixel-art',
    save: true
  });

  console.log('Character spritesheet generated:', result.spritesheet);
  console.log('Metadata:', result.metadata);
}

createCharacter();
```

This will generate a pixel-art spritesheet of a cute robot with idle, walk, and run animations.

### Generating Landscape Sprites

To create a landscape sprite, use the `generateLandscapeSprite` function:

```javascript
import { generateLandscapeSprite } from 'spriteai';

async function createLandscape() {
  const result = await generateLandscapeSprite('a lush forest with a waterfall', {
    size: '1024x1024',
    style: 'pixel-art',
    timeOfDay: 'sunset',
    weather: 'clear',
    perspective: 'side-scrolling',
    save: true
  });

  console.log('Landscape sprite generated:', result.landscape);
  console.log('Metadata:', result.metadata);
}

createLandscape();
```

This will generate a pixel-art side-scrolling landscape of a lush forest with a waterfall at sunset.

## Main Features

SpriteAI offers several powerful features:

1. **Character Spritesheet Generation**: Create animated character sprites with multiple states.
2. **Landscape Sprite Generation**: Design beautiful background landscapes for your games.
3. **Customizable Options**: Adjust size, style, animation states, and more to fit your needs.
4. **Background Removal**: Automatically remove backgrounds from generated sprites.
5. **Metadata Generation**: Get detailed metadata about your generated sprites for easy integration into game engines.

## Advanced Usage

### Fetching Available Animation States

You can retrieve the list of available animation states:

```javascript
import { fetchAvailableAnimationStates } from 'spriteai';

async function getAnimationStates() {
  const states = await fetchAvailableAnimationStates();
  console.log('Available animation states:', states);
}

getAnimationStates();
```

### Fetching Available Sprite Styles

To get the list of available sprite styles:

```javascript
import { fetchAvailableSpriteStyles } from 'spriteai';

async function getSpriteStyles() {
  const styles = await fetchAvailableSpriteStyles();
  console.log('Available sprite styles:', styles);
}

getSpriteStyles();
```

### Generating Environment Sprites

For creating sets of environment elements:

```javascript
import { generateEnvironmentSprites } from 'spriteai';

async function createEnvironment() {
  const result = await generateEnvironmentSprites('medieval town', {
    elements: 6,
    size: '1024x1024',
    style: 'pixel-art',
    theme: 'fantasy',
    save: true
  });

  console.log('Environment tileset generated:', result.tileset);
  console.log('Metadata:', result.metadata);
}

createEnvironment();
```

This will generate a tileset of 6 different medieval town elements in a fantasy theme.

## Conclusion

With SpriteAI, you can quickly generate high-quality sprites and landscapes for your game development projects. Experiment with different options and settings to create the perfect assets for your games. Happy sprite creating!