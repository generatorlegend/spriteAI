<response>

# Getting Started with SpriteAI

Welcome to SpriteAI, a powerful library for generating game sprites and landscapes using AI. This guide will help you get started with installing the library and creating your first sprites.

## Installation

To begin using SpriteAI, you'll need to install it via npm. Open your terminal and run the following command:

```bash
npm install spriteai
```

## Basic Usage

### Importing the Library

After installation, you can import the necessary functions from SpriteAI in your JavaScript file:

```javascript
import { generateCharacterSpritesheet, generateLandscapeSprite } from 'spriteai';
```

### Generating a Character Spritesheet

To create a character spritesheet, use the `generateCharacterSpritesheet` function. Here's a basic example:

```javascript
async function createCharacter() {
  const result = await generateCharacterSpritesheet('a medieval knight in armor', {
    states: ['idle', 'walk', 'attack'],
    framesPerState: 4,
    size: '512x512',
    style: 'pixel-art'
  });

  console.log(result.spritesheet); // Base64 encoded spritesheet
  console.log(result.metadata); // Spritesheet metadata
}

createCharacter();
```

This will generate a pixel-art spritesheet of a medieval knight with idle, walk, and attack animations.

### Generating a Landscape Sprite

To create a landscape sprite, use the `generateLandscapeSprite` function:

```javascript
async function createLandscape() {
  const result = await generateLandscapeSprite('a lush forest with a winding path', {
    size: '1024x1024',
    style: 'pixel-art',
    timeOfDay: 'day',
    weather: 'clear',
    perspective: 'side-scrolling'
  });

  console.log(result.landscape); // Base64 encoded landscape image
  console.log(result.metadata); // Landscape metadata
}

createLandscape();
```

This will generate a pixel-art side-scrolling landscape of a forest during a clear day.

## Advanced Options

Both `generateCharacterSpritesheet` and `generateLandscapeSprite` functions accept various options to customize the output. Refer to the function definitions in the codebase for a complete list of available options.

## Saving Generated Sprites

To save the generated sprites to your local filesystem, you can use the `save` option:

```javascript
const result = await generateCharacterSpritesheet('a space alien', {
  save: true
});
```

This will save the spritesheet in the `assets` folder of your current working directory.

## Next Steps

Now that you've created your first sprites with SpriteAI, you can explore more advanced features:

- Experiment with different animation states and styles
- Try generating various landscape types and perspectives
- Integrate the generated sprites into your game development workflow

For more detailed information on each function and its options, please refer to the API documentation.

Happy sprite generating!

</response># Getting Started with SpriteAI

Welcome to SpriteAI, a powerful library for generating game sprites and landscapes using AI. This guide will help you get started with installing the library and creating your first sprites.

## Installation

To begin using SpriteAI, you'll need to install it via npm. Open your terminal and run the following command:

```bash
npm install spriteai
```

## Basic Usage

### Importing the Library

After installation, you can import the necessary functions from SpriteAI in your JavaScript file:

```javascript
import { generateCharacterSpritesheet, generateLandscapeSprite } from 'spriteai';
```

### Generating a Character Spritesheet

To create a character spritesheet, use the `generateCharacterSpritesheet` function. Here's a basic example:

```javascript
async function createCharacter() {
  const result = await generateCharacterSpritesheet('a medieval knight in armor', {
    states: ['idle', 'walk', 'attack'],
    framesPerState: 4,
    size: '512x512',
    style: 'pixel-art'
  });

  console.log(result.spritesheet); // Base64 encoded spritesheet
  console.log(result.metadata); // Spritesheet metadata
}

createCharacter();
```

This will generate a pixel-art spritesheet of a medieval knight with idle, walk, and attack animations.

### Generating a Landscape Sprite

To create a landscape sprite, use the `generateLandscapeSprite` function:

```javascript
async function createLandscape() {
  const result = await generateLandscapeSprite('a lush forest with a winding path', {
    size: '1024x1024',
    style: 'pixel-art',
    timeOfDay: 'day',
    weather: 'clear',
    perspective: 'side-scrolling'
  });

  console.log(result.landscape); // Base64 encoded landscape image
  console.log(result.metadata); // Landscape metadata
}

createLandscape();
```

This will generate a pixel-art side-scrolling landscape of a forest during a clear day.

## Advanced Options

Both `generateCharacterSpritesheet` and `generateLandscapeSprite` functions accept various options to customize the output. Refer to the function definitions in the codebase for a complete list of available options.

## Saving Generated Sprites

To save the generated sprites to your local filesystem, you can use the `save` option:

```javascript
const result = await generateCharacterSpritesheet('a space alien', {
  save: true
});
```

This will save the spritesheet in the `assets` folder of your current working directory.

## Next Steps

Now that you've created your first sprites with SpriteAI, you can explore more advanced features:

- Experiment with different animation states and styles
- Try generating various landscape types and perspectives
- Integrate the generated sprites into your game development workflow

For more detailed information on each function and its options, please refer to the API documentation.

Happy sprite generating!