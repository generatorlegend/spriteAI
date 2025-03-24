<response>

# Character Spritesheet Generation

This guide explains how to generate character spritesheets using SpriteAI's `generateCharacterSpritesheet` function. This powerful tool allows you to create detailed spritesheets for game characters with various animation states.

## Overview

The `generateCharacterSpritesheet` function uses AI to generate a spritesheet based on a character description and specified options. It creates a single image containing multiple frames for different animation states.

## Function Signature

```javascript
async function generateCharacterSpritesheet(description, options = {})
```

### Parameters

- `description` (string): A detailed description of the character you want to generate.
- `options` (object): Optional parameters to customize the spritesheet generation.

### Options

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `states` | array | `['idle', 'walk', 'run', 'attack']` | Animation states to generate |
| `framesPerState` | number | 6 | Number of frames per animation state |
| `size` | string | '1024x1024' | Output size of the spritesheet |
| `style` | string | 'pixel-art' | Art style of the character |
| `padding` | number | 1 | Padding between sprites |
| `direction` | string | 'right' | Base direction of the character |
| `save` | boolean | false | Whether to save the generated image locally |

## Usage

Here's a basic example of how to use the `generateCharacterSpritesheet` function:

```javascript
import { generateCharacterSpritesheet } from 'spriteAI';

const result = await generateCharacterSpritesheet('A cute cat wizard with a pointy hat and a magic wand', {
  states: ['idle', 'cast', 'walk'],
  framesPerState: 4,
  style: 'pixel-art',
  size: '512x512'
});

console.log(result.spritesheet); // Base64 encoded spritesheet image
console.log(result.metadata); // Metadata about the generated spritesheet
```

## Customizing Output

### Animation States

You can customize the animation states by providing an array of state names in the `states` option. For example:

```javascript
const result = await generateCharacterSpritesheet('A muscular barbarian warrior', {
  states: ['idle', 'attack', 'defend', 'die'],
  framesPerState: 8
});
```

### Art Styles

The `style` option allows you to specify different art styles. While 'pixel-art' is the default, you can experiment with other styles:

```javascript
const result = await generateCharacterSpritesheet('A sleek, futuristic robot', {
  style: 'vector',
  size: '2048x2048'
});
```

### Saving Files

To save the generated spritesheet locally, use the `save` option:

```javascript
const result = await generateCharacterSpritesheet('A mischievous goblin thief', {
  save: true
});
```

This will save the file in the `assets` directory of your project.

## Return Value

The function returns an object with the following properties:

- `original`: URL of the original generated image.
- `spritesheet`: Base64 encoded string of the processed spritesheet.
- `metadata`: An object containing detailed information about the spritesheet, including:
  - `states`: Array of animation states.
  - `framesPerState`: Number of frames per state.
  - `totalFrames`: Total number of frames in the spritesheet.
  - `dimensions`: Width and height of the spritesheet.
  - `frameData`: Detailed information about each animation state's position in the spritesheet.

## Examples

### Fantasy Character

```javascript
const elfArcher = await generateCharacterSpritesheet('An elegant elven archer with long blonde hair and green clothing', {
  states: ['idle', 'aim', 'shoot', 'run'],
  framesPerState: 6,
  style: 'pixel-art',
  direction: 'right'
});
```

### Sci-Fi Character

```javascript
const spaceMarineConfig = {
  states: ['idle', 'shoot', 'reload', 'melee', 'die'],
  framesPerState: 8,
  style: 'vector',
  size: '2048x2048',
  direction: 'left'
};

const spaceMarine = await generateCharacterSpritesheet('A heavily armored space marine with a large plasma rifle', spaceMarineConfig);
```

## Tips for Best Results

1. Be specific in your character descriptions.
2. Experiment with different art styles and sizes to find what works best for your game.
3. Consider the number of frames per state based on the complexity of the animation.
4. Use consistent naming conventions for your animation states.
5. Remember that larger spritesheets may take longer to generate and process.

By leveraging the `generateCharacterSpritesheet` function, you can quickly create diverse and detailed character spritesheets for your game development needs.

