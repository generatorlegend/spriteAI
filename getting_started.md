# Getting Started with SpriteAI

SpriteAI is a powerful library that allows you to generate character spritesheets and landscape sprites using AI. This guide will help you get started with SpriteAI, covering installation, basic usage, and an overview of its main features.

## Installation

To install SpriteAI, follow these steps:

1. Ensure you have Node.js (version 12 or higher) and npm installed on your system.

2. Clone the SpriteAI repository:
   ```bash
   git clone https://github.com/your-username/spriteAI.git
   cd spriteAI
   ```

3. Install the required dependencies:
   ```bash
   npm install
   ```

## Basic Usage

### Generating Character Spritesheets

To generate a character spritesheet, you can use the `generateCharacterSpritesheet` function. Here's a basic example:

```javascript
import { generateCharacterSpritesheet } from './index.js';

async function generateSprite() {
  const result = await generateCharacterSpritesheet('a cute robot', {
    states: ['idle', 'walk', 'run', 'attack'],
    framesPerState: 6,
    size: '1024x1024',
    style: 'pixel-art',
    save: true
  });

  console.log('Spritesheet generated:', result);
}

generateSprite();
```

This will generate a spritesheet of a cute robot with idle, walk, run, and attack animations, each having 6 frames.

### Generating Landscape Sprites

To create a landscape sprite, use the `generateLandscapeSprite` function:

```javascript
import { generateLandscapeSprite } from './index.js';

async function generateLandscape() {
  const result = await generateLandscapeSprite('a lush forest with a waterfall', {
    size: '1024x1024',
    style: 'pixel-art',
    timeOfDay: 'sunset',
    weather: 'clear',
    perspective: 'side-scrolling',
    save: true
  });

  console.log('Landscape sprite generated:', result);
}

generateLandscape();
```

This will create a pixel-art landscape sprite of a lush forest with a waterfall at sunset.

## Main Features

### Character Spritesheet Generation

- Create spritesheets with multiple animation states
- Customize the number of frames per state
- Set the output size and art style
- Option to save the generated spritesheet

### Landscape Sprite Generation

- Generate detailed landscape scenes
- Customize time of day and weather conditions
- Choose perspective (side-scrolling, top-down, isometric)
- Option to remove background color

### Customization Options

Both functions offer various customization options:

- `size`: Set the output image size (e.g., '1024x1024')
- `style`: Choose the art style (e.g., 'pixel-art')
- `save`: Option to automatically save the generated image

Character spritesheets have additional options like `states`, `framesPerState`, and `direction`, while landscape sprites have `timeOfDay`, `weather`, and `perspective` options.

## Advanced Usage

### Removing Background Color

For landscape sprites, you can remove the background color:

```javascript
const result = await generateLandscapeSprite('a desert oasis', {
  removeBackground: true,
  backgroundColor: '#FFFFFF',
  colorThreshold: 0.1
});
```

This will remove the white background from the generated landscape sprite.

## Conclusion

SpriteAI provides a simple yet powerful way to generate game assets using AI. By following this guide, you should now be able to install the library, generate basic character spritesheets and landscape sprites, and understand the main features and customization options available.

For more detailed information on each function and its parameters, refer to the API documentation or explore the source code in `index.js`.