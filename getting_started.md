# Getting Started with SpriteAI

Welcome to SpriteAI, a powerful library for generating game assets using AI. This guide will help you get started with installing the library and using its main features.

## Installation

To install SpriteAI, make sure you have Node.js installed on your system. Then, follow these steps:

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

4. Create a new JavaScript file (e.g., `index.js`) to start using SpriteAI.

## Basic Usage

### Generating Character Spritesheets

SpriteAI allows you to generate character spritesheets with various animation states. Here's a basic example:

```javascript
import { generateCharacterSpritesheet } from 'spriteai';

async function generateSprite() {
  const result = await generateCharacterSpritesheet('a cute cat warrior', {
    states: ['idle', 'walk', 'attack'],
    framesPerState: 4,
    size: '512x512',
    style: 'pixel-art',
    save: true
  });

  console.log('Spritesheet generated:', result.spritesheet);
  console.log('Metadata:', result.metadata);
}

generateSprite();
```

This will generate a pixel-art spritesheet of a cute cat warrior with idle, walk, and attack animations.

### Generating Landscape Sprites

You can also create landscape sprites for game backgrounds:

```javascript
import { generateLandscapeSprite } from 'spriteai';

async function generateLandscape() {
  const result = await generateLandscapeSprite('a lush forest with a flowing river', {
    size: '1024x512',
    style: 'pixel-art',
    timeOfDay: 'sunset',
    weather: 'clear',
    perspective: 'side-scrolling',
    save: true
  });

  console.log('Landscape generated:', result.landscape);
  console.log('Metadata:', result.metadata);
}

generateLandscape();
```

This will create a pixel-art side-scrolling landscape of a lush forest with a flowing river at sunset.

## Main Functions

SpriteAI provides two main functions:

1. `generateCharacterSpritesheet(description, options)`: Generates a character spritesheet with multiple animation states.

2. `generateLandscapeSprite(description, options)`: Creates a landscape sprite for game backgrounds.

Both functions return an object containing the generated image (as a base64-encoded string) and metadata about the sprite.

## Advanced Options

### Character Spritesheets

- `states`: Array of animation states (default: ['idle', 'walk', 'run', 'attack'])
- `framesPerState`: Number of frames per animation state (default: 6)
- `size`: Output image size (default: '1024x1024')
- `style`: Art style (default: 'pixel-art')
- `padding`: Padding between sprites (default: 1)
- `direction`: Base direction of the character (default: 'right')
- `save`: Whether to save the generated image to disk (default: false)

### Landscape Sprites

- `size`: Output image size (default: '1024x1024')
- `style`: Art style (default: 'pixel-art')
- `timeOfDay`: Time setting (default: 'day')
- `weather`: Weather conditions (default: 'clear')
- `perspective`: View perspective (default: 'side-scrolling')
- `save`: Whether to save the generated image to disk (default: false)
- `removeBackground`: Option to remove the background (default: false)
- `backgroundColor`: Background color to remove (used with removeBackground)
- `colorThreshold`: Threshold for background removal (used with removeBackground)

## Next Steps

Now that you're familiar with the basics of SpriteAI, you can start experimenting with different descriptions and options to create unique game assets. Remember to handle errors and implement proper error handling in your production code.

For more advanced usage and detailed API documentation, please refer to our other guides and API reference.

Happy sprite generating!