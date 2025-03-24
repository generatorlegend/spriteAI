# Configuration Options for SpriteAI

This guide provides a detailed overview of all configuration options available in the SpriteAI library. We'll cover the options for both `generateCharacterSpritesheet` and `generateLandscapeSprite` functions, explaining their default values and how they affect the output.

## generateCharacterSpritesheet Options

The `generateCharacterSpritesheet` function accepts an options object with the following properties:

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| states | Array&lt;string&gt; | ['idle', 'walk', 'run', 'attack'] | Animation states to generate |
| framesPerState | number | 6 | Number of frames per animation state |
| size | string | '1024x1024' | Output size of the spritesheet |
| style | string | 'pixel-art' | Art style of the generated sprites |
| padding | number | 1 | Padding between sprites in the spritesheet |
| direction | string | 'right' | Base direction the character is facing |
| save | boolean | false | Whether to save the generated image |

### Example Usage

```javascript
const result = await generateCharacterSpritesheet("a cute robot", {
  states: ['idle', 'walk', 'jump'],
  framesPerState: 8,
  size: '2048x2048',
  style: 'vector',
  padding: 2,
  direction: 'left',
  save: true
});
```

This configuration will generate a character spritesheet with the following characteristics:
- Three animation states: idle, walk, and jump
- 8 frames per state
- A larger output size of 2048x2048 pixels
- Vector art style instead of pixel art
- Increased padding between sprites
- Character facing left
- The generated image will be saved to the assets folder

## generateLandscapeSprite Options

The `generateLandscapeSprite` function accepts an options object with the following properties:

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| size | string | '1024x1024' | Output size of the landscape sprite |
| style | string | 'pixel-art' | Art style of the generated landscape |
| timeOfDay | string | 'day' | Time of day setting (day, night, sunset, dawn) |
| weather | string | 'clear' | Weather conditions (clear, rainy, foggy, snowy) |
| perspective | string | 'side-scrolling' | Perspective of the landscape (side-scrolling, top-down, isometric) |
| save | boolean | false | Whether to save the generated image |
| removeBackground | boolean | undefined | Whether to remove the background (if specified) |
| backgroundColor | string | '#FFFFFF' | Background color to remove (if removeBackground is true) |
| colorThreshold | number | 0.1 | Threshold for background color removal |

### Example Usage

```javascript
const result = await generateLandscapeSprite("a mystical forest", {
  size: '2048x1024',
  style: 'hand-drawn',
  timeOfDay: 'sunset',
  weather: 'foggy',
  perspective: 'isometric',
  save: true,
  removeBackground: true,
  backgroundColor: '#E0E0E0',
  colorThreshold: 0.2
});
```

This configuration will generate a landscape sprite with the following characteristics:
- A wider output size of 2048x1024 pixels
- Hand-drawn art style
- Sunset time of day with foggy weather
- Isometric perspective
- The generated image will be saved
- Background will be removed, targeting a light gray color (#E0E0E0) with a slightly higher color threshold

## Additional Functions

### fetchAvailableAnimationStates

This function returns an array of available animation states that can be used in the `generateCharacterSpritesheet` function.

```javascript
const states = await fetchAvailableAnimationStates();
console.log(states);
// Output: ['idle', 'walk', 'run', 'attack', 'jump', 'fall', 'hurt', 'die']
```

### fetchAvailableSpriteStyles

This function returns an array of available sprite styles that can be used in both `generateCharacterSpritesheet` and `generateLandscapeSprite` functions.

```javascript
const styles = await fetchAvailableSpriteStyles();
console.log(styles);
// Output: ['pixel-art', 'vector', '3d', 'hand-drawn', 'anime']
```

## Tips for Optimal Results

1. **Consistency**: When generating character spritesheets, try to keep the `framesPerState` consistent across different generations to ensure smooth animations.

2. **Style Matching**: Choose a `style` that matches your game's overall aesthetic. For example, 'pixel-art' for retro-style games or 'vector' for modern, clean looks.

3. **Size Considerations**: The `size` option affects the level of detail in your sprites. Larger sizes allow for more detail but may require more processing time and resources.

4. **Background Removal**: When using `removeBackground` for landscape sprites, experiment with the `colorThreshold` to find the best balance between removing the background and preserving important details.

5. **Perspective Matching**: Ensure that the `perspective` option for landscape sprites matches your game's viewpoint for a cohesive look.

By carefully configuring these options, you can generate sprites and landscapes that perfectly fit your game's style and requirements.