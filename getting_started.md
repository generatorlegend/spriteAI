<response>
# Getting Started with SpriteAI

SpriteAI is a powerful library that allows you to generate character spritesheets and landscape sprites using AI. This guide will help you get started with SpriteAI, covering installation, basic usage, and an overview of the main features.

## Installation

To install SpriteAI, make sure you have Node.js installed on your system. Then, run the following command in your project directory:

```bash
npm install spriteai
```

## Basic Usage

### Generating Character Spritesheets

To generate a character spritesheet, you can use the `generateCharacterSpritesheet` function. Here's a basic example:

```javascript
import { generateCharacterSpritesheet } from 'spriteai';

const description = 'A brave knight in shining armor';
const options = {
  states: ['idle', 'walk', 'run', 'attack'],
  framesPerState: 6,
  size: '1024x1024',
  style: 'pixel-art'
};

const result = await generateCharacterSpritesheet(description, options);
console.log(result);
```

This will generate a pixel-art character spritesheet of a knight with four animation states: idle, walk, run, and attack.

### Generating Landscape Sprites

To create a landscape sprite, use the `generateLandscapeSprite` function:

```javascript
import { generateLandscapeSprite } from 'spriteai';

const description = 'A lush forest with a winding river';
const options = {
  size: '1024x1024',
  style: 'pixel-art',
  timeOfDay: 'day',
  weather: 'clear',
  perspective: 'side-scrolling'
};

const result = await generateLandscapeSprite(description, options);
console.log(result);
```

This will generate a pixel-art landscape sprite of a forest scene with a river, suitable for a side-scrolling game.

## Main Features

SpriteAI offers several key features:

1. **Character Spritesheet Generation**: Create complete spritesheets for game characters with multiple animation states.
2. **Landscape Sprite Creation**: Generate background and environment sprites for your game scenes.
3. **Customizable Options**: Adjust various parameters like size, style, weather conditions, and more to fit your game's needs.
4. **Background Removal**: Automatically remove backgrounds from generated sprites (available for landscape sprites).
5. **Metadata Generation**: Receive detailed metadata about the generated sprites, including frame data for animations.

## Advanced Usage

### Fetching Available Animation States

You can retrieve the list of available animation states:

```javascript
import { fetchAvailableAnimationStates } from 'spriteai';

const states = await fetchAvailableAnimationStates();
console.log(states);
```

### Fetching Available Sprite Styles

To get the list of available sprite styles:

```javascript
import { fetchAvailableSpriteStyles } from 'spriteai';

const styles = await fetchAvailableSpriteStyles();
console.log(styles);
```

### Generating Environment Sprites

For creating sets of environment sprites:

```javascript
import { generateEnvironmentSprites } from 'spriteai';

const description = 'Medieval castle elements';
const options = {
  elements: 4,
  size: '1024x1024',
  style: 'pixel-art',
  theme: 'fantasy'
};

const result = await generateEnvironmentSprites(description, options);
console.log(result);
```

This will generate a tileset of four different medieval castle elements in a pixel-art style.

## Conclusion

SpriteAI provides a powerful and flexible way to generate game assets using AI. By leveraging its functions and customizing options, you can create a wide variety of sprites and environments for your game projects. Experiment with different descriptions, styles, and settings to achieve the perfect look for your game!

For more detailed information on each function and its options, refer to the API documentation.
</response>