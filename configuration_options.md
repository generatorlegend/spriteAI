# Configuration Options for Sprite Generation

This guide explains all available configuration options for generating character spritesheets and landscape sprites using our sprite generation SDK.

## Character Spritesheet Configuration

When using the `generateCharacterSpritesheet` function, you can customize various aspects of the generated spritesheet. Here are the available options:

### states
- Type: Array of strings
- Default: `['idle', 'walk', 'run', 'attack']`
- Description: Specifies the animation states to generate for the character. Each state will be represented as a row in the spritesheet.
- Example: `['idle', 'walk', 'run', 'attack', 'jump']`

### framesPerState
- Type: Number
- Default: 6
- Description: Determines the number of frames to generate for each animation state.
- Example: `8`

### size
- Type: String
- Default: '1024x1024'
- Description: Sets the output size of the generated spritesheet.
- Example: '2048x2048'

### style
- Type: String
- Default: 'pixel-art'
- Description: Specifies the art style for the character sprite.
- Example: 'vector'

### padding
- Type: Number
- Default: 1
- Description: Sets the padding between individual sprite frames in the spritesheet.
- Example: 2

### direction
- Type: String
- Default: 'right'
- Description: Determines the base direction the character is facing in the spritesheet.
- Example: 'left'

### save
- Type: Boolean
- Default: false
- Description: When set to true, saves the generated spritesheet to the local file system.
- Example: true

Example usage:

```javascript
const options = {
  states: ['idle', 'walk', 'run', 'attack', 'jump'],
  framesPerState: 8,
  size: '2048x2048',
  style: 'vector',
  padding: 2,
  direction: 'left',
  save: true
};

const result = await generateCharacterSpritesheet('A heroic knight', options);
```

## Landscape Sprite Configuration

When using the `generateLandscapeSprite` function, you can customize various aspects of the generated landscape. Here are the available options:

### size
- Type: String
- Default: '1024x1024'
- Description: Sets the output size of the generated landscape sprite.
- Example: '2048x1024'

### style
- Type: String
- Default: 'pixel-art'
- Description: Specifies the art style for the landscape sprite.
- Example: '3d'

### timeOfDay
- Type: String
- Default: 'day'
- Description: Sets the time of day for the landscape scene.
- Possible values: 'day', 'night', 'sunset', 'dawn'

### weather
- Type: String
- Default: 'clear'
- Description: Specifies the weather conditions for the landscape scene.
- Possible values: 'clear', 'rainy', 'foggy', 'snowy'

### perspective
- Type: String
- Default: 'side-scrolling'
- Description: Determines the perspective of the landscape scene.
- Possible values: 'side-scrolling', 'top-down', 'isometric'

### save
- Type: Boolean
- Default: false
- Description: When set to true, saves the generated landscape sprite to the local file system.
- Example: true

### removeBackground
- Type: Boolean
- Default: false
- Description: When set to true, attempts to remove the background from the generated sprite.

### backgroundColor
- Type: String
- Default: '#FFFFFF'
- Description: Specifies the background color to be removed when `removeBackground` is true.
- Example: '#000000'

### colorThreshold
- Type: Number
- Default: 0.1
- Description: Sets the color difference threshold for background removal. A higher value will remove colors more aggressively.
- Example: 0.2

Example usage:

```javascript
const options = {
  size: '2048x1024',
  style: '3d',
  timeOfDay: 'sunset',
  weather: 'foggy',
  perspective: 'isometric',
  save: true,
  removeBackground: true,
  backgroundColor: '#EEEEEE',
  colorThreshold: 0.15
};

const result = await generateLandscapeSprite('A mystical forest', options);
```

## Additional SDK Functions

### fetchAvailableAnimationStates()

This function returns an array of available animation states that can be used in the `states` option for character spritesheet generation.

Example usage:

```javascript
const availableStates = await fetchAvailableAnimationStates();
console.log(availableStates);
// Output: ['idle', 'walk', 'run', 'attack', 'jump', 'fall', 'hurt', 'die']
```

### fetchAvailableSpriteStyles()

This function returns an array of available sprite styles that can be used in the `style` option for both character and landscape sprite generation.

Example usage:

```javascript
const availableStyles = await fetchAvailableSpriteStyles();
console.log(availableStyles);
// Output: ['pixel-art', 'vector', '3d', 'hand-drawn', 'anime']
```

By utilizing these configuration options and additional SDK functions, you can fine-tune the sprite generation process to meet your specific game development needs.