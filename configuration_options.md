<response>

# Configuration Options for SpriteAI Functions

This guide explains the available configuration options for SpriteAI functions, including `generateCharacterSpritesheet`, `generateLandscapeSprite`, and `generateEnvironmentSprites`. These options allow you to customize the output of your generated sprites and tailor them to your specific needs.

## Common Options

These options are shared across multiple functions:

### `size` (string)

Specifies the output size of the generated image.

- Default: `'1024x1024'`
- Format: `'<width>x<height>'`
- Example: `'512x512'`

### `style` (string)

Defines the art style of the generated sprite.

- Default: `'pixel-art'`
- Available styles: `'pixel-art'`, `'vector'`, `'3d'`, `'hand-drawn'`, `'anime'`

### `save` (boolean)

Determines whether to save the generated image to the local filesystem.

- Default: `false`

## generateCharacterSpritesheet Options

### `states` (array of strings)

Specifies the animation states to generate for the character.

- Default: `['idle', 'walk', 'run', 'attack']`
- Example: `['idle', 'walk', 'jump', 'attack', 'die']`

### `framesPerState` (number)

Sets the number of frames for each animation state.

- Default: `6`

### `padding` (number)

Defines the padding between sprites in the generated spritesheet.

- Default: `1`

### `direction` (string)

Specifies the base direction the character should face.

- Default: `'right'`
- Example: `'left'`

Example usage:

```javascript
const spritesheet = await generateCharacterSpritesheet("a knight in shining armor", {
  states: ['idle', 'walk', 'attack', 'defend'],
  framesPerState: 8,
  size: '2048x2048',
  style: 'pixel-art',
  direction: 'right',
  save: true
});
```

## generateLandscapeSprite Options

### `timeOfDay` (string)

Sets the time of day for the landscape scene.

- Default: `'day'`
- Options: `'day'`, `'night'`, `'sunset'`, `'dawn'`

### `weather` (string)

Specifies the weather conditions for the landscape.

- Default: `'clear'`
- Options: `'clear'`, `'rainy'`, `'foggy'`, `'snowy'`

### `perspective` (string)

Defines the perspective of the landscape scene.

- Default: `'side-scrolling'`
- Options: `'side-scrolling'`, `'top-down'`, `'isometric'`

### `removeBackground` (boolean)

Determines whether to remove the background from the generated image.

- Default: `false`

### `backgroundColor` (string)

Specifies the background color to be removed when `removeBackground` is true.

- Format: CSS color (e.g., `'#FFFFFF'`)
- Only applicable when `removeBackground` is `true`

### `colorThreshold` (number)

Sets the threshold for color removal when using `removeBackground`.

- Default: `0.1`
- Range: `0` to `1`
- Only applicable when `removeBackground` is `true`

Example usage:

```javascript
const landscape = await generateLandscapeSprite("a lush forest with a waterfall", {
  size: '2048x1024',
  style: 'hand-drawn',
  timeOfDay: 'sunset',
  weather: 'clear',
  perspective: 'side-scrolling',
  removeBackground: true,
  backgroundColor: '#FFFFFF',
  colorThreshold: 0.2,
  save: true
});
```

## generateEnvironmentSprites Options

### `elements` (number)

Specifies the number of different environment elements to generate.

- Default: `4`

### `theme` (string)

Sets the theme for the environment tileset.

- Default: `'fantasy'`
- Example: `'sci-fi'`, `'medieval'`, `'modern'`

Example usage:

```javascript
const environmentSprites = await generateEnvironmentSprites("space station interior", {
  elements: 6,
  size: '1024x1024',
  style: '3d',
  padding: 2,
  theme: 'sci-fi',
  save: true
});
```

## Effect of Options on Generated Sprites

- **Size**: Larger sizes produce more detailed sprites but may take longer to generate.
- **Style**: Different styles can dramatically change the look of your sprites, from pixelated to realistic.
- **States and Frames**: More states and frames result in smoother animations but larger spritesheets.
- **Time of Day and Weather**: These options affect the lighting and atmosphere of landscape sprites.
- **Perspective**: Changes how the environment is viewed, impacting game design and level layout.
- **Remove Background**: Useful for creating sprites with transparent backgrounds for easy integration into games.

By adjusting these options, you can fine-tune the output of SpriteAI to match your game's visual style and technical requirements.

</response>