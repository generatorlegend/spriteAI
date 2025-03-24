# Customization Options for SpriteAI

SpriteAI provides a powerful set of customization options for generating both character spritesheets and landscape sprites. This guide will walk you through the available options and demonstrate how they affect the output.

## Character Spritesheet Customization

When using the `generateCharacterSpritesheet` function, you can customize various aspects of the generated spritesheet. Here are the available options:

### Basic Options

- `description`: A string describing the character you want to generate.
- `states`: An array of animation states (default: `['idle', 'walk', 'run', 'attack']`).
- `framesPerState`: Number of frames for each animation state (default: 6).
- `size`: Output size of the spritesheet (default: '1024x1024').
- `style`: Art style of the sprites (default: 'pixel-art').
- `padding`: Padding between individual sprites (default: 1).
- `direction`: Base direction the character faces (default: 'right').
- `save`: Boolean indicating whether to save the generated image (default: false).

### Example Usage

```javascript
const result = await generateCharacterSpritesheet("a fierce orc warrior", {
  states: ['idle', 'walk', 'attack', 'die'],
  framesPerState: 8,
  size: '2048x2048',
  style: 'hand-drawn',
  direction: 'left',
  save: true
});
```

### Effects of Customization

1. **States**: Changing the `states` array affects the number and types of animations in the spritesheet. Each state will be represented by a row in the final spritesheet.

2. **Frames Per State**: Increasing `framesPerState` will result in smoother animations but will also increase the size of the spritesheet.

3. **Size**: Larger sizes will provide more detailed sprites but may take longer to generate.

4. **Style**: Different styles can dramatically change the look of your character. Available styles include 'pixel-art', 'vector', '3d', 'hand-drawn', and 'anime'.

5. **Direction**: This affects the initial facing direction of the character in the spritesheet.

## Landscape Sprite Customization

The `generateLandscapeSprite` function offers options to customize the generated landscape:

### Basic Options

- `description`: A string describing the landscape scene you want to generate.
- `size`: Output size of the sprite (default: '1024x1024').
- `style`: Art style of the landscape (default: 'pixel-art').
- `timeOfDay`: Time setting for the scene (default: 'day').
- `weather`: Weather conditions in the scene (default: 'clear').
- `perspective`: Viewpoint of the landscape (default: 'side-scrolling').
- `save`: Boolean indicating whether to save the generated image (default: false).
- `removeBackground`: Boolean to indicate if the background should be removed (optional).
- `backgroundColor`: Color to be removed if `removeBackground` is true (optional).
- `colorThreshold`: Threshold for color removal (optional).

### Example Usage

```javascript
const result = await generateLandscapeSprite("a mystical forest with glowing mushrooms", {
  size: '2048x1024',
  style: 'hand-drawn',
  timeOfDay: 'night',
  weather: 'foggy',
  perspective: 'isometric',
  save: true,
  removeBackground: true,
  backgroundColor: '#FFFFFF',
  colorThreshold: 0.1
});
```

### Effects of Customization

1. **Time of Day**: Options like 'day', 'night', 'sunset', and 'dawn' will affect the lighting and color palette of the scene.

2. **Weather**: Different weather conditions ('clear', 'rainy', 'foggy', 'snowy') will add atmospheric effects to the landscape.

3. **Perspective**: Changing the perspective ('side-scrolling', 'top-down', 'isometric') will alter the viewpoint of the landscape, affecting its use in different game styles.

4. **Remove Background**: When set to true, this option will attempt to remove the background color, which can be useful for creating sprites with transparency.

## Additional Customization Functions

SpriteAI also provides functions to fetch available options:

### Fetching Available Animation States

```javascript
const states = await fetchAvailableAnimationStates();
console.log(states);
// Output: ['idle', 'walk', 'run', 'attack', 'jump', 'fall', 'hurt', 'die']
```

### Fetching Available Sprite Styles

```javascript
const styles = await fetchAvailableSpriteStyles();
console.log(styles);
// Output: ['pixel-art', 'vector', '3d', 'hand-drawn', 'anime']
```

These functions can be useful for dynamically populating option menus in your application.

## Conclusion

By leveraging these customization options, you can generate a wide variety of character spritesheets and landscape sprites tailored to your specific game or application needs. Experiment with different combinations to achieve the desired visual style and functionality for your project.