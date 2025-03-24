# Customization Options in SpriteAI

SpriteAI offers a wide range of customization options for generating both character spritesheets and landscape sprites. This guide provides a comprehensive overview of all available options and how they affect the output.

## Character Spritesheets

The `generateCharacterSpritesheet` function allows you to create detailed character spritesheets with various animation states. Here are the customization options available:

### Basic Options

- `description` (string): A detailed description of the character you want to generate.
- `states` (array of strings): Animation states to generate. Default: `['idle', 'walk', 'run', 'attack']`
- `framesPerState` (number): Number of frames per animation state. Default: `6`
- `size` (string): Output size of the spritesheet. Default: `'1024x1024'`
- `style` (string): Art style of the character. Default: `'pixel-art'`
- `padding` (number): Padding between sprites in the spritesheet. Default: `1`
- `direction` (string): Base direction the character should face. Default: `'right'`

### Advanced Options

- `save` (boolean): Whether to save the generated spritesheet to the local filesystem. Default: `false`

### Example Usage

```javascript
const characterOptions = {
  states: ['idle', 'walk', 'run', 'jump', 'attack'],
  framesPerState: 8,
  size: '2048x2048',
  style: 'vector',
  padding: 2,
  direction: 'left',
  save: true
};

const result = await generateCharacterSpritesheet("a fierce warrior with glowing armor", characterOptions);
```

### How Options Affect Output

- **states**: Determines the number of rows in the spritesheet, with each row representing a different animation state.
- **framesPerState**: Affects the number of columns in the spritesheet, representing the frames for each animation.
- **size**: Influences the overall resolution and detail of the spritesheet.
- **style**: Changes the visual style of the character (e.g., pixel-art, vector, 3D).
- **padding**: Adjusts the space between individual sprite frames.
- **direction**: Affects the initial facing direction of the character in the spritesheet.

## Landscape Sprites

The `generateLandscapeSprite` function allows you to create detailed landscape scenes. Here are the customization options available:

### Basic Options

- `description` (string): A detailed description of the landscape scene you want to generate.
- `size` (string): Output size of the landscape sprite. Default: `'1024x1024'`
- `style` (string): Art style of the landscape. Default: `'pixel-art'`
- `timeOfDay` (string): Time of day setting. Options: `'day'`, `'night'`, `'sunset'`, `'dawn'`. Default: `'day'`
- `weather` (string): Weather conditions. Options: `'clear'`, `'rainy'`, `'foggy'`, `'snowy'`. Default: `'clear'`
- `perspective` (string): Perspective of the landscape. Options: `'side-scrolling'`, `'top-down'`, `'isometric'`. Default: `'side-scrolling'`

### Advanced Options

- `save` (boolean): Whether to save the generated landscape sprite to the local filesystem. Default: `false`
- `removeBackground` (boolean): Whether to remove the background color. Default: `false`
- `backgroundColor` (string): The background color to remove (if `removeBackground` is `true`). Default: `'#FFFFFF'`
- `colorThreshold` (number): The threshold for color removal (if `removeBackground` is `true`). Default: `0.1`

### Example Usage

```javascript
const landscapeOptions = {
  size: '2048x1024',
  style: 'pixel-art',
  timeOfDay: 'sunset',
  weather: 'foggy',
  perspective: 'isometric',
  save: true,
  removeBackground: true,
  backgroundColor: '#F0F0F0',
  colorThreshold: 0.2
};

const result = await generateLandscapeSprite("a mystical forest with ancient ruins", landscapeOptions);
```

### How Options Affect Output

- **size**: Influences the overall resolution and detail of the landscape sprite.
- **style**: Changes the visual style of the landscape (e.g., pixel-art, vector, 3D).
- **timeOfDay**: Affects the lighting and color palette of the scene.
- **weather**: Adds weather effects and changes the mood of the landscape.
- **perspective**: Determines the viewpoint and layout of the landscape elements.
- **removeBackground**: When true, attempts to remove the specified background color, useful for creating transparent sprites.

## Available Animation States and Styles

SpriteAI provides functions to fetch available animation states and sprite styles:

### Animation States

Use `fetchAvailableAnimationStates()` to get a list of supported animation states:

```javascript
const states = await fetchAvailableAnimationStates();
// Returns: ['idle', 'walk', 'run', 'attack', 'jump', 'fall', 'hurt', 'die']
```

### Sprite Styles

Use `fetchAvailableSpriteStyles()` to get a list of supported sprite styles:

```javascript
const styles = await fetchAvailableSpriteStyles();
// Returns: ['pixel-art', 'vector', '3d', 'hand-drawn', 'anime']
```

## Environment Sprites

The `generateEnvironmentSprites` function allows you to create tileset sprites for game environments:

### Basic Options

- `description` (string): A detailed description of the environment you want to generate.
- `elements` (number): Number of different elements in the tileset. Default: `4`
- `size` (string): Output size of the tileset. Default: `'1024x1024'`
- `style` (string): Art style of the environment. Default: `'pixel-art'`
- `padding` (number): Padding between elements in the tileset. Default: `1`
- `theme` (string): Theme of the environment. Default: `'fantasy'`

### Advanced Options

- `save` (boolean): Whether to save the generated tileset to the local filesystem. Default: `false`

### Example Usage

```javascript
const environmentOptions = {
  elements: 6,
  size: '2048x2048',
  style: 'vector',
  padding: 2,
  theme: 'sci-fi',
  save: true
};

const result = await generateEnvironmentSprites("a futuristic space station interior", environmentOptions);
```

### How Options Affect Output

- **elements**: Determines the number of unique environment pieces in the tileset.
- **size**: Influences the overall resolution and detail of the tileset.
- **style**: Changes the visual style of the environment elements.
- **padding**: Adjusts the space between individual tileset elements.
- **theme**: Affects the overall aesthetic and design direction of the environment pieces.

By understanding and utilizing these customization options, you can create a wide variety of character spritesheets, landscape sprites, and environment tilesets tailored to your specific game development needs.