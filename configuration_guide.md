# Configuration Guide

This guide explains how to configure the SpriteAI library for different use cases. We'll cover setting up API keys, customizing output options, and adjusting generation parameters. We'll also provide examples of common configuration scenarios and best practices for optimizing the library's performance.

## Table of Contents

1. [Setting Up API Keys](#setting-up-api-keys)
2. [Customizing Output Options](#customizing-output-options)
3. [Adjusting Generation Parameters](#adjusting-generation-parameters)
4. [Common Configuration Scenarios](#common-configuration-scenarios)
5. [Best Practices for Optimization](#best-practices-for-optimization)

## Setting Up API Keys

To use the SpriteAI library, you need to set up your OpenAI API key. This key is required for generating images using the DALL-E model.

1. Sign up for an OpenAI account at https://openai.com/ if you haven't already.
2. Generate an API key in your OpenAI dashboard.
3. Set the API key as an environment variable:

```bash
export OPENAI_API_KEY=your_api_key_here
```

Alternatively, you can set the API key programmatically:

```javascript
import OpenAI from "openai";

const openAiObject = new OpenAI({
  apiKey: 'your_api_key_here'
});
```

## Customizing Output Options

The SpriteAI library allows you to customize various output options for both character spritesheets and environment sprites.

### Character Spritesheets

When using the `generateCharacterSpritesheet` function, you can customize the following options:

```javascript
const options = {
  states: ['idle', 'walk', 'run', 'attack'],
  framesPerState: 6,
  size: '1024x1024',
  style: 'pixel-art',
  padding: 1,
  direction: 'right',
  save: true
};

const result = await generateCharacterSpritesheet('a warrior with a sword', options);
```

- `states`: An array of animation states to generate (default: ['idle', 'walk', 'run', 'attack'])
- `framesPerState`: Number of frames per animation state (default: 6)
- `size`: Output image size (default: '1024x1024')
- `style`: Art style of the sprite (default: 'pixel-art')
- `padding`: Padding between sprites (default: 1)
- `direction`: Base direction of the character (default: 'right')
- `save`: Whether to save the generated image to disk (default: false)

### Environment Sprites

For the `generateEnvironmentSprites` function, you can customize these options:

```javascript
const options = {
  elements: 4,
  size: '1024x1024',
  style: 'pixel-art',
  padding: 1,
  theme: 'fantasy',
  save: true
};

const result = await generateEnvironmentSprites('forest', options);
```

- `elements`: Number of different elements to generate (default: 4)
- `size`: Output image size (default: '1024x1024')
- `style`: Art style of the sprites (default: 'pixel-art')
- `padding`: Padding between elements (default: 1)
- `theme`: Theme of the environment (default: 'fantasy')
- `save`: Whether to save the generated image to disk (default: false)

## Adjusting Generation Parameters

The SpriteAI library uses OpenAI's DALL-E 3 model for image generation. While most parameters are handled internally, you can adjust the description and style to influence the output:

1. **Description**: Provide a detailed description of the character or environment you want to generate. Be specific about features, colors, and themes.

2. **Style**: Use the `style` option to specify the desired art style. Available styles can be fetched using the `fetchAvailableSpriteStyles` function:

```javascript
const availableStyles = await fetchAvailableSpriteStyles();
console.log(availableStyles);
// Output: ['pixel-art', 'vector', '3d', 'hand-drawn', 'anime']
```

## Common Configuration Scenarios

### Generating a Character Spritesheet with Custom States

```javascript
const options = {
  states: ['idle', 'walk', 'jump', 'attack'],
  framesPerState: 8,
  size: '2048x2048',
  style: 'anime',
  direction: 'left'
};

const result = await generateCharacterSpritesheet('a ninja with throwing stars', options);
```

### Creating a Tileset for a Game Environment

```javascript
const options = {
  elements: 6,
  size: '2048x2048',
  style: 'pixel-art',
  theme: 'sci-fi',
  save: true
};

const result = await generateEnvironmentSprites('space station interior', options);
```

## Best Practices for Optimization

1. **Reuse API Calls**: Cache and reuse generated sprites when possible to minimize API calls and reduce costs.

2. **Batch Generations**: If you need multiple sprites, consider generating them in a single larger spritesheet and then splitting them programmatically.

3. **Optimize Image Size**: Use the smallest size that meets your quality requirements to reduce processing time and storage needs.

4. **Use Appropriate Frames**: Only generate the number of frames you need for each animation state to optimize performance and reduce generation time.

5. **Leverage Metadata**: Utilize the returned metadata for efficient sprite handling in your game or application.

6. **Background Removal**: If you need sprites with transparent backgrounds, use the `removeBackgroundColor` function after generation:

```javascript
import { removeBackgroundColor } from './path/to/spriteAI';

await removeBackgroundColor(
  'input_image.png',
  'output_image.png',
  '#FFFFFF',  // background color to remove
  0.1         // color threshold
);
```

By following these configuration guidelines and best practices, you can effectively use the SpriteAI library to generate high-quality sprites and optimize your game development workflow.