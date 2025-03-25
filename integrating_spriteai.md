# Integrating SpriteAI into Game Development Workflows

SpriteAI is a powerful tool for generating character spritesheets, landscape sprites, and environment sprites for game development. This guide will walk you through integrating SpriteAI into various game development workflows and engines, providing examples and tips for optimal usage.

## Table of Contents

1. [Getting Started](#getting-started)
2. [Generating Spritesheets](#generating-spritesheets)
3. [Creating Landscape Sprites](#creating-landscape-sprites)
4. [Working with Environment Sprites](#working-with-environment-sprites)
5. [Integrating with Game Engines](#integrating-with-game-engines)
6. [Optimizing Sprite Usage](#optimizing-sprite-usage)
7. [Handling SpriteAI Metadata](#handling-spriteai-metadata)

## Getting Started

To begin using SpriteAI in your game development project, you'll need to import the necessary functions:

```javascript
import { 
  generateCharacterSpritesheet, 
  generateLandscapeSprite, 
  generateEnvironmentSprites,
  fetchAvailableAnimationStates,
  fetchAvailableSpriteStyles
} from 'spriteai';
```

## Generating Spritesheets

Character spritesheets can be generated using the `generateCharacterSpritesheet` function. Here's an example of how to use it:

```javascript
const characterDescription = "A medieval knight in shining armor";
const options = {
  states: ['idle', 'walk', 'run', 'attack'],
  framesPerState: 6,
  size: '1024x1024',
  style: 'pixel-art',
  direction: 'right',
  save: true
};

const result = await generateCharacterSpritesheet(characterDescription, options);
console.log(result.spritesheet); // Base64 encoded spritesheet
console.log(result.metadata); // Spritesheet metadata
```

## Creating Landscape Sprites

To generate landscape sprites, use the `generateLandscapeSprite` function:

```javascript
const landscapeDescription = "A lush forest with a winding river";
const options = {
  size: '1024x1024',
  style: 'pixel-art',
  timeOfDay: 'sunset',
  weather: 'clear',
  perspective: 'side-scrolling',
  save: true,
  removeBackground: true
};

const result = await generateLandscapeSprite(landscapeDescription, options);
console.log(result.landscape); // Base64 encoded landscape sprite
console.log(result.metadata); // Landscape sprite metadata
```

## Working with Environment Sprites

To create environment sprites, use the `generateEnvironmentSprites` function:

```javascript
const environmentDescription = "Medieval castle elements";
const options = {
  elements: 4,
  size: '1024x1024',
  style: 'pixel-art',
  theme: 'fantasy',
  save: true
};

const result = await generateEnvironmentSprites(environmentDescription, options);
console.log(result.tileset); // Base64 encoded environment tileset
console.log(result.metadata); // Environment tileset metadata
```

## Integrating with Game Engines

### Unity

To use SpriteAI-generated assets in Unity:

1. Save the generated spritesheet or sprite as a PNG file.
2. Import the PNG into your Unity project.
3. Set the Texture Type to "Sprite (2D and UI)".
4. For spritesheets, set the Sprite Mode to "Multiple" and use the Sprite Editor to slice the spritesheet.

Example Unity C# script for animating a character using a SpriteAI-generated spritesheet:

```csharp
using UnityEngine;

public class CharacterAnimator : MonoBehaviour
{
    public Sprite[] idleSprites;
    public Sprite[] walkSprites;
    public Sprite[] runSprites;
    public Sprite[] attackSprites;

    private SpriteRenderer spriteRenderer;
    private int currentFrame = 0;
    private float frameTime = 0.1f;
    private float timer = 0f;

    private void Start()
    {
        spriteRenderer = GetComponent<SpriteRenderer>();
    }

    private void Update()
    {
        timer += Time.deltaTime;
        if (timer >= frameTime)
        {
            timer = 0f;
            currentFrame = (currentFrame + 1) % idleSprites.Length;
            spriteRenderer.sprite = idleSprites[currentFrame];
        }
    }
}
```

### Phaser

To use SpriteAI-generated assets in Phaser:

1. Load the spritesheet or sprite in your preload function.
2. Create animations using the loaded spritesheet.

Example Phaser code for loading and animating a character:

```javascript
function preload() {
    this.load.spritesheet('character', 'path/to/spritesheet.png', { 
        frameWidth: 64, 
        frameHeight: 64 
    });
}

function create() {
    this.anims.create({
        key: 'idle',
        frames: this.anims.generateFrameNumbers('character', { start: 0, end: 5 }),
        frameRate: 10,
        repeat: -1
    });

    const player = this.add.sprite(400, 300, 'character');
    player.play('idle');
}
```

## Optimizing Sprite Usage

1. Use appropriate image compression techniques when saving sprites.
2. Consider using texture atlases for multiple small sprites.
3. Implement sprite pooling for frequently used game objects.
4. Use sprite batching to reduce draw calls in your game engine.

## Handling SpriteAI Metadata

SpriteAI functions return metadata that can be useful for game development. Here's how to leverage this information:

1. Use the `dimensions` data to set up your sprite rendering and collision detection.
2. Utilize the `frameData` for character spritesheets to set up animations programmatically.
3. For environment sprites, use the `tileData` to create tile maps or organize your level design.

Example of using metadata to set up character animations:

```javascript
const result = await generateCharacterSpritesheet(description, options);
const { frameData } = result.metadata;

Object.entries(frameData).forEach(([state, data]) => {
    game.anims.create({
        key: state,
        frames: game.anims.generateFrameNumbers('character', { 
            start: data.startFrame, 
            end: data.endFrame 
        }),
        frameRate: 10,
        repeat: -1
    });
});
```

By following these guidelines and examples, you can effectively integrate SpriteAI into your game development workflow, leveraging its powerful sprite generation capabilities to streamline your asset creation process.