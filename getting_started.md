# Getting Started with SpriteAI

SpriteAI is a powerful library that leverages AI to generate game assets, including character spritesheets and landscape sprites. This guide will help you get started with SpriteAI, covering installation, basic usage, and an overview of its main features.

## Installation

To install SpriteAI, you'll need Node.js and npm (Node Package Manager) installed on your system. Follow these steps to set up SpriteAI in your project:

1. Open your terminal or command prompt.
2. Navigate to your project directory.
3. Run the following command to install SpriteAI and its dependencies:

```bash
npm install spriteai
```

## Basic Usage

### Importing SpriteAI

To use SpriteAI in your project, import the necessary functions:

```javascript
import { generateCharacterSpritesheet, generateLandscapeSprite } from 'spriteai';
```

### Generating Character Spritesheets

To create a character spritesheet, use the `generateCharacterSpritesheet` function:

```javascript
const characterDescription = "A brave knight in shining armor";
const options = {
  states: ['idle', 'walk', 'run', 'attack'],
  framesPerState: 6,
  size: '1024x1024',
  style: 'pixel-art',
  direction: 'right',
  save: true
};

const result = await generateCharacterSpritesheet(characterDescription, options);
console.log(result);
```

This will generate a spritesheet with the specified animation states and save it to the `assets` folder in your project directory.

### Generating Landscape Sprites

To create a landscape sprite, use the `generateLandscapeSprite` function:

```javascript
const landscapeDescription = "A lush forest with a winding river";
const options = {
  size: '1024x1024',
  style: 'pixel-art',
  timeOfDay: 'day',
  weather: 'clear',
  perspective: 'side-scrolling',
  save: true
};

const result = await generateLandscapeSprite(landscapeDescription, options);
console.log(result);
```

This will generate a landscape sprite based on the description and save it to the `assets` folder.

## Main Features

SpriteAI offers several key features:

1. **Character Spritesheet Generation**: Create animated character spritesheets with customizable states, frames, and styles.
2. **Landscape Sprite Generation**: Generate detailed landscape sprites for game backgrounds with various options for time of day, weather, and perspective.
3. **Customizable Output**: Control the size, style, and other parameters of your generated sprites.
4. **Background Removal**: Option to remove backgrounds from generated sprites for easy integration into your game.
5. **Metadata**: Receive detailed metadata about generated sprites, including frame data for animations.

## Advanced Usage

### Removing Backgrounds

To remove the background from a generated landscape sprite:

```javascript
const options = {
  // ... other options ...
  removeBackground: true,
  backgroundColor: '#FFFFFF',
  colorThreshold: 0.1
};

const result = await generateLandscapeSprite(description, options);
```

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

## Next Steps

Now that you're familiar with the basics of SpriteAI, you can start integrating it into your game development workflow. Experiment with different descriptions, styles, and options to create unique assets for your projects.

For more detailed information on each function and its parameters, refer to the API documentation.

Happy sprite generating!