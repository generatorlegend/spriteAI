# Customization Options

This guide provides a comprehensive overview of the customization options available in the SpriteAI library. These options allow you to fine-tune the generation of character spritesheets, landscape sprites, and environment sprites to match your specific game or application requirements.

## Character Spritesheet Customization

The `generateCharacterSpritesheet` function offers several customization options to tailor the output to your needs.

### Animation States

You can specify the animation states for your character spritesheet using the `states` option. By default, the following states are included:

- idle
- walk
- run
- attack

To customize the states, provide an array of desired animation states:

```javascript
const options = {
  states: ['idle', 'walk', 'jump', 'crouch', 'swim']
};
```

To fetch the available animation states, use the `fetchAvailableAnimationStates` function:

```javascript
const availableStates = await fetchAvailableAnimationStates();
console.log(availableStates);
// Output: ['idle', 'walk', 'run', 'attack', 'jump', 'fall', 'hurt', 'die']
```

### Frames Per State

Control the number of frames for each animation state using the `framesPerState` option. The default is 6 frames per state.

```javascript
const options = {
  framesPerState: 8
};
```

### Image Size

Adjust the size of the generated spritesheet using the `size` option. The default size is '1024x1024'.

```javascript
const options = {
  size: '2048x2048'
};
```

### Sprite Style

Customize the visual style of your sprites using the `style` option. The default style is 'pixel-art'.

```javascript
const options = {
  style: 'vector'
};
```

To fetch the available sprite styles, use the `fetchAvailableSpriteStyles` function:

```javascript
const availableStyles = await fetchAvailableSpriteStyles();
console.log(availableStyles);
// Output: ['pixel-art', 'vector', '3d', 'hand-drawn', 'anime']
```

### Padding

Adjust the padding between individual sprite frames using the `padding` option. The default padding is 1 pixel.

```javascript
const options = {
  padding: 2
};
```

### Direction

Specify the base direction the character should face using the `direction` option. The default direction is 'right'.

```javascript
const options = {
  direction: 'left'
};
```

### Saving the Spritesheet

To save the generated spritesheet to disk, use the `save` option:

```javascript
const options = {
  save: true
};
```

## Landscape Sprite Customization

The `generateLandscapeSprite` function provides options to customize the generated landscape sprites.

### Image Size

Similar to character spritesheets, you can specify the size of the landscape sprite:

```javascript
const options = {
  size: '2048x1024'
};
```

### Style

Choose the art style for your landscape sprite:

```javascript
const options = {
  style: 'pixel-art'
};
```

### Time of Day

Set the time of day for the landscape scene:

```javascript
const options = {
  timeOfDay: 'sunset' // Options: 'day', 'night', 'sunset', 'dawn'
};
```

### Weather

Specify the weather conditions for the landscape:

```javascript
const options = {
  weather: 'rainy' // Options: 'clear', 'rainy', 'foggy', 'snowy'
};
```

### Perspective

Choose the perspective for the landscape sprite:

```javascript
const options = {
  perspective: 'isometric' // Options: 'side-scrolling', 'top-down', 'isometric'
};
```

### Saving the Landscape Sprite

To save the generated landscape sprite to disk, use the `save` option:

```javascript
const options = {
  save: true
};
```

### Background Removal

You can remove the background of the generated landscape sprite:

```javascript
const options = {
  removeBackground: true,
  backgroundColor: '#FFFFFF', // Color to remove
  colorThreshold: 0.1 // Tolerance for color matching
};
```

## Environment Sprites Customization

The `generateEnvironmentSprites` function allows you to create customized environment sprite sets.

### Number of Elements

Specify the number of distinct environment elements to generate:

```javascript
const options = {
  elements: 6
};
```

### Image Size

Set the size of the generated tileset:

```javascript
const options = {
  size: '2048x2048'
};
```

### Style

Choose the art style for your environment sprites:

```javascript
const options = {
  style: 'hand-drawn'
};
```

### Padding

Adjust the padding between individual environment sprites:

```javascript
const options = {
  padding: 2
};
```

### Theme

Specify the theme for the environment sprites:

```javascript
const options = {
  theme: 'sci-fi' // Default is 'fantasy'
};
```

### Saving the Environment Sprites

To save the generated environment sprite tileset to disk, use the `save` option:

```javascript
const options = {
  save: true
};
```

By utilizing these customization options, you can create a wide variety of sprites and tilesets tailored to your specific game or application needs using the SpriteAI library.