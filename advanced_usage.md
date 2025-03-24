<response>

# Advanced Usage Guide for SpriteAI

## Table of Contents
1. [Introduction](#introduction)
2. [Custom Animation States](#custom-animation-states)
3. [Complex Sprite Descriptions](#complex-sprite-descriptions)
4. [Integrating Generated Sprites](#integrating-generated-sprites)
5. [Advanced Techniques](#advanced-techniques)

## Introduction

This guide covers advanced usage of SpriteAI, including customizing animation states, creating complex sprite descriptions, and integrating generated sprites into various game engines and frameworks.

## Custom Animation States

By default, SpriteAI generates character spritesheets with four animation states: idle, walk, run, and attack. However, you can customize these states to fit your specific game requirements.

### Fetching Available Animation States

To see the full list of available animation states, use the `fetchAvailableAnimationStates` function:

```javascript
import { fetchAvailableAnimationStates } from 'spriteAI';

const availableStates = await fetchAvailableAnimationStates();
console.log(availableStates);
// Output: ['idle', 'walk', 'run', 'attack', 'jump', 'fall', 'hurt', 'die']
```

### Customizing Animation States

When calling `generateCharacterSpritesheet`, you can specify custom animation states:

```javascript
import { generateCharacterSpritesheet } from 'spriteAI';

const result = await generateCharacterSpritesheet('a warrior', {
  states: ['idle', 'attack', 'defend', 'cast_spell'],
  framesPerState: 8
});
```

This will generate a spritesheet with four rows, each representing the specified animation state with 8 frames per state.

## Complex Sprite Descriptions

To get the best results from SpriteAI, it's important to provide detailed and specific descriptions. Here are some tips for creating complex sprite descriptions:

1. Be specific about character features:
   ```javascript
   const description = 'a tall, muscular orc warrior with green skin, wearing heavy plate armor and wielding a massive battle axe';
   ```

2. Include environmental context:
   ```javascript
   const description = 'a stealthy elven archer in a dense, misty forest, wearing camouflage and holding a longbow';
   ```

3. Specify art style details:
   ```javascript
   const options = {
     style: 'pixel-art',
     description: 'a cute, chibi-style wizard with oversized head and bright, colorful robes, casting a fireball spell'
   };
   ```

### Fetching Available Sprite Styles

To see the available sprite styles, use the `fetchAvailableSpriteStyles` function:

```javascript
import { fetchAvailableSpriteStyles } from 'spriteAI';

const availableStyles = await fetchAvailableSpriteStyles();
console.log(availableStyles);
// Output: ['pixel-art', 'vector', '3d', 'hand-drawn', 'anime']
```

## Integrating Generated Sprites

SpriteAI generates spritesheets that can be easily integrated into various game engines and frameworks. Here are some examples:

### Phaser 3

```javascript
function preload() {
  this.load.spritesheet('character', 'path/to/generated_spritesheet.png', {
    frameWidth: 64,  // Adjust based on your sprite size
    frameHeight: 64
  });
}

function create() {
  const character = this.add.sprite(400, 300, 'character');
  
  this.anims.create({
    key: 'idle',
    frames: this.anims.generateFrameNumbers('character', { start: 0, end: 5 }),
    frameRate: 10,
    repeat: -1
  });
  
  character.play('idle');
}
```

### Unity (C#)

```csharp
public class CharacterController : MonoBehaviour
{
    public Sprite[] sprites;
    private SpriteRenderer spriteRenderer;
    
    void Start()
    {
        spriteRenderer = GetComponent<SpriteRenderer>();
        StartCoroutine(AnimateSprite());
    }
    
    IEnumerator AnimateSprite()
    {
        int currentFrame = 0;
        while (true)
        {
            spriteRenderer.sprite = sprites[currentFrame];
            currentFrame = (currentFrame + 1) % sprites.Length;
            yield return new WaitForSeconds(0.1f);  // Adjust timing as needed
        }
    }
}
```

## Advanced Techniques

### Generating Environment Sprites

In addition to character sprites, SpriteAI can generate environment sprites using the `generateEnvironmentSprites` function:

```javascript
import { generateEnvironmentSprites } from 'spriteAI';

const result = await generateEnvironmentSprites('medieval castle', {
  elements: 6,
  style: 'pixel-art',
  theme: 'fantasy'
});

console.log(result.tileset);  // Base64 encoded tileset image
console.log(result.metadata);  // Metadata about the generated tileset
```

This generates a tileset with 6 different elements suitable for creating a medieval castle environment in a fantasy-themed game.

### Removing Backgrounds

For sprites that require transparency, you can use the `removeBackgroundColor` function:

```javascript
import { removeBackgroundColor } from 'spriteAI';

await removeBackgroundColor(
  'input_image.png',
  'output_image.png',
  '#FFFFFF',  // Target color to remove (white in this case)
  0.1  // Color threshold
);
```

This function removes the specified background color, making it transparent. Adjust the color threshold to fine-tune the removal process.

By leveraging these advanced techniques and customization options, you can create unique and tailored sprite assets for your game development projects using SpriteAI.

</response>