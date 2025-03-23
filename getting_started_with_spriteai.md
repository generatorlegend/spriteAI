<response>
# Getting Started with SpriteAI

SpriteAI is a powerful library that allows you to generate game assets, including character spritesheets and landscape sprites, using AI-powered image generation. This guide will help you get started with SpriteAI, covering installation, basic usage, and an overview of key features.

## Installation

To install SpriteAI, make sure you have Node.js installed on your system. Then, run the following command in your project directory:

```bash
npm install spriteai
```

## Basic Usage

### Importing SpriteAI

First, import the necessary functions from the SpriteAI library:

```javascript
import { generateCharacterSpritesheet, generateLandscapeSprite } from 'spriteai';
```

### Generating a Character Spritesheet

To generate a character spritesheet, use the `generateCharacterSpritesheet` function:

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

To generate a landscape sprite, use the `generateLandscapeSprite` function:

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

## Key Features

SpriteAI offers several powerful features for game asset generation:

1. **Character Spritesheets**: Generate complete character spritesheets with multiple animation states.
2. **Landscape Sprites**: Create detailed landscape sprites for game backgrounds.
3. **Customizable Options**: Adjust various parameters like style, size, and animation states to fit your needs.
4. **Metadata**: Receive comprehensive metadata about generated assets for easy integration into game engines.
5. **Background Removal**: Option to remove backgrounds from generated sprites (for landscape sprites).
6. **Asset Saving**: Automatically save generated assets to your project's asset folder.

## Advanced Usage

### Fetching Available Animation States

You can fetch the list of available animation states:

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

For creating environment tilesets:

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
console.log(result.metadata); // Metadata about the generated tileset
```

## Conclusion

SpriteAI provides a robust set of tools for generating game assets using AI. By leveraging these functions, you can quickly create high-quality spritesheets, landscapes, and environment tilesets for your game development projects. Experiment with different descriptions and options to achieve the desired results for your game's unique art style and requirements.
</response>