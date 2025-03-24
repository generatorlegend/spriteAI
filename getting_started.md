<response>

# Getting Started with SpriteAI

SpriteAI is a powerful library that allows you to generate character spritesheets and landscape sprites using AI. This guide will help you get started with SpriteAI, covering installation, basic usage, and an overview of available options.

## Installation

To install SpriteAI, follow these steps:

1. Make sure you have Node.js installed on your system.
2. Create a new directory for your project and navigate to it in the terminal.
3. Initialize a new Node.js project by running:
   ```
   npm init -y
   ```
4. Install SpriteAI and its dependencies by running:
   ```
   npm install spriteai openai axios sharp jimp
   ```

## Basic Usage

### Generating a Character Spritesheet

To generate a character spritesheet, use the `generateCharacterSpritesheet` function. Here's a basic example:

```javascript
import { generateCharacterSpritesheet } from 'spriteai';

async function generateSprite() {
  const result = await generateCharacterSpritesheet('a medieval knight in armor');
  console.log(result.spritesheet); // Base64 encoded spritesheet
  console.log(result.metadata); // Metadata about the generated spritesheet
}

generateSprite();
```

### Generating a Landscape Sprite

To generate a landscape sprite, use the `generateLandscapeSprite` function:

```javascript
import { generateLandscapeSprite } from 'spriteai';

async function generateLandscape() {
  const result = await generateLandscapeSprite('a lush forest with a winding river');
  console.log(result.landscape); // Base64 encoded landscape sprite
  console.log(result.metadata); // Metadata about the generated landscape
}

generateLandscape();
```

## Available Options

Both `generateCharacterSpritesheet` and `generateLandscapeSprite` functions accept an options object as a second parameter to customize the output.

### Character Spritesheet Options

- `states`: Array of animation states (default: `['idle', 'walk', 'run', 'attack']`)
- `framesPerState`: Number of frames per animation state (default: `6`)
- `size`: Output size (default: `'1024x1024'`)
- `style`: Art style (default: `'pixel-art'`)
- `padding`: Padding between sprites (default: `1`)
- `direction`: Base direction of character (default: `'right'`)
- `save`: Whether to save the generated image (default: `false`)

Example with custom options:

```javascript
const options = {
  states: ['idle', 'walk', 'jump'],
  framesPerState: 8,
  size: '2048x2048',
  style: 'vector',
  direction: 'left',
  save: true
};

const result = await generateCharacterSpritesheet('a futuristic robot', options);
```

### Landscape Sprite Options

- `size`: Output size (default: `'1024x1024'`)
- `style`: Art style (default: `'pixel-art'`)
- `timeOfDay`: Time of day setting (default: `'day'`)
- `weather`: Weather conditions (default: `'clear'`)
- `perspective`: Perspective view (default: `'side-scrolling'`)
- `save`: Whether to save the generated image (default: `false`)
- `removeBackground`: Whether to remove the background (default: `false`)
- `backgroundColor`: Background color to remove (used with `removeBackground`)
- `colorThreshold`: Threshold for background color removal (used with `removeBackground`)

Example with custom options:

```javascript
const options = {
  size: '2048x2048',
  style: '3d',
  timeOfDay: 'night',
  weather: 'rainy',
  perspective: 'isometric',
  save: true,
  removeBackground: true,
  backgroundColor: '#FFFFFF',
  colorThreshold: 0.1
};

const result = await generateLandscapeSprite('a cyberpunk city skyline', options);
```

## Additional Features

SpriteAI also provides functions to fetch available animation states and sprite styles:

```javascript
import { fetchAvailableAnimationStates, fetchAvailableSpriteStyles } from 'spriteai';

async function getAvailableOptions() {
  const states = await fetchAvailableAnimationStates();
  console.log('Available animation states:', states);

  const styles = await fetchAvailableSpriteStyles();
  console.log('Available sprite styles:', styles);
}

getAvailableOptions();
```

These functions can be useful for dynamically populating option lists in your application.

With this guide, you should be able to start using SpriteAI to generate character spritesheets and landscape sprites for your projects. Experiment with different descriptions and options to create unique and diverse game assets!

