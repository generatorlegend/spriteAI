<response>

# Character Spritesheet Generation Guide

This guide explains how to use SpriteAI to generate character spritesheets for your game development projects. You'll learn about available options, customizing animation states, and best practices for achieving desired results.

## Table of Contents

1. [Introduction](#introduction)
2. [Basic Usage](#basic-usage)
3. [Configuration Options](#configuration-options)
4. [Customizing Animation States](#customizing-animation-states)
5. [Character Styles](#character-styles)
6. [Best Practices](#best-practices)
7. [Examples](#examples)

## Introduction

SpriteAI's `generateCharacterSpritesheet` function allows you to create pixel art character spritesheets with various animation states. This powerful tool uses AI to generate high-quality sprites based on your descriptions and preferences.

## Basic Usage

To generate a character spritesheet, use the following code:

```javascript
import { generateCharacterSpritesheet } from 'spriteAI';

const result = await generateCharacterSpritesheet('medieval knight in armor');

console.log(result.spritesheet); // Base64 encoded PNG
console.log(result.metadata);    // Spritesheet metadata
```

This will create a default spritesheet with idle, walk, run, and attack animations for a medieval knight character.

## Configuration Options

The `generateCharacterSpritesheet` function accepts an options object to customize the output:

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

const result = await generateCharacterSpritesheet('medieval knight in armor', options);
```

| Option | Description | Default |
|--------|-------------|---------|
| `states` | Array of animation states to generate | `['idle', 'walk', 'run', 'attack']` |
| `framesPerState` | Number of frames per animation state | `6` |
| `size` | Output image size | `'1024x1024'` |
| `style` | Art style of the character | `'pixel-art'` |
| `padding` | Padding between sprites | `1` |
| `direction` | Base direction of the character | `'right'` |
| `save` | Whether to save the generated image to disk | `false` |

## Customizing Animation States

You can customize the animation states by modifying the `states` array in the options:

```javascript
const options = {
  states: ['idle', 'walk', 'run', 'attack', 'jump', 'fall'],
  framesPerState: 8
};

const result = await generateCharacterSpritesheet('ninja warrior', options);
```

This will generate a spritesheet with six animation states, each containing 8 frames.

To fetch available animation states, use the `fetchAvailableAnimationStates` function:

```javascript
import { fetchAvailableAnimationStates } from 'spriteAI';

const availableStates = await fetchAvailableAnimationStates();
console.log(availableStates);
```

## Character Styles

SpriteAI supports various character styles. To fetch available styles, use the `fetchAvailableSpriteStyles` function:

```javascript
import { fetchAvailableSpriteStyles } from 'spriteAI';

const availableStyles = await fetchAvailableSpriteStyles();
console.log(availableStyles);
```

To specify a style, use the `style` option:

```javascript
const options = {
  style: 'vector'
};

const result = await generateCharacterSpritesheet('cartoon superhero', options);
```

## Best Practices

1. **Provide clear descriptions**: Be specific about the character's appearance, theme, and style in your description.
2. **Experiment with styles**: Try different art styles to find the best fit for your game's aesthetic.
3. **Adjust frame count**: Increase `framesPerState` for smoother animations or decrease for simpler characters.
4. **Use consistent sizes**: Keep the `size` option consistent across all your character generations for uniformity.
5. **Save generated assets**: Enable the `save` option to keep your generated spritesheets on disk for future use.

## Examples

Here are some examples of generating different character types:

### Fantasy Wizard

```javascript
const wizardOptions = {
  states: ['idle', 'cast', 'walk', 'teleport'],
  style: 'pixel-art',
  framesPerState: 8
};

const wizard = await generateCharacterSpritesheet('wise old wizard with long beard and staff', wizardOptions);
```

### Sci-Fi Robot

```javascript
const robotOptions = {
  states: ['idle', 'move', 'attack', 'repair', 'shutdown'],
  style: 'vector',
  direction: 'left'
};

const robot = await generateCharacterSpritesheet('futuristic battle robot with glowing parts', robotOptions);
```

### Cute Animal

```javascript
const animalOptions = {
  states: ['idle', 'walk', 'run', 'eat', 'sleep'],
  style: 'hand-drawn',
  size: '2048x2048'
};

const animal = await generateCharacterSpritesheet('adorable panda cub', animalOptions);
```

By following this guide, you can create diverse and high-quality character spritesheets for your game projects using SpriteAI. Experiment with different options and descriptions to achieve the perfect look for your characters!

</response># Character Spritesheet Generation Guide

This guide explains how to use SpriteAI to generate character spritesheets for your game development projects. You'll learn about available options, customizing animation states, and best practices for achieving desired results.

## Table of Contents

1. [Introduction](#introduction)
2. [Basic Usage](#basic-usage)
3. [Configuration Options](#configuration-options)
4. [Customizing Animation States](#customizing-animation-states)
5. [Character Styles](#character-styles)
6. [Best Practices](#best-practices)
7. [Examples](#examples)

## Introduction

SpriteAI's `generateCharacterSpritesheet` function allows you to create pixel art character spritesheets with various animation states. This powerful tool uses AI to generate high-quality sprites based on your descriptions and preferences.

## Basic Usage

To generate a character spritesheet, use the following code:

```javascript
import { generateCharacterSpritesheet } from 'spriteAI';

const result = await generateCharacterSpritesheet('medieval knight in armor');

console.log(result.spritesheet); // Base64 encoded PNG
console.log(result.metadata);    // Spritesheet metadata
```

This will create a default spritesheet with idle, walk, run, and attack animations for a medieval knight character.

## Configuration Options

The `generateCharacterSpritesheet` function accepts an options object to customize the output:

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

const result = await generateCharacterSpritesheet('medieval knight in armor', options);
```

| Option | Description | Default |
|--------|-------------|---------|
| `states` | Array of animation states to generate | `['idle', 'walk', 'run', 'attack']` |
| `framesPerState` | Number of frames per animation state | `6` |
| `size` | Output image size | `'1024x1024'` |
| `style` | Art style of the character | `'pixel-art'` |
| `padding` | Padding between sprites | `1` |
| `direction` | Base direction of the character | `'right'` |
| `save` | Whether to save the generated image to disk | `false` |

## Customizing Animation States

You can customize the animation states by modifying the `states` array in the options:

```javascript
const options = {
  states: ['idle', 'walk', 'run', 'attack', 'jump', 'fall'],
  framesPerState: 8
};

const result = await generateCharacterSpritesheet('ninja warrior', options);
```

This will generate a spritesheet with six animation states, each containing 8 frames.

To fetch available animation states, use the `fetchAvailableAnimationStates` function:

```javascript
import { fetchAvailableAnimationStates } from 'spriteAI';

const availableStates = await fetchAvailableAnimationStates();
console.log(availableStates);
```

## Character Styles

SpriteAI supports various character styles. To fetch available styles, use the `fetchAvailableSpriteStyles` function:

```javascript
import { fetchAvailableSpriteStyles } from 'spriteAI';

const availableStyles = await fetchAvailableSpriteStyles();
console.log(availableStyles);
```

To specify a style, use the `style` option:

```javascript
const options = {
  style: 'vector'
};

const result = await generateCharacterSpritesheet('cartoon superhero', options);
```

## Best Practices

1. **Provide clear descriptions**: Be specific about the character's appearance, theme, and style in your description.
2. **Experiment with styles**: Try different art styles to find the best fit for your game's aesthetic.
3. **Adjust frame count**: Increase `framesPerState` for smoother animations or decrease for simpler characters.
4. **Use consistent sizes**: Keep the `size` option consistent across all your character generations for uniformity.
5. **Save generated assets**: Enable the `save` option to keep your generated spritesheets on disk for future use.

## Examples

Here are some examples of generating different character types:

### Fantasy Wizard

```javascript
const wizardOptions = {
  states: ['idle', 'cast', 'walk', 'teleport'],
  style: 'pixel-art',
  framesPerState: 8
};

const wizard = await generateCharacterSpritesheet('wise old wizard with long beard and staff', wizardOptions);
```

### Sci-Fi Robot

```javascript
const robotOptions = {
  states: ['idle', 'move', 'attack', 'repair', 'shutdown'],
  style: 'vector',
  direction: 'left'
};

const robot = await generateCharacterSpritesheet('futuristic battle robot with glowing parts', robotOptions);
```

### Cute Animal

```javascript
const animalOptions = {
  states: ['idle', 'walk', 'run', 'eat', 'sleep'],
  style: 'hand-drawn',
  size: '2048x2048'
};

const animal = await generateCharacterSpritesheet('adorable panda cub', animalOptions);
```

By following this guide, you can create diverse and high-quality character spritesheets for your game projects using SpriteAI. Experiment with different options and descriptions to achieve the perfect look for your characters!