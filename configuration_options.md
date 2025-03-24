<response>

# Configuration Options

This page provides a comprehensive guide to all configuration options available in the SpriteAI library. Understanding these options will help you customize the sprite generation process to suit your specific needs.

## Character Spritesheet Configuration

The `generateCharacterSpritesheet` function accepts the following configuration options:

### states
- **Type**: Array of strings
- **Default**: `['idle', 'walk', 'run', 'attack']`
- **Description**: Defines the animation states to generate for the character. Each state will be represented as a row in the resulting spritesheet.

### framesPerState
- **Type**: Number
- **Default**: `6`
- **Description**: Specifies the number of frames to generate for each animation state. This determines the number of columns in each row of the spritesheet.

### size
- **Type**: String
- **Default**: `'1024x1024'`
- **Description**: Sets the dimensions of the output image. Format is 'widthxheight' in pixels.

### style
- **Type**: String
- **Default**: `'pixel-art'`
- **Description**: Defines the art style for the generated sprites. Options include 'pixel-art', 'vector', '3d', 'hand-drawn', and 'anime'.

### padding
- **Type**: Number
- **Default**: `1`
- **Description**: Specifies the padding between individual sprites in the spritesheet.

### direction
- **Type**: String
- **Default**: `'right'`
- **Description**: Sets the base direction the character is facing in the spritesheet.

### save
- **Type**: Boolean
- **Default**: `false`
- **Description**: When set to `true`, the generated spritesheet will be saved to the local filesystem in the `assets` directory.

Example usage:

```javascript
const result = await generateCharacterSpritesheet("a medieval knight", {
  states: ['idle', 'walk', 'attack', 'defend'],
  framesPerState: 8,
  size: '2048x2048',
  style: 'pixel-art',
  padding: 2,
  direction: 'left',
  save: true
});
```

## Environment Sprites Configuration

The `generateEnvironmentSprites` function accepts the following configuration options:

### elements
- **Type**: Number
- **Default**: `4`
- **Description**: Specifies the number of distinct environment elements to generate.

### size
- **Type**: String
- **Default**: `'1024x1024'`
- **Description**: Sets the dimensions of the output image. Format is 'widthxheight' in pixels.

### style
- **Type**: String
- **Default**: `'pixel-art'`
- **Description**: Defines the art style for the generated environment sprites.

### padding
- **Type**: Number
- **Default**: `1`
- **Description**: Specifies the padding between individual elements in the tileset.

### theme
- **Type**: String
- **Default**: `'fantasy'`
- **Description**: Sets the overall theme for the environment sprites.

### save
- **Type**: Boolean
- **Default**: `false`
- **Description**: When set to `true`, the generated tileset will be saved to the local filesystem in the `assets` directory.

Example usage:

```javascript
const result = await generateEnvironmentSprites("forest", {
  elements: 6,
  size: '2048x2048',
  style: 'hand-drawn',
  padding: 2,
  theme: 'enchanted',
  save: true
});
```

## Landscape Sprite Configuration

The `generateLandscapeSprite` function accepts the following configuration options:

### size
- **Type**: String
- **Default**: `'1024x1024'`
- **Description**: Sets the dimensions of the output image. Format is 'widthxheight' in pixels.

### style
- **Type**: String
- **Default**: `'pixel-art'`
- **Description**: Defines the art style for the generated landscape sprite.

### timeOfDay
- **Type**: String
- **Default**: `'day'`
- **Description**: Specifies the time of day for the landscape. Options include 'day', 'night', 'sunset', and 'dawn'.

### weather
- **Type**: String
- **Default**: `'clear'`
- **Description**: Sets the weather conditions for the landscape. Options include 'clear', 'rainy', 'foggy', and 'snowy'.

### perspective
- **Type**: String
- **Default**: `'side-scrolling'`
- **Description**: Defines the perspective of the landscape. Options include 'side-scrolling', 'top-down', and 'isometric'.

### save
- **Type**: Boolean
- **Default**: `false`
- **Description**: When set to `true`, the generated landscape sprite will be saved to the local filesystem in the `assets` directory.

### removeBackground
- **Type**: Boolean
- **Default**: `false`
- **Description**: When set to `true`, attempts to remove the background from the generated image.

### backgroundColor
- **Type**: String
- **Default**: `'#FFFFFF'`
- **Description**: Specifies the background color to be removed when `removeBackground` is `true`.

### colorThreshold
- **Type**: Number
- **Default**: `0.1`
- **Description**: Sets the threshold for color difference when removing the background. A lower value means stricter color matching.

Example usage:

```javascript
const result = await generateLandscapeSprite("mountain range", {
  size: '2048x1024',
  style: 'pixel-art',
  timeOfDay: 'sunset',
  weather: 'clear',
  perspective: 'side-scrolling',
  save: true,
  removeBackground: true,
  backgroundColor: '#FFFFFF',
  colorThreshold: 0.05
});
```

By carefully adjusting these configuration options, you can fine-tune the sprite generation process to create assets that perfectly match your game's visual style and requirements.

