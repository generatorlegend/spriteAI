---
title: Character Spritesheet Guide
description: Learn how to create character spritesheets using SpriteAI
---

# Character Spritesheet Guide

This guide will walk you through the process of creating character spritesheets using SpriteAI. You'll learn about spritesheets, available animation states, customization options, and best practices for generating high-quality character sprites.

## Table of Contents

1. [Introduction to Spritesheets](#introduction-to-spritesheets)
2. [Using SpriteAI for Character Spritesheets](#using-spriteai-for-character-spritesheets)
3. [Available Animation States](#available-animation-states)
4. [Customization Options](#customization-options)
5. [Best Practices](#best-practices)
6. [Examples](#examples)

## Introduction to Spritesheets

A spritesheet is a collection of images arranged in a grid format, typically used in game development to efficiently manage and render character animations. Each row in a spritesheet usually represents a different animation state, with individual frames of that animation laid out horizontally.

## Using SpriteAI for Character Spritesheets

SpriteAI provides a powerful function called `generateCharacterSpritesheet` to create custom character spritesheets. Here's how to use it:

```javascript
import { generateCharacterSpritesheet } from 'spriteAI';

const characterDescription = "a brave knight in shining armor";
const options = {
  states: ['idle', 'walk', 'run', 'attack'],
  framesPerState: 6,
  size: '1024x1024',
  style: 'pixel-art',
  direction: 'right'
};

const result = await generateCharacterSpritesheet(characterDescription, options);
```

This function generates a spritesheet based on your description and options, returning an object with the original image URL, the spritesheet data, and metadata about the generated sprites.

## Available Animation States

SpriteAI supports various animation states for your characters. You can fetch the available states using the `fetchAvailableAnimationStates` function:

```javascript
import { fetchAvailableAnimationStates } from 'spriteAI';

const states = await fetchAvailableAnimationStates();
console.log(states);
// Output: ['idle', 'walk', 'run', 'attack', 'jump', 'fall', 'hurt', 'die']
```

By default, the `generateCharacterSpritesheet` function uses 'idle', 'walk', 'run', and 'attack' states, but you can customize this in the options.

## Customization Options

When generating a character spritesheet, you can customize various aspects:

- `states`: An array of animation states to include (default: ['idle', 'walk', 'run', 'attack'])
- `framesPerState`: Number of frames for each animation state (default: 6)
- `size`: Output size of the spritesheet (default: '1024x1024')
- `style`: Art style of the character (default: 'pixel-art')
- `padding`: Padding between sprites (default: 1)
- `direction`: Base direction the character faces (default: 'right')

You can also specify whether to save the generated spritesheet by setting `save: true` in the options.

## Best Practices

1. **Consistent Character Size**: Ensure your character description maintains a consistent size across all frames for smooth animations.

2. **Clear Descriptions**: Provide clear and detailed character descriptions to get the best results from the AI.

3. **Appropriate Frame Count**: Choose an appropriate number of frames per state. More frames can lead to smoother animations but larger file sizes.

4. **Style Consistency**: Stick to a consistent art style throughout your game for a cohesive look.

5. **Test Different Options**: Experiment with different styles, sizes, and animation states to find what works best for your game.

6. **Optimize Performance**: Balance between quality and performance by choosing appropriate spritesheet sizes and frame counts.

## Examples

Here are a few examples of different character types and styles you can create:

1. Pixel Art Warrior:
```javascript
const warriorSprite = await generateCharacterSpritesheet("a fierce warrior with a large sword", {
  style: 'pixel-art',
  states: ['idle', 'walk', 'attack', 'defend']
});
```

2. Vector Art Wizard:
```javascript
const wizardSprite = await generateCharacterSpritesheet("a wise old wizard with a long beard", {
  style: 'vector',
  states: ['idle', 'cast', 'teleport', 'die'],
  size: '2048x2048'
});
```

3. 3D Style Robot:
```javascript
const robotSprite = await generateCharacterSpritesheet("a futuristic robot with glowing parts", {
  style: '3d',
  states: ['idle', 'walk', 'run', 'attack', 'power-up'],
  framesPerState: 8
});
```

Remember to handle the returned spritesheet data and metadata appropriately in your game engine or rendering system.

By following this guide, you should now be able to create diverse and high-quality character spritesheets using SpriteAI for your game development projects.