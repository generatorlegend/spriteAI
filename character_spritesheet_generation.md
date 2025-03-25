# Character Spritesheet Generation

## Overview

The SpriteAI library provides a powerful function `generateCharacterSpritesheet` for creating character spritesheets using AI-generated images. This guide will walk you through the process of using this function, explain its parameters and options, and provide tips for getting the best results.

## Function Signature

```javascript
async function generateCharacterSpritesheet(description, options = {})
```

### Parameters

- `description` (string): A detailed description of the character you want to generate.
- `options` (object): An optional object containing customization parameters.

## Options

The `options` object can include the following properties:

- `states` (array): Animation states to generate (default: `['idle', 'walk', 'run', 'attack']`)
- `framesPerState` (number): Number of frames per animation state (default: `6`)
- `size` (string): Output size of the spritesheet (default: `'1024x1024'`)
- `style` (string): Art style of the character (default: `'pixel-art'`)
- `padding` (number): Padding between sprites (default: `1`)
- `direction` (string): Base direction of the character (default: `'right'`)
- `save` (boolean): Whether to save the generated image to disk (default: `false`)

## Usage Example

```javascript
import { generateCharacterSpritesheet } from 'spriteAI';

const result = await generateCharacterSpritesheet('A fierce warrior with armor and a sword', {
  states: ['idle', 'walk', 'run', 'attack', 'jump'],
  framesPerState: 8,
  style: 'pixel-art',
  direction: 'left'
});

console.log(result);
```

## Returned Data Structure

The function returns an object with the following properties:

- `original` (string): URL of the original generated image
- `spritesheet` (string): Base64-encoded PNG data of the processed spritesheet
- `metadata` (object): Contains information about the generated spritesheet
  - `states` (array): List of animation states
  - `framesPerState` (number): Number of frames per state
  - `totalFrames` (number): Total number of frames in the spritesheet
  - `dimensions` (object): Width and height of the spritesheet
  - `frameData` (object): Detailed information about each animation state

## Tips for Best Results

1. **Detailed Descriptions**: Provide a clear and detailed description of the character, including appearance, clothing, and any distinctive features.

2. **Consistent Style**: Specify a consistent art style in the `style` option to ensure coherent results across different generations.

3. **Appropriate Frame Count**: Adjust the `framesPerState` based on the complexity of the animation. More frames can result in smoother animations but may require more processing time.

4. **Balanced States**: Choose a set of animation states that provide a good range of character actions without overwhelming the spritesheet.

5. **Size Considerations**: The `size` option affects the overall quality and detail of the spritesheet. Larger sizes may provide more detail but require more processing time.

6. **Direction Matters**: The `direction` option sets the base orientation of the character. Consider how this will affect your game's design and choose accordingly.

7. **Iterate and Refine**: Don't hesitate to generate multiple spritesheets with slightly different descriptions or options to find the best result for your needs.

## Advanced Usage

### Custom Animation States

You can specify custom animation states to suit your game's needs:

```javascript
const result = await generateCharacterSpritesheet('A mage casting spells', {
  states: ['idle', 'cast', 'teleport', 'defend', 'die'],
  framesPerState: 10
});
```

### Different Art Styles

Experiment with different art styles to find the perfect look for your game:

```javascript
const pixelArtResult = await generateCharacterSpritesheet('A cute robot', { style: 'pixel-art' });
const vectorResult = await generateCharacterSpritesheet('A cute robot', { style: 'vector' });
const animeResult = await generateCharacterSpritesheet('A cute robot', { style: 'anime' });
```

### Saving Generated Spritesheets

To automatically save the generated spritesheet to disk:

```javascript
const result = await generateCharacterSpritesheet('A stealthy ninja', {
  save: true
});
// The spritesheet will be saved in the 'assets' folder
```

## Conclusion

The `generateCharacterSpritesheet` function provides a powerful tool for quickly creating character spritesheets for your game development needs. By understanding its options and following the tips provided, you can generate high-quality, customized spritesheets that bring your characters to life.

Remember to experiment with different descriptions, styles, and options to achieve the best results for your specific game requirements.