</response># Character Spritesheet Generation

This guide explains how to generate character spritesheets using SpriteAI's `generateCharacterSpritesheet` function. This powerful tool allows you to create detailed spritesheets for game characters with various animation states.

## Overview

The `generateCharacterSpritesheet` function uses AI to generate a spritesheet based on a character description and specified options. It creates a single image containing multiple frames for different animation states.

## Function Signature

```javascript
async function generateCharacterSpritesheet(description, options = {})
```

### Parameters

- `description` (string): A detailed description of the character you want to generate.
- `options` (object): Optional parameters to customize the spritesheet generation.

### Options

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `states` | array | `['idle', 'walk', 'run', 'attack']` | Animation states to generate |
| `framesPerState` | number | 6 | Number of frames per animation state |
| `size` | string | '1024x1024' | Output size of the spritesheet |
| `style` | string | 'pixel-art' | Art style of the character |
| `padding` | number | 1 | Padding between sprites |
| `direction` | string | 'right' | Base direction of the character |
| `save` | boolean | false | Whether to save the generated image locally |

## Usage

Here's a basic example of how to use the `generateCharacterSpritesheet` function:

```javascript
import { generateCharacterSpritesheet } from 'spriteAI';

const result = await generateCharacterSpritesheet('A cute cat wizard with a pointy hat and a magic wand', {
  states: ['idle', 'cast', 'walk'],
  framesPerState: 4,
  style: 'pixel-art',
  size: '512x512'
});

console.log(result.spritesheet); // Base64 encoded spritesheet image
console.log(result.metadata); // Metadata about the generated spritesheet
```

## Customizing Output

### Animation States

You can customize the animation states by providing an array of state names in the `states` option. For example:

```javascript
const result = await generateCharacterSpritesheet('A muscular barbarian warrior', {
  states: ['idle', 'attack', 'defend', 'die'],
  framesPerState: 8
});
```

### Art Styles

The `style` option allows you to specify different art styles. While 'pixel-art' is the default, you can experiment with other styles:

```javascript
const result = await generateCharacterSpritesheet('A sleek, futuristic robot', {
  style: 'vector',
  size: '2048x2048'
});
```

### Saving Files

To save the generated spritesheet locally, use the `save` option:

```javascript
const result = await generateCharacterSpritesheet('A mischievous goblin thief', {
  save: true
});
```

This will save the file in the `assets` directory of your project.

## Return Value

The function returns an object with the following properties:

- `original`: URL of the original generated image.
- `spritesheet`: Base64 encoded string of the processed spritesheet.
- `metadata`: An object containing detailed information about the spritesheet, including:
  - `states`: Array of animation states.
  - `framesPerState`: Number of frames per state.
  - `totalFrames`: Total number of frames in the spritesheet.
  - `dimensions`: Width and height of the spritesheet.
  - `frameData`: Detailed information about each animation state's position in the spritesheet.

## Examples

### Fantasy Character

```javascript
const elfArcher = await generateCharacterSpritesheet('An elegant elven archer with long blonde hair and green clothing', {
  states: ['idle', 'aim', 'shoot', 'run'],
  framesPerState: 6,
  style: 'pixel-art',
  direction: 'right'
});
```

### Sci-Fi Character

```javascript
const spaceMarineConfig = {
  states: ['idle', 'shoot', 'reload', 'melee', 'die'],
  framesPerState: 8,
  style: 'vector',
  size: '2048x2048',
  direction: 'left'
};

const spaceMarine = await generateCharacterSpritesheet('A heavily armored space marine with a large plasma rifle', spaceMarineConfig);
```

## Tips for Best Results

1. Be specific in your character descriptions.
2. Experiment with different art styles and sizes to find what works best for your game.
3. Consider the number of frames per state based on the complexity of the animation.
4. Use consistent naming conventions for your animation states.
5. Remember that larger spritesheets may take longer to generate and process.

By leveraging the `generateCharacterSpritesheet` function, you can quickly create diverse and detailed character spritesheets for your game development needs.