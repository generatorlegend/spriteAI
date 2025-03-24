<response>

# SpriteAI API Reference

## Table of Contents

1. [Character Sprite Generation](#character-sprite-generation)
   - [generateCharacterSpritesheet](#generatecharacterspritesheet)
2. [Environment Sprite Generation](#environment-sprite-generation)
   - [generateLandscapeSprite](#generatelandscapesprite)
   - [generateEnvironmentSprites](#generateenvironmentsprites)
3. [Utility Functions](#utility-functions)
   - [removeBackgroundColor](#removebackgroundcolor)
4. [SDK-specific Functions](#sdk-specific-functions)
   - [fetchAvailableAnimationStates](#fetchavailableanimationstates)
   - [fetchAvailableSpriteStyles](#fetchavailablespritestyles)

## Character Sprite Generation

### generateCharacterSpritesheet

Generates a character spritesheet based on the provided description and options.

**Location**: `index.js`, `spriteAI/index.js`

**Syntax**:
```javascript
async function generateCharacterSpritesheet(description, options = {})
```

**Parameters**:
- `description` (string): A description of the character to generate.
- `options` (object, optional): Configuration options for the spritesheet generation.
  - `states` (array of strings, default: `['idle', 'walk', 'run', 'attack']`): Animation states to generate.
  - `framesPerState` (number, default: 6): Number of frames per animation state.
  - `size` (string, default: '1024x1024'): Output size of the spritesheet.
  - `style` (string, default: 'pixel-art'): Art style of the character.
  - `padding` (number, default: 1): Padding between sprites.
  - `direction` (string, default: 'right'): Base direction of the character.
  - `save` (boolean, optional): Whether to save the generated image to file.

**Returns**: (object)
- `original` (string): URL of the original generated image.
- `spritesheet` (string): Base64-encoded data URL of the processed spritesheet.
- `metadata` (object): Metadata about the generated spritesheet.
  - `states` (array): List of animation states.
  - `framesPerState` (number): Number of frames per state.
  - `totalFrames` (number): Total number of frames in the spritesheet.
  - `dimensions` (object): Width and height of the spritesheet.
  - `frameData` (object): Detailed information about each animation state.

**Example Usage**:
```javascript
const result = await generateCharacterSpritesheet('a medieval knight', {
  states: ['idle', 'walk', 'attack'],
  framesPerState: 8,
  size: '2048x2048',
  style: 'pixel-art',
  save: true
});
console.log(result.metadata);
```

## Environment Sprite Generation

### generateLandscapeSprite

Generates a landscape sprite based on the provided description and options.

**Location**: `index.js`

**Syntax**:
```javascript
async function generateLandscapeSprite(description, options = {})
```

**Parameters**:
- `description` (string): A description of the landscape to generate.
- `options` (object, optional): Configuration options for the landscape generation.
  - `size` (string, default: '1024x1024'): Output size of the sprite.
  - `style` (string, default: 'pixel-art'): Art style of the landscape.
  - `timeOfDay` (string, default: 'day'): Time of day setting (day, night, sunset, dawn).
  - `weather` (string, default: 'clear'): Weather conditions (clear, rainy, foggy, snowy).
  - `perspective` (string, default: 'side-scrolling'): Perspective of the landscape (side-scrolling, top-down, isometric).
  - `save` (boolean, default: false): Whether to save the generated image to file.
  - `removeBackground` (boolean, optional): Whether to remove the background.
  - `backgroundColor` (string, optional): Background color to remove (if removeBackground is true).
  - `colorThreshold` (number, optional): Threshold for background color removal.

**Returns**: (object)
- `original` (string): URL of the original generated image.
- `landscape` (string): Base64-encoded data URL of the processed landscape sprite.
- `metadata` (object): Metadata about the generated landscape.
  - `description` (string): Original description of the landscape.
  - `style` (string): Art style used.
  - `timeOfDay` (string): Time of day setting.
  - `weather` (string): Weather conditions.
  - `perspective` (string): Perspective of the landscape.
  - `dimensions` (object): Width and height of the sprite.

**Example Usage**:
```javascript
const result = await generateLandscapeSprite('a lush forest with a waterfall', {
  size: '2048x1024',
  style: 'pixel-art',
  timeOfDay: 'sunset',
  weather: 'clear',
  perspective: 'side-scrolling',
  save: true,
  removeBackground: true,
  backgroundColor: '#FFFFFF'
});
console.log(result.metadata);
```

### generateEnvironmentSprites

Generates a set of environment sprites based on the provided description and options.

**Location**: `spriteAI/index.js`

**Syntax**:
```javascript
async function generateEnvironmentSprites(description, options = {})
```

**Parameters**:
- `description` (string): A description of the environment to generate.
- `options` (object, optional): Configuration options for the environment generation.
  - `elements` (number, default: 4): Number of different elements to generate.
  - `size` (string, default: '1024x1024'): Output size of the tileset.
  - `style` (string, default: 'pixel-art'): Art style of the environment.
  - `padding` (number, default: 1): Padding between elements.
  - `theme` (string, default: 'fantasy'): Theme of the environment.
  - `save` (boolean, optional): Whether to save the generated image to file.

**Returns**: (object)
- `original` (string): URL of the original generated image.
- `tileset` (string): Base64-encoded data URL of the processed environment tileset.
- `metadata` (object): Metadata about the generated environment sprites.
  - `elements` (number): Number of different elements generated.
  - `theme` (string): Theme of the environment.
  - `dimensions` (object): Width and height of the tileset.
  - `tileData` (object): Information about the tile arrangement.

**Example Usage**:
```javascript
const result = await generateEnvironmentSprites('a sci-fi space station', {
  elements: 6,
  size: '2048x2048',
  style: 'vector',
  theme: 'futuristic',
  save: true
});
console.log(result.metadata);
```

## Utility Functions

### removeBackgroundColor

Removes a specified background color from an image.

**Location**: `index.js`, `spriteAI/index.js`

**Syntax**:
```javascript
async function removeBackgroundColor(inputPath, outputPath, targetColor, colorThreshold = 0, options = {})
```

**Parameters**:
- `inputPath` (string): Path to the input image file.
- `outputPath` (string): Path where the processed image will be saved.
- `targetColor` (string): CSS color string of the background color to remove.
- `colorThreshold` (number, default: 0): Threshold for color matching.
- `options` (object, optional): Additional options for background removal.

**Returns**: Promise that resolves when the background removal is complete.

**Example Usage**:
```javascript
await removeBackgroundColor('input.png', 'output.png', '#FFFFFF', 0.1);
```

## SDK-specific Functions

### fetchAvailableAnimationStates

Retrieves a list of available animation states for character sprites.

**Location**: `spriteAI/index.js`

**Syntax**:
```javascript
async function fetchAvailableAnimationStates()
```

**Returns**: (array) List of available animation states.

**Example Usage**:
```javascript
const states = await fetchAvailableAnimationStates();
console.log(states); // ['idle', 'walk', 'run', 'attack', 'jump', 'fall', 'hurt', 'die']
```

### fetchAvailableSpriteStyles

Retrieves a list of available sprite styles.

**Location**: `spriteAI/index.js`

**Syntax**:
```javascript
async function fetchAvailableSpriteStyles()
```

**Returns**: (array) List of available sprite styles.

**Example Usage**:
```javascript
const styles = await fetchAvailableSpriteStyles();
console.log(styles); // ['pixel-art', 'vector', '3d', 'hand-drawn', 'anime']
```

</response># SpriteAI API Reference

## Table of Contents

1. [Character Sprite Generation](#character-sprite-generation)
   - [generateCharacterSpritesheet](#generatecharacterspritesheet)
2. [Environment Sprite Generation](#environment-sprite-generation)
   - [generateLandscapeSprite](#generatelandscapesprite)
   - [generateEnvironmentSprites](#generateenvironmentsprites)
3. [Utility Functions](#utility-functions)
   - [removeBackgroundColor](#removebackgroundcolor)
4. [SDK-specific Functions](#sdk-specific-functions)
   - [fetchAvailableAnimationStates](#fetchavailableanimationstates)
   - [fetchAvailableSpriteStyles](#fetchavailablespritestyles)

## Character Sprite Generation

### generateCharacterSpritesheet

Generates a character spritesheet based on the provided description and options.

**Location**: `index.js`, `spriteAI/index.js`

**Syntax**:
```javascript
async function generateCharacterSpritesheet(description, options = {})
```

**Parameters**:
- `description` (string): A description of the character to generate.
- `options` (object, optional): Configuration options for the spritesheet generation.
  - `states` (array of strings, default: `['idle', 'walk', 'run', 'attack']`): Animation states to generate.
  - `framesPerState` (number, default: 6): Number of frames per animation state.
  - `size` (string, default: '1024x1024'): Output size of the spritesheet.
  - `style` (string, default: 'pixel-art'): Art style of the character.
  - `padding` (number, default: 1): Padding between sprites.
  - `direction` (string, default: 'right'): Base direction of the character.
  - `save` (boolean, optional): Whether to save the generated image to file.

**Returns**: (object)
- `original` (string): URL of the original generated image.
- `spritesheet` (string): Base64-encoded data URL of the processed spritesheet.
- `metadata` (object): Metadata about the generated spritesheet.
  - `states` (array): List of animation states.
  - `framesPerState` (number): Number of frames per state.
  - `totalFrames` (number): Total number of frames in the spritesheet.
  - `dimensions` (object): Width and height of the spritesheet.
  - `frameData` (object): Detailed information about each animation state.

**Example Usage**:
```javascript
const result = await generateCharacterSpritesheet('a medieval knight', {
  states: ['idle', 'walk', 'attack'],
  framesPerState: 8,
  size: '2048x2048',
  style: 'pixel-art',
  save: true
});
console.log(result.metadata);
```

## Environment Sprite Generation

### generateLandscapeSprite

Generates a landscape sprite based on the provided description and options.

**Location**: `index.js`

**Syntax**:
```javascript
async function generateLandscapeSprite(description, options = {})
```

**Parameters**:
- `description` (string): A description of the landscape to generate.
- `options` (object, optional): Configuration options for the landscape generation.
  - `size` (string, default: '1024x1024'): Output size of the sprite.
  - `style` (string, default: 'pixel-art'): Art style of the landscape.
  - `timeOfDay` (string, default: 'day'): Time of day setting (day, night, sunset, dawn).
  - `weather` (string, default: 'clear'): Weather conditions (clear, rainy, foggy, snowy).
  - `perspective` (string, default: 'side-scrolling'): Perspective of the landscape (side-scrolling, top-down, isometric).
  - `save` (boolean, default: false): Whether to save the generated image to file.
  - `removeBackground` (boolean, optional): Whether to remove the background.
  - `backgroundColor` (string, optional): Background color to remove (if removeBackground is true).
  - `colorThreshold` (number, optional): Threshold for background color removal.

**Returns**: (object)
- `original` (string): URL of the original generated image.
- `landscape` (string): Base64-encoded data URL of the processed landscape sprite.
- `metadata` (object): Metadata about the generated landscape.
  - `description` (string): Original description of the landscape.
  - `style` (string): Art style used.
  - `timeOfDay` (string): Time of day setting.
  - `weather` (string): Weather conditions.
  - `perspective` (string): Perspective of the landscape.
  - `dimensions` (object): Width and height of the sprite.

**Example Usage**:
```javascript
const result = await generateLandscapeSprite('a lush forest with a waterfall', {
  size: '2048x1024',
  style: 'pixel-art',
  timeOfDay: 'sunset',
  weather: 'clear',
  perspective: 'side-scrolling',
  save: true,
  removeBackground: true,
  backgroundColor: '#FFFFFF'
});
console.log(result.metadata);
```

### generateEnvironmentSprites

Generates a set of environment sprites based on the provided description and options.

**Location**: `spriteAI/index.js`

**Syntax**:
```javascript
async function generateEnvironmentSprites(description, options = {})
```

**Parameters**:
- `description` (string): A description of the environment to generate.
- `options` (object, optional): Configuration options for the environment generation.
  - `elements` (number, default: 4): Number of different elements to generate.
  - `size` (string, default: '1024x1024'): Output size of the tileset.
  - `style` (string, default: 'pixel-art'): Art style of the environment.
  - `padding` (number, default: 1): Padding between elements.
  - `theme` (string, default: 'fantasy'): Theme of the environment.
  - `save` (boolean, optional): Whether to save the generated image to file.

**Returns**: (object)
- `original` (string): URL of the original generated image.
- `tileset` (string): Base64-encoded data URL of the processed environment tileset.
- `metadata` (object): Metadata about the generated environment sprites.
  - `elements` (number): Number of different elements generated.
  - `theme` (string): Theme of the environment.
  - `dimensions` (object): Width and height of the tileset.
  - `tileData` (object): Information about the tile arrangement.

**Example Usage**:
```javascript
const result = await generateEnvironmentSprites('a sci-fi space station', {
  elements: 6,
  size: '2048x2048',
  style: 'vector',
  theme: 'futuristic',
  save: true
});
console.log(result.metadata);
```

## Utility Functions

### removeBackgroundColor

Removes a specified background color from an image.

**Location**: `index.js`, `spriteAI/index.js`

**Syntax**:
```javascript
async function removeBackgroundColor(inputPath, outputPath, targetColor, colorThreshold = 0, options = {})
```

**Parameters**:
- `inputPath` (string): Path to the input image file.
- `outputPath` (string): Path where the processed image will be saved.
- `targetColor` (string): CSS color string of the background color to remove.
- `colorThreshold` (number, default: 0): Threshold for color matching.
- `options` (object, optional): Additional options for background removal.

**Returns**: Promise that resolves when the background removal is complete.

**Example Usage**:
```javascript
await removeBackgroundColor('input.png', 'output.png', '#FFFFFF', 0.1);
```

## SDK-specific Functions

### fetchAvailableAnimationStates

Retrieves a list of available animation states for character sprites.

**Location**: `spriteAI/index.js`

**Syntax**:
```javascript
async function fetchAvailableAnimationStates()
```

**Returns**: (array) List of available animation states.

**Example Usage**:
```javascript
const states = await fetchAvailableAnimationStates();
console.log(states); // ['idle', 'walk', 'run', 'attack', 'jump', 'fall', 'hurt', 'die']
```

### fetchAvailableSpriteStyles

Retrieves a list of available sprite styles.

**Location**: `spriteAI/index.js`

**Syntax**:
```javascript
async function fetchAvailableSpriteStyles()
```

**Returns**: (array) List of available sprite styles.

**Example Usage**:
```javascript
const styles = await fetchAvailableSpriteStyles();
console.log(styles); // ['pixel-art', 'vector', '3d', 'hand-drawn', 'anime']
```