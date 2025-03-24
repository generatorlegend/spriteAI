<response>
# Getting Started with SpriteAI

SpriteAI is a powerful tool for generating game assets using AI. This guide will help you get started with SpriteAI, covering installation, basic usage, and key features.

## Installation

To install SpriteAI, follow these steps:

1. Ensure you have Node.js installed on your system.
2. Create a new directory for your project and navigate to it in the terminal.
3. Initialize a new Node.js project:
   ```
   npm init -y
   ```
4. Install SpriteAI and its dependencies:
   ```
   npm install spriteai openai axios sharp jimp
   ```

## Basic Usage

### Generating Character Spritesheets

To generate a character spritesheet, use the `generateCharacterSpritesheet` function:

```javascript
import { generateCharacterSpritesheet } from 'spriteai';

const description = 'A brave knight in shining armor';
const options = {
  states: ['idle', 'walk', 'run', 'attack'],
  framesPerState: 6,
  size: '1024x1024',
  style: 'pixel-art',
  direction: 'right'
};

const result = await generateCharacterSpritesheet(description, options);
console.log(result);
```

This will generate a spritesheet with the specified animation states and return an object containing the original image URL, the base64-encoded spritesheet, and metadata about the generated sprites.

### Generating Landscape Sprites

To generate a landscape sprite, use the `generateLandscapeSprite` function:

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

This will generate a landscape sprite based on the provided description and options, returning an object with the original image URL, the base64-encoded landscape sprite, and relevant metadata.

## Key Features

1. **Character Spritesheet Generation**: Create animated character spritesheets with customizable states, frames, and styles.

2. **Landscape Sprite Generation**: Generate detailed landscape sprites for game backgrounds with various environmental settings.

3. **Customizable Options**: Adjust parameters such as size, style, time of day, weather, and perspective to fine-tune your generated assets.

4. **Background Removal**: Automatically remove backgrounds from generated sprites for easier integration into your game.

5. **Metadata**: Receive detailed metadata about generated assets, including frame data for character animations and dimension information.

6. **File Saving**: Option to automatically save generated assets to your project's assets folder.

7. **Flexible Art Styles**: Generate assets in various styles, including pixel art, vector, 3D, hand-drawn, and anime.

## Advanced Usage

### Fetching Available Animation States

You can fetch the list of available animation states using the `fetchAvailableAnimationStates` function:

```javascript
import { fetchAvailableAnimationStates } from 'spriteai';

const states = await fetchAvailableAnimationStates();
console.log(states);
```

### Fetching Available Sprite Styles

To get the list of available sprite styles, use the `fetchAvailableSpriteStyles` function:

```javascript
import { fetchAvailableSpriteStyles } from 'spriteai';

const styles = await fetchAvailableSpriteStyles();
console.log(styles);
```

### Generating Environment Sprites

For creating sets of environment sprites, use the `generateEnvironmentSprites` function:

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

This will generate a tileset of environment sprites based on the provided description and options.

## Next Steps

Now that you're familiar with the basics of SpriteAI, you can start integrating it into your game development workflow. Experiment with different descriptions, styles, and options to create unique and engaging game assets for your projects.

For more detailed information on each function and its parameters, refer to the API documentation.
</response># Getting Started with SpriteAI

SpriteAI is a powerful tool for generating game assets using AI. This guide will help you get started with SpriteAI, covering installation, basic usage, and key features.

## Installation

To install SpriteAI, follow these steps:

1. Ensure you have Node.js installed on your system.
2. Create a new directory for your project and navigate to it in the terminal.
3. Initialize a new Node.js project:
   ```
   npm init -y
   ```
4. Install SpriteAI and its dependencies:
   ```
   npm install spriteai openai axios sharp jimp
   ```

## Basic Usage

### Generating Character Spritesheets

To generate a character spritesheet, use the `generateCharacterSpritesheet` function:

```javascript
import { generateCharacterSpritesheet } from 'spriteai';

const description = 'A brave knight in shining armor';
const options = {
  states: ['idle', 'walk', 'run', 'attack'],
  framesPerState: 6,
  size: '1024x1024',
  style: 'pixel-art',
  direction: 'right'
};

const result = await generateCharacterSpritesheet(description, options);
console.log(result);
```

This will generate a spritesheet with the specified animation states and return an object containing the original image URL, the base64-encoded spritesheet, and metadata about the generated sprites.

### Generating Landscape Sprites

To generate a landscape sprite, use the `generateLandscapeSprite` function:

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

This will generate a landscape sprite based on the provided description and options, returning an object with the original image URL, the base64-encoded landscape sprite, and relevant metadata.

## Key Features

1. **Character Spritesheet Generation**: Create animated character spritesheets with customizable states, frames, and styles.

2. **Landscape Sprite Generation**: Generate detailed landscape sprites for game backgrounds with various environmental settings.

3. **Customizable Options**: Adjust parameters such as size, style, time of day, weather, and perspective to fine-tune your generated assets.

4. **Background Removal**: Automatically remove backgrounds from generated sprites for easier integration into your game.

5. **Metadata**: Receive detailed metadata about generated assets, including frame data for character animations and dimension information.

6. **File Saving**: Option to automatically save generated assets to your project's assets folder.

7. **Flexible Art Styles**: Generate assets in various styles, including pixel art, vector, 3D, hand-drawn, and anime.

## Advanced Usage

### Fetching Available Animation States

You can fetch the list of available animation states using the `fetchAvailableAnimationStates` function:

```javascript
import { fetchAvailableAnimationStates } from 'spriteai';

const states = await fetchAvailableAnimationStates();
console.log(states);
```

### Fetching Available Sprite Styles

To get the list of available sprite styles, use the `fetchAvailableSpriteStyles` function:

```javascript
import { fetchAvailableSpriteStyles } from 'spriteai';

const styles = await fetchAvailableSpriteStyles();
console.log(styles);
```

### Generating Environment Sprites

For creating sets of environment sprites, use the `generateEnvironmentSprites` function:

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

This will generate a tileset of environment sprites based on the provided description and options.

## Next Steps

Now that you're familiar with the basics of SpriteAI, you can start integrating it into your game development workflow. Experiment with different descriptions, styles, and options to create unique and engaging game assets for your projects.

For more detailed information on each function and its parameters, refer to the API documentation.