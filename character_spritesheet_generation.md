# Character Spritesheet Generation

This guide explains how to generate character spritesheets using SpriteAI's `generateCharacterSpritesheet` function. You'll learn about available options, see examples of different configurations, and get tips for achieving the best results.

## Table of Contents

1. [Function Overview](#function-overview)
2. [Parameters](#parameters)
3. [Options](#options)
4. [Usage Examples](#usage-examples)
5. [Tips for Best Results](#tips-for-best-results)
6. [Return Value](#return-value)

## Function Overview

The `generateCharacterSpritesheet` function creates a character spritesheet based on a provided description. It uses AI to generate pixel art animations for various states like idle, walking, running, and attacking.

```javascript
const result = await generateCharacterSpritesheet(description, options);
```

## Parameters

- `description` (string): A detailed description of the character you want to generate.
- `options` (object): An optional object to customize the spritesheet generation.

## Options

The `options` object can include the following properties:

- `states` (array of strings): Animation states to generate. Default: `['idle', 'walk', 'run', 'attack']`
- `framesPerState` (number): Number of frames per animation state. Default: `6`
- `size` (string): Output size of the spritesheet. Default: `'1024x1024'`
- `style` (string): Art style for the character. Default: `'pixel-art'`
- `padding` (number): Padding between sprites. Default: `1`
- `direction` (string): Base direction the character faces. Default: `'right'`
- `save` (boolean): Whether to save the generated image to disk. Default: `false`

## Usage Examples

### Basic Usage

Generate a default character spritesheet:

```javascript
const result = await generateCharacterSpritesheet('A cute cat wizard with a pointy hat and magic wand');
```

### Custom Configuration

Generate a spritesheet with custom options:

```javascript
const result = await generateCharacterSpritesheet('A fierce orc warrior with an axe', {
  states: ['idle', 'walk', 'attack', 'death'],
  framesPerState: 8,
  size: '2048x2048',
  style: 'pixel-art',
  direction: 'left',
  save: true
});
```

### Minimal States

Generate a spritesheet with only idle and walk animations:

```javascript
const result = await generateCharacterSpritesheet('A sneaky rogue with dual daggers', {
  states: ['idle', 'walk'],
  framesPerState: 4
});
```

## Tips for Best Results

1. **Detailed Descriptions**: Provide clear and detailed character descriptions for better results. Include information about appearance, clothing, weapons, and unique features.

2. **Consistent Style**: When generating multiple characters for the same game, use the same `style` option to maintain consistency.

3. **Frame Count**: Adjust `framesPerState` based on the complexity of animations. More frames can result in smoother animations but larger file sizes.

4. **Size Consideration**: Choose an appropriate `size` based on your game's resolution and required detail level. Larger sizes provide more detail but increase processing time and file size.

5. **State Selection**: Only include necessary animation states to keep the spritesheet focused and reduce generation time.

6. **Direction**: Use the `direction` option to ensure characters face the correct way for your game's default orientation.

7. **Saving Files**: Enable the `save` option to automatically save the generated spritesheet to your project's `assets` folder.

## Return Value

The function returns an object with the following properties:

- `original` (string): URL of the original generated image.
- `spritesheet` (string): Base64-encoded PNG data of the processed spritesheet.
- `metadata` (object): Contains information about the generated spritesheet:
  - `states` (array): List of animation states.
  - `framesPerState` (number): Number of frames per state.
  - `totalFrames` (number): Total number of frames in the spritesheet.
  - `dimensions` (object): Width and height of the spritesheet.
  - `frameData` (object): Detailed information about each animation state, including row, frame count, and frame indices.

Example of accessing the generated spritesheet:

```javascript
const result = await generateCharacterSpritesheet('A robot with glowing eyes');
const spritesheetImage = new Image();
spritesheetImage.src = result.spritesheet;
// Use spritesheetImage in your game engine or rendering code
```

By following this guide, you should now be able to generate custom character spritesheets using SpriteAI's `generateCharacterSpritesheet` function. Experiment with different options and descriptions to create unique characters for your game projects.