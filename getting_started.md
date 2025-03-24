<response>

# Getting Started with SpriteAI

SpriteAI is a powerful library that allows you to generate character spritesheets and landscape sprites using AI. This guide will help you get started with SpriteAI, covering installation, basic usage, and an overview of its main features.

## Installation

To install SpriteAI, you need to have Node.js and npm (Node Package Manager) installed on your system. Once you have these prerequisites, you can install SpriteAI using npm:

```bash
npm install spriteai
```

## Basic Usage

### Generating Character Spritesheets

To generate a character spritesheet, you can use the `generateCharacterSpritesheet` function. Here's a basic example:

```javascript
import { generateCharacterSpritesheet } from 'spriteai';

async function createCharacterSpritesheet() {
  const description = 'a cute cat warrior';
  const options = {
    states: ['idle', 'walk', 'run', 'attack'],
    framesPerState: 6,
    size: '1024x1024',
    style: 'pixel-art',
    direction: 'right'
  };

  try {
    const result = await generateCharacterSpritesheet(description, options);
    console.log('Spritesheet generated:', result.spritesheet);
    console.log('Metadata:', result.metadata);
  } catch (error) {
    console.error('Error generating spritesheet:', error);
  }
}

createCharacterSpritesheet();
```

This example generates a pixel-art spritesheet of a cute cat warrior with four animation states: idle, walk, run, and attack.

### Generating Landscape Sprites

To create a landscape sprite, you can use the `generateLandscapeSprite` function:

```javascript
import { generateLandscapeSprite } from 'spriteai';

async function createLandscapeSprite() {
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
    console.log('Landscape sprite generated:', result.landscape);
    console.log('Metadata:', result.metadata);
  } catch (error) {
    console.error('Error generating landscape sprite:', error);
  }
}

createLandscapeSprite();
```

This example generates a pixel-art landscape sprite of a lush forest with a winding river, set during daytime with clear weather and a side-scrolling perspective.

## Main Features

SpriteAI offers several key features:

1. **Character Spritesheet Generation**: Create detailed character spritesheets with multiple animation states.
2. **Landscape Sprite Generation**: Generate beautiful landscape sprites for game backgrounds.
3. **Customizable Options**: Adjust various parameters like size, style, and animation states to suit your needs.
4. **Metadata**: Receive detailed metadata about the generated sprites, including dimensions and frame data.
5. **Background Removal**: Option to remove backgrounds from generated sprites (for landscape sprites).
6. **Automatic Saving**: Save generated sprites directly to your project's asset folder.

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

For creating sets of environment sprites:

```javascript
import { generateEnvironmentSprites } from 'spriteai';

async function createEnvironmentSprites() {
  const description = 'medieval castle';
  const options = {
    elements: 4,
    size: '1024x1024',
    style: 'pixel-art',
    theme: 'fantasy'
  };

  try {
    const result = await generateEnvironmentSprites(description, options);
    console.log('Environment sprites generated:', result.tileset);
    console.log('Metadata:', result.metadata);
  } catch (error) {
    console.error('Error generating environment sprites:', error);
  }
}

createEnvironmentSprites();
```

This generates a set of 4 medieval castle environment sprites in a pixel-art fantasy style.

## Conclusion

SpriteAI provides a powerful and flexible way to generate game assets using AI. By leveraging its various functions and customization options, you can quickly create high-quality sprites and landscapes for your game development projects. Experiment with different descriptions, styles, and settings to achieve the perfect look for your game!

</response># Getting Started with SpriteAI

SpriteAI is a powerful library that allows you to generate character spritesheets and landscape sprites using AI. This guide will help you get started with SpriteAI, covering installation, basic usage, and an overview of its main features.

## Installation

To install SpriteAI, you need to have Node.js and npm (Node Package Manager) installed on your system. Once you have these prerequisites, you can install SpriteAI using npm:

```bash
npm install spriteai
```

## Basic Usage

### Generating Character Spritesheets

To generate a character spritesheet, you can use the `generateCharacterSpritesheet` function. Here's a basic example:

```javascript
import { generateCharacterSpritesheet } from 'spriteai';

async function createCharacterSpritesheet() {
  const description = 'a cute cat warrior';
  const options = {
    states: ['idle', 'walk', 'run', 'attack'],
    framesPerState: 6,
    size: '1024x1024',
    style: 'pixel-art',
    direction: 'right'
  };

  try {
    const result = await generateCharacterSpritesheet(description, options);
    console.log('Spritesheet generated:', result.spritesheet);
    console.log('Metadata:', result.metadata);
  } catch (error) {
    console.error('Error generating spritesheet:', error);
  }
}

createCharacterSpritesheet();
```

This example generates a pixel-art spritesheet of a cute cat warrior with four animation states: idle, walk, run, and attack.

### Generating Landscape Sprites

To create a landscape sprite, you can use the `generateLandscapeSprite` function:

```javascript
import { generateLandscapeSprite } from 'spriteai';

async function createLandscapeSprite() {
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
    console.log('Landscape sprite generated:', result.landscape);
    console.log('Metadata:', result.metadata);
  } catch (error) {
    console.error('Error generating landscape sprite:', error);
  }
}

createLandscapeSprite();
```

This example generates a pixel-art landscape sprite of a lush forest with a winding river, set during daytime with clear weather and a side-scrolling perspective.

## Main Features

SpriteAI offers several key features:

1. **Character Spritesheet Generation**: Create detailed character spritesheets with multiple animation states.
2. **Landscape Sprite Generation**: Generate beautiful landscape sprites for game backgrounds.
3. **Customizable Options**: Adjust various parameters like size, style, and animation states to suit your needs.
4. **Metadata**: Receive detailed metadata about the generated sprites, including dimensions and frame data.
5. **Background Removal**: Option to remove backgrounds from generated sprites (for landscape sprites).
6. **Automatic Saving**: Save generated sprites directly to your project's asset folder.

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

For creating sets of environment sprites:

```javascript
import { generateEnvironmentSprites } from 'spriteai';

async function createEnvironmentSprites() {
  const description = 'medieval castle';
  const options = {
    elements: 4,
    size: '1024x1024',
    style: 'pixel-art',
    theme: 'fantasy'
  };

  try {
    const result = await generateEnvironmentSprites(description, options);
    console.log('Environment sprites generated:', result.tileset);
    console.log('Metadata:', result.metadata);
  } catch (error) {
    console.error('Error generating environment sprites:', error);
  }
}

createEnvironmentSprites();
```

This generates a set of 4 medieval castle environment sprites in a pixel-art fantasy style.

## Conclusion

SpriteAI provides a powerful and flexible way to generate game assets using AI. By leveraging its various functions and customization options, you can quickly create high-quality sprites and landscapes for your game development projects. Experiment with different descriptions, styles, and settings to achieve the perfect look for your game!