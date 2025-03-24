Here's the new documentation page content for "advanced_usage.md":

<response>
# Advanced Usage Guide for SpriteAI

This guide covers advanced topics and techniques for using the SpriteAI library to generate and customize game sprites and environments.

## Table of Contents

1. [Customizing Animation States](#customizing-animation-states)
2. [Working with Different Art Styles](#working-with-different-art-styles)
3. [Optimizing Sprite Generation](#optimizing-sprite-generation)
4. [Integrating SpriteAI Outputs into Game Development Workflows](#integrating-spriteai-outputs-into-game-development-workflows)
5. [Advanced Examples and Use Cases](#advanced-examples-and-use-cases)

## Customizing Animation States

SpriteAI allows you to customize the animation states for your character spritesheets. By default, the library generates sprites for 'idle', 'walk', 'run', and 'attack' states, but you can easily modify this to suit your game's needs.

### Fetching Available Animation States

To see the full list of available animation states:

```javascript
import { fetchAvailableAnimationStates } from 'spriteAI';

const states = await fetchAvailableAnimationStates();
console.log(states);
// Output: ['idle', 'walk', 'run', 'attack', 'jump', 'fall', 'hurt', 'die']
```

### Specifying Custom States

When generating a character spritesheet, you can specify the exact states you want:

```javascript
import { generateCharacterSpritesheet } from 'spriteAI';

const result = await generateCharacterSpritesheet('medieval knight', {
  states: ['idle', 'attack', 'block', 'die'],
  framesPerState: 8
});
```

This will generate a spritesheet with four rows, each representing one of the specified states, and eight frames per state.

## Working with Different Art Styles

SpriteAI supports various art styles for sprite generation. You can fetch the available styles and specify your preferred style when generating sprites.

### Fetching Available Styles

```javascript
import { fetchAvailableSpriteStyles } from 'spriteAI';

const styles = await fetchAvailableSpriteStyles();
console.log(styles);
// Output: ['pixel-art', 'vector', '3d', 'hand-drawn', 'anime']
```

### Generating Sprites in Different Styles

```javascript
const pixelArtCharacter = await generateCharacterSpritesheet('cyberpunk hacker', {
  style: 'pixel-art'
});

const animeCharacter = await generateCharacterSpritesheet('magical girl', {
  style: 'anime'
});
```

## Optimizing Sprite Generation

To optimize the sprite generation process, consider the following tips:

1. **Adjust image size**: Smaller sizes generate faster but may lack detail. Find the right balance for your needs.

```javascript
const result = await generateCharacterSpritesheet('robot warrior', {
  size: '512x512' // Smaller size for faster generation
});
```

2. **Limit states and frames**: Generate only the necessary states and frames to reduce generation time and resource usage.

3. **Use caching**: Implement a caching system to store and reuse previously generated sprites when appropriate.

## Integrating SpriteAI Outputs into Game Development Workflows

### Saving Generated Sprites

To save generated sprites for use in your game engine:

```javascript
const result = await generateCharacterSpritesheet('elf archer', {
  save: true // This will save the spritesheet to the assets folder
});

console.log(`Spritesheet saved to: ${result.metadata.savedPath}`);
```

### Processing Spritesheets

You can further process the generated spritesheets using libraries like `sharp` or `Jimp`:

```javascript
import sharp from 'sharp';

const result = await generateCharacterSpritesheet('fire elemental');
const buffer = Buffer.from(result.spritesheet.split(',')[1], 'base64');

await sharp(buffer)
  .resize(800, 600)
  .toFile('resized_fire_elemental.png');
```

## Advanced Examples and Use Cases

### Generating Environment Sprites

Create a set of environment sprites for your game:

```javascript
import { generateEnvironmentSprites } from 'spriteAI';

const forestEnvironment = await generateEnvironmentSprites('dense forest', {
  elements: 6,
  style: 'pixel-art',
  theme: 'fantasy'
});

console.log(forestEnvironment.metadata);
```

### Creating a Multi-Character Scene

Generate multiple characters and combine them into a single scene:

```javascript
async function createPartyScene() {
  const warrior = await generateCharacterSpritesheet('muscular warrior');
  const mage = await generateCharacterSpritesheet('elderly wizard');
  const rogue = await generateCharacterSpritesheet('stealthy assassin');

  // Combine characters into a single image (implementation depends on your image processing library)
  // ...

  return combinedScene;
}
```

### Dynamic Sprite Generation Based on Game State

Implement a system that generates sprites based on the current game state or player choices:

```javascript
async function generateDynamicBoss(playerLevel, environment) {
  let bossDescription = 'powerful boss';

  if (playerLevel > 50) bossDescription = 'legendary ' + bossDescription;
  if (environment === 'fire') bossDescription = 'fiery ' + bossDescription;

  return await generateCharacterSpritesheet(bossDescription, {
    states: ['idle', 'attack', 'special1', 'special2', 'die'],
    style: playerLevel > 75 ? '3d' : 'pixel-art'
  });
}
```

By leveraging these advanced techniques, you can create more dynamic and customized sprite assets for your game development projects using SpriteAI.
</response># Advanced Usage Guide for SpriteAI

This guide covers advanced topics and techniques for using the SpriteAI library to generate and customize game sprites and environments.

## Table of Contents

1. [Customizing Animation States](#customizing-animation-states)
2. [Working with Different Art Styles](#working-with-different-art-styles)
3. [Optimizing Sprite Generation](#optimizing-sprite-generation)
4. [Integrating SpriteAI Outputs into Game Development Workflows](#integrating-spriteai-outputs-into-game-development-workflows)
5. [Advanced Examples and Use Cases](#advanced-examples-and-use-cases)

## Customizing Animation States

SpriteAI allows you to customize the animation states for your character spritesheets. By default, the library generates sprites for 'idle', 'walk', 'run', and 'attack' states, but you can easily modify this to suit your game's needs.

### Fetching Available Animation States

To see the full list of available animation states:

```javascript
import { fetchAvailableAnimationStates } from 'spriteAI';

const states = await fetchAvailableAnimationStates();
console.log(states);
// Output: ['idle', 'walk', 'run', 'attack', 'jump', 'fall', 'hurt', 'die']
```

### Specifying Custom States

When generating a character spritesheet, you can specify the exact states you want:

```javascript
import { generateCharacterSpritesheet } from 'spriteAI';

const result = await generateCharacterSpritesheet('medieval knight', {
  states: ['idle', 'attack', 'block', 'die'],
  framesPerState: 8
});
```

This will generate a spritesheet with four rows, each representing one of the specified states, and eight frames per state.

## Working with Different Art Styles

SpriteAI supports various art styles for sprite generation. You can fetch the available styles and specify your preferred style when generating sprites.

### Fetching Available Styles

```javascript
import { fetchAvailableSpriteStyles } from 'spriteAI';

const styles = await fetchAvailableSpriteStyles();
console.log(styles);
// Output: ['pixel-art', 'vector', '3d', 'hand-drawn', 'anime']
```

### Generating Sprites in Different Styles

```javascript
const pixelArtCharacter = await generateCharacterSpritesheet('cyberpunk hacker', {
  style: 'pixel-art'
});

const animeCharacter = await generateCharacterSpritesheet('magical girl', {
  style: 'anime'
});
```

## Optimizing Sprite Generation

To optimize the sprite generation process, consider the following tips:

1. **Adjust image size**: Smaller sizes generate faster but may lack detail. Find the right balance for your needs.

```javascript
const result = await generateCharacterSpritesheet('robot warrior', {
  size: '512x512' // Smaller size for faster generation
});
```

2. **Limit states and frames**: Generate only the necessary states and frames to reduce generation time and resource usage.

3. **Use caching**: Implement a caching system to store and reuse previously generated sprites when appropriate.

## Integrating SpriteAI Outputs into Game Development Workflows

### Saving Generated Sprites

To save generated sprites for use in your game engine:

```javascript
const result = await generateCharacterSpritesheet('elf archer', {
  save: true // This will save the spritesheet to the assets folder
});

console.log(`Spritesheet saved to: ${result.metadata.savedPath}`);
```

### Processing Spritesheets

You can further process the generated spritesheets using libraries like `sharp` or `Jimp`:

```javascript
import sharp from 'sharp';

const result = await generateCharacterSpritesheet('fire elemental');
const buffer = Buffer.from(result.spritesheet.split(',')[1], 'base64');

await sharp(buffer)
  .resize(800, 600)
  .toFile('resized_fire_elemental.png');
```

## Advanced Examples and Use Cases

### Generating Environment Sprites

Create a set of environment sprites for your game:

```javascript
import { generateEnvironmentSprites } from 'spriteAI';

const forestEnvironment = await generateEnvironmentSprites('dense forest', {
  elements: 6,
  style: 'pixel-art',
  theme: 'fantasy'
});

console.log(forestEnvironment.metadata);
```

### Creating a Multi-Character Scene

Generate multiple characters and combine them into a single scene:

```javascript
async function createPartyScene() {
  const warrior = await generateCharacterSpritesheet('muscular warrior');
  const mage = await generateCharacterSpritesheet('elderly wizard');
  const rogue = await generateCharacterSpritesheet('stealthy assassin');

  // Combine characters into a single image (implementation depends on your image processing library)
  // ...

  return combinedScene;
}
```

### Dynamic Sprite Generation Based on Game State

Implement a system that generates sprites based on the current game state or player choices:

```javascript
async function generateDynamicBoss(playerLevel, environment) {
  let bossDescription = 'powerful boss';

  if (playerLevel > 50) bossDescription = 'legendary ' + bossDescription;
  if (environment === 'fire') bossDescription = 'fiery ' + bossDescription;

  return await generateCharacterSpritesheet(bossDescription, {
    states: ['idle', 'attack', 'special1', 'special2', 'die'],
    style: playerLevel > 75 ? '3d' : 'pixel-art'
  });
}
```

By leveraging these advanced techniques, you can create more dynamic and customized sprite assets for your game development projects using SpriteAI.