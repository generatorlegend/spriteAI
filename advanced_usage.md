# Advanced Usage Guide for SpriteAI

## Table of Contents

1. [Customizing Animation States](#customizing-animation-states)
2. [Working with Different Art Styles](#working-with-different-art-styles)
3. [Optimizing Sprite Generation for Performance](#optimizing-sprite-generation-for-performance)
4. [Integrating SpriteAI Outputs into Game Development Workflows](#integrating-spriteai-outputs-into-game-development-workflows)
5. [Advanced Examples and Best Practices](#advanced-examples-and-best-practices)

## Customizing Animation States

SpriteAI offers powerful customization options for animation states. By default, the library generates sprites for 'idle', 'walk', 'run', and 'attack' states, but you can easily modify this to suit your specific game requirements.

### Fetching Available Animation States

To see what animation states are available, use the `fetchAvailableAnimationStates` function:

```javascript
import { fetchAvailableAnimationStates } from 'spriteAI';

const availableStates = await fetchAvailableAnimationStates();
console.log(availableStates);
// Output: ['idle', 'walk', 'run', 'attack', 'jump', 'fall', 'hurt', 'die']
```

### Specifying Custom Animation States

When generating a character spritesheet, you can specify custom animation states:

```javascript
import { generateCharacterSpritesheet } from 'spriteAI';

const result = await generateCharacterSpritesheet('warrior', {
  states: ['idle', 'attack', 'defend', 'cast_spell'],
  framesPerState: 8
});
```

This will generate a spritesheet with four rows, each representing the specified animation state with 8 frames per state.

## Working with Different Art Styles

SpriteAI supports various art styles to cater to different game aesthetics. You can specify the style when generating sprites.

### Available Sprite Styles

To fetch the available sprite styles:

```javascript
import { fetchAvailableSpriteStyles } from 'spriteAI';

const availableStyles = await fetchAvailableSpriteStyles();
console.log(availableStyles);
// Output: ['pixel-art', 'vector', '3d', 'hand-drawn', 'anime']
```

### Generating Sprites in Different Styles

When generating character spritesheets or environment sprites, specify the desired style:

```javascript
const pixelArtCharacter = await generateCharacterSpritesheet('ninja', {
  style: 'pixel-art'
});

const animeEnvironment = await generateEnvironmentSprites('forest', {
  style: 'anime',
  theme: 'fantasy'
});
```

## Optimizing Sprite Generation for Performance

To optimize sprite generation for performance, consider the following strategies:

1. **Limit the number of frames**: Reduce `framesPerState` for less critical animations.
2. **Optimize image size**: Use smaller dimensions for mobile games or when performance is crucial.
3. **Batch generate sprites**: Generate multiple sprites in one session to reduce API calls.

Example of optimized sprite generation:

```javascript
const optimizedCharacter = await generateCharacterSpritesheet('archer', {
  states: ['idle', 'attack'],
  framesPerState: 4,
  size: '512x512'
});
```

## Integrating SpriteAI Outputs into Game Development Workflows

SpriteAI generates spritesheets that can be easily integrated into various game engines and frameworks. Here's how you can work with the output:

1. **Accessing the spritesheet**:
   ```javascript
   const { spritesheet, metadata } = await generateCharacterSpritesheet('mage');
   ```

2. **Using the metadata**: The `metadata` object contains crucial information about the spritesheet, including frame data for each animation state.

3. **Implementing in a game engine**:
   ```javascript
   // Pseudo-code for implementing in a game engine
   const spriteTexture = loadTexture(result.spritesheet);
   const characterSprite = createSprite(spriteTexture);

   function animateCharacter(state) {
     const { startFrame, endFrame } = result.metadata.frameData[state];
     characterSprite.playAnimation(startFrame, endFrame);
   }

   // Usage
   animateCharacter('run');
   ```

## Advanced Examples and Best Practices

### Generating a Complex Character Set

```javascript
async function generateComplexCharacter(description) {
  const baseCharacter = await generateCharacterSpritesheet(description, {
    states: ['idle', 'walk', 'run', 'attack', 'defend'],
    framesPerState: 8,
    size: '1024x1024'
  });

  const specialMoves = await generateCharacterSpritesheet(`${description} special moves`, {
    states: ['cast_spell', 'ultimate_attack', 'dodge'],
    framesPerState: 10,
    size: '1024x1024'
  });

  return {
    base: baseCharacter,
    special: specialMoves
  };
}

const heroSet = await generateComplexCharacter('elemental wizard');
```

### Creating a Themed Environment Set

```javascript
async function generateThemedEnvironment(theme, elements) {
  const background = await generateLandscapeSprite(`${theme} landscape`, {
    perspective: 'side-scrolling',
    timeOfDay: 'day',
    weather: 'clear'
  });

  const environmentElements = await generateEnvironmentSprites(`${theme} elements`, {
    elements: elements,
    theme: theme
  });

  return {
    background: background,
    elements: environmentElements
  };
}

const forestTheme = await generateThemedEnvironment('enchanted forest', 6);
```

### Best Practices

1. **Consistent Art Direction**: When generating multiple assets, use consistent descriptions and styles to maintain a cohesive look.

2. **Iterative Refinement**: If the generated sprites don't meet your expectations, try refining your descriptions or adjusting parameters like `style` and `framesPerState`.

3. **Asset Management**: Implement a naming convention and folder structure for saved sprites to keep your project organized.

4. **Version Control**: Keep track of successful prompts and parameters that produce good results for future reference.

5. **Performance Considerations**: Balance the quality and quantity of generated sprites with your game's performance requirements, especially for mobile or web-based games.

By leveraging these advanced techniques and best practices, you can fully utilize the power of SpriteAI to streamline your game development process and create rich, diverse game assets efficiently.