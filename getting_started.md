# Getting Started with SpriteAI

Welcome to SpriteAI, a powerful library for generating game assets using AI. This guide will help you get started with installing the library and using its main features.

## Installation

To install SpriteAI, you can use npm (Node Package Manager). Run the following command in your terminal:

```bash
npm install spriteai
```

Make sure you have Node.js version 14 or higher installed on your system.

## Basic Usage

### Importing the Library

To use SpriteAI in your project, import the necessary functions:

```javascript
import { generateCharacterSpritesheet, generateLandscapeSprite } from 'spriteai';
```

### Generating a Character Spritesheet

To create a character spritesheet, use the `generateCharacterSpritesheet` function:

```javascript
const description = 'a brave knight in shining armor';
const options = {
  states: ['idle', 'walk', 'run', 'attack'],
  framesPerState: 6,
  size: '1024x1024',
  style: 'pixel-art',
  direction: 'right'
};

const result = await generateCharacterSpritesheet(description, options);

console.log(result.spritesheet); // Base64 encoded spritesheet image
console.log(result.metadata); // Metadata about the generated spritesheet
```

### Generating a Landscape Sprite

To create a landscape sprite, use the `generateLandscapeSprite` function:

```javascript
const description = 'a lush forest with a winding river';
const options = {
  size: '1024x1024',
  style: 'pixel-art',
  timeOfDay: 'day',
  weather: 'clear',
  perspective: 'side-scrolling'
};

const result = await generateLandscapeSprite(description, options);

console.log(result.landscape); // Base64 encoded landscape image
console.log(result.metadata); // Metadata about the generated landscape
```

## Main Features

SpriteAI offers several key features for game asset generation:

1. **Character Spritesheets**: Create animated character sprites with multiple states (e.g., idle, walk, run, attack).
2. **Landscape Sprites**: Generate game backgrounds and environment pieces.
3. **Customizable Options**: Adjust parameters like size, style, weather, and perspective to fit your game's needs.
4. **Metadata**: Receive detailed metadata about generated assets for easy integration into game engines.
5. **Background Removal**: Option to remove backgrounds from generated sprites (available for landscape sprites).

## Advanced Usage

### Fetching Available Animation States

You can retrieve the list of available animation states:

```javascript
import { fetchAvailableAnimationStates } from 'spriteai';

const states = await fetchAvailableAnimationStates();
console.log(states); // ['idle', 'walk', 'run', 'attack', 'jump', 'fall', 'hurt', 'die']
```

### Fetching Available Sprite Styles

To get the list of available sprite styles:

```javascript
import { fetchAvailableSpriteStyles } from 'spriteai';

const styles = await fetchAvailableSpriteStyles();
console.log(styles); // ['pixel-art', 'vector', '3d', 'hand-drawn', 'anime']
```

### Generating Environment Sprites

For creating sets of environment sprites:

```javascript
import { generateEnvironmentSprites } from 'spriteai';

const description = 'medieval castle';
const options = {
  elements: 4,
  size: '1024x1024',
  style: 'pixel-art',
  theme: 'fantasy'
};

const result = await generateEnvironmentSprites(description, options);

console.log(result.tileset); // Base64 encoded tileset image
console.log(result.metadata); // Metadata about the generated environment sprites
```

## Next Steps

Now that you're familiar with the basics of SpriteAI, you can start integrating it into your game development workflow. Experiment with different descriptions and options to create unique assets for your projects.

For more detailed information on each function and its parameters, refer to the API documentation.

Happy sprite generating!