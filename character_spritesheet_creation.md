# Character Spritesheet Creation

This guide provides detailed information on how to use the `generateCharacterSpritesheet` function to create character spritesheets for your game or application. We'll cover the function's parameters, available options, best practices for creating effective prompts, and tips for optimizing the generated spritesheets.

## Function Overview

The `generateCharacterSpritesheet` function allows you to generate a character spritesheet based on a text description. It uses AI-powered image generation to create a series of animation frames for different character states.

```javascript
const result = await generateCharacterSpritesheet(description, options);
```

## Parameters

1. `description` (string): A detailed description of the character you want to generate.
2. `options` (object): An optional object containing configuration options for the spritesheet generation.

## Options

The `options` object can include the following properties:

- `states` (array of strings): Animation states to generate. Default: `['idle', 'walk', 'run', 'attack']`
- `framesPerState` (number): Number of frames per animation state. Default: `6`
- `size` (string): Output size of the spritesheet. Default: `'1024x1024'`
- `style` (string): Art style of the character. Default: `'pixel-art'`
- `padding` (number): Padding between sprites. Default: `1`
- `direction` (string): Base direction the character faces. Default: `'right'`
- `save` (boolean): Whether to save the generated image to disk. Default: `false`

## Best Practices for Creating Effective Prompts

When crafting your character description, consider the following tips:

1. Be specific about the character's appearance, including clothing, accessories, and notable features.
2. Mention the character's overall style or theme (e.g., "medieval warrior" or "futuristic robot").
3. Include details about the character's personality or role, as this can influence their posture and expressions.
4. Specify any unique elements or abilities that should be represented in the animations.

Example prompt:
```
"A fierce orc warrior with green skin, wearing leather armor and wielding a large battle axe. The character has a muscular build and a menacing expression."
```

## Using the Function

Here's an example of how to use the `generateCharacterSpritesheet` function with custom options:

```javascript
import { generateCharacterSpritesheet } from './spriteAI';

const description = "A nimble elven archer with long blond hair, wearing a green tunic and brown leather boots. The character carries a wooden longbow and has a quiver of arrows on their back.";

const options = {
  states: ['idle', 'walk', 'run', 'attack', 'dodge'],
  framesPerState: 8,
  size: '2048x2048',
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
```

## Understanding the Result

The function returns an object with the following properties:

- `original` (string): URL of the original generated image.
- `spritesheet` (string): Base64-encoded data URL of the processed spritesheet.
- `metadata` (object): Contains information about the generated spritesheet, including:
  - `states` (array): List of animation states.
  - `framesPerState` (number): Number of frames per state.
  - `totalFrames` (number): Total number of frames in the spritesheet.
  - `dimensions` (object): Width and height of the spritesheet.
  - `frameData` (object): Detailed information about each animation state's frames.

## Tips for Optimizing Generated Spritesheets

1. **Consistent Character Size**: Ensure your description emphasizes the need for a consistent character size across all frames.

2. **Clear Separation**: Request clear separation between frames in your prompt to make it easier to extract individual sprites.

3. **Appropriate Frame Count**: Choose an appropriate `framesPerState` value. More frames can result in smoother animations but larger file sizes.

4. **Optimize Image Size**: Use the `size` option to generate an appropriate resolution for your needs. Larger sizes provide more detail but require more processing time and storage.

5. **Use Appropriate Art Style**: The `style` option can significantly affect the final result. Choose a style that fits your game's aesthetic and is suitable for spritesheet creation.

6. **Background Removal**: The function automatically generates sprites with a white background. If you need transparent backgrounds, you may need to post-process the spritesheet.

7. **Save and Reuse**: Use the `save` option to store generated spritesheets for future use, reducing the need for repeated API calls.

## Conclusion

The `generateCharacterSpritesheet` function provides a powerful tool for creating character spritesheets using AI-generated imagery. By following these guidelines and best practices, you can efficiently create high-quality spritesheets for your game development needs.

Remember to experiment with different descriptions and options to achieve the best results for your specific character designs and game requirements.