<response>

# Character Spritesheet Generation Guide

This guide explains how to use the `generateCharacterSpritesheet` function to create custom character spritesheets for your game or application. The function leverages AI-powered image generation to produce high-quality, customizable character animations.

## Table of Contents

1. [Function Overview](#function-overview)
2. [Basic Usage](#basic-usage)
3. [Customization Options](#customization-options)
4. [Animation States](#animation-states)
5. [Best Practices](#best-practices)
6. [Examples](#examples)

## Function Overview

The `generateCharacterSpritesheet` function creates a character spritesheet based on a provided description and optional customization parameters. It uses the DALL-E 3 AI model to generate the initial image and then processes it into a structured spritesheet.

## Basic Usage

To generate a basic character spritesheet, you can call the function with just a description:

```javascript
import { generateCharacterSpritesheet } from 'spriteAI';

const result = await generateCharacterSpritesheet('a medieval knight in armor');
```

This will generate a spritesheet with default animation states and options.

## Customization Options

The function accepts an options object as its second parameter, allowing you to customize various aspects of the spritesheet generation:

```javascript
const options = {
  states: ['idle', 'walk', 'run', 'attack'],
  framesPerState: 6,
  size: '1024x1024',
  style: 'pixel-art',
  padding: 1,
  direction: 'right',
  save: false
};

const result = await generateCharacterSpritesheet('a sci-fi robot', options);
```

Here's a breakdown of the available options:

- `states`: An array of animation states to generate (default: `['idle', 'walk', 'run', 'attack']`)
- `framesPerState`: Number of frames for each animation state (default: `6`)
- `size`: Output image size (default: `'1024x1024'`)
- `style`: Art style of the character (default: `'pixel-art'`)
- `padding`: Padding between individual sprites (default: `1`)
- `direction`: Base direction the character faces (default: `'right'`)
- `save`: Whether to save the generated spritesheet to disk (default: `false`)

## Animation States

You can customize the animation states for your character by modifying the `states` array in the options. The function will generate a row of frames for each specified state. Common animation states include:

- `idle`: Character's resting pose
- `walk`: Walking animation
- `run`: Running or sprinting animation
- `attack`: Basic attack or action animation
- `jump`: Jumping or leaping animation
- `fall`: Falling or descending animation
- `hurt`: Character reacting to damage
- `die`: Death or defeat animation

Example of custom states:

```javascript
const options = {
  states: ['idle', 'walk', 'jump', 'attack', 'die'],
  framesPerState: 8
};

const result = await generateCharacterSpritesheet('a ninja character', options);
```

## Best Practices

1. **Be specific in your descriptions**: Provide clear and detailed descriptions of your character to get the best results.
2. **Consistent style**: Keep the art style consistent across different characters in your game or application.
3. **Frame count**: Choose an appropriate number of frames per state based on the complexity of the animation and your performance requirements.
4. **Test different options**: Experiment with different combinations of options to find the best result for your needs.
5. **Post-processing**: Consider additional post-processing or touch-ups on the generated spritesheet for fine-tuning.

## Examples

### Fantasy Character

```javascript
const fantasyOptions = {
  states: ['idle', 'walk', 'cast', 'attack'],
  framesPerState: 6,
  style: 'pixel-art',
  direction: 'right'
};

const wizardSprite = await generateCharacterSpritesheet('a wise old wizard with a long beard and pointy hat', fantasyOptions);
```

### Sci-Fi Character

```javascript
const scifiOptions = {
  states: ['idle', 'run', 'shoot', 'dodge'],
  framesPerState: 8,
  style: 'vector',
  size: '2048x2048'
};

const androidSprite = await generateCharacterSpritesheet('a sleek android with glowing eyes and smooth metallic skin', scifiOptions);
```

### Cartoon Character

```javascript
const cartoonOptions = {
  states: ['idle', 'walk', 'jump', 'wave'],
  framesPerState: 10,
  style: 'hand-drawn',
  direction: 'left'
};

const mascotSprite = await generateCharacterSpritesheet('a cute and friendly animal mascot with big eyes and a cheerful expression', cartoonOptions);
```

By following this guide and experimenting with different options, you can create diverse and engaging character spritesheets for your projects using the `generateCharacterSpritesheet` function.

</response># Character Spritesheet Generation Guide

This guide explains how to use the `generateCharacterSpritesheet` function to create custom character spritesheets for your game or application. The function leverages AI-powered image generation to produce high-quality, customizable character animations.

## Table of Contents

1. [Function Overview](#function-overview)
2. [Basic Usage](#basic-usage)
3. [Customization Options](#customization-options)
4. [Animation States](#animation-states)
5. [Best Practices](#best-practices)
6. [Examples](#examples)

## Function Overview

The `generateCharacterSpritesheet` function creates a character spritesheet based on a provided description and optional customization parameters. It uses the DALL-E 3 AI model to generate the initial image and then processes it into a structured spritesheet.

## Basic Usage

To generate a basic character spritesheet, you can call the function with just a description:

```javascript
import { generateCharacterSpritesheet } from 'spriteAI';

const result = await generateCharacterSpritesheet('a medieval knight in armor');
```

This will generate a spritesheet with default animation states and options.

## Customization Options

The function accepts an options object as its second parameter, allowing you to customize various aspects of the spritesheet generation:

```javascript
const options = {
  states: ['idle', 'walk', 'run', 'attack'],
  framesPerState: 6,
  size: '1024x1024',
  style: 'pixel-art',
  padding: 1,
  direction: 'right',
  save: false
};

const result = await generateCharacterSpritesheet('a sci-fi robot', options);
```

Here's a breakdown of the available options:

- `states`: An array of animation states to generate (default: `['idle', 'walk', 'run', 'attack']`)
- `framesPerState`: Number of frames for each animation state (default: `6`)
- `size`: Output image size (default: `'1024x1024'`)
- `style`: Art style of the character (default: `'pixel-art'`)
- `padding`: Padding between individual sprites (default: `1`)
- `direction`: Base direction the character faces (default: `'right'`)
- `save`: Whether to save the generated spritesheet to disk (default: `false`)

## Animation States

You can customize the animation states for your character by modifying the `states` array in the options. The function will generate a row of frames for each specified state. Common animation states include:

- `idle`: Character's resting pose
- `walk`: Walking animation
- `run`: Running or sprinting animation
- `attack`: Basic attack or action animation
- `jump`: Jumping or leaping animation
- `fall`: Falling or descending animation
- `hurt`: Character reacting to damage
- `die`: Death or defeat animation

Example of custom states:

```javascript
const options = {
  states: ['idle', 'walk', 'jump', 'attack', 'die'],
  framesPerState: 8
};

const result = await generateCharacterSpritesheet('a ninja character', options);
```

## Best Practices

1. **Be specific in your descriptions**: Provide clear and detailed descriptions of your character to get the best results.
2. **Consistent style**: Keep the art style consistent across different characters in your game or application.
3. **Frame count**: Choose an appropriate number of frames per state based on the complexity of the animation and your performance requirements.
4. **Test different options**: Experiment with different combinations of options to find the best result for your needs.
5. **Post-processing**: Consider additional post-processing or touch-ups on the generated spritesheet for fine-tuning.

## Examples

### Fantasy Character

```javascript
const fantasyOptions = {
  states: ['idle', 'walk', 'cast', 'attack'],
  framesPerState: 6,
  style: 'pixel-art',
  direction: 'right'
};

const wizardSprite = await generateCharacterSpritesheet('a wise old wizard with a long beard and pointy hat', fantasyOptions);
```

### Sci-Fi Character

```javascript
const scifiOptions = {
  states: ['idle', 'run', 'shoot', 'dodge'],
  framesPerState: 8,
  style: 'vector',
  size: '2048x2048'
};

const androidSprite = await generateCharacterSpritesheet('a sleek android with glowing eyes and smooth metallic skin', scifiOptions);
```

### Cartoon Character

```javascript
const cartoonOptions = {
  states: ['idle', 'walk', 'jump', 'wave'],
  framesPerState: 10,
  style: 'hand-drawn',
  direction: 'left'
};

const mascotSprite = await generateCharacterSpritesheet('a cute and friendly animal mascot with big eyes and a cheerful expression', cartoonOptions);
```

By following this guide and experimenting with different options, you can create diverse and engaging character spritesheets for your projects using the `generateCharacterSpritesheet` function.