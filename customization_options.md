<response>

# Customization Options in SpriteAI

SpriteAI offers a wide range of customization options to help you create unique and diverse sprites for your game development needs. This guide will walk you through the various options available for customizing character spritesheets, landscape sprites, and environment sprites.

## Character Spritesheets

The `generateCharacterSpritesheet` function allows you to create customized character spritesheets with various animation states. Here are the available options:

### Basic Options

- `description`: A string describing the character you want to generate.
- `states`: An array of animation states (default: `['idle', 'walk', 'run', 'attack']`).
- `framesPerState`: Number of frames for each animation state (default: 6).
- `size`: Output size of the spritesheet (default: '1024x1024').
- `style`: Art style of the sprite (default: 'pixel-art').
- `padding`: Padding between sprites (default: 1).
- `direction`: Base direction of the character (default: 'right').

### Example Usage

```javascript
const result = await generateCharacterSpritesheet("a cute robot", {
  states: ['idle', 'walk', 'run', 'attack', 'jump'],
  framesPerState: 8,
  size: '2048x2048',
  style: 'vector',
  padding: 2,
  direction: 'left'
});
```

### Available Animation States

You can use the `fetchAvailableAnimationStates` function to get a list of supported animation states:

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
- `style`: Art style of the sprite (default: 'pixel-art').
- `timeOfDay`: Time of day setting (default: 'day', options: 'day', 'night', 'sunset', 'dawn').
- `weather`: Weather conditions (default: 'clear', options: 'clear', 'rainy', 'foggy', 'snowy').
- `perspective`: Perspective of the landscape (default: 'side-scrolling', options: 'side-scrolling', 'top-down', 'isometric').
- `save`: Whether to save the generated image (default: false).

### Advanced Options

- `removeBackground`: Set to true to remove the background (default: false).
- `backgroundColor`: The background color to remove (default: '#FFFFFF').
- `colorThreshold`: Threshold for color removal (default: 0.1).

### Example Usage

```javascript
const result = await generateLandscapeSprite("a lush forest with a waterfall", {
  size: '2048x1024',
  style: 'hand-drawn',
  timeOfDay: 'sunset',
  weather: 'foggy',
  perspective: 'isometric',
  save: true,
  removeBackground: true,
  backgroundColor: '#F0F0F0',
  colorThreshold: 0.2
});
```

## Environment Sprites

The `generateEnvironmentSprites` function allows you to create customized environment sprites. Here are the available options:

### Basic Options

- `description`: A string describing the environment you want to generate.
- `elements`: Number of different elements to generate (default: 4).
- `size`: Output size of the tileset (default: '1024x1024').
- `style`: Art style of the sprites (default: 'pixel-art').
- `padding`: Padding between elements (default: 1).
- `theme`: Theme of the environment (default: 'fantasy').

### Example Usage

```javascript
const result = await generateEnvironmentSprites("medieval castle", {
  elements: 6,
  size: '2048x2048',
  style: '3d',
  padding: 2,
  theme: 'medieval'
});
```

## Tips for Creating Unique and Diverse Sprites

1. Experiment with different art styles to achieve various visual effects.
2. Combine different weather and time of day settings for landscape sprites to create diverse environments.
3. Use the `removeBackground` option for landscape sprites to create sprites that can be easily layered in your game.
4. Mix and match different animation states for character spritesheets to create unique character behaviors.
5. Adjust the `framesPerState` option to create smoother or more stylized animations.
6. Utilize the `perspective` option for landscape sprites to create environments that fit your game's viewpoint.
7. Experiment with different themes for environment sprites to create cohesive game worlds.

By leveraging these customization options, you can create a wide variety of sprites tailored to your specific game development needs using SpriteAI.

</response># Customization Options in SpriteAI

SpriteAI offers a wide range of customization options to help you create unique and diverse sprites for your game development needs. This guide will walk you through the various options available for customizing character spritesheets, landscape sprites, and environment sprites.

## Character Spritesheets

The `generateCharacterSpritesheet` function allows you to create customized character spritesheets with various animation states. Here are the available options:

### Basic Options

- `description`: A string describing the character you want to generate.
- `states`: An array of animation states (default: `['idle', 'walk', 'run', 'attack']`).
- `framesPerState`: Number of frames for each animation state (default: 6).
- `size`: Output size of the spritesheet (default: '1024x1024').
- `style`: Art style of the sprite (default: 'pixel-art').
- `padding`: Padding between sprites (default: 1).
- `direction`: Base direction of the character (default: 'right').

### Example Usage

```javascript
const result = await generateCharacterSpritesheet("a cute robot", {
  states: ['idle', 'walk', 'run', 'attack', 'jump'],
  framesPerState: 8,
  size: '2048x2048',
  style: 'vector',
  padding: 2,
  direction: 'left'
});
```

### Available Animation States

You can use the `fetchAvailableAnimationStates` function to get a list of supported animation states:

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
- `style`: Art style of the sprite (default: 'pixel-art').
- `timeOfDay`: Time of day setting (default: 'day', options: 'day', 'night', 'sunset', 'dawn').
- `weather`: Weather conditions (default: 'clear', options: 'clear', 'rainy', 'foggy', 'snowy').
- `perspective`: Perspective of the landscape (default: 'side-scrolling', options: 'side-scrolling', 'top-down', 'isometric').
- `save`: Whether to save the generated image (default: false).

### Advanced Options

- `removeBackground`: Set to true to remove the background (default: false).
- `backgroundColor`: The background color to remove (default: '#FFFFFF').
- `colorThreshold`: Threshold for color removal (default: 0.1).

### Example Usage

```javascript
const result = await generateLandscapeSprite("a lush forest with a waterfall", {
  size: '2048x1024',
  style: 'hand-drawn',
  timeOfDay: 'sunset',
  weather: 'foggy',
  perspective: 'isometric',
  save: true,
  removeBackground: true,
  backgroundColor: '#F0F0F0',
  colorThreshold: 0.2
});
```

## Environment Sprites

The `generateEnvironmentSprites` function allows you to create customized environment sprites. Here are the available options:

### Basic Options

- `description`: A string describing the environment you want to generate.
- `elements`: Number of different elements to generate (default: 4).
- `size`: Output size of the tileset (default: '1024x1024').
- `style`: Art style of the sprites (default: 'pixel-art').
- `padding`: Padding between elements (default: 1).
- `theme`: Theme of the environment (default: 'fantasy').

### Example Usage

```javascript
const result = await generateEnvironmentSprites("medieval castle", {
  elements: 6,
  size: '2048x2048',
  style: '3d',
  padding: 2,
  theme: 'medieval'
});
```

## Tips for Creating Unique and Diverse Sprites

1. Experiment with different art styles to achieve various visual effects.
2. Combine different weather and time of day settings for landscape sprites to create diverse environments.
3. Use the `removeBackground` option for landscape sprites to create sprites that can be easily layered in your game.
4. Mix and match different animation states for character spritesheets to create unique character behaviors.
5. Adjust the `framesPerState` option to create smoother or more stylized animations.
6. Utilize the `perspective` option for landscape sprites to create environments that fit your game's viewpoint.
7. Experiment with different themes for environment sprites to create cohesive game worlds.

By leveraging these customization options, you can create a wide variety of sprites tailored to your specific game development needs using SpriteAI.