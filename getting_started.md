# Getting Started with SpriteAI

SpriteAI is a powerful library that allows you to generate game-ready character spritesheets and landscape sprites using AI. This guide will help you get started with SpriteAI, covering installation, basic usage, and an overview of the main features.

## Installation

To install SpriteAI, you'll need Node.js and npm (Node Package Manager) installed on your system. Once you have these prerequisites, follow these steps:

1. Create a new directory for your project:
   ```
   mkdir my-spriteai-project
   cd my-spriteai-project
   ```

2. Initialize a new Node.js project:
   ```
   npm init -y
   ```

3. Install SpriteAI and its dependencies:
   ```
   npm install spriteai openai axios sharp jimp
   ```

## Basic Usage

### Generating Character Spritesheets

To generate a character spritesheet, you can use the `generateCharacterSpritesheet` function. Here's a basic example:

```javascript
import { generateCharacterSpritesheet } from 'spriteai';

async function generateCharacter() {
  const result = await generateCharacterSpritesheet('a cute cat warrior', {
    states: ['idle', 'walk', 'run', 'attack'],
    framesPerState: 6,
    size: '1024x1024',
    style: 'pixel-art',
    save: true
  });

  console.log('Character spritesheet generated:', result);
}

generateCharacter();
```

This will generate a pixel-art spritesheet of a cute cat warrior with idle, walk, run, and attack animations, each with 6 frames.

### Generating Landscape Sprites

To create a landscape sprite, use the `generateLandscapeSprite` function:

```javascript
import { generateLandscapeSprite } from 'spriteai';

async function generateLandscape() {
  const result = await generateLandscapeSprite('a lush forest with a waterfall', {
    size: '1024x1024',
    style: 'pixel-art',
    timeOfDay: 'day',
    weather: 'clear',
    perspective: 'side-scrolling',
    save: true
  });

  console.log('Landscape sprite generated:', result);
}

generateLandscape();
```

This will create a pixel-art landscape sprite of a lush forest with a waterfall, perfect for a side-scrolling game background.

## Main Features

SpriteAI offers several key features to enhance your game development workflow:

1. **Character Spritesheet Generation**: Create animated character spritesheets with customizable states, frames, and styles.

2. **Landscape Sprite Creation**: Generate detailed landscape sprites for game backgrounds with various environmental settings.

3. **Customizable Options**: Both character and landscape generations offer a wide range of customization options, including:
   - Size
   - Art style (e.g., pixel-art, vector, 3D)
   - Animation states (for characters)
   - Time of day and weather conditions (for landscapes)
   - Perspective (for landscapes)

4. **Automatic Saving**: Option to automatically save generated sprites to your project's assets folder.

5. **Metadata**: Each generated sprite comes with detailed metadata, including dimensions, frame data, and other relevant information.

6. **Background Removal**: For landscape sprites, there's an option to remove the background, making it easier to integrate into your games.

## Advanced Usage

### Fetching Available Animation States

You can retrieve a list of available animation states for character spritesheets:

```javascript
import { fetchAvailableAnimationStates } from 'spriteai';

async function getAnimationStates() {
  const states = await fetchAvailableAnimationStates();
  console.log('Available animation states:', states);
}

getAnimationStates();
```

### Fetching Available Sprite Styles

To get a list of available sprite styles:

```javascript
import { fetchAvailableSpriteStyles } from 'spriteai';

async function getSpriteStyles() {
  const styles = await fetchAvailableSpriteStyles();
  console.log('Available sprite styles:', styles);
}

getSpriteStyles();
```

### Generating Environment Sprites

For creating sets of environment sprites:

```javascript
import { generateEnvironmentSprites } from 'spriteai';

async function generateEnvironment() {
  const result = await generateEnvironmentSprites('medieval town', {
    elements: 4,
    size: '1024x1024',
    style: 'pixel-art',
    theme: 'fantasy',
    save: true
  });

  console.log('Environment sprites generated:', result);
}

generateEnvironment();
```

This will create a tileset of 4 different medieval town elements in a pixel-art style, suitable for a fantasy game environment.

## Conclusion

SpriteAI provides a powerful and flexible way to generate game assets using AI. By leveraging these functions, you can quickly create high-quality spritesheets and background elements for your games, saving time and resources in the development process.

For more detailed information on each function and its options, refer to the API documentation. Happy sprite generating!