</response># Getting Started with SpriteAI

SpriteAI is a powerful library that allows you to generate character spritesheets and landscape sprites using AI. This guide will help you get started with SpriteAI, covering installation, basic usage, and an overview of available options.

## Installation

To install SpriteAI, follow these steps:

1. Make sure you have Node.js installed on your system.
2. Create a new directory for your project and navigate to it in the terminal.
3. Initialize a new Node.js project by running:
   ```
   npm init -y
   ```
4. Install SpriteAI and its dependencies by running:
   ```
   npm install spriteai openai axios sharp jimp
   ```

## Basic Usage

### Generating a Character Spritesheet

To generate a character spritesheet, use the `generateCharacterSpritesheet` function. Here's a basic example:

```javascript
import { generateCharacterSpritesheet } from 'spriteai';

async function generateSprite() {
  const result = await generateCharacterSpritesheet('a medieval knight in armor');
  console.log(result.spritesheet); // Base64 encoded spritesheet
  console.log(result.metadata); // Metadata about the generated spritesheet
}

generateSprite();
```

### Generating a Landscape Sprite

To generate a landscape sprite, use the `generateLandscapeSprite` function:

```javascript
import { generateLandscapeSprite } from 'spriteai';

async function generateLandscape() {
  const result = await generateLandscapeSprite('a lush forest with a winding river');
  console.log(result.landscape); // Base64 encoded landscape sprite
  console.log(result.metadata); // Metadata about the generated landscape
}

generateLandscape();
```

## Available Options

Both `generateCharacterSpritesheet` and `generateLandscapeSprite` functions accept an options object as a second parameter to customize the output.

### Character Spritesheet Options

- `states`: Array of animation states (default: `['idle', 'walk', 'run', 'attack']`)
- `framesPerState`: Number of frames per animation state (default: `6`)
- `size`: Output size (default: `'1024x1024'`)
- `style`: Art style (default: `'pixel-art'`)
- `padding`: Padding between sprites (default: `1`)
- `direction`: Base direction of character (default: `'right'`)
- `save`: Whether to save the generated image (default: `false`)

Example with custom options:

```javascript
const options = {
  states: ['idle', 'walk', 'jump'],
  framesPerState: 8,
  size: '2048x2048',
  style: 'vector',
  direction: 'left',
  save: true
};

const result = await generateCharacterSpritesheet('a futuristic robot', options);
```

### Landscape Sprite Options

- `size`: Output size (default: `'1024x1024'`)
- `style`: Art style (default: `'pixel-art'`)
- `timeOfDay`: Time of day setting (default: `'day'`)
- `weather`: Weather conditions (default: `'clear'`)
- `perspective`: Perspective view (default: `'side-scrolling'`)
- `save`: Whether to save the generated image (default: `false`)
- `removeBackground`: Whether to remove the background (default: `false`)
- `backgroundColor`: Background color to remove (used with `removeBackground`)
- `colorThreshold`: Threshold for background color removal (used with `removeBackground`)

Example with custom options:

```javascript
const options = {
  size: '2048x2048',
  style: '3d',
  timeOfDay: 'night',
  weather: 'rainy',
  perspective: 'isometric',
  save: true,
  removeBackground: true,
  backgroundColor: '#FFFFFF',
  colorThreshold: 0.1
};

const result = await generateLandscapeSprite('a cyberpunk city skyline', options);
```

## Additional Features

SpriteAI also provides functions to fetch available animation states and sprite styles:

```javascript
import { fetchAvailableAnimationStates, fetchAvailableSpriteStyles } from 'spriteai';

async function getAvailableOptions() {
  const states = await fetchAvailableAnimationStates();
  console.log('Available animation states:', states);

  const styles = await fetchAvailableSpriteStyles();
  console.log('Available sprite styles:', styles);
}

getAvailableOptions();
```

These functions can be useful for dynamically populating option lists in your application.

With this guide, you should be able to start using SpriteAI to generate character spritesheets and landscape sprites for your projects. Experiment with different descriptions and options to create unique and diverse game assets!