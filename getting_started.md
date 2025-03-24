# Getting Started with SpriteAI

SpriteAI is a powerful library that allows you to generate character spritesheets and landscape sprites using AI. This guide will walk you through the installation process and provide basic usage examples to help you get started quickly.

## Installation

To install SpriteAI, you need to have Node.js and npm (Node Package Manager) installed on your system. Once you have these prerequisites, follow these steps:

1. Open your terminal or command prompt.
2. Navigate to your project directory.
3. Run the following command to install SpriteAI and its dependencies:

```bash
npm install spriteai
```

This will install SpriteAI along with its required dependencies: axios, jimp, openai, and sharp.

## Basic Usage

### Importing SpriteAI

To use SpriteAI in your project, you need to import the necessary functions. Here's how you can do it:

```javascript
import { generateCharacterSpritesheet, generateLandscapeSprite } from 'spriteai';
```

### Generating a Character Spritesheet

To generate a character spritesheet, use the `generateCharacterSpritesheet` function. Here's a basic example:

```javascript
const description = 'a brave knight in shining armor';
const options = {
  states: ['idle', 'walk', 'run', 'attack'],
  framesPerState: 6,
  size: '1024x1024',
  style: 'pixel-art',
  direction: 'right'
};

try {
  const result = await generateCharacterSpritesheet(description, options);
  console.log('Character spritesheet generated:', result);
} catch (error) {
  console.error('Error generating character spritesheet:', error);
}
```

This will generate a pixel-art spritesheet of a knight with four animation states: idle, walk, run, and attack.

### Generating a Landscape Sprite

To generate a landscape sprite, use the `generateLandscapeSprite` function. Here's an example:

```javascript
const description = 'a lush forest with a winding river';
const options = {
  size: '1024x1024',
  style: 'pixel-art',
  timeOfDay: 'day',
  weather: 'clear',
  perspective: 'side-scrolling'
};

try {
  const result = await generateLandscapeSprite(description, options);
  console.log('Landscape sprite generated:', result);
} catch (error) {
  console.error('Error generating landscape sprite:', error);
}
```

This will generate a pixel-art landscape sprite of a forest with a river, suitable for a side-scrolling game.

## Main Features

SpriteAI offers several key features:

1. **Character Spritesheet Generation**: Create animated character spritesheets with multiple states and frames.
2. **Landscape Sprite Generation**: Generate detailed landscape sprites for game backgrounds.
3. **Customizable Options**: Adjust various parameters like size, style, and animation states to fit your needs.
4. **Background Removal**: Option to remove backgrounds from generated sprites (for landscape sprites).
5. **Metadata**: Receive detailed metadata about the generated sprites, including dimensions and frame data.

## Advanced Usage

### Fetching Available Animation States

You can fetch the list of available animation states using the `fetchAvailableAnimationStates` function:

```javascript
import { fetchAvailableAnimationStates } from 'spriteai';

const states = await fetchAvailableAnimationStates();
console.log('Available animation states:', states);
```

### Fetching Available Sprite Styles

To get the list of available sprite styles, use the `fetchAvailableSpriteStyles` function:

```javascript
import { fetchAvailableSpriteStyles } from 'spriteai';

const styles = await fetchAvailableSpriteStyles();
console.log('Available sprite styles:', styles);
```

### Generating Environment Sprites

For creating environment sprites or tilesets, use the `generateEnvironmentSprites` function:

```javascript
import { generateEnvironmentSprites } from 'spriteai';

const description = 'medieval town buildings';
const options = {
  elements: 4,
  size: '1024x1024',
  style: 'pixel-art',
  theme: 'fantasy'
};

try {
  const result = await generateEnvironmentSprites(description, options);
  console.log('Environment sprites generated:', result);
} catch (error) {
  console.error('Error generating environment sprites:', error);
}
```

This will generate a tileset of medieval town buildings with four distinct elements in a fantasy theme.

## Conclusion

This guide has covered the basics of getting started with SpriteAI, including installation, basic usage, and an overview of main features. As you become more familiar with the library, you can explore more advanced options and customize the sprite generation process to fit your specific needs.

For more detailed information on each function and its options, refer to the API documentation.