</response># Configuration Options

This page provides a comprehensive guide to all configuration options available in the SpriteAI library. Understanding these options will help you customize the sprite generation process to suit your specific needs.

## Character Spritesheet Configuration

The `generateCharacterSpritesheet` function accepts the following configuration options:

### states
- **Type**: Array of strings
- **Default**: `['idle', 'walk', 'run', 'attack']`
- **Description**: Defines the animation states to generate for the character. Each state will be represented as a row in the resulting spritesheet.

### framesPerState
- **Type**: Number
- **Default**: `6`
- **Description**: Specifies the number of frames to generate for each animation state. This determines the number of columns in each row of the spritesheet.

### size
- **Type**: String
- **Default**: `'1024x1024'`
- **Description**: Sets the dimensions of the output image. Format is 'widthxheight' in pixels.

### style
- **Type**: String
- **Default**: `'pixel-art'`
- **Description**: Defines the art style for the generated sprites. Options include 'pixel-art', 'vector', '3d', 'hand-drawn', and 'anime'.

### padding
- **Type**: Number
- **Default**: `1`
- **Description**: Specifies the padding between individual sprites in the spritesheet.

### direction
- **Type**: String
- **Default**: `'right'`
- **Description**: Sets the base direction the character is facing in the spritesheet.

### save
- **Type**: Boolean
- **Default**: `false`
- **Description**: When set to `true`, the generated spritesheet will be saved to the local filesystem in the `assets` directory.

Example usage:

```javascript
const result = await generateCharacterSpritesheet("a medieval knight", {
  states: ['idle', 'walk', 'attack', 'defend'],
  framesPerState: 8,
  size: '2048x2048',
  style: 'pixel-art',
  padding: 2,
  direction: 'left',
  save: true
});
```

## Environment Sprites Configuration

The `generateEnvironmentSprites` function accepts the following configuration options:

### elements
- **Type**: Number
- **Default**: `4`
- **Description**: Specifies the number of distinct environment elements to generate.

### size
- **Type**: String
- **Default**: `'1024x1024'`
- **Description**: Sets the dimensions of the output image. Format is 'widthxheight' in pixels.

### style
- **Type**: String
- **Default**: `'pixel-art'`
- **Description**: Defines the art style for the generated environment sprites.

### padding
- **Type**: Number
- **Default**: `1`
- **Description**: Specifies the padding between individual elements in the tileset.

### theme
- **Type**: String
- **Default**: `'fantasy'`
- **Description**: Sets the overall theme for the environment sprites.

### save
- **Type**: Boolean
- **Default**: `false`
- **Description**: When set to `true`, the generated tileset will be saved to the local filesystem in the `assets` directory.

Example usage:

```javascript
const result = await generateEnvironmentSprites("forest", {
  elements: 6,
  size: '2048x2048',
  style: 'hand-drawn',
  padding: 2,
  theme: 'enchanted',
  save: true
});
```

## Landscape Sprite Configuration

The `generateLandscapeSprite` function accepts the following configuration options:

### size
- **Type**: String
- **Default**: `'1024x1024'`
- **Description**: Sets the dimensions of the output image. Format is 'widthxheight' in pixels.

### style
- **Type**: String
- **Default**: `'pixel-art'`
- **Description**: Defines the art style for the generated landscape sprite.

### timeOfDay
- **Type**: String
- **Default**: `'day'`
- **Description**: Specifies the time of day for the landscape. Options include 'day', 'night', 'sunset', and 'dawn'.

### weather
- **Type**: String
- **Default**: `'clear'`
- **Description**: Sets the weather conditions for the landscape. Options include 'clear', 'rainy', 'foggy', and 'snowy'.

### perspective
- **Type**: String
- **Default**: `'side-scrolling'`
- **Description**: Defines the perspective of the landscape. Options include 'side-scrolling', 'top-down', and 'isometric'.

### save
- **Type**: Boolean
- **Default**: `false`
- **Description**: When set to `true`, the generated landscape sprite will be saved to the local filesystem in the `assets` directory.

### removeBackground
- **Type**: Boolean
- **Default**: `false`
- **Description**: When set to `true`, attempts to remove the background from the generated image.

### backgroundColor
- **Type**: String
- **Default**: `'#FFFFFF'`
- **Description**: Specifies the background color to be removed when `removeBackground` is `true`.

### colorThreshold
- **Type**: Number
- **Default**: `0.1`
- **Description**: Sets the threshold for color difference when removing the background. A lower value means stricter color matching.

Example usage:

```javascript
const result = await generateLandscapeSprite("mountain range", {
  size: '2048x1024',
  style: 'pixel-art',
  timeOfDay: 'sunset',
  weather: 'clear',
  perspective: 'side-scrolling',
  save: true,
  removeBackground: true,
  backgroundColor: '#FFFFFF',
  colorThreshold: 0.05
});
```

By carefully adjusting these configuration options, you can fine-tune the sprite generation process to create assets that perfectly match your game's visual style and requirements.