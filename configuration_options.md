Here's the new documentation page content for "configuration_options.md":

<response>
# Configuration Options

This guide explains all configuration options available in the SpriteAI library. We'll cover the options for `generateCharacterSpritesheet` and `generateLandscapeSprite`, including size, style, states, and other customizable parameters.

## generateCharacterSpritesheet

The `generateCharacterSpritesheet` function creates a character spritesheet based on a given description and configuration options. Here are the available options:

### Options

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| states | array | `['idle', 'walk', 'run', 'attack']` | Animation states to generate |
| framesPerState | number | 6 | Number of frames per animation state |
| size | string | '1024x1024' | Output size of the spritesheet |
| style | string | 'pixel-art' | Art style of the character |
| padding | number | 1 | Padding between sprites |
| direction | string | 'right' | Base direction of the character |
| save | boolean | false | Whether to save the generated image |

### Example Usage

```javascript
const result = await generateCharacterSpritesheet("a cute cat warrior", {
  states: ['idle', 'walk', 'run', 'attack', 'jump'],
  framesPerState: 8,
  size: '2048x2048',
  style: 'vector',
  padding: 2,
  direction: 'left',
  save: true
});
```

### How Configuration Affects Output

- **states**: Determines the number of rows in the spritesheet, with each row representing a different animation state.
- **framesPerState**: Sets the number of columns in the spritesheet, affecting the smoothness of animations.
- **size**: Influences the overall resolution and detail of the spritesheet.
- **style**: Changes the visual appearance of the character (e.g., pixel-art vs. vector).
- **padding**: Adds space between individual sprite frames, useful for preventing bleed during rendering.
- **direction**: Affects the initial facing direction of the character in the spritesheet.
- **save**: When true, saves the generated spritesheet to the local filesystem.

## generateLandscapeSprite

The `generateLandscapeSprite` function creates a landscape sprite based on a given description and configuration options. Here are the available options:

### Options

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| size | string | '1024x1024' | Output size of the landscape sprite |
| style | string | 'pixel-art' | Art style of the landscape |
| timeOfDay | string | 'day' | Time of day setting (day, night, sunset, dawn) |
| weather | string | 'clear' | Weather conditions (clear, rainy, foggy, snowy) |
| perspective | string | 'side-scrolling' | Perspective of the landscape (side-scrolling, top-down, isometric) |
| save | boolean | false | Whether to save the generated image |
| removeBackground | boolean | false | Whether to remove the background |
| backgroundColor | string | '#FFFFFF' | Background color to remove (if removeBackground is true) |
| colorThreshold | number | 0.1 | Color threshold for background removal |

### Example Usage

```javascript
const result = await generateLandscapeSprite("a lush forest with a winding river", {
  size: '2048x1024',
  style: 'vector',
  timeOfDay: 'sunset',
  weather: 'foggy',
  perspective: 'isometric',
  save: true,
  removeBackground: true,
  backgroundColor: '#E0E0E0',
  colorThreshold: 0.2
});
```

### How Configuration Affects Output

- **size**: Determines the dimensions of the generated landscape sprite.
- **style**: Influences the visual style of the landscape (e.g., pixel-art, vector).
- **timeOfDay**: Affects the lighting and color palette of the scene.
- **weather**: Adds weather effects to the landscape, changing its appearance and mood.
- **perspective**: Changes the viewpoint of the landscape, affecting its layout and depth.
- **save**: When true, saves the generated landscape sprite to the local filesystem.
- **removeBackground**: When true, attempts to remove the background color from the sprite.
- **backgroundColor**: Specifies the color to be removed when removeBackground is true.
- **colorThreshold**: Adjusts the sensitivity of background removal (higher values remove more colors).

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

By understanding and utilizing these configuration options, you can create highly customized and diverse sprites and landscapes for your game development needs using the SpriteAI library.
</response># Configuration Options

This guide explains all configuration options available in the SpriteAI library. We'll cover the options for `generateCharacterSpritesheet` and `generateLandscapeSprite`, including size, style, states, and other customizable parameters.

## generateCharacterSpritesheet

The `generateCharacterSpritesheet` function creates a character spritesheet based on a given description and configuration options. Here are the available options:

### Options

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| states | array | `['idle', 'walk', 'run', 'attack']` | Animation states to generate |
| framesPerState | number | 6 | Number of frames per animation state |
| size | string | '1024x1024' | Output size of the spritesheet |
| style | string | 'pixel-art' | Art style of the character |
| padding | number | 1 | Padding between sprites |
| direction | string | 'right' | Base direction of the character |
| save | boolean | false | Whether to save the generated image |

### Example Usage

```javascript
const result = await generateCharacterSpritesheet("a cute cat warrior", {
  states: ['idle', 'walk', 'run', 'attack', 'jump'],
  framesPerState: 8,
  size: '2048x2048',
  style: 'vector',
  padding: 2,
  direction: 'left',
  save: true
});
```

### How Configuration Affects Output

- **states**: Determines the number of rows in the spritesheet, with each row representing a different animation state.
- **framesPerState**: Sets the number of columns in the spritesheet, affecting the smoothness of animations.
- **size**: Influences the overall resolution and detail of the spritesheet.
- **style**: Changes the visual appearance of the character (e.g., pixel-art vs. vector).
- **padding**: Adds space between individual sprite frames, useful for preventing bleed during rendering.
- **direction**: Affects the initial facing direction of the character in the spritesheet.
- **save**: When true, saves the generated spritesheet to the local filesystem.

## generateLandscapeSprite

The `generateLandscapeSprite` function creates a landscape sprite based on a given description and configuration options. Here are the available options:

### Options

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| size | string | '1024x1024' | Output size of the landscape sprite |
| style | string | 'pixel-art' | Art style of the landscape |
| timeOfDay | string | 'day' | Time of day setting (day, night, sunset, dawn) |
| weather | string | 'clear' | Weather conditions (clear, rainy, foggy, snowy) |
| perspective | string | 'side-scrolling' | Perspective of the landscape (side-scrolling, top-down, isometric) |
| save | boolean | false | Whether to save the generated image |
| removeBackground | boolean | false | Whether to remove the background |
| backgroundColor | string | '#FFFFFF' | Background color to remove (if removeBackground is true) |
| colorThreshold | number | 0.1 | Color threshold for background removal |

### Example Usage

```javascript
const result = await generateLandscapeSprite("a lush forest with a winding river", {
  size: '2048x1024',
  style: 'vector',
  timeOfDay: 'sunset',
  weather: 'foggy',
  perspective: 'isometric',
  save: true,
  removeBackground: true,
  backgroundColor: '#E0E0E0',
  colorThreshold: 0.2
});
```

### How Configuration Affects Output

- **size**: Determines the dimensions of the generated landscape sprite.
- **style**: Influences the visual style of the landscape (e.g., pixel-art, vector).
- **timeOfDay**: Affects the lighting and color palette of the scene.
- **weather**: Adds weather effects to the landscape, changing its appearance and mood.
- **perspective**: Changes the viewpoint of the landscape, affecting its layout and depth.
- **save**: When true, saves the generated landscape sprite to the local filesystem.
- **removeBackground**: When true, attempts to remove the background color from the sprite.
- **backgroundColor**: Specifies the color to be removed when removeBackground is true.
- **colorThreshold**: Adjusts the sensitivity of background removal (higher values remove more colors).

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

By understanding and utilizing these configuration options, you can create highly customized and diverse sprites and landscapes for your game development needs using the SpriteAI library.