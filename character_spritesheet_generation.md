# Character Spritesheet Generation

This guide provides a detailed explanation of how to generate character spritesheets using the SpriteAI library's `generateCharacterSpritesheet` function. This powerful tool allows you to create customized spritesheets for game characters with various animation states, styles, and sizes.

## Overview

The `generateCharacterSpritesheet` function uses AI-powered image generation to create a complete character spritesheet based on your description and specified options. It's designed to streamline the process of creating game assets, particularly for pixel art style games.

## Function Signature

```javascript
async function generateCharacterSpritesheet(description, options = {})
```

### Parameters

1. `description` (string): A textual description of the character you want to generate.
2. `options` (object): An optional configuration object to customize the spritesheet generation.

## Options

The `options` object allows you to customize various aspects of the spritesheet generation. Here are the available options with their default values:

```javascript
{
  states: ['idle', 'walk', 'run', 'attack'],  // Animation states to generate
  framesPerState: 6,                          // Frames per animation state
  size: '1024x1024',                          // Output size
  style: 'pixel-art',                         // Art style
  padding: 1,                                 // Padding between sprites
  direction: 'right',                         // Base direction of character
  save: false                                 // Whether to save the generated image
}
```

### Customizing Options

- **states**: An array of strings representing the animation states you want to generate. Each state will be a row in the resulting spritesheet.
- **framesPerState**: The number of frames to generate for each animation state.
- **size**: The dimensions of the output image in the format 'WIDTHxHEIGHT'.
- **style**: The artistic style of the spritesheet. By default, it's set to 'pixel-art'.
- **padding**: The number of pixels to add as padding between individual sprite frames.
- **direction**: The base direction the character should face.
- **save**: A boolean indicating whether to save the generated spritesheet to disk.

## Usage Example

Here's a basic example of how to use the `generateCharacterSpritesheet` function:

```javascript
import { generateCharacterSpritesheet } from 'spriteai';

async function createWarriorSpritesheet() {
  const description = "A muscular warrior with a large sword and heavy armor";
  const options = {
    states: ['idle', 'walk', 'attack', 'defend'],
    framesPerState: 8,
    size: '1536x1536',
    style: 'pixel-art',
    direction: 'right',
    save: true
  };

  try {
    const result = await generateCharacterSpritesheet(description, options);
    console.log('Spritesheet generated successfully:', result);
  } catch (error) {
    console.error('Error generating spritesheet:', error);
  }
}

createWarriorSpritesheet();
```

## Return Value

The function returns a Promise that resolves to an object containing:

- `original`: URL of the original generated image.
- `spritesheet`: Base64-encoded string of the processed spritesheet image.
- `metadata`: An object containing detailed information about the generated spritesheet.

### Metadata Structure

```javascript
{
  states: ['idle', 'walk', 'run', 'attack'],
  framesPerState: 6,
  totalFrames: 24,
  dimensions: {
    width: 1024,
    height: 1024
  },
  frameData: {
    idle: { row: 0, frames: 6, startFrame: 0, endFrame: 5 },
    walk: { row: 1, frames: 6, startFrame: 6, endFrame: 11 },
    run: { row: 2, frames: 6, startFrame: 12, endFrame: 17 },
    attack: { row: 3, frames: 6, startFrame: 18, endFrame: 23 }
  }
}
```

This metadata provides valuable information for integrating the spritesheet into your game engine or animation system.

## Best Practices

1. **Detailed Descriptions**: Provide clear and detailed character descriptions for better results.
2. **Consistent Styles**: Keep the style consistent across different character generations for a cohesive game look.
3. **Optimize Frame Count**: Balance between smooth animations and file size by adjusting `framesPerState`.
4. **Test Different Sizes**: Experiment with different output sizes to find the best balance between detail and performance.
5. **Save Option**: Use the `save` option to automatically store generated spritesheets in your project's asset folder.

## Limitations and Considerations

- The quality and consistency of the generated spritesheets may vary based on the complexity of the description and the chosen options.
- Generation times can vary depending on the size and complexity of the requested spritesheet.
- Ensure you have the necessary permissions and comply with OpenAI's usage policies when using this function, as it relies on the DALL-E model.

## Conclusion

The `generateCharacterSpritesheet` function offers a powerful way to create custom character spritesheets for your game development projects. By leveraging AI-generated content, you can rapidly prototype and create diverse character animations, saving time in the asset creation process.