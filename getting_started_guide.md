# Getting Started with SpriteAI

## Introduction

SpriteAI is a powerful library that allows you to generate character spritesheets and landscape sprites using AI-powered image generation. This guide will walk you through the installation process and provide basic usage examples to help you get started with SpriteAI.

## Installation

To install SpriteAI, follow these steps:

1. Ensure you have Node.js installed on your system.
2. Create a new directory for your project and navigate to it in your terminal.
3. Initialize a new Node.js project by running:
   ```
   npm init -y
   ```
4. Install SpriteAI and its dependencies by running:
   ```
   npm install spriteai axios jimp openai sharp
   ```

## Basic Usage

### Generating Character Spritesheets

To generate a character spritesheet, you can use the `generateCharacterSpritesheet` function. Here's a basic example:

```javascript
import { generateCharacterSpritesheet } from 'spriteai';

async function createCharacterSprite() {
  const result = await generateCharacterSpritesheet('a cute robot', {
    states: ['idle', 'walk', 'run', 'attack'],
    framesPerState: 6,
    size: '1024x1024',
    style: 'pixel-art',
    save: true
  });

  console.log('Spritesheet generated:', result.spritesheet);
  console.log('Metadata:', result.metadata);
}

createCharacterSprite();
```

This example generates a pixel-art spritesheet of a cute robot with four animation states: idle, walk, run, and attack. Each state has 6 frames, and the resulting image is saved to the `assets` folder.

### Generating Landscape Sprites

To create a landscape sprite, use the `generateLandscapeSprite` function:

```javascript
import { generateLandscapeSprite } from 'spriteai';

async function createLandscapeSprite() {
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

createLandscapeSprite();
```

This example generates a pixel-art landscape of a lush forest with a waterfall, set during sunset with clear weather and a side-scrolling perspective.

## Main Features

### Character Spritesheet Generation

- Create spritesheets with multiple animation states
- Customize the number of frames per state
- Set output size and art style
- Automatically organize frames into a grid
- Generate metadata for easy integration into game engines

### Landscape Sprite Generation

- Create detailed landscape scenes for game backgrounds
- Customize time of day, weather conditions, and perspective
- Option to remove background for transparent sprites
- Save generated images to local files

### Customization Options

Both character and landscape sprite generation functions offer various customization options:

- `size`: Set the output image dimensions
- `style`: Choose the art style (e.g., 'pixel-art')
- `save`: Automatically save the generated image to the `assets` folder
- `removeBackground`: Remove the background from landscape sprites (landscape only)
- `timeOfDay` and `weather`: Set environmental conditions (landscape only)
- `states` and `framesPerState`: Customize animation states and frame counts (character only)

## Advanced Usage

For more advanced usage and detailed API documentation, please refer to the full API reference (link to be added).

## Conclusion

SpriteAI provides an easy way to generate game assets using AI. By following this guide, you should now be able to install the library and start creating your own character spritesheets and landscape sprites. Experiment with different options and descriptions to unleash your creativity!