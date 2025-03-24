# Customization Options in SpriteAI

This guide explains the various customization options available in the SpriteAI library. You'll learn how to adjust parameters for character spritesheets, landscape sprites, and other generated assets. We'll cover style options, animation states, and image processing features like background removal.

## Character Spritesheets

The `generateCharacterSpritesheet` function allows you to create customized character spritesheets. Here are the available options:

### Basic Options

- `description`: A string describing the character you want to generate.
- `states`: An array of animation states (default: `['idle', 'walk', 'run', 'attack']`).
- `framesPerState`: Number of frames for each animation state (default: 6).
- `size`: Output size of the spritesheet (default: '1024x1024').
- `style`: Art style of the character (default: 'pixel-art').
- `padding`: Padding between sprites (default: 1).
- `direction`: Base direction of the character (default: 'right').

### Example Usage

```javascript
const result = await generateCharacterSpritesheet("a cute robot", {
  states: ['idle', 'walk', 'run', 'jump'],
  framesPerState: 8,
  size: '2048x2048',
  style: 'vector',
  padding: 2,
  direction: 'left'
});
```

### Available Animation States

You can fetch the available animation states using the `fetchAvailableAnimationStates` function:

```javascript
const states = await fetchAvailableAnimationStates();
console.log(states);
// Output: ['idle', 'walk', 'run', 'attack', 'jump', 'fall', 'hurt', 'die']
```

### Available Sprite Styles

To get a list of available sprite styles, use the `fetchAvailableSpriteStyles` function:

```javascript
const styles = await fetchAvailableSpriteStyles();
console.log(styles);
// Output: ['pixel-art', 'vector', '3d', 'hand-drawn', 'anime']
```

## Landscape Sprites

The `generateLandscapeSprite` function allows you to create customized landscape sprites. Here are the available options:

### Basic Options

- `description`: A string describing the landscape you want to generate.
- `size`: Output size of the sprite (default: '1024x1024').
- `style`: Art style of the landscape (default: 'pixel-art').
- `timeOfDay`: Time of day setting (default: 'day', options: 'day', 'night', 'sunset', 'dawn').
- `weather`: Weather conditions (default: 'clear', options: 'clear', 'rainy', 'foggy', 'snowy').
- `perspective`: Perspective of the landscape (default: 'side-scrolling', options: 'side-scrolling', 'top-down', 'isometric').
- `save`: Whether to save the generated image (default: false).

### Example Usage

```javascript
const result = await generateLandscapeSprite("a lush forest with a river", {
  size: '2048x1024',
  style: 'hand-drawn',
  timeOfDay: 'sunset',
  weather: 'foggy',
  perspective: 'isometric',
  save: true
});
```

### Background Removal

You can remove the background of the generated landscape sprite by setting the `removeBackground` option to `true`. Additional options for background removal include:

- `backgroundColor`: The color to be removed (default: '#FFFFFF').
- `colorThreshold`: Threshold for color matching (default: 0.1).

Example:

```javascript
const result = await generateLandscapeSprite("a desert oasis", {
  removeBackground: true,
  backgroundColor: '#FFF8DC',
  colorThreshold: 0.2
});
```

## Environment Sprites

The `generateEnvironmentSprites` function allows you to create customized environment sprites. Here are the available options:

### Basic Options

- `description`: A string describing the environment you want to generate.
- `elements`: Number of different elements to generate (default: 4).
- `size`: Output size of the tileset (default: '1024x1024').
- `style`: Art style of the environment (default: 'pixel-art').
- `padding`: Padding between elements (default: 1).
- `theme`: Theme of the environment (default: 'fantasy').

### Example Usage

```javascript
const result = await generateEnvironmentSprites("underwater coral reef", {
  elements: 6,
  size: '2048x2048',
  style: '3d',
  padding: 2,
  theme: 'ocean'
});
```

## Saving Generated Assets

For all generation functions (`generateCharacterSpritesheet`, `generateLandscapeSprite`, and `generateEnvironmentSprites`), you can save the generated asset by setting the `save` option to `true`. The assets will be saved in the `assets` folder of your current working directory.

```javascript
const result = await generateCharacterSpritesheet("a medieval knight", {
  save: true
});
```

This will save the spritesheet as `assets/a_medieval_knight_spritesheet.png`.

## Conclusion

By utilizing these customization options, you can generate a wide variety of sprites and assets tailored to your specific needs. Experiment with different combinations of options to achieve the desired results for your game or application.