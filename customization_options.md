# Customization Options in SpriteAI

This guide explains the various customization options available in SpriteAI for generating character spritesheets and environment sprites. These options allow you to tailor the output to your specific needs and achieve different visual results.

## Character Spritesheet Customization

When using the `generateCharacterSpritesheet` function, you can customize the following options:

### Animation States

- **Option**: `states`
- **Default**: `['idle', 'walk', 'run', 'attack']`
- **Description**: An array of animation states to generate for the character.

Example:
```javascript
const options = {
  states: ['idle', 'walk', 'run', 'attack', 'jump']
};
```

You can use the `fetchAvailableAnimationStates` function to get a list of all available animation states:

```javascript
const availableStates = await fetchAvailableAnimationStates();
console.log(availableStates);
// Output: ['idle', 'walk', 'run', 'attack', 'jump', 'fall', 'hurt', 'die']
```

### Frames Per State

- **Option**: `framesPerState`
- **Default**: `6`
- **Description**: The number of frames to generate for each animation state.

Example:
```javascript
const options = {
  framesPerState: 8
};
```

### Size

- **Option**: `size`
- **Default**: `'1024x1024'`
- **Description**: The output size of the generated spritesheet.

Example:
```javascript
const options = {
  size: '2048x2048'
};
```

### Art Style

- **Option**: `style`
- **Default**: `'pixel-art'`
- **Description**: The art style to use for the character sprites.

Example:
```javascript
const options = {
  style: 'vector'
};
```

You can use the `fetchAvailableSpriteStyles` function to get a list of all available styles:

```javascript
const availableStyles = await fetchAvailableSpriteStyles();
console.log(availableStyles);
// Output: ['pixel-art', 'vector', '3d', 'hand-drawn', 'anime']
```

### Padding

- **Option**: `padding`
- **Default**: `1`
- **Description**: The padding between individual sprites in the spritesheet.

Example:
```javascript
const options = {
  padding: 2
};
```

### Direction

- **Option**: `direction`
- **Default**: `'right'`
- **Description**: The base direction the character should face.

Example:
```javascript
const options = {
  direction: 'left'
};
```

### Save Option

- **Option**: `save`
- **Default**: `false`
- **Description**: Whether to save the generated spritesheet to the file system.

Example:
```javascript
const options = {
  save: true
};
```

## Environment Sprite Customization

When using the `generateEnvironmentSprites` function, you can customize the following options:

### Number of Elements

- **Option**: `elements`
- **Default**: `4`
- **Description**: The number of different environment elements to generate.

Example:
```javascript
const options = {
  elements: 6
};
```

### Size

- **Option**: `size`
- **Default**: `'1024x1024'`
- **Description**: The output size of the generated tileset.

Example:
```javascript
const options = {
  size: '2048x2048'
};
```

### Art Style

- **Option**: `style`
- **Default**: `'pixel-art'`
- **Description**: The art style to use for the environment sprites.

Example:
```javascript
const options = {
  style: 'hand-drawn'
};
```

### Padding

- **Option**: `padding`
- **Default**: `1`
- **Description**: The padding between individual sprites in the tileset.

Example:
```javascript
const options = {
  padding: 2
};
```

### Theme

- **Option**: `theme`
- **Default**: `'fantasy'`
- **Description**: The theme of the environment sprites.

Example:
```javascript
const options = {
  theme: 'sci-fi'
};
```

### Save Option

- **Option**: `save`
- **Default**: `false`
- **Description**: Whether to save the generated tileset to the file system.

Example:
```javascript
const options = {
  save: true
};
```

## Example Usage

Here's an example of how to use these customization options when generating a character spritesheet:

```javascript
import { generateCharacterSpritesheet } from 'spriteAI';

const description = 'A heroic knight in shining armor';
const options = {
  states: ['idle', 'walk', 'run', 'attack', 'defend'],
  framesPerState: 8,
  size: '2048x2048',
  style: 'pixel-art',
  padding: 2,
  direction: 'right',
  save: true
};

const result = await generateCharacterSpritesheet(description, options);
console.log(result);
```

And here's an example for generating environment sprites:

```javascript
import { generateEnvironmentSprites } from 'spriteAI';

const description = 'A lush forest with ancient ruins';
const options = {
  elements: 6,
  size: '2048x2048',
  style: 'hand-drawn',
  padding: 2,
  theme: 'fantasy',
  save: true
};

const result = await generateEnvironmentSprites(description, options);
console.log(result);
```

By adjusting these options, you can create a wide variety of sprites and environments tailored to your specific game or application needs.