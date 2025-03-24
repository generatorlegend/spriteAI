<response>

# Getting Started with SpriteAI

SpriteAI is a powerful tool for generating game assets using AI. This guide will walk you through the process of setting up SpriteAI and using its main features to create character spritesheets and landscape sprites.

## Installation

To get started with SpriteAI, follow these steps:

1. Ensure you have Node.js installed on your system.
2. Create a new directory for your project and navigate to it in your terminal.
3. Initialize a new Node.js project:

```bash
npm init -y
```

4. Install SpriteAI and its dependencies:

```bash
npm install spriteai openai axios sharp jimp
```

5. Create a new file named `index.js` in your project directory.

## Basic Usage

### Importing SpriteAI

To use SpriteAI in your project, import the necessary functions at the top of your `index.js` file:

```javascript
import { generateCharacterSpritesheet, generateLandscapeSprite } from 'spriteai';
```

### Generating a Character Spritesheet

To create a character spritesheet, use the `generateCharacterSpritesheet` function:

```javascript
async function createCharacter() {
  const result = await generateCharacterSpritesheet('a medieval knight', {
    states: ['idle', 'walk', 'attack'],
    framesPerState: 4,
    size: '1024x1024',
    style: 'pixel-art',
    save: true
  });

  console.log('Character spritesheet generated:', result);
}

createCharacter();
```

This will generate a pixel-art spritesheet of a medieval knight with idle, walk, and attack animations.

### Generating a Landscape Sprite

To create a landscape sprite, use the `generateLandscapeSprite` function:

```javascript
async function createLandscape() {
  const result = await generateLandscapeSprite('a lush forest with a hidden waterfall', {
    size: '1024x1024',
    style: 'pixel-art',
    timeOfDay: 'day',
    weather: 'clear',
    perspective: 'side-scrolling',
    save: true
  });

  console.log('Landscape sprite generated:', result);
}

createLandscape();
```

This will generate a pixel-art landscape of a lush forest with a hidden waterfall, suitable for a side-scrolling game.

## Main Features

SpriteAI offers several key features for game asset generation:

1. **Character Spritesheets**: Create animated character sprites with customizable states, frames, and styles.
2. **Landscape Sprites**: Generate game backgrounds and environments with various settings and perspectives.
3. **Customizable Options**: Adjust parameters like size, style, time of day, weather, and more to fine-tune your generated assets.
4. **Background Removal**: Automatically remove backgrounds from generated sprites (available for landscape sprites).
5. **Asset Saving**: Option to save generated assets directly to your project's asset folder.

## Advanced Usage

### Fetching Available Animation States

SpriteAI provides a function to fetch available animation states for character spritesheets:

```javascript
import { fetchAvailableAnimationStates } from 'spriteai';

async function getAnimationStates() {
  const states = await fetchAvailableAnimationStates();
  console.log('Available animation states:', states);
}

getAnimationStates();
```

### Fetching Available Sprite Styles

You can also fetch the available sprite styles:

```javascript
import { fetchAvailableSpriteStyles } from 'spriteai';

async function getSpriteStyles() {
  const styles = await fetchAvailableSpriteStyles();
  console.log('Available sprite styles:', styles);
}

getSpriteStyles();
```

### Generating Environment Sprites

For creating sets of environment elements, use the `generateEnvironmentSprites` function:

```javascript
import { generateEnvironmentSprites } from 'spriteai';

async function createEnvironment() {
  const result = await generateEnvironmentSprites('desert oasis', {
    elements: 6,
    size: '1024x1024',
    style: 'pixel-art',
    theme: 'fantasy',
    save: true
  });

  console.log('Environment sprites generated:', result);
}

createEnvironment();
```

This will generate a set of 6 fantasy-themed, pixel-art desert oasis environment elements.

## Conclusion

SpriteAI provides a powerful and flexible way to generate game assets using AI. By leveraging its various functions and customization options, you can quickly create high-quality sprites and environments for your game projects. Experiment with different settings and parameters to achieve the desired results for your unique game aesthetics.

