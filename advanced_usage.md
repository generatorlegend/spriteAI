# Advanced Usage of SpriteAI

## Custom Animation States

The SpriteAI library allows you to create custom animation states for your character spritesheets. By default, the `generateCharacterSpritesheet` function uses predefined states, but you can easily customize these to fit your specific game requirements.

```javascript
import { generateCharacterSpritesheet } from 'spriteAI';

const customStates = ['idle', 'walk', 'jump', 'crouch', 'swim'];

const result = await generateCharacterSpritesheet('a cyberpunk ninja', {
  states: customStates,
  framesPerState: 8,
  style: 'pixel-art'
});
```

This example creates a spritesheet with custom animation states, including a 'swim' state that isn't in the default set.

## Complex Scene Generation

For more elaborate game environments, you can use the `generateEnvironmentSprites` function to create detailed tilesets.

```javascript
import { generateEnvironmentSprites } from 'spriteAI';

const environmentResult = await generateEnvironmentSprites('futuristic cityscape', {
  elements: 6,
  style: 'vector',
  theme: 'sci-fi',
  size: '2048x2048'
});
```

This will generate a tileset with 6 different elements in a vector style, suitable for a sci-fi themed game.

## Integrating with Game Engines

### Phaser Integration

Here's an example of how to load and use a generated spritesheet in Phaser:

```javascript
function preload() {
  this.load.spritesheet('character', 
    'path/to/generated_spritesheet.png',
    { frameWidth: 64, frameHeight: 64 }
  );
}

function create() {
  const character = this.add.sprite(400, 300, 'character');
  
  this.anims.create({
    key: 'walk',
    frames: this.anims.generateFrameNumbers('character', { start: 6, end: 11 }),
    frameRate: 10,
    repeat: -1
  });
  
  character.play('walk');
}
```

### Web Application Integration

For web applications, you can use the base64 encoded spritesheet directly:

```javascript
import { generateCharacterSpritesheet } from 'spriteAI';

async function createCharacter() {
  const result = await generateCharacterSpritesheet('medieval knight');
  
  const img = new Image();
  img.src = result.spritesheet;
  document.body.appendChild(img);
  
  // Use result.metadata for animation frame data
  console.log(result.metadata.frameData);
}
```

## Advanced Techniques

### Background Removal

The `generateLandscapeSprite` function includes an option to remove the background:

```javascript
import { generateLandscapeSprite } from 'spriteAI';

const landscapeResult = await generateLandscapeSprite('tropical beach', {
  removeBackground: true,
  backgroundColor: '#FFFFFF',
  colorThreshold: 0.1
});
```

This creates a landscape sprite with a transparent background, which can be useful for layering in your game scenes.

### Combining Multiple Sprites

You can create complex scenes by combining multiple generated sprites:

```javascript
import { generateCharacterSpritesheet, generateLandscapeSprite, generateEnvironmentSprites } from 'spriteAI';

async function createGameScene() {
  const character = await generateCharacterSpritesheet('space explorer');
  const landscape = await generateLandscapeSprite('alien planet surface');
  const props = await generateEnvironmentSprites('alien flora', { elements: 8 });
  
  // Combine these elements in your game engine or rendering system
}
```

This approach allows you to create diverse and rich game environments by mixing and matching different generated elements.

## Performance Considerations

When using SpriteAI in your game development workflow, keep in mind that generating sprites can be computationally intensive. Consider implementing caching mechanisms or generating sprites during your build process rather than at runtime for better performance.

Remember to handle API rate limits and potential network issues when making requests to the OpenAI service in your production applications.

By leveraging these advanced techniques, you can create unique and dynamic game assets using SpriteAI, enhancing your game development process and creating visually appealing experiences for your players.