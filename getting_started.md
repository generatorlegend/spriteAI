# Getting Started with SpriteAI

## Introduction

SpriteAI is a powerful library that leverages artificial intelligence to generate game sprites and landscapes. This guide will help you get started with SpriteAI, covering installation, basic usage, and customization options.

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
   npm install spriteai openai axios sharp jimp
   ```

## Basic Usage

### Generating Character Spritesheets

The `generateCharacterSpritesheet` function allows you to create spritesheets for game characters. Here's a basic example:

```javascript
import { generateCharacterSpritesheet } from 'spriteai';

async function createCharacter() {
  const result = await generateCharacterSpritesheet('a brave knight in shining armor');
  console.log(result);
}

createCharacter();
```

This will generate a spritesheet with default animation states (idle, walk, run, attack) for a knight character.

### Generating Landscape Sprites

To create landscape sprites, use the `generateLandscapeSprite` function:

```javascript
import { generateLandscapeSprite } from 'spriteai';

async function createLandscape() {
  const result = await generateLandscapeSprite('a lush forest with a winding river');
  console.log(result);
}

createLandscape();
```

This generates a pixel art landscape of a forest with a river.

## Customizing Sprite Generation

Both functions accept an options object to customize the output:

### Character Spritesheet Options

```javascript
const options = {
  states: ['idle', 'walk', 'jump'],
  framesPerState: 8,
  size: '1024x1024',
  style: 'pixel-art',
  padding: 2,
  direction: 'left',
  save: true
};

const result = await generateCharacterSpritesheet('a nimble elf archer', options);
```

### Landscape Sprite Options

```javascript
const options = {
  size: '2048x1024',
  style: 'pixel-art',
  timeOfDay: 'sunset',
  weather: 'foggy',
  perspective: 'side-scrolling',
  save: true
};

const result = await generateLandscapeSprite('a mysterious abandoned castle', options);
```

## Understanding the Output

Both functions return an object containing:

- `original`: URL of the original AI-generated image
- `spritesheet` or `landscape`: Base64-encoded image data of the processed sprite
- `metadata`: Information about the generated sprite, including dimensions and animation data (for character spritesheets)

## Next Steps

- Experiment with different descriptions and options to create varied sprites
- Integrate the generated sprites into your game engine
- Explore advanced features like background removal and custom animation states

For more detailed information on available functions and options, refer to the API documentation.