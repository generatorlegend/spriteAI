# Getting Started with SpriteAI

Welcome to SpriteAI, a powerful library for generating game assets using AI! This guide will help you get up and running with SpriteAI, covering installation, basic configuration, and simple usage examples.

## Installation

To start using SpriteAI, you'll need to install it along with its dependencies. Make sure you have Node.js installed on your system, then follow these steps:

1. Create a new directory for your project and navigate to it in your terminal.

2. Initialize a new Node.js project:

   ```
   npm init -y
   ```

3. Install SpriteAI and its dependencies:

   ```
   npm install spriteai openai axios sharp jimp
   ```

## Basic Configuration

Before using SpriteAI, you need to set up your OpenAI API key. This key is required to generate images using DALL-E 3.

1. Sign up for an OpenAI account and obtain an API key from the OpenAI dashboard.

2. Set your API key as an environment variable:

   ```
   export OPENAI_API_KEY=your_api_key_here
   ```

   Alternatively, you can set it in your code (not recommended for production):

   ```javascript
   import OpenAI from "openai";

   const openai = new OpenAI({
     apiKey: 'your_api_key_here'
   });
   ```

## Generating Character Spritesheets

SpriteAI allows you to generate character spritesheets with various animation states. Here's a simple example:

```javascript
import { generateCharacterSpritesheet } from 'spriteai';

async function createCharacter() {
  const result = await generateCharacterSpritesheet("a cute robot", {
    states: ['idle', 'walk', 'run'],
    framesPerState: 4,
    style: 'pixel-art',
    save: true
  });

  console.log("Spritesheet generated:", result.spritesheet);
  console.log("Metadata:", result.metadata);
}

createCharacter();
```

This will generate a pixel-art spritesheet of a cute robot with idle, walk, and run animations, each having 4 frames.

## Generating Landscape Sprites

You can also create landscape sprites for game backgrounds:

```javascript
import { generateLandscapeSprite } from 'spriteai';

async function createLandscape() {
  const result = await generateLandscapeSprite("a lush forest with a waterfall", {
    style: 'pixel-art',
    timeOfDay: 'sunset',
    weather: 'clear',
    perspective: 'side-scrolling',
    save: true
  });

  console.log("Landscape generated:", result.landscape);
  console.log("Metadata:", result.metadata);
}

createLandscape();
```

This will create a pixel-art side-scrolling landscape of a lush forest with a waterfall at sunset.

## Key Concepts

- **Spritesheet**: A single image containing multiple frames of an animation or multiple related sprites.
- **Animation States**: Different actions a character can perform (e.g., idle, walk, run, attack).
- **Frames**: Individual images that make up an animation when played in sequence.
- **Style**: The artistic style of the generated sprites (e.g., pixel-art, vector, 3D).

## Advanced Features

SpriteAI offers additional features for more customized sprite generation:

- Fetching available animation states:

  ```javascript
  import { fetchAvailableAnimationStates } from 'spriteai';

  const states = await fetchAvailableAnimationStates();
  console.log("Available animation states:", states);
  ```

- Fetching available sprite styles:

  ```javascript
  import { fetchAvailableSpriteStyles } from 'spriteai';

  const styles = await fetchAvailableSpriteStyles();
  console.log("Available sprite styles:", styles);
  ```

- Generating environment sprites:

  ```javascript
  import { generateEnvironmentSprites } from 'spriteai';

  const environment = await generateEnvironmentSprites("medieval town", {
    elements: 6,
    style: 'pixel-art',
    theme: 'fantasy'
  });

  console.log("Environment tileset:", environment.tileset);
  ```

## Next Steps

Now that you're familiar with the basics of SpriteAI, you can start experimenting with different descriptions, styles, and options to create unique assets for your game projects. Remember to refer to the API documentation for more detailed information on each function and its parameters.

Happy sprite generating!