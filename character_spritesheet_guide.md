<response>

# Character Spritesheet Guide

## Introduction

This guide will walk you through the process of generating character spritesheets using SpriteAI. You'll learn how to create dynamic, customizable character animations for your game or project.

## Table of Contents

1. [Basic Usage](#basic-usage)
2. [Understanding Animation States](#understanding-animation-states)
3. [Customizing Your Spritesheet](#customizing-your-spritesheet)
4. [Examples](#examples)
5. [Advanced Options](#advanced-options)

## Basic Usage

To generate a character spritesheet, use the `generateCharacterSpritesheet` function:

```javascript
import { generateCharacterSpritesheet } from 'spriteAI';

const result = await generateCharacterSpritesheet('a warrior with armor and sword');
```

This will create a default spritesheet with basic animation states.

## Understanding Animation States

Animation states represent different actions your character can perform. By default, SpriteAI generates the following states:

- Idle
- Walk
- Run
- Attack

Each state is represented by a row in the spritesheet, containing multiple frames to create smooth animations.

To check available animation states:

```javascript
import { fetchAvailableAnimationStates } from 'spriteAI';

const states = await fetchAvailableAnimationStates();
console.log(states); // ['idle', 'walk', 'run', 'attack', 'jump', 'fall', 'hurt', 'die']
```

## Customizing Your Spritesheet

You can customize various aspects of your spritesheet:

```javascript
const options = {
  states: ['idle', 'walk', 'attack', 'die'],
  framesPerState: 8,
  size: '2048x2048',
  style: 'pixel-art',
  direction: 'left'
};

const result = await generateCharacterSpritesheet('a mage with staff and robes', options);
```

### Options Explained:

- `states`: Array of animation states to include
- `framesPerState`: Number of frames for each animation (default: 6)
- `size`: Output image size (default: '1024x1024')
- `style`: Art style (default: 'pixel-art')
- `direction`: Base direction of the character (default: 'right')

## Examples

### Fantasy Warrior

```javascript
const warriorResult = await generateCharacterSpritesheet('a heavily armored knight with a large sword', {
  states: ['idle', 'walk', 'attack', 'block'],
  style: 'pixel-art'
});
```

### Sci-Fi Robot

```javascript
const robotResult = await generateCharacterSpritesheet('a sleek, futuristic robot with glowing parts', {
  states: ['idle', 'walk', 'run', 'attack', 'fly'],
  style: 'vector',
  size: '2048x2048'
});
```

## Advanced Options

### Saving the Spritesheet

To save the generated spritesheet:

```javascript
const result = await generateCharacterSpritesheet('an elf archer', {
  save: true
});
```

This will save the spritesheet in the `assets` folder of your current working directory.

### Accessing Metadata

The `generateCharacterSpritesheet` function returns valuable metadata:

```javascript
const { metadata } = await generateCharacterSpritesheet('a ninja character');

console.log(metadata.totalFrames);
console.log(metadata.dimensions);
console.log(metadata.frameData);
```

Use this metadata to correctly implement your character animations in your game engine.

### Changing Art Styles

SpriteAI supports various art styles:

```javascript
import { fetchAvailableSpriteStyles } from 'spriteAI';

const styles = await fetchAvailableSpriteStyles();
console.log(styles); // ['pixel-art', 'vector', '3d', 'hand-drawn', 'anime']

const animeCharacter = await generateCharacterSpritesheet('a magical girl', { style: 'anime' });
```

## Conclusion

With SpriteAI, you can quickly generate custom character spritesheets for your game development needs. Experiment with different descriptions, states, and styles to create unique and engaging characters for your projects.

</response># Character Spritesheet Guide

## Introduction

This guide will walk you through the process of generating character spritesheets using SpriteAI. You'll learn how to create dynamic, customizable character animations for your game or project.

## Table of Contents

1. [Basic Usage](#basic-usage)
2. [Understanding Animation States](#understanding-animation-states)
3. [Customizing Your Spritesheet](#customizing-your-spritesheet)
4. [Examples](#examples)
5. [Advanced Options](#advanced-options)

## Basic Usage

To generate a character spritesheet, use the `generateCharacterSpritesheet` function:

```javascript
import { generateCharacterSpritesheet } from 'spriteAI';

const result = await generateCharacterSpritesheet('a warrior with armor and sword');
```

This will create a default spritesheet with basic animation states.

## Understanding Animation States

Animation states represent different actions your character can perform. By default, SpriteAI generates the following states:

- Idle
- Walk
- Run
- Attack

Each state is represented by a row in the spritesheet, containing multiple frames to create smooth animations.

To check available animation states:

```javascript
import { fetchAvailableAnimationStates } from 'spriteAI';

const states = await fetchAvailableAnimationStates();
console.log(states); // ['idle', 'walk', 'run', 'attack', 'jump', 'fall', 'hurt', 'die']
```

## Customizing Your Spritesheet

You can customize various aspects of your spritesheet:

```javascript
const options = {
  states: ['idle', 'walk', 'attack', 'die'],
  framesPerState: 8,
  size: '2048x2048',
  style: 'pixel-art',
  direction: 'left'
};

const result = await generateCharacterSpritesheet('a mage with staff and robes', options);
```

### Options Explained:

- `states`: Array of animation states to include
- `framesPerState`: Number of frames for each animation (default: 6)
- `size`: Output image size (default: '1024x1024')
- `style`: Art style (default: 'pixel-art')
- `direction`: Base direction of the character (default: 'right')

## Examples

### Fantasy Warrior

```javascript
const warriorResult = await generateCharacterSpritesheet('a heavily armored knight with a large sword', {
  states: ['idle', 'walk', 'attack', 'block'],
  style: 'pixel-art'
});
```

### Sci-Fi Robot

```javascript
const robotResult = await generateCharacterSpritesheet('a sleek, futuristic robot with glowing parts', {
  states: ['idle', 'walk', 'run', 'attack', 'fly'],
  style: 'vector',
  size: '2048x2048'
});
```

## Advanced Options

### Saving the Spritesheet

To save the generated spritesheet:

```javascript
const result = await generateCharacterSpritesheet('an elf archer', {
  save: true
});
```

This will save the spritesheet in the `assets` folder of your current working directory.

### Accessing Metadata

The `generateCharacterSpritesheet` function returns valuable metadata:

```javascript
const { metadata } = await generateCharacterSpritesheet('a ninja character');

console.log(metadata.totalFrames);
console.log(metadata.dimensions);
console.log(metadata.frameData);
```

Use this metadata to correctly implement your character animations in your game engine.

### Changing Art Styles

SpriteAI supports various art styles:

```javascript
import { fetchAvailableSpriteStyles } from 'spriteAI';

const styles = await fetchAvailableSpriteStyles();
console.log(styles); // ['pixel-art', 'vector', '3d', 'hand-drawn', 'anime']

const animeCharacter = await generateCharacterSpritesheet('a magical girl', { style: 'anime' });
```

## Conclusion

With SpriteAI, you can quickly generate custom character spritesheets for your game development needs. Experiment with different descriptions, states, and styles to create unique and engaging characters for your projects.