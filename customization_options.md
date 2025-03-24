<response>

# Customization Options in SpriteAI

SpriteAI offers a wide range of customization options to help you create diverse and unique sprites for your game projects. This guide will walk you through the various parameters you can adjust when generating character spritesheets and environment sprites.

## Character Spritesheet Customization

When using the `generateCharacterSpritesheet` function, you can customize several aspects of your character sprites. Here's a breakdown of the available options:

### Animation States

By default, SpriteAI generates sprites for four animation states: idle, walk, run, and attack. However, you can customize this list to include different states or change the order.

```javascript
const options = {
  states: ['idle', 'walk', 'jump', 'attack', 'die']
};
```

To fetch the list of available animation states, you can use the `fetchAvailableAnimationStates` function:

```javascript
const availableStates = await fetchAvailableAnimationStates();
console.log(availableStates);
// Output: ['idle', 'walk', 'run', 'attack', 'jump', 'fall', 'hurt', 'die']
```

### Frames Per State

You can adjust the number of frames for each animation state. The default is 6 frames per state.

```javascript
const options = {
  framesPerState: 8
};
```

### Sprite Size

Control the output size of your spritesheet. The default size is 1024x1024 pixels.

```javascript
const options = {
  size: '2048x2048'
};
```

### Art Style

SpriteAI supports various art styles for your sprites. The default style is 'pixel-art'.

```javascript
const options = {
  style: 'vector'
};
```

To get a list of available sprite styles, use the `fetchAvailableSpriteStyles` function:

```javascript
const availableStyles = await fetchAvailableSpriteStyles();
console.log(availableStyles);
// Output: ['pixel-art', 'vector', '3d', 'hand-drawn', 'anime']
```

### Padding

Adjust the padding between individual sprites in the spritesheet. The default padding is 1 pixel.

```javascript
const options = {
  padding: 2
};
```

### Character Direction

Specify the base direction the character should face. The default is 'right'.

```javascript
const options = {
  direction: 'left'
};
```

### Saving the Spritesheet

You can choose to save the generated spritesheet to your local filesystem.

```javascript
const options = {
  save: true
};
```

## Environment Sprite Customization

For generating environment sprites using the `generateEnvironmentSprites` function, you have the following customization options:

### Number of Elements

Specify the number of distinct environment pieces to generate. The default is 4.

```javascript
const options = {
  elements: 6
};
```

### Sprite Size

Similar to character spritesheets, you can control the output size of your environment tileset.

```javascript
const options = {
  size: '2048x2048'
};
```

### Art Style

Choose the art style for your environment sprites. The default is 'pixel-art'.

```javascript
const options = {
  style: 'hand-drawn'
};
```

### Padding

Adjust the padding between individual environment sprites in the tileset.

```javascript
const options = {
  padding: 2
};
```

### Theme

Specify a theme for your environment sprites. The default theme is 'fantasy'.

```javascript
const options = {
  theme: 'sci-fi'
};
```

### Saving the Tileset

Like character spritesheets, you can choose to save the generated environment tileset.

```javascript
const options = {
  save: true
};
```

## Putting It All Together

Here's an example of how you might use these customization options to generate a unique character spritesheet:

```javascript
const description = "A cyberpunk robot warrior";
const options = {
  states: ['idle', 'walk', 'attack', 'power-up', 'shutdown'],
  framesPerState: 8,
  size: '2048x2048',
  style: 'vector',
  padding: 2,
  direction: 'left',
  save: true
};

const result = await generateCharacterSpritesheet(description, options);
console.log(result.metadata);
```

And here's an example for generating custom environment sprites:

```javascript
const description = "Alien planet landscape";
const options = {
  elements: 6,
  size: '2048x2048',
  style: '3d',
  padding: 2,
  theme: 'sci-fi',
  save: true
};

const result = await generateEnvironmentSprites(description, options);
console.log(result.metadata);
```

By leveraging these customization options, you can create a wide variety of sprites tailored to your specific game requirements and art style preferences.

