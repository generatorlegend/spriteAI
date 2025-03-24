<response>

# Character Spritesheet Generation

This guide explains how to use the SpriteAI library to generate character spritesheets for your game development projects. The `generateCharacterSpritesheet` function allows you to create customized spritesheets with various animation states, styles, and options.

## Table of Contents

1. [Function Overview](#function-overview)
2. [Parameters](#parameters)
3. [Options](#options)
4. [Return Value](#return-value)
5. [Usage Examples](#usage-examples)
6. [Tips for Best Results](#tips-for-best-results)
7. [Advanced Customization](#advanced-customization)

## Function Overview

The `generateCharacterSpritesheet` function uses AI-powered image generation to create a spritesheet based on your character description and specified options. It supports multiple animation states and allows for customization of various aspects of the spritesheet.

```javascript
async function generateCharacterSpritesheet(description, options = {})
```

## Parameters

- `description` (string): A detailed description of the character you want to generate.
- `options` (object): An optional object containing customization parameters.

## Options

The `options` object can include the following properties:

- `states` (array of strings): Animation states to generate. Default: `['idle', 'walk', 'run', 'attack']`
- `framesPerState` (number): Number of frames per animation state. Default: `6`
- `size` (string): Output size of the spritesheet. Default: `'1024x1024'`
- `style` (string): Art style of the character. Default: `'pixel-art'`
- `padding` (number): Padding between sprites. Default: `1`
- `direction` (string): Base direction of the character. Default: `'right'`
- `save` (boolean): Whether to save the generated image to the local filesystem. Default: `false`

## Return Value

The function returns an object with the following properties:

- `original` (string): URL of the original generated image.
- `spritesheet` (string): Base64-encoded PNG data of the processed spritesheet.
- `metadata` (object): Contains information about the generated spritesheet, including:
  - `states` (array): List of animation states.
  - `framesPerState` (number): Number of frames per state.
  - `totalFrames` (number): Total number of frames in the spritesheet.
  - `dimensions` (object): Width and height of the spritesheet.
  - `frameData` (object): Detailed information about each animation state's frames.

## Usage Examples

### Basic Usage

```javascript
import { generateCharacterSpritesheet } from 'spriteAI';

const result = await generateCharacterSpritesheet('A cute cat warrior with armor');
console.log(result.spritesheet); // Base64-encoded PNG data
console.log(result.metadata); // Spritesheet metadata
```

### Custom Animation States

```javascript
const result = await generateCharacterSpritesheet('A powerful wizard', {
  states: ['cast', 'fly', 'teleport', 'meditate'],
  framesPerState: 8
});
```

### Different Art Style

```javascript
const result = await generateCharacterSpritesheet('A stealthy ninja', {
  style: 'anime',
  size: '2048x2048'
});
```

### Saving the Spritesheet

```javascript
const result = await generateCharacterSpritesheet('A heroic knight', {
  save: true // This will save the spritesheet in the assets folder
});
```

## Tips for Best Results

1. **Be Specific**: Provide detailed descriptions of your character, including their appearance, clothing, and any notable features.

2. **Consider Art Style**: The default 'pixel-art' style works well for retro-style games, but you can experiment with other styles like 'vector' or 'hand-drawn' for different visual effects.

3. **Adjust Frames**: Increase `framesPerState` for smoother animations, but be mindful of the total spritesheet size.

4. **Test Different Sizes**: While the default size is 1024x1024, you can try larger sizes for more detailed sprites or smaller sizes for performance optimization.

5. **Consistent Character**: To maintain consistency across different spritesheets of the same character, include key identifying features in your description each time.

## Advanced Customization

### Custom Animation Sequence

You can create a custom animation sequence by specifying the exact order of states:

```javascript
const result = await generateCharacterSpritesheet('A transforming robot', {
  states: ['idle', 'transform_start', 'transform_mid', 'transform_end', 'attack'],
  framesPerState: 10
});
```

### Directional Characters

For games requiring characters facing different directions, you can generate multiple spritesheets:

```javascript
const directions = ['left', 'right', 'up', 'down'];
const spritesheets = await Promise.all(directions.map(direction => 
  generateCharacterSpritesheet('A versatile adventurer', { direction })
));
```

### Combining with Background Removal

If you need characters with transparent backgrounds, you can use the `removeBackgroundColor` function after generating the spritesheet:

```javascript
import { removeBackgroundColor } from 'spriteAI';

const result = await generateCharacterSpritesheet('A ghost character');
const transparentSpritesheet = await removeBackgroundColor(
  result.spritesheet,
  'output_transparent.png',
  '#FFFFFF', // Assuming white background
  0.1 // Color threshold
);
```

By leveraging these techniques and the flexibility of the `generateCharacterSpritesheet` function, you can create a wide variety of character spritesheets tailored to your game's specific needs.

</response># Character Spritesheet Generation

This guide explains how to use the SpriteAI library to generate character spritesheets for your game development projects. The `generateCharacterSpritesheet` function allows you to create customized spritesheets with various animation states, styles, and options.

## Table of Contents

1. [Function Overview](#function-overview)
2. [Parameters](#parameters)
3. [Options](#options)
4. [Return Value](#return-value)
5. [Usage Examples](#usage-examples)
6. [Tips for Best Results](#tips-for-best-results)
7. [Advanced Customization](#advanced-customization)

## Function Overview

The `generateCharacterSpritesheet` function uses AI-powered image generation to create a spritesheet based on your character description and specified options. It supports multiple animation states and allows for customization of various aspects of the spritesheet.

```javascript
async function generateCharacterSpritesheet(description, options = {})
```

## Parameters

- `description` (string): A detailed description of the character you want to generate.
- `options` (object): An optional object containing customization parameters.

## Options

The `options` object can include the following properties:

- `states` (array of strings): Animation states to generate. Default: `['idle', 'walk', 'run', 'attack']`
- `framesPerState` (number): Number of frames per animation state. Default: `6`
- `size` (string): Output size of the spritesheet. Default: `'1024x1024'`
- `style` (string): Art style of the character. Default: `'pixel-art'`
- `padding` (number): Padding between sprites. Default: `1`
- `direction` (string): Base direction of the character. Default: `'right'`
- `save` (boolean): Whether to save the generated image to the local filesystem. Default: `false`

## Return Value

The function returns an object with the following properties:

- `original` (string): URL of the original generated image.
- `spritesheet` (string): Base64-encoded PNG data of the processed spritesheet.
- `metadata` (object): Contains information about the generated spritesheet, including:
  - `states` (array): List of animation states.
  - `framesPerState` (number): Number of frames per state.
  - `totalFrames` (number): Total number of frames in the spritesheet.
  - `dimensions` (object): Width and height of the spritesheet.
  - `frameData` (object): Detailed information about each animation state's frames.

## Usage Examples

### Basic Usage

```javascript
import { generateCharacterSpritesheet } from 'spriteAI';

const result = await generateCharacterSpritesheet('A cute cat warrior with armor');
console.log(result.spritesheet); // Base64-encoded PNG data
console.log(result.metadata); // Spritesheet metadata
```

### Custom Animation States

```javascript
const result = await generateCharacterSpritesheet('A powerful wizard', {
  states: ['cast', 'fly', 'teleport', 'meditate'],
  framesPerState: 8
});
```

### Different Art Style

```javascript
const result = await generateCharacterSpritesheet('A stealthy ninja', {
  style: 'anime',
  size: '2048x2048'
});
```

### Saving the Spritesheet

```javascript
const result = await generateCharacterSpritesheet('A heroic knight', {
  save: true // This will save the spritesheet in the assets folder
});
```

## Tips for Best Results

1. **Be Specific**: Provide detailed descriptions of your character, including their appearance, clothing, and any notable features.

2. **Consider Art Style**: The default 'pixel-art' style works well for retro-style games, but you can experiment with other styles like 'vector' or 'hand-drawn' for different visual effects.

3. **Adjust Frames**: Increase `framesPerState` for smoother animations, but be mindful of the total spritesheet size.

4. **Test Different Sizes**: While the default size is 1024x1024, you can try larger sizes for more detailed sprites or smaller sizes for performance optimization.

5. **Consistent Character**: To maintain consistency across different spritesheets of the same character, include key identifying features in your description each time.

## Advanced Customization

### Custom Animation Sequence

You can create a custom animation sequence by specifying the exact order of states:

```javascript
const result = await generateCharacterSpritesheet('A transforming robot', {
  states: ['idle', 'transform_start', 'transform_mid', 'transform_end', 'attack'],
  framesPerState: 10
});
```

### Directional Characters

For games requiring characters facing different directions, you can generate multiple spritesheets:

```javascript
const directions = ['left', 'right', 'up', 'down'];
const spritesheets = await Promise.all(directions.map(direction => 
  generateCharacterSpritesheet('A versatile adventurer', { direction })
));
```

### Combining with Background Removal

If you need characters with transparent backgrounds, you can use the `removeBackgroundColor` function after generating the spritesheet:

```javascript
import { removeBackgroundColor } from 'spriteAI';

const result = await generateCharacterSpritesheet('A ghost character');
const transparentSpritesheet = await removeBackgroundColor(
  result.spritesheet,
  'output_transparent.png',
  '#FFFFFF', // Assuming white background
  0.1 // Color threshold
);
```

By leveraging these techniques and the flexibility of the `generateCharacterSpritesheet` function, you can create a wide variety of character spritesheets tailored to your game's specific needs.