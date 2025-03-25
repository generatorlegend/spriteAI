# Customization Options for SpriteAI

## Introduction

SpriteAI offers a wide range of customization options to create unique and diverse sprites for various game genres and art styles. This guide will walk you through the available options and how to use them effectively.

## Animation States

SpriteAI supports multiple animation states for character sprites. You can customize these states using the `states` option in the `generateCharacterSpritesheet` function.

### Available States

To fetch the available animation states, use the `fetchAvailableAnimationStates` function:

```javascript
const availableStates = await fetchAvailableAnimationStates();
console.log(availableStates);
// Output: ['idle', 'walk', 'run', 'attack', 'jump', 'fall', 'hurt', 'die']
```

### Customizing States

When generating a character spritesheet, you can specify which states to include:

```javascript
const result = await generateCharacterSpritesheet("warrior", {
  states: ['idle', 'attack', 'die'],
  framesPerState: 8
});
```

## Art Styles

SpriteAI supports various art styles for both character and environment sprites.

### Available Styles

To fetch the available sprite styles, use the `fetchAvailableSpriteStyles` function:

```javascript
const availableStyles = await fetchAvailableSpriteStyles();
console.log(availableStyles);
// Output: ['pixel-art', 'vector', '3d', 'hand-drawn', 'anime']
```

### Applying Styles

Specify the desired style when generating sprites:

```javascript
const characterSprite = await generateCharacterSpritesheet("elf archer", {
  style: 'anime'
});

const environmentSprite = await generateEnvironmentSprites("forest", {
  style: 'pixel-art'
});
```

## Sprite Sizes

You can customize the size of your sprites using the `size` option:

```javascript
const largeSprite = await generateCharacterSpritesheet("giant robot", {
  size: '2048x2048'
});

const smallSprite = await generateEnvironmentSprites("item icons", {
  size: '512x512'
});
```

## Background Removal

For sprites that require transparency, you can use the `removeBackgroundColor` function:

```javascript
const inputPath = 'path/to/input/image.png';
const outputPath = 'path/to/output/image.png';
const targetColor = '#FFFFFF'; // White background
const colorThreshold = 0.1;

await removeBackgroundColor(inputPath, outputPath, targetColor, colorThreshold);
```

You can also apply background removal directly when generating landscape sprites:

```javascript
const landscapeSprite = await generateLandscapeSprite("mountain range", {
  removeBackground: true,
  backgroundColor: '#FFFFFF',
  colorThreshold: 0.1
});
```

## Special Effects

### Adding Borders

To add a border to your sprite, use the `generateSpriteWithBorder` function:

```javascript
const borderedSprite = await generateSpriteWithBorder('knight', 
  { r: 255, g: 0, b: 0, alpha: 255 }, // Red border
  5 // 5 pixel thickness
);
```

### Customizing Environment Sprites

When generating environment sprites, you can specify the number of elements and theme:

```javascript
const dungeonTileset = await generateEnvironmentSprites("dungeon", {
  elements: 6,
  theme: 'dark fantasy',
  padding: 2
});
```

## Metadata and Frame Data

Both character and environment sprites come with metadata that can be useful for game development:

```javascript
const { metadata } = await generateCharacterSpritesheet("wizard");
console.log(metadata);
// Output:
// {
//   states: ['idle', 'walk', 'run', 'attack'],
//   framesPerState: 6,
//   totalFrames: 24,
//   dimensions: { width: '1024', height: '1024' },
//   frameData: {
//     idle: { row: 0, frames: 6, startFrame: 0, endFrame: 5 },
//     walk: { row: 1, frames: 6, startFrame: 6, endFrame: 11 },
//     // ...
//   }
// }
```

## Conclusion

By leveraging these customization options, you can create a wide variety of sprites tailored to your game's specific needs. Experiment with different combinations of states, styles, and effects to achieve the perfect look for your game assets.