<response>

# Advanced Usage of SpriteAI

This guide covers advanced techniques and customization options for the SpriteAI library. Learn how to fine-tune sprite generation, work with various animation states, and integrate SpriteAI into your game development workflow.

## Table of Contents

1. [Customizing Sprite Generation](#customizing-sprite-generation)
2. [Working with Animation States](#working-with-animation-states)
3. [Environment Sprite Generation](#environment-sprite-generation)
4. [Integrating SpriteAI into Game Development](#integrating-spriteai-into-game-development)
5. [Advanced Techniques](#advanced-techniques)

## Customizing Sprite Generation

SpriteAI offers various options to customize the sprite generation process. Here's how you can leverage these options:

### Character Spritesheet Customization

When generating character spritesheets, you can customize several parameters:

```javascript
const options = {
  states: ['idle', 'walk', 'run', 'attack'],
  framesPerState: 6,
  size: '1024x1024',
  style: 'pixel-art',
  padding: 1,
  direction: 'right'
};

const result = await generateCharacterSpritesheet('warrior with a sword', options);
```

- `states`: An array of animation states to generate
- `framesPerState`: Number of frames for each animation state
- `size`: Output size of the spritesheet
- `style`: Art style of the sprite (e.g., 'pixel-art', 'vector', '3d', 'hand-drawn', 'anime')
- `padding`: Padding between individual sprites
- `direction`: Base direction the character faces

### Fetching Available Options

You can retrieve the available animation states and sprite styles using these functions:

```javascript
const availableStates = await fetchAvailableAnimationStates();
const availableStyles = await fetchAvailableSpriteStyles();
```

## Working with Animation States

SpriteAI generates spritesheets with multiple animation states. Here's how to work with them effectively:

### Accessing Frame Data

The `generateCharacterSpritesheet` function returns metadata that includes frame data for each animation state:

```javascript
const result = await generateCharacterSpritesheet('mage casting spells');
const { frameData } = result.metadata;

console.log(frameData.idle); // { row: 0, frames: 6, startFrame: 0, endFrame: 5 }
console.log(frameData.attack); // { row: 3, frames: 6, startFrame: 18, endFrame: 23 }
```

Use this data to correctly slice and animate your sprites in your game engine.

## Environment Sprite Generation

For generating environment sprites, use the `generateEnvironmentSprites` function:

```javascript
const options = {
  elements: 4,
  size: '1024x1024',
  style: 'pixel-art',
  padding: 1,
  theme: 'fantasy'
};

const result = await generateEnvironmentSprites('forest trees and rocks', options);
```

This generates a tileset with multiple environment elements, perfect for creating diverse game backgrounds.

## Integrating SpriteAI into Game Development

To seamlessly integrate SpriteAI into your game development workflow:

1. Generate sprites during your asset pipeline or build process.
2. Save generated spritesheets using the `save` option:

```javascript
const options = {
  // ... other options
  save: true
};

await generateCharacterSpritesheet('hero character', options);
// Saves to: {current_working_directory}/assets/hero_character_spritesheet.png
```

3. Use the returned metadata to set up your sprite animations in your game engine.

## Advanced Techniques

### Background Removal

For landscape sprites, you can remove the background:

```javascript
const options = {
  removeBackground: true,
  backgroundColor: '#FFFFFF',
  colorThreshold: 0.1
};

const result = await generateLandscapeSprite('mountain range', options);
```

This process uses color differencing to make the background transparent, which is useful for creating layered backgrounds or sprites that blend seamlessly with other game elements.

### Customizing Prompts

While SpriteAI generates prompts automatically, you can influence the output by being specific in your descriptions:

```javascript
const description = 'steampunk robot with brass gears and steam pipes';
const result = await generateCharacterSpritesheet(description);
```

Experiment with different descriptions to achieve the desired style and characteristics for your sprites.

By leveraging these advanced features and techniques, you can create unique and tailored sprites for your game projects using SpriteAI.

</response># Advanced Usage of SpriteAI

This guide covers advanced techniques and customization options for the SpriteAI library. Learn how to fine-tune sprite generation, work with various animation states, and integrate SpriteAI into your game development workflow.

## Table of Contents

1. [Customizing Sprite Generation](#customizing-sprite-generation)
2. [Working with Animation States](#working-with-animation-states)
3. [Environment Sprite Generation](#environment-sprite-generation)
4. [Integrating SpriteAI into Game Development](#integrating-spriteai-into-game-development)
5. [Advanced Techniques](#advanced-techniques)

## Customizing Sprite Generation

SpriteAI offers various options to customize the sprite generation process. Here's how you can leverage these options:

### Character Spritesheet Customization

When generating character spritesheets, you can customize several parameters:

```javascript
const options = {
  states: ['idle', 'walk', 'run', 'attack'],
  framesPerState: 6,
  size: '1024x1024',
  style: 'pixel-art',
  padding: 1,
  direction: 'right'
};

const result = await generateCharacterSpritesheet('warrior with a sword', options);
```

- `states`: An array of animation states to generate
- `framesPerState`: Number of frames for each animation state
- `size`: Output size of the spritesheet
- `style`: Art style of the sprite (e.g., 'pixel-art', 'vector', '3d', 'hand-drawn', 'anime')
- `padding`: Padding between individual sprites
- `direction`: Base direction the character faces

### Fetching Available Options

You can retrieve the available animation states and sprite styles using these functions:

```javascript
const availableStates = await fetchAvailableAnimationStates();
const availableStyles = await fetchAvailableSpriteStyles();
```

## Working with Animation States

SpriteAI generates spritesheets with multiple animation states. Here's how to work with them effectively:

### Accessing Frame Data

The `generateCharacterSpritesheet` function returns metadata that includes frame data for each animation state:

```javascript
const result = await generateCharacterSpritesheet('mage casting spells');
const { frameData } = result.metadata;

console.log(frameData.idle); // { row: 0, frames: 6, startFrame: 0, endFrame: 5 }
console.log(frameData.attack); // { row: 3, frames: 6, startFrame: 18, endFrame: 23 }
```

Use this data to correctly slice and animate your sprites in your game engine.

## Environment Sprite Generation

For generating environment sprites, use the `generateEnvironmentSprites` function:

```javascript
const options = {
  elements: 4,
  size: '1024x1024',
  style: 'pixel-art',
  padding: 1,
  theme: 'fantasy'
};

const result = await generateEnvironmentSprites('forest trees and rocks', options);
```

This generates a tileset with multiple environment elements, perfect for creating diverse game backgrounds.

## Integrating SpriteAI into Game Development

To seamlessly integrate SpriteAI into your game development workflow:

1. Generate sprites during your asset pipeline or build process.
2. Save generated spritesheets using the `save` option:

```javascript
const options = {
  // ... other options
  save: true
};

await generateCharacterSpritesheet('hero character', options);
// Saves to: {current_working_directory}/assets/hero_character_spritesheet.png
```

3. Use the returned metadata to set up your sprite animations in your game engine.

## Advanced Techniques

### Background Removal

For landscape sprites, you can remove the background:

```javascript
const options = {
  removeBackground: true,
  backgroundColor: '#FFFFFF',
  colorThreshold: 0.1
};

const result = await generateLandscapeSprite('mountain range', options);
```

This process uses color differencing to make the background transparent, which is useful for creating layered backgrounds or sprites that blend seamlessly with other game elements.

### Customizing Prompts

While SpriteAI generates prompts automatically, you can influence the output by being specific in your descriptions:

```javascript
const description = 'steampunk robot with brass gears and steam pipes';
const result = await generateCharacterSpritesheet(description);
```

Experiment with different descriptions to achieve the desired style and characteristics for your sprites.

By leveraging these advanced features and techniques, you can create unique and tailored sprites for your game projects using SpriteAI.