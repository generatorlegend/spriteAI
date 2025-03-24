<response>

# Character Spritesheet Generation

This guide provides a detailed overview of generating character spritesheets using SpriteAI. Learn how to create customized character animations for various game genres and styles.

## Table of Contents

1. [Introduction](#introduction)
2. [Basic Usage](#basic-usage)
3. [Available Options](#available-options)
4. [Animation States](#animation-states)
5. [Customizing Output](#customizing-output)
6. [Examples](#examples)
7. [Best Practices](#best-practices)

## Introduction

SpriteAI's `generateCharacterSpritesheet` function allows you to create detailed character spritesheets with multiple animation states. This powerful tool uses AI to generate pixel art characters based on your descriptions and customization options.

## Basic Usage

To generate a character spritesheet, use the `generateCharacterSpritesheet` function:

```javascript
import { generateCharacterSpritesheet } from 'spriteAI';

const result = await generateCharacterSpritesheet('a heroic knight in shining armor');
```

This will create a default spritesheet with idle, walk, run, and attack animations for the described character.

## Available Options

The `generateCharacterSpritesheet` function accepts an options object to customize the output:

- `states`: Array of animation states (default: `['idle', 'walk', 'run', 'attack']`)
- `framesPerState`: Number of frames for each animation state (default: `6`)
- `size`: Output image size (default: `'1024x1024'`)
- `style`: Art style (default: `'pixel-art'`)
- `padding`: Padding between sprites (default: `1`)
- `direction`: Base direction of the character (default: `'right'`)
- `save`: Boolean to save the generated image (default: `false`)

Example with custom options:

```javascript
const result = await generateCharacterSpritesheet('a stealthy ninja', {
  states: ['idle', 'sneak', 'throw', 'disappear'],
  framesPerState: 8,
  size: '2048x2048',
  style: 'anime',
  direction: 'left'
});
```

## Animation States

You can customize the animation states for your character. The default states are:

- idle
- walk
- run
- attack

To fetch available animation states, use the `fetchAvailableAnimationStates` function:

```javascript
import { fetchAvailableAnimationStates } from 'spriteAI';

const availableStates = await fetchAvailableAnimationStates();
console.log(availableStates);
// ['idle', 'walk', 'run', 'attack', 'jump', 'fall', 'hurt', 'die']
```

## Customizing Output

### Sprite Styles

SpriteAI supports various sprite styles. To fetch available styles:

```javascript
import { fetchAvailableSpriteStyles } from 'spriteAI';

const availableStyles = await fetchAvailableSpriteStyles();
console.log(availableStyles);
// ['pixel-art', 'vector', '3d', 'hand-drawn', 'anime']
```

### Size and Direction

Adjust the size and direction of your character:

```javascript
const result = await generateCharacterSpritesheet('a fierce dragon', {
  size: '2048x2048',
  direction: 'left'
});
```

## Examples

### Fantasy RPG Character

```javascript
const wizardSprite = await generateCharacterSpritesheet('a wise old wizard with a long beard', {
  states: ['idle', 'cast', 'walk', 'teleport'],
  style: 'pixel-art',
  framesPerState: 8
});
```

### Sci-Fi Game Character

```javascript
const androidSprite = await generateCharacterSpritesheet('a sleek android with glowing circuits', {
  states: ['idle', 'run', 'shoot', 'shield'],
  style: 'vector',
  size: '2048x2048'
});
```

### Platform Game Character

```javascript
const platformerHero = await generateCharacterSpritesheet('a cute, cartoonish blob monster', {
  states: ['idle', 'walk', 'jump', 'squish'],
  style: 'hand-drawn',
  framesPerState: 10
});
```

## Best Practices

1. **Be Specific**: Provide detailed descriptions for more accurate results.
2. **Consistent Style**: Keep the style consistent across all characters in your game.
3. **Optimize Frames**: Use an appropriate number of frames per state for smooth animations without excessive file sizes.
4. **Test Different Styles**: Experiment with different art styles to find the best fit for your game's aesthetic.
5. **Save Resources**: Use the `save` option to store generated spritesheets for future use.

By leveraging SpriteAI's character spritesheet generation, you can quickly create diverse and high-quality character animations for your game development projects.

</response># Character Spritesheet Generation

This guide provides a detailed overview of generating character spritesheets using SpriteAI. Learn how to create customized character animations for various game genres and styles.

## Table of Contents

1. [Introduction](#introduction)
2. [Basic Usage](#basic-usage)
3. [Available Options](#available-options)
4. [Animation States](#animation-states)
5. [Customizing Output](#customizing-output)
6. [Examples](#examples)
7. [Best Practices](#best-practices)

## Introduction

SpriteAI's `generateCharacterSpritesheet` function allows you to create detailed character spritesheets with multiple animation states. This powerful tool uses AI to generate pixel art characters based on your descriptions and customization options.

## Basic Usage

To generate a character spritesheet, use the `generateCharacterSpritesheet` function:

```javascript
import { generateCharacterSpritesheet } from 'spriteAI';

const result = await generateCharacterSpritesheet('a heroic knight in shining armor');
```

This will create a default spritesheet with idle, walk, run, and attack animations for the described character.

## Available Options

The `generateCharacterSpritesheet` function accepts an options object to customize the output:

- `states`: Array of animation states (default: `['idle', 'walk', 'run', 'attack']`)
- `framesPerState`: Number of frames for each animation state (default: `6`)
- `size`: Output image size (default: `'1024x1024'`)
- `style`: Art style (default: `'pixel-art'`)
- `padding`: Padding between sprites (default: `1`)
- `direction`: Base direction of the character (default: `'right'`)
- `save`: Boolean to save the generated image (default: `false`)

Example with custom options:

```javascript
const result = await generateCharacterSpritesheet('a stealthy ninja', {
  states: ['idle', 'sneak', 'throw', 'disappear'],
  framesPerState: 8,
  size: '2048x2048',
  style: 'anime',
  direction: 'left'
});
```

## Animation States

You can customize the animation states for your character. The default states are:

- idle
- walk
- run
- attack

To fetch available animation states, use the `fetchAvailableAnimationStates` function:

```javascript
import { fetchAvailableAnimationStates } from 'spriteAI';

const availableStates = await fetchAvailableAnimationStates();
console.log(availableStates);
// ['idle', 'walk', 'run', 'attack', 'jump', 'fall', 'hurt', 'die']
```

## Customizing Output

### Sprite Styles

SpriteAI supports various sprite styles. To fetch available styles:

```javascript
import { fetchAvailableSpriteStyles } from 'spriteAI';

const availableStyles = await fetchAvailableSpriteStyles();
console.log(availableStyles);
// ['pixel-art', 'vector', '3d', 'hand-drawn', 'anime']
```

### Size and Direction

Adjust the size and direction of your character:

```javascript
const result = await generateCharacterSpritesheet('a fierce dragon', {
  size: '2048x2048',
  direction: 'left'
});
```

## Examples

### Fantasy RPG Character

```javascript
const wizardSprite = await generateCharacterSpritesheet('a wise old wizard with a long beard', {
  states: ['idle', 'cast', 'walk', 'teleport'],
  style: 'pixel-art',
  framesPerState: 8
});
```

### Sci-Fi Game Character

```javascript
const androidSprite = await generateCharacterSpritesheet('a sleek android with glowing circuits', {
  states: ['idle', 'run', 'shoot', 'shield'],
  style: 'vector',
  size: '2048x2048'
});
```

### Platform Game Character

```javascript
const platformerHero = await generateCharacterSpritesheet('a cute, cartoonish blob monster', {
  states: ['idle', 'walk', 'jump', 'squish'],
  style: 'hand-drawn',
  framesPerState: 10
});
```

## Best Practices

1. **Be Specific**: Provide detailed descriptions for more accurate results.
2. **Consistent Style**: Keep the style consistent across all characters in your game.
3. **Optimize Frames**: Use an appropriate number of frames per state for smooth animations without excessive file sizes.
4. **Test Different Styles**: Experiment with different art styles to find the best fit for your game's aesthetic.
5. **Save Resources**: Use the `save` option to store generated spritesheets for future use.

By leveraging SpriteAI's character spritesheet generation, you can quickly create diverse and high-quality character animations for your game development projects.