</response># Customization Options in SpriteAI

SpriteAI offers a wide range of customization options to help you create diverse and unique sprites for your game projects. This guide will walk you through the various parameters you can adjust when generating character spritesheets and environment sprites.

## Character Spritesheet Customization

When using the `generateCharacterSpritesheet` function, you can customize several aspects of your character sprites. Here's a breakdown of the available options:

### Animation States

By default, SpriteAI generates sprites for four animation states: idle, walk, run, and attack. However, you can customize this list to include different states or change the order.

```javascript
const options = {
  states: ['idle', 'walk', 'jump', 'attack', 'die']
};
```

To fetch the list of available animation states, you can use the `fetchAvailableAnimationStates` function:

```javascript
const availableStates = await fetchAvailableAnimationStates();
console.log(availableStates);
// Output: ['idle', 'walk', 'run', 'attack', 'jump', 'fall', 'hurt', 'die']
```

### Frames Per State

You can adjust the number of frames for each animation state. The default is 6 frames per state.

```javascript
const options = {
  framesPerState: 8
};
```

### Sprite Size

Control the output size of your spritesheet. The default size is 1024x1024 pixels.

```javascript
const options = {
  size: '2048x2048'
};
```

### Art Style

SpriteAI supports various art styles for your sprites. The default style is 'pixel-art'.

```javascript
const options = {
  style: 'vector'
};
```

To get a list of available sprite styles, use the `fetchAvailableSpriteStyles` function:

```javascript
const availableStyles = await fetchAvailableSpriteStyles();
console.log(availableStyles);
// Output: ['pixel-art', 'vector', '3d', 'hand-drawn', 'anime']
```

### Padding

Adjust the padding between individual sprites in the spritesheet. The default padding is 1 pixel.

```javascript
const options = {
  padding: 2
};
```

### Character Direction

Specify the base direction the character should face. The default is 'right'.

```javascript
const options = {
  direction: 'left'
};
```

### Saving the Spritesheet

You can choose to save the generated spritesheet to your local filesystem.

```javascript
const options = {
  save: true
};
```

## Environment Sprite Customization

For generating environment sprites using the `generateEnvironmentSprites` function, you have the following customization options:

### Number of Elements

Specify the number of distinct environment pieces to generate. The default is 4.

```javascript
const options = {
  elements: 6
};
```

### Sprite Size

Similar to character spritesheets, you can control the output size of your environment tileset.

```javascript
const options = {
  size: '2048x2048'
};
```

### Art Style

Choose the art style for your environment sprites. The default is 'pixel-art'.

```javascript
const options = {
  style: 'hand-drawn'
};
```

### Padding

Adjust the padding between individual environment sprites in the tileset.

```javascript
const options = {
  padding: 2
};
```

### Theme

Specify a theme for your environment sprites. The default theme is 'fantasy'.

```javascript
const options = {
  theme: 'sci-fi'
};
```

### Saving the Tileset

Like character spritesheets, you can choose to save the generated environment tileset.

```javascript
const options = {
  save: true
};
```

## Putting It All Together

Here's an example of how you might use these customization options to generate a unique character spritesheet:

```javascript
const description = "A cyberpunk robot warrior";
const options = {
  states: ['idle', 'walk', 'attack', 'power-up', 'shutdown'],
  framesPerState: 8,
  size: '2048x2048',
  style: 'vector',
  padding: 2,
  direction: 'left',
  save: true
};

const result = await generateCharacterSpritesheet(description, options);
console.log(result.metadata);
```

And here's an example for generating custom environment sprites:

```javascript
const description = "Alien planet landscape";
const options = {
  elements: 6,
  size: '2048x2048',
  style: '3d',
  padding: 2,
  theme: 'sci-fi',
  save: true
};

const result = await generateEnvironmentSprites(description, options);
console.log(result.metadata);
```

By leveraging these customization options, you can create a wide variety of sprites tailored to your specific game requirements and art style preferences.