</response># Getting Started with SpriteAI

SpriteAI is a powerful tool for generating game assets using AI. This guide will walk you through the process of setting up SpriteAI and using its main features to create character spritesheets and landscape sprites.

## Installation

To get started with SpriteAI, follow these steps:

1. Ensure you have Node.js installed on your system.
2. Create a new directory for your project and navigate to it in your terminal.
3. Initialize a new Node.js project:

```bash
npm init -y
```

4. Install SpriteAI and its dependencies:

```bash
npm install spriteai openai axios sharp jimp
```

5. Create a new file named `index.js` in your project directory.

## Basic Usage

### Importing SpriteAI

To use SpriteAI in your project, import the necessary functions at the top of your `index.js` file:

```javascript
import { generateCharacterSpritesheet, generateLandscapeSprite } from 'spriteai';
```

### Generating a Character Spritesheet

To create a character spritesheet, use the `generateCharacterSpritesheet` function:

```javascript
async function createCharacter() {
  const result = await generateCharacterSpritesheet('a medieval knight', {
    states: ['idle', 'walk', 'attack'],
    framesPerState: 4,
    size: '1024x1024',
    style: 'pixel-art',
    save: true
  });

  console.log('Character spritesheet generated:', result);
}

createCharacter();
```

This will generate a pixel-art spritesheet of a medieval knight with idle, walk, and attack animations.

### Generating a Landscape Sprite

To create a landscape sprite, use the `generateLandscapeSprite` function:

```javascript
async function createLandscape() {
  const result = await generateLandscapeSprite('a lush forest with a hidden waterfall', {
    size: '1024x1024',
    style: 'pixel-art',
    timeOfDay: 'day',
    weather: 'clear',
    perspective: 'side-scrolling',
    save: true
  });

  console.log('Landscape sprite generated:', result);
}

createLandscape();
```

This will generate a pixel-art landscape of a lush forest with a hidden waterfall, suitable for a side-scrolling game.

## Main Features

SpriteAI offers several key features for game asset generation:

1. **Character Spritesheets**: Create animated character sprites with customizable states, frames, and styles.
2. **Landscape Sprites**: Generate game backgrounds and environments with various settings and perspectives.
3. **Customizable Options**: Adjust parameters like size, style, time of day, weather, and more to fine-tune your generated assets.
4. **Background Removal**: Automatically remove backgrounds from generated sprites (available for landscape sprites).
5. **Asset Saving**: Option to save generated assets directly to your project's asset folder.

## Advanced Usage

### Fetching Available Animation States

SpriteAI provides a function to fetch available animation states for character spritesheets:

```javascript
import { fetchAvailableAnimationStates } from 'spriteai';

async function getAnimationStates() {
  const states = await fetchAvailableAnimationStates();
  console.log('Available animation states:', states);
}

getAnimationStates();
```

### Fetching Available Sprite Styles

You can also fetch the available sprite styles:

```javascript
import { fetchAvailableSpriteStyles } from 'spriteai';

async function getSpriteStyles() {
  const styles = await fetchAvailableSpriteStyles();
  console.log('Available sprite styles:', styles);
}

getSpriteStyles();
```

### Generating Environment Sprites

For creating sets of environment elements, use the `generateEnvironmentSprites` function:

```javascript
import { generateEnvironmentSprites } from 'spriteai';

async function createEnvironment() {
  const result = await generateEnvironmentSprites('desert oasis', {
    elements: 6,
    size: '1024x1024',
    style: 'pixel-art',
    theme: 'fantasy',
    save: true
  });

  console.log('Environment sprites generated:', result);
}

createEnvironment();
```

This will generate a set of 6 fantasy-themed, pixel-art desert oasis environment elements.

## Conclusion

SpriteAI provides a powerful and flexible way to generate game assets using AI. By leveraging its various functions and customization options, you can quickly create high-quality sprites and environments for your game projects. Experiment with different settings and parameters to achieve the desired results for your unique game aesthetics.