<response>

# Getting Started with SpriteAI

Welcome to SpriteAI, a powerful tool for generating game assets using AI! This guide will help you get started with SpriteAI, covering installation, basic usage, and key features.

## Table of Contents

1. [Installation](#installation)
2. [Basic Usage](#basic-usage)
   - [Generating Character Spritesheets](#generating-character-spritesheets)
   - [Generating Landscape Sprites](#generating-landscape-sprites)
3. [Key Features](#key-features)
4. [Examples](#examples)

## Installation

To get started with SpriteAI, follow these steps:

1. Ensure you have Node.js installed on your system.
2. Create a new directory for your project and navigate to it in your terminal.
3. Initialize a new Node.js project:
   ```
   npm init -y
   ```
4. Install SpriteAI and its dependencies:
   ```
   npm install spriteai openai axios sharp jimp
   ```

## Basic Usage

SpriteAI provides two main functions for generating game assets: `generateCharacterSpritesheet` and `generateLandscapeSprite`. Let's explore how to use each of these functions.

### Generating Character Spritesheets

The `generateCharacterSpritesheet` function allows you to create animated character spritesheets. Here's a basic example:

```javascript
import { generateCharacterSpritesheet } from 'spriteai';

async function createCharacter() {
  const result = await generateCharacterSpritesheet('a cute robot', {
    states: ['idle', 'walk', 'run'],
    framesPerState: 4,
    size: '512x512',
    style: 'pixel-art'
  });

  console.log(result.spritesheet); // Base64 encoded spritesheet
  console.log(result.metadata); // Spritesheet metadata
}

createCharacter();
```

This will generate a pixel-art spritesheet of a cute robot with idle, walk, and run animations.

### Generating Landscape Sprites

The `generateLandscapeSprite` function is used to create background landscapes for your game. Here's how to use it:

```javascript
import { generateLandscapeSprite } from 'spriteai';

async function createLandscape() {
  const result = await generateLandscapeSprite('a lush forest with a river', {
    size: '1024x1024',
    style: 'pixel-art',
    timeOfDay: 'sunset',
    weather: 'clear',
    perspective: 'side-scrolling'
  });

  console.log(result.landscape); // Base64 encoded landscape image
  console.log(result.metadata); // Landscape metadata
}

createLandscape();
```

This will generate a pixel-art side-scrolling landscape of a lush forest with a river at sunset.

## Key Features

SpriteAI offers several powerful features:

1. **AI-Powered Generation**: Utilizes OpenAI's DALL-E 3 model to create high-quality game assets.
2. **Customizable Output**: Adjust parameters like size, style, and animation states to suit your needs.
3. **Multiple Asset Types**: Generate both character spritesheets and landscape sprites.
4. **Metadata**: Receive detailed metadata about generated assets for easy integration into game engines.
5. **Background Removal**: Option to remove backgrounds from generated images (for landscape sprites).

## Examples

Here are a few more examples to showcase SpriteAI's capabilities:

### Creating a Character with Multiple Animation States

```javascript
const warrior = await generateCharacterSpritesheet('a fierce warrior', {
  states: ['idle', 'walk', 'run', 'attack', 'jump'],
  framesPerState: 6,
  size: '1024x1024',
  style: 'hand-drawn',
  direction: 'right'
});
```

### Generating a Dynamic Landscape

```javascript
const nightSkyline = await generateLandscapeSprite('a futuristic city skyline', {
  size: '2048x1024',
  style: 'vector',
  timeOfDay: 'night',
  weather: 'rainy',
  perspective: 'panoramic',
  removeBackground: true
});
```

With these basics, you're ready to start creating amazing game assets with SpriteAI! Experiment with different descriptions, styles, and options to unleash your creativity and bring your game world to life.

</response># Getting Started with SpriteAI

Welcome to SpriteAI, a powerful tool for generating game assets using AI! This guide will help you get started with SpriteAI, covering installation, basic usage, and key features.

## Table of Contents

1. [Installation](#installation)
2. [Basic Usage](#basic-usage)
   - [Generating Character Spritesheets](#generating-character-spritesheets)
   - [Generating Landscape Sprites](#generating-landscape-sprites)
3. [Key Features](#key-features)
4. [Examples](#examples)

## Installation

To get started with SpriteAI, follow these steps:

1. Ensure you have Node.js installed on your system.
2. Create a new directory for your project and navigate to it in your terminal.
3. Initialize a new Node.js project:
   ```
   npm init -y
   ```
4. Install SpriteAI and its dependencies:
   ```
   npm install spriteai openai axios sharp jimp
   ```

## Basic Usage

SpriteAI provides two main functions for generating game assets: `generateCharacterSpritesheet` and `generateLandscapeSprite`. Let's explore how to use each of these functions.

### Generating Character Spritesheets

The `generateCharacterSpritesheet` function allows you to create animated character spritesheets. Here's a basic example:

```javascript
import { generateCharacterSpritesheet } from 'spriteai';

async function createCharacter() {
  const result = await generateCharacterSpritesheet('a cute robot', {
    states: ['idle', 'walk', 'run'],
    framesPerState: 4,
    size: '512x512',
    style: 'pixel-art'
  });

  console.log(result.spritesheet); // Base64 encoded spritesheet
  console.log(result.metadata); // Spritesheet metadata
}

createCharacter();
```

This will generate a pixel-art spritesheet of a cute robot with idle, walk, and run animations.

### Generating Landscape Sprites

The `generateLandscapeSprite` function is used to create background landscapes for your game. Here's how to use it:

```javascript
import { generateLandscapeSprite } from 'spriteai';

async function createLandscape() {
  const result = await generateLandscapeSprite('a lush forest with a river', {
    size: '1024x1024',
    style: 'pixel-art',
    timeOfDay: 'sunset',
    weather: 'clear',
    perspective: 'side-scrolling'
  });

  console.log(result.landscape); // Base64 encoded landscape image
  console.log(result.metadata); // Landscape metadata
}

createLandscape();
```

This will generate a pixel-art side-scrolling landscape of a lush forest with a river at sunset.

## Key Features

SpriteAI offers several powerful features:

1. **AI-Powered Generation**: Utilizes OpenAI's DALL-E 3 model to create high-quality game assets.
2. **Customizable Output**: Adjust parameters like size, style, and animation states to suit your needs.
3. **Multiple Asset Types**: Generate both character spritesheets and landscape sprites.
4. **Metadata**: Receive detailed metadata about generated assets for easy integration into game engines.
5. **Background Removal**: Option to remove backgrounds from generated images (for landscape sprites).

## Examples

Here are a few more examples to showcase SpriteAI's capabilities:

### Creating a Character with Multiple Animation States

```javascript
const warrior = await generateCharacterSpritesheet('a fierce warrior', {
  states: ['idle', 'walk', 'run', 'attack', 'jump'],
  framesPerState: 6,
  size: '1024x1024',
  style: 'hand-drawn',
  direction: 'right'
});
```

### Generating a Dynamic Landscape

```javascript
const nightSkyline = await generateLandscapeSprite('a futuristic city skyline', {
  size: '2048x1024',
  style: 'vector',
  timeOfDay: 'night',
  weather: 'rainy',
  perspective: 'panoramic',
  removeBackground: true
});
```

With these basics, you're ready to start creating amazing game assets with SpriteAI! Experiment with different descriptions, styles, and options to unleash your creativity and bring your game world to life.