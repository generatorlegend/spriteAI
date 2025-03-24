<response>
# Getting Started with SpriteAI

## Introduction

SpriteAI is a powerful library that allows you to generate character spritesheets and landscape sprites using AI. This guide will help you get started with SpriteAI, covering installation, basic usage, and key concepts.

## Installation

To install SpriteAI, you'll need Node.js and npm installed on your system. Once you have those, you can install SpriteAI using npm:

```bash
npm install spriteai
```

## Basic Usage

### Generating Character Spritesheets

To generate a character spritesheet, you can use the `generateCharacterSpritesheet` function. Here's a basic example:

```javascript
import { generateCharacterSpritesheet } from 'spriteai';

async function createCharacter() {
  const result = await generateCharacterSpritesheet('a brave knight in armor', {
    states: ['idle', 'walk', 'run', 'attack'],
    framesPerState: 6,
    size: '1024x1024',
    style: 'pixel-art',
    direction: 'right'
  });

  console.log(result.spritesheet); // Base64 encoded spritesheet
  console.log(result.metadata); // Metadata about the generated spritesheet
}

createCharacter();
```

### Generating Landscape Sprites

To generate a landscape sprite, use the `generateLandscapeSprite` function:

```javascript
import { generateLandscapeSprite } from 'spriteai';

async function createLandscape() {
  const result = await generateLandscapeSprite('a lush forest with a winding path', {
    size: '1024x1024',
    style: 'pixel-art',
    timeOfDay: 'day',
    weather: 'clear',
    perspective: 'side-scrolling'
  });

  console.log(result.landscape); // Base64 encoded landscape sprite
  console.log(result.metadata); // Metadata about the generated landscape
}

createLandscape();
```

## Key Concepts

### Character Spritesheets

- **States**: Different animation states for the character (e.g., idle, walk, run, attack).
- **Frames Per State**: The number of frames for each animation state.
- **Style**: The visual style of the spritesheet (e.g., pixel-art, vector).
- **Direction**: The base direction the character is facing.

### Landscape Sprites

- **Time of Day**: The lighting condition of the landscape (e.g., day, night, sunset).
- **Weather**: Weather conditions in the landscape (e.g., clear, rainy, foggy).
- **Perspective**: The viewpoint of the landscape (e.g., side-scrolling, top-down).

## Advanced Features

### Removing Background Color

SpriteAI includes a utility function to remove background colors from generated sprites:

```javascript
import { removeBackgroundColor } from 'spriteai';

async function processSprite() {
  await removeBackgroundColor(
    'input_sprite.png',
    'output_sprite.png',
    '#FFFFFF', // Color to remove
    0.1 // Color threshold
  );
}

processSprite();
```

### Fetching Available Options

SpriteAI provides functions to fetch available animation states and sprite styles:

```javascript
import { fetchAvailableAnimationStates, fetchAvailableSpriteStyles } from 'spriteai';

async function getOptions() {
  const states = await fetchAvailableAnimationStates();
  const styles = await fetchAvailableSpriteStyles();

  console.log('Available animation states:', states);
  console.log('Available sprite styles:', styles);
}

getOptions();
```

## Next Steps

Now that you're familiar with the basics of SpriteAI, you can start creating amazing game assets with AI-generated sprites. Experiment with different descriptions, styles, and options to achieve the perfect look for your game characters and environments.

For more detailed information on each function and its parameters, refer to the API documentation.

Happy sprite generation!
</response># Getting Started with SpriteAI

## Introduction

SpriteAI is a powerful library that allows you to generate character spritesheets and landscape sprites using AI. This guide will help you get started with SpriteAI, covering installation, basic usage, and key concepts.

## Installation

To install SpriteAI, you'll need Node.js and npm installed on your system. Once you have those, you can install SpriteAI using npm:

```bash
npm install spriteai
```

## Basic Usage

### Generating Character Spritesheets

To generate a character spritesheet, you can use the `generateCharacterSpritesheet` function. Here's a basic example:

```javascript
import { generateCharacterSpritesheet } from 'spriteai';

async function createCharacter() {
  const result = await generateCharacterSpritesheet('a brave knight in armor', {
    states: ['idle', 'walk', 'run', 'attack'],
    framesPerState: 6,
    size: '1024x1024',
    style: 'pixel-art',
    direction: 'right'
  });

  console.log(result.spritesheet); // Base64 encoded spritesheet
  console.log(result.metadata); // Metadata about the generated spritesheet
}

createCharacter();
```

### Generating Landscape Sprites

To generate a landscape sprite, use the `generateLandscapeSprite` function:

```javascript
import { generateLandscapeSprite } from 'spriteai';

async function createLandscape() {
  const result = await generateLandscapeSprite('a lush forest with a winding path', {
    size: '1024x1024',
    style: 'pixel-art',
    timeOfDay: 'day',
    weather: 'clear',
    perspective: 'side-scrolling'
  });

  console.log(result.landscape); // Base64 encoded landscape sprite
  console.log(result.metadata); // Metadata about the generated landscape
}

createLandscape();
```

## Key Concepts

### Character Spritesheets

- **States**: Different animation states for the character (e.g., idle, walk, run, attack).
- **Frames Per State**: The number of frames for each animation state.
- **Style**: The visual style of the spritesheet (e.g., pixel-art, vector).
- **Direction**: The base direction the character is facing.

### Landscape Sprites

- **Time of Day**: The lighting condition of the landscape (e.g., day, night, sunset).
- **Weather**: Weather conditions in the landscape (e.g., clear, rainy, foggy).
- **Perspective**: The viewpoint of the landscape (e.g., side-scrolling, top-down).

## Advanced Features

### Removing Background Color

SpriteAI includes a utility function to remove background colors from generated sprites:

```javascript
import { removeBackgroundColor } from 'spriteai';

async function processSprite() {
  await removeBackgroundColor(
    'input_sprite.png',
    'output_sprite.png',
    '#FFFFFF', // Color to remove
    0.1 // Color threshold
  );
}

processSprite();
```

### Fetching Available Options

SpriteAI provides functions to fetch available animation states and sprite styles:

```javascript
import { fetchAvailableAnimationStates, fetchAvailableSpriteStyles } from 'spriteai';

async function getOptions() {
  const states = await fetchAvailableAnimationStates();
  const styles = await fetchAvailableSpriteStyles();

  console.log('Available animation states:', states);
  console.log('Available sprite styles:', styles);
}

getOptions();
```

## Next Steps

Now that you're familiar with the basics of SpriteAI, you can start creating amazing game assets with AI-generated sprites. Experiment with different descriptions, styles, and options to achieve the perfect look for your game characters and environments.

For more detailed information on each function and its parameters, refer to the API documentation.

Happy sprite generation!