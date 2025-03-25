# Customization Guide for SpriteAI

This guide explains how to customize sprite generation in SpriteAI. You'll learn how to adjust various parameters to achieve your desired results when creating character spritesheets, landscape sprites, and environment sprites.

## Table of Contents

1. [Character Spritesheets](#character-spritesheets)
2. [Landscape Sprites](#landscape-sprites)
3. [Environment Sprites](#environment-sprites)
4. [Tips for Achieving Desired Results](#tips-for-achieving-desired-results)

## Character Spritesheets

The `generateCharacterSpritesheet` function allows you to create customized character spritesheets. Here are the parameters you can adjust:

- `description`: A string describing the character you want to generate.
- `options`: An object containing various customization options:
  - `states`: An array of animation states (default: `['idle', 'walk', 'run', 'attack']`)
  - `framesPerState`: Number of frames per animation state (default: 6)
  - `size`: Output size of the spritesheet (default: '1024x1024')
  - `style`: Art style of the sprite (default: 'pixel-art')
  - `padding`: Padding between sprites (default: 1)
  - `direction`: Base direction of the character (default: 'right')

Example usage:

```javascript
const result = await generateCharacterSpritesheet("a cute robot", {
  states: ['idle', 'walk', 'run', 'jump'],
  framesPerState: 8,
  size: '2048x2048',
  style: 'vector',
  direction: 'left'
});
```

This will generate a vector-style spritesheet of a cute robot with 4 animation states (idle, walk, run, jump), 8 frames per state, facing left, in a 2048x2048 image.

## Landscape Sprites

The `generateLandscapeSprite` function allows you to create customized landscape sprites. Here are the parameters you can adjust:

- `description`: A string describing the landscape you want to generate.
- `options`: An object containing various customization options:
  - `size`: Output size of the sprite (default: '1024x1024')
  - `style`: Art style of the sprite (default: 'pixel-art')
  - `timeOfDay`: Time of day setting (default: 'day')
  - `weather`: Weather conditions (default: 'clear')
  - `perspective`: Perspective of the landscape (default: 'side-scrolling')
  - `save`: Whether to save the generated image (default: false)
  - `removeBackground`: Whether to remove the background (optional)
  - `backgroundColor`: Background color to remove (if removeBackground is true)
  - `colorThreshold`: Threshold for background color removal (if removeBackground is true)

Example usage:

```javascript
const result = await generateLandscapeSprite("a mystical forest", {
  size: '2048x1024',
  style: 'hand-drawn',
  timeOfDay: 'night',
  weather: 'foggy',
  perspective: 'isometric',
  removeBackground: true,
  backgroundColor: '#FFFFFF',
  colorThreshold: 0.1
});
```

This will generate a hand-drawn, isometric view of a mystical forest at night with foggy weather, removing the white background.

## Environment Sprites

The `generateEnvironmentSprites` function allows you to create customized environment sprites. Here are the parameters you can adjust:

- `description`: A string describing the environment you want to generate.
- `options`: An object containing various customization options:
  - `elements`: Number of different elements to generate (default: 4)
  - `size`: Output size of the tileset (default: '1024x1024')
  - `style`: Art style of the sprites (default: 'pixel-art')
  - `padding`: Padding between elements (default: 1)
  - `theme`: Theme of the environment (default: 'fantasy')

Example usage:

```javascript
const result = await generateEnvironmentSprites("desert oasis", {
  elements: 6,
  size: '2048x2048',
  style: '3d',
  theme: 'post-apocalyptic'
});
```

This will generate a 3D-style tileset of 6 different post-apocalyptic desert oasis elements in a 2048x2048 image.

## Tips for Achieving Desired Results

1. **Be specific in your descriptions**: The more detailed your description, the better the AI can understand and generate what you're looking for.

2. **Experiment with different styles**: Try various art styles to find the one that best fits your project's aesthetic.

3. **Adjust frame counts**: For character spritesheets, increasing the `framesPerState` can result in smoother animations, while decreasing it can be more suitable for simpler or retro-style games.

4. **Play with time and weather**: For landscape sprites, combining different times of day and weather conditions can create unique atmospheres for your game environments.

5. **Use the right perspective**: Choose the perspective that matches your game's viewpoint (e.g., side-scrolling for platformers, isometric for strategy games).

6. **Leverage background removal**: For landscape and environment sprites, use the `removeBackground` option to create sprites with transparent backgrounds, making them easier to integrate into your game.

7. **Iterate and refine**: Don't be afraid to generate multiple versions of a sprite, adjusting parameters each time until you get the desired result.

By leveraging these customization options and tips, you can create a wide variety of sprites tailored to your specific game development needs using SpriteAI.