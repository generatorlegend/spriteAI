<response>

# Getting Started with SpriteAI

Welcome to SpriteAI! This guide will help you get up and running with our powerful sprite generation library. Follow these steps to start creating amazing character spritesheets and landscape sprites for your games.

## Installation

To begin using SpriteAI, you'll need to install it via npm. Open your terminal and run the following command:

```bash
npm install spriteai
```

This will install SpriteAI and its dependencies in your project.

## Basic Configuration

Before you start generating sprites, you need to set up your OpenAI API key. SpriteAI uses the DALL-E model for image generation, so an OpenAI account is required.

1. Sign up for an OpenAI account if you haven't already: [OpenAI Sign Up](https://beta.openai.com/signup/)
2. Generate an API key in your OpenAI dashboard.
3. Set your API key as an environment variable:

```bash
export OPENAI_API_KEY='your-api-key-here'
```

Alternatively, you can set the API key in your JavaScript code:

```javascript
import OpenAI from "openai";

const openai = new OpenAI({
  apiKey: 'your-api-key-here',
});
```

## Generating Character Spritesheets

SpriteAI makes it easy to generate character spritesheets with various animation states. Here's a simple example:

```javascript
import { generateCharacterSpritesheet } from 'spriteai';

async function createCharacterSprite() {
  const result = await generateCharacterSpritesheet('a medieval knight in armor', {
    states: ['idle', 'walk', 'attack'],
    framesPerState: 4,
    style: 'pixel-art',
    size: '512x512',
    save: true
  });

  console.log('Spritesheet generated:', result.spritesheet);
  console.log('Metadata:', result.metadata);
}

createCharacterSprite();
```

This will generate a pixel-art spritesheet of a medieval knight with idle, walk, and attack animations, each containing 4 frames.

## Creating Landscape Sprites

SpriteAI also allows you to generate beautiful landscape sprites for your game backgrounds. Here's how to do it:

```javascript
import { generateLandscapeSprite } from 'spriteai';

async function createLandscapeSprite() {
  const result = await generateLandscapeSprite('a lush forest with a winding river', {
    style: 'pixel-art',
    timeOfDay: 'sunset',
    weather: 'clear',
    perspective: 'side-scrolling',
    size: '1024x512',
    save: true
  });

  console.log('Landscape sprite generated:', result.landscape);
  console.log('Metadata:', result.metadata);
}

createLandscapeSprite();
```

This will create a pixel-art landscape sprite of a forest with a river at sunset, perfect for a side-scrolling game.

## Advanced Features

### Removing Background Color

SpriteAI includes a function to remove background colors from your sprites:

```javascript
import { removeBackgroundColor } from 'spriteai';

async function removeBackground() {
  await removeBackgroundColor(
    'input-image.png',
    'output-image.png',
    '#FFFFFF',  // Target color to remove
    10  // Color threshold
  );
  console.log('Background removed successfully');
}

removeBackground();
```

This function is useful for cleaning up generated sprites or preparing existing images for use in your game.

## Next Steps

Now that you've got the basics, here are some ideas to explore further:

1. Experiment with different animation states and frame counts for character spritesheets.
2. Try generating landscapes with various weather conditions and times of day.
3. Use the `removeBackgroundColor` function to process your generated sprites for transparency.
4. Combine multiple sprites to create complex game scenes.

For more detailed information on available functions and options, check out our [API Reference](api-reference.md) documentation.

Happy sprite generating!

</response># Getting Started with SpriteAI

Welcome to SpriteAI! This guide will help you get up and running with our powerful sprite generation library. Follow these steps to start creating amazing character spritesheets and landscape sprites for your games.

## Installation

To begin using SpriteAI, you'll need to install it via npm. Open your terminal and run the following command:

```bash
npm install spriteai
```

This will install SpriteAI and its dependencies in your project.

## Basic Configuration

Before you start generating sprites, you need to set up your OpenAI API key. SpriteAI uses the DALL-E model for image generation, so an OpenAI account is required.

1. Sign up for an OpenAI account if you haven't already: [OpenAI Sign Up](https://beta.openai.com/signup/)
2. Generate an API key in your OpenAI dashboard.
3. Set your API key as an environment variable:

```bash
export OPENAI_API_KEY='your-api-key-here'
```

Alternatively, you can set the API key in your JavaScript code:

```javascript
import OpenAI from "openai";

const openai = new OpenAI({
  apiKey: 'your-api-key-here',
});
```

## Generating Character Spritesheets

SpriteAI makes it easy to generate character spritesheets with various animation states. Here's a simple example:

```javascript
import { generateCharacterSpritesheet } from 'spriteai';

async function createCharacterSprite() {
  const result = await generateCharacterSpritesheet('a medieval knight in armor', {
    states: ['idle', 'walk', 'attack'],
    framesPerState: 4,
    style: 'pixel-art',
    size: '512x512',
    save: true
  });

  console.log('Spritesheet generated:', result.spritesheet);
  console.log('Metadata:', result.metadata);
}

createCharacterSprite();
```

This will generate a pixel-art spritesheet of a medieval knight with idle, walk, and attack animations, each containing 4 frames.

## Creating Landscape Sprites

SpriteAI also allows you to generate beautiful landscape sprites for your game backgrounds. Here's how to do it:

```javascript
import { generateLandscapeSprite } from 'spriteai';

async function createLandscapeSprite() {
  const result = await generateLandscapeSprite('a lush forest with a winding river', {
    style: 'pixel-art',
    timeOfDay: 'sunset',
    weather: 'clear',
    perspective: 'side-scrolling',
    size: '1024x512',
    save: true
  });

  console.log('Landscape sprite generated:', result.landscape);
  console.log('Metadata:', result.metadata);
}

createLandscapeSprite();
```

This will create a pixel-art landscape sprite of a forest with a river at sunset, perfect for a side-scrolling game.

## Advanced Features

### Removing Background Color

SpriteAI includes a function to remove background colors from your sprites:

```javascript
import { removeBackgroundColor } from 'spriteai';

async function removeBackground() {
  await removeBackgroundColor(
    'input-image.png',
    'output-image.png',
    '#FFFFFF',  // Target color to remove
    10  // Color threshold
  );
  console.log('Background removed successfully');
}

removeBackground();
```

This function is useful for cleaning up generated sprites or preparing existing images for use in your game.

## Next Steps

Now that you've got the basics, here are some ideas to explore further:

1. Experiment with different animation states and frame counts for character spritesheets.
2. Try generating landscapes with various weather conditions and times of day.
3. Use the `removeBackgroundColor` function to process your generated sprites for transparency.
4. Combine multiple sprites to create complex game scenes.

For more detailed information on available functions and options, check out our [API Reference](api-reference.md) documentation.

Happy sprite generating!