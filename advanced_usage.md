# Advanced Usage Guide for SpriteAI

## Table of Contents
1. [Introduction](#introduction)
2. [Customizing Sprite Generation](#customizing-sprite-generation)
3. [Working with Different Animation States](#working-with-different-animation-states)
4. [Optimizing Performance](#optimizing-performance)
5. [Complex Sprite Generation Scenarios](#complex-sprite-generation-scenarios)
6. [Leveraging SpriteAI in Game Development](#leveraging-spriteai-in-game-development)

## Introduction

This guide covers advanced usage of SpriteAI, providing in-depth information on customizing sprite generation, working with various animation states, optimizing performance, and leveraging the full potential of the library in game development projects.

## Customizing Sprite Generation

SpriteAI offers extensive customization options for generating sprites. Here are some advanced techniques:

### Adjusting Generation Parameters

When calling `generateCharacterSpritesheet`, you can fine-tune various parameters:

```javascript
const customSprite = await generateCharacterSpritesheet("a steampunk robot", {
  states: ['idle', 'walk', 'run', 'attack', 'jump'],
  framesPerState: 8,
  size: '2048x2048',
  style: 'pixel-art',
  padding: 2,
  direction: 'left'
});
```

This example creates a more complex spritesheet with additional animation states, more frames per state, and a larger output size.

### Customizing Art Styles

While 'pixel-art' is the default style, you can experiment with other styles:

```javascript
const vectorSprite = await generateCharacterSpritesheet("a magical fairy", {
  style: 'vector'
});

const animeSprite = await generateCharacterSpritesheet("a samurai warrior", {
  style: 'anime'
});
```

Use `fetchAvailableSpriteStyles()` to get a list of all available styles.

## Working with Different Animation States

SpriteAI supports various animation states for character sprites. Here's how to work with them effectively:

### Fetching Available States

Use the `fetchAvailableAnimationStates` function to get all possible animation states:

```javascript
const availableStates = await fetchAvailableAnimationStates();
console.log(availableStates);
// Output: ['idle', 'walk', 'run', 'attack', 'jump', 'fall', 'hurt', 'die']
```

### Creating Custom State Combinations

You can create unique combinations of states for your sprites:

```javascript
const bossSpritesheet = await generateCharacterSpritesheet("a dragon boss", {
  states: ['idle', 'roar', 'breathe-fire', 'fly', 'land', 'tail-swipe'],
  framesPerState: 10
});
```

This creates a spritesheet with custom states specific to a boss character.

## Optimizing Performance

When working with SpriteAI in larger projects, consider these optimization strategies:

### Caching Generated Sprites

Store generated spritesheets to avoid unnecessary API calls:

```javascript
const cachedSprites = new Map();

async function getOrGenerateSprite(description, options) {
  const cacheKey = JSON.stringify({ description, options });
  
  if (cachedSprites.has(cacheKey)) {
    return cachedSprites.get(cacheKey);
  }

  const sprite = await generateCharacterSpritesheet(description, options);
  cachedSprites.set(cacheKey, sprite);
  return sprite;
}
```

### Batch Generation

For games with many characters, batch generate sprites during loading:

```javascript
async function generateAllGameSprites() {
  const characterDescriptions = [
    "a knight in shining armor",
    "a mischievous goblin",
    "an elegant elven archer",
    // ... more descriptions
  ];

  const spritePromises = characterDescriptions.map(desc => 
    generateCharacterSpritesheet(desc)
  );

  return Promise.all(spritePromises);
}
```

## Complex Sprite Generation Scenarios

SpriteAI can handle complex scenarios for advanced game development needs:

### Generating Environment Sprites

Use `generateEnvironmentSprites` for creating game world elements:

```javascript
const forestEnvironment = await generateEnvironmentSprites("dense forest", {
  elements: 6,
  style: 'pixel-art',
  theme: 'fantasy',
  size: '2048x2048'
});
```

This generates a tileset of forest elements suitable for building game levels.

### Combining Character and Environment Sprites

Create immersive game scenes by combining character and environment sprites:

```javascript
async function createGameScene(characterDesc, environmentDesc) {
  const character = await generateCharacterSpritesheet(characterDesc);
  const environment = await generateEnvironmentSprites(environmentDesc);

  return {
    character: character.spritesheet,
    environment: environment.tileset,
    metadata: {
      characterFrames: character.metadata.frameData,
      environmentTiles: environment.metadata.tileData
    }
  };
}

const gameScene = await createGameScene("a brave adventurer", "ancient ruins");
```

## Leveraging SpriteAI in Game Development

Integrate SpriteAI seamlessly into your game development workflow:

### Dynamic Character Creation

Allow players to generate custom characters on-the-fly:

```javascript
async function createCustomCharacter(playerDescription) {
  const customChar = await generateCharacterSpritesheet(playerDescription, {
    states: ['idle', 'walk', 'attack'],
    style: 'pixel-art'
  });

  return {
    sprite: customChar.spritesheet,
    animations: customChar.metadata.frameData
  };
}

// In-game usage
const playerChar = await createCustomCharacter("a cyborg ninja with glowing eyes");
game.setPlayerSprite(playerChar.sprite);
game.setPlayerAnimations(playerChar.animations);
```

### Procedural World Generation

Use SpriteAI to create diverse game worlds:

```javascript
async function generateWorldTile(biome) {
  const tileDescriptions = {
    forest: "lush forest with tall trees and underbrush",
    desert: "arid desert with sand dunes and cacti",
    mountains: "rocky mountains with snow-capped peaks",
    // ... more biomes
  };

  return generateEnvironmentSprites(tileDescriptions[biome], {
    elements: 8,
    theme: biome
  });
}

async function createWorldMap(width, height) {
  const worldMap = [];
  for (let y = 0; y < height; y++) {
    for (let x = 0; x < width; x++) {
      const biome = getRandomBiome(); // Your biome selection logic
      const tile = await generateWorldTile(biome);
      worldMap.push({ x, y, tile });
    }
  }
  return worldMap;
}
```

This approach allows for the creation of vast, varied game worlds using procedurally generated sprites.

By leveraging these advanced techniques, you can fully utilize the power of SpriteAI to create rich, dynamic game assets and enhance your game development process.