# Character Spritesheet Generator Guide

## Introduction

The `generateCharacterSpritesheet` function is a powerful tool for creating custom character spritesheets using AI-generated images. This guide will walk you through the process of using this function, explain all available options, and provide examples of different use cases.

## Function Signature

```javascript
generateCharacterSpritesheet(description, options = {})
```

## Parameters

1. `description` (string): A detailed description of the character you want to generate.
2. `options` (object): An optional object containing customization parameters.

## Options

The `options` object can include the following properties:

- `states` (array of strings): Animation states to generate. Default: `['idle', 'walk', 'run', 'attack']`
- `framesPerState` (number): Number of frames per animation state. Default: `6`
- `size` (string): Output size of the spritesheet. Default: `'1024x1024'`
- `style` (string): Art style of the character. Default: `'pixel-art'`
- `padding` (number): Padding between sprites. Default: `1`
- `direction` (string): Base direction the character is facing. Default: `'right'`
- `save` (boolean): Whether to save the generated image to the local filesystem. Default: `false`

## Basic Usage

Here's a simple example of how to use the `generateCharacterSpritesheet` function:

```javascript
import { generateCharacterSpritesheet } from './spriteAI';

async function generateSprite() {
  const result = await generateCharacterSpritesheet('a cute cat wizard with a pointy hat and magic wand');
  console.log(result);
}

generateSprite();
```

This will generate a spritesheet of a cat wizard character with default animation states and options.

## Customizing Animation States

You can customize the animation states by providing an array of state names in the `options` object:

```javascript
const options = {
  states: ['idle', 'cast', 'fly', 'land'],
  framesPerState: 8
};

const result = await generateCharacterSpritesheet('a dragon with colorful scales', options);
```

This will create a spritesheet with four animation states (idle, cast, fly, and land) and 8 frames per state.

## Changing Art Style and Size

You can adjust the art style and size of the generated spritesheet:

```javascript
const options = {
  style: 'hand-drawn',
  size: '2048x2048'
};

const result = await generateCharacterSpritesheet('a steampunk robot with gears and steam pipes', options);
```

This will generate a larger, hand-drawn style spritesheet of a steampunk robot character.

## Saving the Generated Spritesheet

To save the generated spritesheet to your local filesystem, set the `save` option to `true`:

```javascript
const options = {
  save: true
};

const result = await generateCharacterSpritesheet('a space marine in futuristic armor', options);
```

The spritesheet will be saved in the `assets` folder of your project with a filename based on the description.

## Advanced Usage: Combining Options

You can combine multiple options to create highly customized spritesheets:

```javascript
const options = {
  states: ['idle', 'attack', 'defend', 'die'],
  framesPerState: 10,
  size: '2048x2048',
  style: 'pixel-art',
  padding: 2,
  direction: 'left',
  save: true
};

const result = await generateCharacterSpritesheet('a medieval knight with shining armor and a longsword', options);
```

This will generate a large pixel-art spritesheet of a knight character facing left, with four animation states, 10 frames per state, and increased padding between sprites. The result will also be saved to the local filesystem.

## Understanding the Result

The `generateCharacterSpritesheet` function returns an object with the following properties:

- `original`: URL of the originally generated image from DALL-E.
- `spritesheet`: Base64-encoded string of the processed spritesheet image.
- `metadata`: An object containing detailed information about the generated spritesheet, including:
  - `states`: Array of animation states.
  - `framesPerState`: Number of frames per state.
  - `totalFrames`: Total number of frames in the spritesheet.
  - `dimensions`: Width and height of the spritesheet.
  - `frameData`: Detailed information about each animation state, including row, number of frames, start frame, and end frame.

You can use this information to integrate the generated spritesheet into your game or application.

## Conclusion

The `generateCharacterSpritesheet` function provides a flexible and powerful way to create custom character spritesheets for your projects. By adjusting the description and options, you can generate a wide variety of characters and animations to suit your needs.

Remember to experiment with different descriptions, animation states, and styles to get the best results for your specific use case. Happy sprite generating!