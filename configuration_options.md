# Configuration Options

This guide provides a detailed overview of all configuration options available in the SpriteAI library. We'll cover options for character spritesheets, landscape sprites, and environment sprites, explaining the impact of each option and providing recommended settings for different use cases.

## Character Spritesheets

The `generateCharacterSpritesheet` function accepts an options object with the following properties:

### states
- Type: Array of strings
- Default: `['idle', 'walk', 'run', 'attack']`
- Description: Defines the animation states to generate for the character.
- Impact: Determines the number and types of animations in the spritesheet.
- Recommended: Use the default for basic characters. Add more states like 'jump', 'fall', or 'die' for more complex characters.

### framesPerState
- Type: Number
- Default: 6
- Description: Specifies the number of frames for each animation state.
- Impact: Affects the smoothness of animations and the overall size of the spritesheet.
- Recommended: 4-8 frames for most animations. Use more frames for smoother animations or complex movements.

### size
- Type: String
- Default: '1024x1024'
- Description: Sets the output size of the generated image.
- Impact: Determines the resolution and file size of the spritesheet.
- Recommended: Use the default for high-quality sprites. Consider smaller sizes like '512x512' for mobile games or performance-critical applications.

### style
- Type: String
- Default: 'pixel-art'
- Description: Specifies the art style of the generated character.
- Impact: Affects the visual appearance and detail level of the sprite.
- Recommended: 'pixel-art' for retro-style games, 'vector' for modern 2D games, '3d' for isometric or 3D-style sprites.

### padding
- Type: Number
- Default: 1
- Description: Sets the padding between individual sprites in the sheet.
- Impact: Affects the spacing between frames and can prevent bleeding during rendering.
- Recommended: 1-2 pixels for most cases. Increase for larger sprites or to ensure clear separation.

### direction
- Type: String
- Default: 'right'
- Description: Specifies the base direction the character is facing.
- Impact: Determines the initial orientation of the character in the spritesheet.
- Recommended: Use 'right' for standard side-scrolling games. Consider 'left' or 'front' for specific game designs.

Example usage:

```javascript
const characterOptions = {
  states: ['idle', 'walk', 'run', 'attack', 'jump'],
  framesPerState: 8,
  size: '512x512',
  style: 'vector',
  padding: 2,
  direction: 'right'
};

const result = await generateCharacterSpritesheet('warrior', characterOptions);
```

## Landscape Sprites

The `generateLandscapeSprite` function accepts an options object with the following properties:

### size
- Type: String
- Default: '1024x1024'
- Description: Sets the output size of the generated landscape image.
- Impact: Determines the resolution and file size of the landscape sprite.
- Recommended: Use the default for detailed backgrounds. Consider larger sizes like '2048x2048' for scrolling backgrounds or smaller sizes for simple scenes.

### style
- Type: String
- Default: 'pixel-art'
- Description: Specifies the art style of the generated landscape.
- Impact: Affects the visual appearance and detail level of the landscape.
- Recommended: Match the style with your character sprites for consistency.

### timeOfDay
- Type: String
- Default: 'day'
- Options: 'day', 'night', 'sunset', 'dawn'
- Description: Sets the time of day for the landscape scene.
- Impact: Affects lighting, colors, and mood of the generated landscape.
- Recommended: Choose based on your game's setting or level design needs.

### weather
- Type: String
- Default: 'clear'
- Options: 'clear', 'rainy', 'foggy', 'snowy'
- Description: Specifies the weather conditions in the landscape.
- Impact: Affects visibility, atmosphere, and environmental elements in the scene.
- Recommended: Vary weather to create diverse environments or match your game's narrative.

### perspective
- Type: String
- Default: 'side-scrolling'
- Options: 'side-scrolling', 'top-down', 'isometric'
- Description: Sets the viewpoint of the landscape scene.
- Impact: Determines how the landscape is rendered and perceived.
- Recommended: Choose based on your game's camera perspective and gameplay style.

### save
- Type: Boolean
- Default: false
- Description: When true, saves the generated image to the local filesystem.
- Impact: Allows for persistent storage of generated landscapes.
- Recommended: Use true during development for easy access to generated assets.

### removeBackground
- Type: Boolean
- Default: undefined
- Description: When true, attempts to remove the white background from the generated image.
- Impact: Creates a transparent background, useful for layering sprites.
- Recommended: Use when you need to composite the landscape with other elements.

### backgroundColor
- Type: String
- Default: '#FFFFFF'
- Description: Specifies the background color to remove when removeBackground is true.
- Impact: Affects the color detection for background removal.
- Recommended: Adjust if the default white background removal isn't effective.

### colorThreshold
- Type: Number
- Default: 0.1
- Description: Sets the threshold for color difference when removing the background.
- Impact: Affects the sensitivity of background color detection.
- Recommended: Increase for more aggressive background removal, decrease for more conservative removal.

Example usage:

```javascript
const landscapeOptions = {
  size: '2048x1024',
  style: 'pixel-art',
  timeOfDay: 'sunset',
  weather: 'clear',
  perspective: 'side-scrolling',
  save: true,
  removeBackground: true,
  colorThreshold: 0.2
};

const result = await generateLandscapeSprite('mountain range', landscapeOptions);
```

## Environment Sprites

The `generateEnvironmentSprites` function accepts an options object with the following properties:

### elements
- Type: Number
- Default: 4
- Description: Specifies the number of distinct environment pieces to generate.
- Impact: Determines the variety and complexity of the generated tileset.
- Recommended: 4-9 for basic tilesets, more for complex environments.

### size
- Type: String
- Default: '1024x1024'
- Description: Sets the output size of the generated tileset image.
- Impact: Affects the resolution and detail of individual tiles.
- Recommended: Use the default for most cases. Increase for very detailed tilesets.

### style
- Type: String
- Default: 'pixel-art'
- Description: Specifies the art style of the generated environment sprites.
- Impact: Affects the visual appearance and detail level of the tiles.
- Recommended: Match the style with your character and landscape sprites for consistency.

### padding
- Type: Number
- Default: 1
- Description: Sets the padding between individual tiles in the set.
- Impact: Affects the spacing between tiles and can prevent bleeding during rendering.
- Recommended: 1-2 pixels for most cases. Increase for larger tiles or to ensure clear separation.

### theme
- Type: String
- Default: 'fantasy'
- Description: Specifies the thematic style of the environment.
- Impact: Influences the types of elements and overall aesthetic of the tileset.
- Recommended: Choose a theme that matches your game's setting (e.g., 'sci-fi', 'medieval', 'modern').

### save
- Type: Boolean
- Default: false
- Description: When true, saves the generated tileset to the local filesystem.
- Impact: Allows for persistent storage of generated environment sprites.
- Recommended: Use true during development for easy access to generated assets.

Example usage:

```javascript
const environmentOptions = {
  elements: 9,
  size: '1536x1536',
  style: 'pixel-art',
  padding: 2,
  theme: 'sci-fi',
  save: true
};

const result = await generateEnvironmentSprites('space station interior', environmentOptions);
```

By understanding and effectively using these configuration options, you can fine-tune the output of the SpriteAI library to match your specific game development needs. Experiment with different combinations to achieve the desired visual style and functionality for your project.