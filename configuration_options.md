<response>

# Configuration Options for SpriteAI Functions

This document outlines the various configuration options available for SpriteAI functions, including sprite generation, image processing settings, and output options. Understanding these options will help you customize the output to meet your specific needs.

## Table of Contents

1. [Character Spritesheet Generation](#character-spritesheet-generation)
2. [Landscape Sprite Generation](#landscape-sprite-generation)
3. [Environment Sprites Generation](#environment-sprites-generation)
4. [Common Options](#common-options)

## Character Spritesheet Generation

The `generateCharacterSpritesheet` function allows you to create customized character spritesheets. Here are the available options:

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

await generateCharacterSpritesheet(description, options);
```

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `states` | Array of strings | `['idle', 'walk', 'run', 'attack']` | Animation states to generate |
| `framesPerState` | Number | 6 | Number of frames per animation state |
| `size` | String | '1024x1024' | Output size of the spritesheet |
| `style` | String | 'pixel-art' | Art style of the character |
| `padding` | Number | 1 | Padding between sprites |
| `direction` | String | 'right' | Base direction of the character |
| `save` | Boolean | false | Whether to save the generated image |

### Example Usage

```javascript
const characterOptions = {
  states: ['idle', 'walk', 'run', 'jump'],
  framesPerState: 8,
  size: '2048x2048',
  style: 'vector',
  direction: 'left',
  save: true
};

const result = await generateCharacterSpritesheet('a medieval knight', characterOptions);
console.log(result.metadata);
```

## Landscape Sprite Generation

The `generateLandscapeSprite` function allows you to create customized landscape sprites. Here are the available options:

```javascript
const options = {
  size: '1024x1024',
  style: 'pixel-art',
  timeOfDay: 'day',
  weather: 'clear',
  perspective: 'side-scrolling',
  save: false,
  removeBackground: false,
  backgroundColor: '#FFFFFF',
  colorThreshold: 0.1
};

await generateLandscapeSprite(description, options);
```

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `size` | String | '1024x1024' | Output size of the landscape sprite |
| `style` | String | 'pixel-art' | Art style of the landscape |
| `timeOfDay` | String | 'day' | Time of day setting (day, night, sunset, dawn) |
| `weather` | String | 'clear' | Weather conditions (clear, rainy, foggy, snowy) |
| `perspective` | String | 'side-scrolling' | Perspective of the landscape (side-scrolling, top-down, isometric) |
| `save` | Boolean | false | Whether to save the generated image |
| `removeBackground` | Boolean | false | Whether to remove the background |
| `backgroundColor` | String | '#FFFFFF' | Background color to remove (if removeBackground is true) |
| `colorThreshold` | Number | 0.1 | Threshold for background color removal |

### Example Usage

```javascript
const landscapeOptions = {
  size: '2048x1024',
  style: 'vector',
  timeOfDay: 'sunset',
  weather: 'foggy',
  perspective: 'isometric',
  save: true,
  removeBackground: true,
  backgroundColor: '#F0F0F0',
  colorThreshold: 0.2
};

const result = await generateLandscapeSprite('a mystical forest', landscapeOptions);
console.log(result.metadata);
```

## Environment Sprites Generation

The `generateEnvironmentSprites` function allows you to create customized environment sprite sets. Here are the available options:

```javascript
const options = {
  elements: 4,
  size: '1024x1024',
  style: 'pixel-art',
  padding: 1,
  theme: 'fantasy',
  save: false
};

await generateEnvironmentSprites(description, options);
```

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `elements` | Number | 4 | Number of different elements in the tileset |
| `size` | String | '1024x1024' | Output size of the tileset |
| `style` | String | 'pixel-art' | Art style of the environment sprites |
| `padding` | Number | 1 | Padding between sprites |
| `theme` | String | 'fantasy' | Theme of the environment |
| `save` | Boolean | false | Whether to save the generated image |

### Example Usage

```javascript
const environmentOptions = {
  elements: 6,
  size: '2048x2048',
  style: 'hand-drawn',
  padding: 2,
  theme: 'sci-fi',
  save: true
};

const result = await generateEnvironmentSprites('space station interior', environmentOptions);
console.log(result.metadata);
```

## Common Options

Some options are common across multiple functions:

- `size`: Determines the output image size. Always specified as a string in the format 'WIDTHxHEIGHT'.
- `style`: Defines the art style of the generated sprites. Common values include 'pixel-art', 'vector', '3d', 'hand-drawn', and 'anime'.
- `save`: A boolean flag that, when set to true, saves the generated image to the local file system.

### Available Animation States

You can fetch the list of available animation states using the `fetchAvailableAnimationStates` function:

```javascript
const availableStates = await fetchAvailableAnimationStates();
console.log(availableStates);
// Output: ['idle', 'walk', 'run', 'attack', 'jump', 'fall', 'hurt', 'die']
```

### Available Sprite Styles

To get the list of available sprite styles, use the `fetchAvailableSpriteStyles` function:

```javascript
const availableStyles = await fetchAvailableSpriteStyles();
console.log(availableStyles);
// Output: ['pixel-art', 'vector', '3d', 'hand-drawn', 'anime']
```

By leveraging these configuration options, you can fine-tune the output of SpriteAI functions to match your specific requirements for game development or other graphical projects.

</response># Configuration Options for SpriteAI Functions

This document outlines the various configuration options available for SpriteAI functions, including sprite generation, image processing settings, and output options. Understanding these options will help you customize the output to meet your specific needs.

## Table of Contents

1. [Character Spritesheet Generation](#character-spritesheet-generation)
2. [Landscape Sprite Generation](#landscape-sprite-generation)
3. [Environment Sprites Generation](#environment-sprites-generation)
4. [Common Options](#common-options)

## Character Spritesheet Generation

The `generateCharacterSpritesheet` function allows you to create customized character spritesheets. Here are the available options:

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

await generateCharacterSpritesheet(description, options);
```

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `states` | Array of strings | `['idle', 'walk', 'run', 'attack']` | Animation states to generate |
| `framesPerState` | Number | 6 | Number of frames per animation state |
| `size` | String | '1024x1024' | Output size of the spritesheet |
| `style` | String | 'pixel-art' | Art style of the character |
| `padding` | Number | 1 | Padding between sprites |
| `direction` | String | 'right' | Base direction of the character |
| `save` | Boolean | false | Whether to save the generated image |

### Example Usage

```javascript
const characterOptions = {
  states: ['idle', 'walk', 'run', 'jump'],
  framesPerState: 8,
  size: '2048x2048',
  style: 'vector',
  direction: 'left',
  save: true
};

const result = await generateCharacterSpritesheet('a medieval knight', characterOptions);
console.log(result.metadata);
```

## Landscape Sprite Generation

The `generateLandscapeSprite` function allows you to create customized landscape sprites. Here are the available options:

```javascript
const options = {
  size: '1024x1024',
  style: 'pixel-art',
  timeOfDay: 'day',
  weather: 'clear',
  perspective: 'side-scrolling',
  save: false,
  removeBackground: false,
  backgroundColor: '#FFFFFF',
  colorThreshold: 0.1
};

await generateLandscapeSprite(description, options);
```

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `size` | String | '1024x1024' | Output size of the landscape sprite |
| `style` | String | 'pixel-art' | Art style of the landscape |
| `timeOfDay` | String | 'day' | Time of day setting (day, night, sunset, dawn) |
| `weather` | String | 'clear' | Weather conditions (clear, rainy, foggy, snowy) |
| `perspective` | String | 'side-scrolling' | Perspective of the landscape (side-scrolling, top-down, isometric) |
| `save` | Boolean | false | Whether to save the generated image |
| `removeBackground` | Boolean | false | Whether to remove the background |
| `backgroundColor` | String | '#FFFFFF' | Background color to remove (if removeBackground is true) |
| `colorThreshold` | Number | 0.1 | Threshold for background color removal |

### Example Usage

```javascript
const landscapeOptions = {
  size: '2048x1024',
  style: 'vector',
  timeOfDay: 'sunset',
  weather: 'foggy',
  perspective: 'isometric',
  save: true,
  removeBackground: true,
  backgroundColor: '#F0F0F0',
  colorThreshold: 0.2
};

const result = await generateLandscapeSprite('a mystical forest', landscapeOptions);
console.log(result.metadata);
```

## Environment Sprites Generation

The `generateEnvironmentSprites` function allows you to create customized environment sprite sets. Here are the available options:

```javascript
const options = {
  elements: 4,
  size: '1024x1024',
  style: 'pixel-art',
  padding: 1,
  theme: 'fantasy',
  save: false
};

await generateEnvironmentSprites(description, options);
```

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `elements` | Number | 4 | Number of different elements in the tileset |
| `size` | String | '1024x1024' | Output size of the tileset |
| `style` | String | 'pixel-art' | Art style of the environment sprites |
| `padding` | Number | 1 | Padding between sprites |
| `theme` | String | 'fantasy' | Theme of the environment |
| `save` | Boolean | false | Whether to save the generated image |

### Example Usage

```javascript
const environmentOptions = {
  elements: 6,
  size: '2048x2048',
  style: 'hand-drawn',
  padding: 2,
  theme: 'sci-fi',
  save: true
};

const result = await generateEnvironmentSprites('space station interior', environmentOptions);
console.log(result.metadata);
```

## Common Options

Some options are common across multiple functions:

- `size`: Determines the output image size. Always specified as a string in the format 'WIDTHxHEIGHT'.
- `style`: Defines the art style of the generated sprites. Common values include 'pixel-art', 'vector', '3d', 'hand-drawn', and 'anime'.
- `save`: A boolean flag that, when set to true, saves the generated image to the local file system.

### Available Animation States

You can fetch the list of available animation states using the `fetchAvailableAnimationStates` function:

```javascript
const availableStates = await fetchAvailableAnimationStates();
console.log(availableStates);
// Output: ['idle', 'walk', 'run', 'attack', 'jump', 'fall', 'hurt', 'die']
```

### Available Sprite Styles

To get the list of available sprite styles, use the `fetchAvailableSpriteStyles` function:

```javascript
const availableStyles = await fetchAvailableSpriteStyles();
console.log(availableStyles);
// Output: ['pixel-art', 'vector', '3d', 'hand-drawn', 'anime']
```

By leveraging these configuration options, you can fine-tune the output of SpriteAI functions to match your specific requirements for game development or other graphical projects.