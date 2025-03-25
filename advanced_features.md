# Advanced Features of SpriteAI

This guide covers advanced features of SpriteAI, including environment sprite generation, custom animation states, and complex sprite generation scenarios. Learn how to leverage these features to create more diverse and dynamic game assets.

## Environment Sprite Generation

SpriteAI now supports the generation of environment sprites, allowing you to create diverse game backgrounds and level elements quickly.

### Using `generateEnvironmentSprites`

The `generateEnvironmentSprites` function allows you to create a tileset of environment elements. Here's how to use it:

```javascript
import { generateEnvironmentSprites } from 'spriteAI';

const environmentSprites = await generateEnvironmentSprites('forest', {
  elements: 6,
  size: '1024x1024',
  style: 'pixel-art',
  padding: 2,
  theme: 'fantasy'
});
```

#### Parameters:

- `description`: A string describing the environment (e.g., 'forest', 'desert', 'space station')
- `options`: An object with the following properties:
  - `elements`: Number of distinct environment pieces to generate (default: 4)
  - `size`: Output size of the tileset (default: '1024x1024')
  - `style`: Art style of the sprites (default: 'pixel-art')
  - `padding`: Padding between elements in the tileset (default: 1)
  - `theme`: Overall theme of the environment (default: 'fantasy')

#### Return Value:

The function returns an object containing:

- `original`: URL of the originally generated image
- `tileset`: Base64-encoded string of the processed tileset
- `metadata`: Object containing information about the generated tileset

### Example: Creating a Diverse Forest Tileset

```javascript
const forestTileset = await generateEnvironmentSprites('dense forest with ancient ruins', {
  elements: 8,
  style: 'pixel-art',
  theme: 'mystical'
});

console.log(forestTileset.metadata);
// Use forestTileset.tileset to display or save the generated sprites
```

## Custom Animation States

SpriteAI allows you to define custom animation states for character spritesheets, giving you more control over the types of animations generated.

### Defining Custom States

When using the `generateCharacterSpritesheet` function, you can specify custom animation states:

```javascript
import { generateCharacterSpritesheet } from 'spriteAI';

const customStates = ['idle', 'walk', 'jump', 'attack', 'cast_spell'];

const characterSprites = await generateCharacterSpritesheet('wizard', {
  states: customStates,
  framesPerState: 8,
  style: 'pixel-art'
});
```

### Available Animation States

To see what animation states are available, you can use the `fetchAvailableAnimationStates` function:

```javascript
import { fetchAvailableAnimationStates } from 'spriteAI';

const availableStates = await fetchAvailableAnimationStates();
console.log(availableStates);
// Output: ['idle', 'walk', 'run', 'attack', 'jump', 'fall', 'hurt', 'die']
```

## Complex Sprite Generation Scenarios

SpriteAI can handle complex sprite generation scenarios by combining different features and options. Here are some advanced use cases:

### Multi-Directional Character Spritesheet

Generate a character spritesheet with multiple directions:

```javascript
const directions = ['left', 'right', 'up', 'down'];
const states = ['idle', 'walk'];

for (const direction of directions) {
  const spritesheet = await generateCharacterSpritesheet(`warrior facing ${direction}`, {
    states: states,
    direction: direction,
    size: '512x512'
  });
  
  // Process or save each directional spritesheet
  console.log(`Generated ${direction} facing spritesheet:`, spritesheet.metadata);
}
```

### Themed Environment Set

Create a cohesive set of environment sprites for a game level:

```javascript
const themes = ['entrance', 'main hall', 'treasure room', 'boss chamber'];

for (const theme of themes) {
  const environmentSet = await generateEnvironmentSprites(`ancient temple ${theme}`, {
    elements: 6,
    style: 'pixel-art',
    theme: 'fantasy',
    size: '1024x1024'
  });
  
  // Process or save each themed environment set
  console.log(`Generated ${theme} environment set:`, environmentSet.metadata);
}
```

### Character with Special Effects

Generate a character spritesheet with special effects for certain states:

```javascript
const mageStates = ['idle', 'walk', 'cast_fire', 'cast_ice', 'teleport'];

const mageSprites = await generateCharacterSpritesheet('elemental mage', {
  states: mageStates,
  framesPerState: 10,
  style: 'pixel-art',
  size: '1024x1024'
});

console.log('Mage spritesheet generated:', mageSprites.metadata);
```

## Best Practices and Limitations

When working with advanced features of SpriteAI, keep the following in mind:

1. **Consistency**: When generating multiple related sprites (e.g., characters or environments), use consistent options for style, size, and theme to ensure visual coherence.

2. **Performance**: Generating complex spritesheets or multiple environment sets can be time-consuming. Consider implementing caching or background processing for large-scale sprite generation.

3. **Rate Limits**: Be aware of any rate limits imposed by the underlying AI image generation service. Implement appropriate error handling and retries in your application.

4. **Style Limitations**: While SpriteAI supports various styles, some complex or highly specific art styles may not produce optimal results. Experiment with different style descriptions to find the best output for your needs.

5. **Customization**: For highly specific sprite requirements, you may need to post-process the generated sprites using image editing tools or additional algorithms.

By leveraging these advanced features and following best practices, you can create rich, diverse, and customized sprite assets for your game development projects using SpriteAI.