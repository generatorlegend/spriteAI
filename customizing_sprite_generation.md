<response>

# Customizing Sprite Generation in SpriteAI

SpriteAI offers powerful customization options for generating both character spritesheets and landscape sprites. This guide will walk you through the various options available and how to use them effectively.

## Character Spritesheets

The `generateCharacterSpritesheet` function allows you to create detailed character spritesheets with multiple animation states. Here's how you can customize your sprite generation:

### Basic Usage

```javascript
import { generateCharacterSpritesheet } from 'spriteAI';

const result = await generateCharacterSpritesheet('a medieval knight in armor');
```

### Customization Options

You can pass an options object to customize various aspects of the spritesheet:

```javascript
const options = {
  states: ['idle', 'walk', 'run', 'attack'],
  framesPerState: 6,
  size: '1024x1024',
  style: 'pixel-art',
  padding: 1,
  direction: 'right',
  save: true
};

const result = await generateCharacterSpritesheet('a medieval knight in armor', options);
```

#### Available Options:

- `states`: An array of animation states (default: `['idle', 'walk', 'run', 'attack']`)
- `framesPerState`: Number of frames for each animation state (default: 6)
- `size`: Output size of the spritesheet (default: '1024x1024')
- `style`: Art style of the sprite (default: 'pixel-art')
- `padding`: Padding between sprites (default: 1)
- `direction`: Base direction of the character (default: 'right')
- `save`: Whether to save the generated image (default: false)

### Fetching Available Options

You can use these helper functions to get the available animation states and sprite styles:

```javascript
import { fetchAvailableAnimationStates, fetchAvailableSpriteStyles } from 'spriteAI';

const states = await fetchAvailableAnimationStates();
const styles = await fetchAvailableSpriteStyles();
```

## Landscape Sprites

The `generateLandscapeSprite` function allows you to create detailed landscape scenes for game backgrounds. Here's how you can customize your landscape generation:

### Basic Usage

```javascript
import { generateLandscapeSprite } from 'spriteAI';

const result = await generateLandscapeSprite('a lush forest with a river');
```

### Customization Options

You can pass an options object to customize various aspects of the landscape:

```javascript
const options = {
  size: '1024x1024',
  style: 'pixel-art',
  timeOfDay: 'sunset',
  weather: 'foggy',
  perspective: 'side-scrolling',
  save: true,
  removeBackground: true,
  backgroundColor: '#FFFFFF',
  colorThreshold: 0.1
};

const result = await generateLandscapeSprite('a lush forest with a river', options);
```

#### Available Options:

- `size`: Output size of the landscape (default: '1024x1024')
- `style`: Art style of the landscape (default: 'pixel-art')
- `timeOfDay`: Time setting (options: 'day', 'night', 'sunset', 'dawn'; default: 'day')
- `weather`: Weather conditions (options: 'clear', 'rainy', 'foggy', 'snowy'; default: 'clear')
- `perspective`: Viewport perspective (options: 'side-scrolling', 'top-down', 'isometric'; default: 'side-scrolling')
- `save`: Whether to save the generated image (default: false)
- `removeBackground`: Whether to remove the background (default: false)
- `backgroundColor`: Color to be removed if removeBackground is true (default: '#FFFFFF')
- `colorThreshold`: Threshold for color removal (default: 0.1)

## Environment Sprites

The `generateEnvironmentSprites` function allows you to create tilesets of environmental elements. Here's how you can customize your environment sprite generation:

### Basic Usage

```javascript
import { generateEnvironmentSprites } from 'spriteAI';

const result = await generateEnvironmentSprites('forest');
```

### Customization Options

You can pass an options object to customize various aspects of the environment tileset:

```javascript
const options = {
  elements: 6,
  size: '1024x1024',
  style: 'pixel-art',
  padding: 1,
  theme: 'fantasy',
  save: true
};

const result = await generateEnvironmentSprites('forest', options);
```

#### Available Options:

- `elements`: Number of different elements in the tileset (default: 4)
- `size`: Output size of the tileset (default: '1024x1024')
- `style`: Art style of the sprites (default: 'pixel-art')
- `padding`: Padding between elements (default: 1)
- `theme`: Theme of the environment (default: 'fantasy')
- `save`: Whether to save the generated image (default: false)

## Best Practices

1. **Consistent Style**: When generating multiple sprites for a game, maintain a consistent style across all assets by using the same `style` option.

2. **Optimal Size**: Choose an appropriate size based on your game's resolution and scaling needs. Larger sizes offer more detail but require more processing time.

3. **Animation Frames**: For smooth animations, use at least 4-6 frames per state in character spritesheets.

4. **Background Removal**: When generating landscape sprites, use the `removeBackground` option if you need transparent backgrounds for layering in your game.

5. **Save Option**: Use the `save` option during development to easily access and review generated sprites.

6. **Themed Environments**: When generating environment sprites, use the `theme` option to ensure consistency with your game's overall aesthetic.

By leveraging these customization options, you can generate sprites that perfectly fit your game's needs and style. Experiment with different combinations to achieve the best results for your project.

</response>