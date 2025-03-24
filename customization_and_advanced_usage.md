<response>

# Customization and Advanced Usage of SpriteAI

## Table of Contents
1. [Introduction](#introduction)
2. [Modifying Generation Prompts](#modifying-generation-prompts)
3. [Working with Different Art Styles](#working-with-different-art-styles)
4. [Handling Complex Animation States](#handling-complex-animation-states)
5. [Integrating SpriteAI Outputs](#integrating-spriteai-outputs)
6. [Advanced Techniques for Power Users](#advanced-techniques-for-power-users)

## Introduction

This guide covers advanced usage and customization techniques for the SpriteAI library. It's designed for developers who want to push the boundaries of what's possible with AI-generated game assets.

## Modifying Generation Prompts

The SpriteAI library uses DALL-E 3 to generate images based on prompts. You can customize these prompts to achieve specific results.

### Character Spritesheets

For character spritesheets, you can modify the prompt in the `generateCharacterSpritesheet` function:

```javascript
const prompt = `Create a ${style} character spritesheet of ${description} with these animation states: ${statesDescription}.
  Each row should be a different animation state with ${framesPerState} frames.
  Character should face ${direction}.
  Style requirements:
  - Clean pixel art style
  - Consistent character size across all frames
  - White background
  - Clear separation between frames
  - ${states.length} rows of animations
  - ${framesPerState} frames per row
  - Each row represents a different animation state in sequence`;
```

To customize this prompt:

1. Add specific details about the character's appearance.
2. Include instructions for unique poses or actions.
3. Specify color palette or theme requirements.

Example of a customized prompt:

```javascript
const prompt = `Create a ${style} character spritesheet of a battle-worn knight with glowing blue armor and a flaming sword. Animation states: ${statesDescription}.
  Each row should be a different animation state with ${framesPerState} frames.
  Character should face ${direction}.
  Style requirements:
  - Detailed pixel art style with a dark fantasy theme
  - Consistent character size across all frames
  - Transparent background
  - Clear separation between frames
  - ${states.length} rows of animations
  - ${framesPerState} frames per row
  - Each row represents a different animation state in sequence
  - Include dramatic lighting effects and particle animations`;
```

## Working with Different Art Styles

SpriteAI supports various art styles. You can fetch available styles using the `fetchAvailableSpriteStyles` function:

```javascript
const styles = await fetchAvailableSpriteStyles();
console.log(styles); // ['pixel-art', 'vector', '3d', 'hand-drawn', 'anime']
```

To use a specific style, pass it as an option when generating sprites:

```javascript
const animeCharacter = await generateCharacterSpritesheet('samurai', {
  style: 'anime',
  size: '1024x1024',
  states: ['idle', 'attack', 'defend'],
  framesPerState: 8
});
```

## Handling Complex Animation States

For more complex animations, you can customize the `states` array and `framesPerState`:

```javascript
const complexCharacter = await generateCharacterSpritesheet('shape-shifting monster', {
  states: ['idle', 'morph', 'attack', 'defend', 'special_ability', 'death'],
  framesPerState: 12,
  size: '2048x2048'
});
```

You can also fetch available animation states:

```javascript
const availableStates = await fetchAvailableAnimationStates();
console.log(availableStates);
```

## Integrating SpriteAI Outputs

SpriteAI returns both the original image URL and a base64-encoded spritesheet. Here's how you can use these in different contexts:

### Web Applications

```javascript
const spriteData = await generateCharacterSpritesheet('wizard');

// Display the original image
document.getElementById('original').src = spriteData.original;

// Use the spritesheet in a canvas or game engine
const img = new Image();
img.src = spriteData.spritesheet;
img.onload = () => {
  // Your sprite rendering code here
};
```

### Game Engines (e.g., Phaser)

```javascript
function preload() {
  this.load.spritesheet('character', spriteData.spritesheet, {
    frameWidth: spriteData.metadata.dimensions.width / spriteData.metadata.framesPerState,
    frameHeight: spriteData.metadata.dimensions.height / spriteData.metadata.states.length
  });
}

function create() {
  const character = this.add.sprite(400, 300, 'character');
  
  // Create animations for each state
  spriteData.metadata.states.forEach((state, index) => {
    this.anims.create({
      key: state,
      frames: this.anims.generateFrameNumbers('character', {
        start: spriteData.metadata.frameData[state].startFrame,
        end: spriteData.metadata.frameData[state].endFrame
      }),
      frameRate: 10,
      repeat: -1
    });
  });

  // Play an animation
  character.play('idle');
}
```

## Advanced Techniques for Power Users

### Removing Backgrounds

You can remove backgrounds from generated sprites using the `removeBackgroundColor` function:

```javascript
const tempInputPath = 'path/to/input/image.png';
const tempOutputPath = 'path/to/output/image.png';

await removeBackgroundColor(
  tempInputPath,
  tempOutputPath,
  '#FFFFFF', // Target color to remove
  0.1 // Color threshold
);
```

### Generating Environment Sprites

For creating game environments, use the `generateEnvironmentSprites` function:

```javascript
const environmentSprites = await generateEnvironmentSprites('medieval castle', {
  elements: 6,
  size: '2048x2048',
  style: 'pixel-art',
  theme: 'fantasy',
  save: true
});

console.log(environmentSprites.metadata);
```

### Custom Post-Processing

You can apply custom post-processing to the generated sprites using libraries like Sharp or Jimp:

```javascript
import sharp from 'sharp';

async function applyCustomEffect(inputBuffer) {
  return await sharp(inputBuffer)
    .grayscale()
    .tint({ r: 255, g: 200, b: 0 })
    .toBuffer();
}

const spriteData = await generateCharacterSpritesheet('robot');
const processedBuffer = await applyCustomEffect(Buffer.from(spriteData.spritesheet.split(',')[1], 'base64'));

// Use the processed buffer as needed
```

By leveraging these advanced techniques, you can create unique and highly customized game assets using the SpriteAI library. Experiment with different combinations of options, styles, and post-processing techniques to achieve the perfect look for your game.

</response># Customization and Advanced Usage of SpriteAI

## Table of Contents
1. [Introduction](#introduction)
2. [Modifying Generation Prompts](#modifying-generation-prompts)
3. [Working with Different Art Styles](#working-with-different-art-styles)
4. [Handling Complex Animation States](#handling-complex-animation-states)
5. [Integrating SpriteAI Outputs](#integrating-spriteai-outputs)
6. [Advanced Techniques for Power Users](#advanced-techniques-for-power-users)

## Introduction

This guide covers advanced usage and customization techniques for the SpriteAI library. It's designed for developers who want to push the boundaries of what's possible with AI-generated game assets.

## Modifying Generation Prompts

The SpriteAI library uses DALL-E 3 to generate images based on prompts. You can customize these prompts to achieve specific results.

### Character Spritesheets

For character spritesheets, you can modify the prompt in the `generateCharacterSpritesheet` function:

```javascript
const prompt = `Create a ${style} character spritesheet of ${description} with these animation states: ${statesDescription}.
  Each row should be a different animation state with ${framesPerState} frames.
  Character should face ${direction}.
  Style requirements:
  - Clean pixel art style
  - Consistent character size across all frames
  - White background
  - Clear separation between frames
  - ${states.length} rows of animations
  - ${framesPerState} frames per row
  - Each row represents a different animation state in sequence`;
```

To customize this prompt:

1. Add specific details about the character's appearance.
2. Include instructions for unique poses or actions.
3. Specify color palette or theme requirements.

Example of a customized prompt:

```javascript
const prompt = `Create a ${style} character spritesheet of a battle-worn knight with glowing blue armor and a flaming sword. Animation states: ${statesDescription}.
  Each row should be a different animation state with ${framesPerState} frames.
  Character should face ${direction}.
  Style requirements:
  - Detailed pixel art style with a dark fantasy theme
  - Consistent character size across all frames
  - Transparent background
  - Clear separation between frames
  - ${states.length} rows of animations
  - ${framesPerState} frames per row
  - Each row represents a different animation state in sequence
  - Include dramatic lighting effects and particle animations`;
```

## Working with Different Art Styles

SpriteAI supports various art styles. You can fetch available styles using the `fetchAvailableSpriteStyles` function:

```javascript
const styles = await fetchAvailableSpriteStyles();
console.log(styles); // ['pixel-art', 'vector', '3d', 'hand-drawn', 'anime']
```

To use a specific style, pass it as an option when generating sprites:

```javascript
const animeCharacter = await generateCharacterSpritesheet('samurai', {
  style: 'anime',
  size: '1024x1024',
  states: ['idle', 'attack', 'defend'],
  framesPerState: 8
});
```

## Handling Complex Animation States

For more complex animations, you can customize the `states` array and `framesPerState`:

```javascript
const complexCharacter = await generateCharacterSpritesheet('shape-shifting monster', {
  states: ['idle', 'morph', 'attack', 'defend', 'special_ability', 'death'],
  framesPerState: 12,
  size: '2048x2048'
});
```

You can also fetch available animation states:

```javascript
const availableStates = await fetchAvailableAnimationStates();
console.log(availableStates);
```

## Integrating SpriteAI Outputs

SpriteAI returns both the original image URL and a base64-encoded spritesheet. Here's how you can use these in different contexts:

### Web Applications

```javascript
const spriteData = await generateCharacterSpritesheet('wizard');

// Display the original image
document.getElementById('original').src = spriteData.original;

// Use the spritesheet in a canvas or game engine
const img = new Image();
img.src = spriteData.spritesheet;
img.onload = () => {
  // Your sprite rendering code here
};
```

### Game Engines (e.g., Phaser)

```javascript
function preload() {
  this.load.spritesheet('character', spriteData.spritesheet, {
    frameWidth: spriteData.metadata.dimensions.width / spriteData.metadata.framesPerState,
    frameHeight: spriteData.metadata.dimensions.height / spriteData.metadata.states.length
  });
}

function create() {
  const character = this.add.sprite(400, 300, 'character');
  
  // Create animations for each state
  spriteData.metadata.states.forEach((state, index) => {
    this.anims.create({
      key: state,
      frames: this.anims.generateFrameNumbers('character', {
        start: spriteData.metadata.frameData[state].startFrame,
        end: spriteData.metadata.frameData[state].endFrame
      }),
      frameRate: 10,
      repeat: -1
    });
  });

  // Play an animation
  character.play('idle');
}
```

## Advanced Techniques for Power Users

### Removing Backgrounds

You can remove backgrounds from generated sprites using the `removeBackgroundColor` function:

```javascript
const tempInputPath = 'path/to/input/image.png';
const tempOutputPath = 'path/to/output/image.png';

await removeBackgroundColor(
  tempInputPath,
  tempOutputPath,
  '#FFFFFF', // Target color to remove
  0.1 // Color threshold
);
```

### Generating Environment Sprites

For creating game environments, use the `generateEnvironmentSprites` function:

```javascript
const environmentSprites = await generateEnvironmentSprites('medieval castle', {
  elements: 6,
  size: '2048x2048',
  style: 'pixel-art',
  theme: 'fantasy',
  save: true
});

console.log(environmentSprites.metadata);
```

### Custom Post-Processing

You can apply custom post-processing to the generated sprites using libraries like Sharp or Jimp:

```javascript
import sharp from 'sharp';

async function applyCustomEffect(inputBuffer) {
  return await sharp(inputBuffer)
    .grayscale()
    .tint({ r: 255, g: 200, b: 0 })
    .toBuffer();
}

const spriteData = await generateCharacterSpritesheet('robot');
const processedBuffer = await applyCustomEffect(Buffer.from(spriteData.spritesheet.split(',')[1], 'base64'));

// Use the processed buffer as needed
```

By leveraging these advanced techniques, you can create unique and highly customized game assets using the SpriteAI library. Experiment with different combinations of options, styles, and post-processing techniques to achieve the perfect look for your game.