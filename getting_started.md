# Getting Started with SpriteAI

SpriteAI is a powerful library that allows you to generate character spritesheets and environment sprites using AI. This guide will help you get started with SpriteAI, covering installation, basic configuration, and a simple example of generating a character spritesheet.

## Installation

To install SpriteAI, follow these steps:

1. Ensure you have Node.js installed on your system.
2. Open your terminal or command prompt.
3. Run the following command to install SpriteAI:

```bash
npm install spriteai
```

## Basic Configuration

Before using SpriteAI, you need to set up your OpenAI API key. Here's how:

1. Sign up for an OpenAI account if you don't have one already.
2. Obtain your API key from the OpenAI dashboard.
3. Set your API key as an environment variable:

```bash
export OPENAI_API_KEY=your_api_key_here
```

Alternatively, you can set the API key in your code:

```javascript
import OpenAI from "openai";

const openai = new OpenAI({
  apiKey: 'your_api_key_here',
});
```

## Generating a Character Spritesheet

Let's create a simple example to generate a character spritesheet using SpriteAI.

```javascript
import { generateCharacterSpritesheet } from 'spriteai';

async function createCharacterSprite() {
  const options = {
    states: ['idle', 'walk', 'run'],
    framesPerState: 4,
    size: '512x512',
    style: 'pixel-art',
    direction: 'right'
  };

  try {
    const result = await generateCharacterSpritesheet('a cute robot', options);
    console.log('Spritesheet generated:', result.spritesheet);
    console.log('Metadata:', result.metadata);
  } catch (error) {
    console.error('Error generating spritesheet:', error);
  }
}

createCharacterSprite();
```

This script will generate a pixel-art spritesheet of a cute robot with idle, walk, and run animations.

## Understanding the Result

The `generateCharacterSpritesheet` function returns an object with the following properties:

- `original`: URL of the original generated image.
- `spritesheet`: Base64-encoded string of the processed spritesheet.
- `metadata`: Object containing information about the spritesheet, including:
  - `states`: Array of animation states.
  - `framesPerState`: Number of frames per animation state.
  - `totalFrames`: Total number of frames in the spritesheet.
  - `dimensions`: Width and height of the spritesheet.
  - `frameData`: Detailed information about each animation state.

## Next Steps

Now that you've generated your first spritesheet, you can explore more advanced features of SpriteAI:

- Try generating environment sprites using `generateEnvironmentSprites`.
- Experiment with different styles and animation states.
- Integrate the generated spritesheets into your game or application.

For more detailed information on available functions and options, refer to the API documentation.