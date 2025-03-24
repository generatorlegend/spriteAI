<response>
---
title: SpriteAI SDK Usage Guide
description: A comprehensive guide on using the SpriteAI SDK, including features, best practices, and integration tips.
---

# SpriteAI SDK Usage Guide

This guide provides a comprehensive overview of the SpriteAI SDK, its features, and best practices for integration into various project types.

## Table of Contents

1. [Introduction](#introduction)
2. [Installation](#installation)
3. [Key Features](#key-features)
4. [Generating Character Spritesheets](#generating-character-spritesheets)
5. [Generating Environment Sprites](#generating-environment-sprites)
6. [Fetching Available Animation States](#fetching-available-animation-states)
7. [Fetching Available Sprite Styles](#fetching-available-sprite-styles)
8. [Best Practices](#best-practices)
9. [Integration Examples](#integration-examples)

## Introduction

The SpriteAI SDK is a powerful tool for generating game assets programmatically. It leverages AI to create character spritesheets and environment sprites based on text descriptions, making it an invaluable resource for game developers and designers.

## Installation

To install the SpriteAI SDK, use npm:

```bash
npm install spriteai-sdk
```

## Key Features

The SpriteAI SDK offers several key features:

1. Character spritesheet generation
2. Environment sprite generation
3. Fetching available animation states
4. Fetching available sprite styles

## Generating Character Spritesheets

The `generateCharacterSpritesheet` function is the core of the SDK for creating character animations. Here's how to use it:

```javascript
import { generateCharacterSpritesheet } from 'spriteai-sdk';

const result = await generateCharacterSpritesheet('a medieval knight in armor', {
  states: ['idle', 'walk', 'run', 'attack'],
  framesPerState: 6,
  size: '1024x1024',
  style: 'pixel-art',
  padding: 1,
  direction: 'right',
  save: true
});

console.log(result.spritesheet); // Base64 encoded PNG
console.log(result.metadata); // Metadata about the generated spritesheet
```

### Options

- `states`: Array of animation states (default: ['idle', 'walk', 'run', 'attack'])
- `framesPerState`: Number of frames per animation state (default: 6)
- `size`: Size of the output image (default: '1024x1024')
- `style`: Art style of the sprite (default: 'pixel-art')
- `padding`: Padding between frames (default: 1)
- `direction`: Direction the character faces (default: 'right')
- `save`: Whether to save the spritesheet to disk (default: false)

## Generating Environment Sprites

The `generateEnvironmentSprites` function creates tileset-style environment sprites:

```javascript
import { generateEnvironmentSprites } from 'spriteai-sdk';

const result = await generateEnvironmentSprites('forest', {
  elements: 4,
  size: '1024x1024',
  style: 'pixel-art',
  padding: 1,
  theme: 'fantasy',
  save: true
});

console.log(result.tileset); // Base64 encoded PNG
console.log(result.metadata); // Metadata about the generated tileset
```

### Options

- `elements`: Number of distinct environment pieces (default: 4)
- `size`: Size of the output image (default: '1024x1024')
- `style`: Art style of the sprites (default: 'pixel-art')
- `padding`: Padding between elements (default: 1)
- `theme`: Theme of the environment (default: 'fantasy')
- `save`: Whether to save the tileset to disk (default: false)

## Fetching Available Animation States

The SDK provides a function to fetch the available animation states:

```javascript
import { fetchAvailableAnimationStates } from 'spriteai-sdk';

const states = await fetchAvailableAnimationStates();
console.log(states); // ['idle', 'walk', 'run', 'attack', 'jump', 'fall', 'hurt', 'die']
```

## Fetching Available Sprite Styles

Similarly, you can fetch the available sprite styles:

```javascript
import { fetchAvailableSpriteStyles } from 'spriteai-sdk';

const styles = await fetchAvailableSpriteStyles();
console.log(styles); // ['pixel-art', 'vector', '3d', 'hand-drawn', 'anime']
```

## Best Practices

1. **Consistent Descriptions**: When generating multiple related sprites, use consistent descriptions to maintain a cohesive style.

2. **Optimize API Calls**: Cache the results of `fetchAvailableAnimationStates` and `fetchAvailableSpriteStyles` to reduce unnecessary API calls.

3. **Error Handling**: Always implement proper error handling when using the SDK functions, as they involve network requests.

4. **Asset Management**: Use the `save` option judiciously and implement a proper asset management system in your project.

5. **Performance Considerations**: Generate sprites during development or as part of your build process, rather than at runtime, to avoid performance issues.

## Integration Examples

### React Application

```javascript
import React, { useState, useEffect } from 'react';
import { generateCharacterSpritesheet, fetchAvailableAnimationStates } from 'spriteai-sdk';

function SpriteGenerator() {
  const [spritesheet, setSpritesheet] = useState(null);
  const [states, setStates] = useState([]);

  useEffect(() => {
    fetchAvailableAnimationStates().then(setStates);
  }, []);

  const handleGenerate = async () => {
    const result = await generateCharacterSpritesheet('a heroic warrior', {
      states: states.slice(0, 4),
      style: 'pixel-art'
    });
    setSpritesheet(result.spritesheet);
  };

  return (
    <div>
      <button onClick={handleGenerate}>Generate Sprite</button>
      {spritesheet && <img src={spritesheet} alt="Generated Spritesheet" />}
    </div>
  );
}
```

### Node.js CLI Tool

```javascript
#!/usr/bin/env node
import { generateEnvironmentSprites } from 'spriteai-sdk';
import fs from 'fs';

const description = process.argv[2];
const theme = process.argv[3];

if (!description || !theme) {
  console.error('Usage: generate-environment <description> <theme>');
  process.exit(1);
}

async function generateEnvironment() {
  try {
    const result = await generateEnvironmentSprites(description, { theme, save: true });
    console.log(`Environment sprites generated and saved to: ${result.metadata.filename}`);
  } catch (error) {
    console.error('Error generating environment sprites:', error);
  }
}

generateEnvironment();
```

By following this guide, you should be well-equipped to integrate and utilize the SpriteAI SDK in your projects, leveraging its powerful features to generate high-quality game assets programmatically.
</response>---
title: SpriteAI SDK Usage Guide
description: A comprehensive guide on using the SpriteAI SDK, including features, best practices, and integration tips.
---

# SpriteAI SDK Usage Guide

This guide provides a comprehensive overview of the SpriteAI SDK, its features, and best practices for integration into various project types.

## Table of Contents

1. [Introduction](#introduction)
2. [Installation](#installation)
3. [Key Features](#key-features)
4. [Generating Character Spritesheets](#generating-character-spritesheets)
5. [Generating Environment Sprites](#generating-environment-sprites)
6. [Fetching Available Animation States](#fetching-available-animation-states)
7. [Fetching Available Sprite Styles](#fetching-available-sprite-styles)
8. [Best Practices](#best-practices)
9. [Integration Examples](#integration-examples)

## Introduction

The SpriteAI SDK is a powerful tool for generating game assets programmatically. It leverages AI to create character spritesheets and environment sprites based on text descriptions, making it an invaluable resource for game developers and designers.

## Installation

To install the SpriteAI SDK, use npm:

```bash
npm install spriteai-sdk
```

## Key Features

The SpriteAI SDK offers several key features:

1. Character spritesheet generation
2. Environment sprite generation
3. Fetching available animation states
4. Fetching available sprite styles

## Generating Character Spritesheets

The `generateCharacterSpritesheet` function is the core of the SDK for creating character animations. Here's how to use it:

```javascript
import { generateCharacterSpritesheet } from 'spriteai-sdk';

const result = await generateCharacterSpritesheet('a medieval knight in armor', {
  states: ['idle', 'walk', 'run', 'attack'],
  framesPerState: 6,
  size: '1024x1024',
  style: 'pixel-art',
  padding: 1,
  direction: 'right',
  save: true
});

console.log(result.spritesheet); // Base64 encoded PNG
console.log(result.metadata); // Metadata about the generated spritesheet
```

### Options

- `states`: Array of animation states (default: ['idle', 'walk', 'run', 'attack'])
- `framesPerState`: Number of frames per animation state (default: 6)
- `size`: Size of the output image (default: '1024x1024')
- `style`: Art style of the sprite (default: 'pixel-art')
- `padding`: Padding between frames (default: 1)
- `direction`: Direction the character faces (default: 'right')
- `save`: Whether to save the spritesheet to disk (default: false)

## Generating Environment Sprites

The `generateEnvironmentSprites` function creates tileset-style environment sprites:

```javascript
import { generateEnvironmentSprites } from 'spriteai-sdk';

const result = await generateEnvironmentSprites('forest', {
  elements: 4,
  size: '1024x1024',
  style: 'pixel-art',
  padding: 1,
  theme: 'fantasy',
  save: true
});

console.log(result.tileset); // Base64 encoded PNG
console.log(result.metadata); // Metadata about the generated tileset
```

### Options

- `elements`: Number of distinct environment pieces (default: 4)
- `size`: Size of the output image (default: '1024x1024')
- `style`: Art style of the sprites (default: 'pixel-art')
- `padding`: Padding between elements (default: 1)
- `theme`: Theme of the environment (default: 'fantasy')
- `save`: Whether to save the tileset to disk (default: false)

## Fetching Available Animation States

The SDK provides a function to fetch the available animation states:

```javascript
import { fetchAvailableAnimationStates } from 'spriteai-sdk';

const states = await fetchAvailableAnimationStates();
console.log(states); // ['idle', 'walk', 'run', 'attack', 'jump', 'fall', 'hurt', 'die']
```

## Fetching Available Sprite Styles

Similarly, you can fetch the available sprite styles:

```javascript
import { fetchAvailableSpriteStyles } from 'spriteai-sdk';

const styles = await fetchAvailableSpriteStyles();
console.log(styles); // ['pixel-art', 'vector', '3d', 'hand-drawn', 'anime']
```

## Best Practices

1. **Consistent Descriptions**: When generating multiple related sprites, use consistent descriptions to maintain a cohesive style.

2. **Optimize API Calls**: Cache the results of `fetchAvailableAnimationStates` and `fetchAvailableSpriteStyles` to reduce unnecessary API calls.

3. **Error Handling**: Always implement proper error handling when using the SDK functions, as they involve network requests.

4. **Asset Management**: Use the `save` option judiciously and implement a proper asset management system in your project.

5. **Performance Considerations**: Generate sprites during development or as part of your build process, rather than at runtime, to avoid performance issues.

## Integration Examples

### React Application

```javascript
import React, { useState, useEffect } from 'react';
import { generateCharacterSpritesheet, fetchAvailableAnimationStates } from 'spriteai-sdk';

function SpriteGenerator() {
  const [spritesheet, setSpritesheet] = useState(null);
  const [states, setStates] = useState([]);

  useEffect(() => {
    fetchAvailableAnimationStates().then(setStates);
  }, []);

  const handleGenerate = async () => {
    const result = await generateCharacterSpritesheet('a heroic warrior', {
      states: states.slice(0, 4),
      style: 'pixel-art'
    });
    setSpritesheet(result.spritesheet);
  };

  return (
    <div>
      <button onClick={handleGenerate}>Generate Sprite</button>
      {spritesheet && <img src={spritesheet} alt="Generated Spritesheet" />}
    </div>
  );
}
```

### Node.js CLI Tool

```javascript
#!/usr/bin/env node
import { generateEnvironmentSprites } from 'spriteai-sdk';
import fs from 'fs';

const description = process.argv[2];
const theme = process.argv[3];

if (!description || !theme) {
  console.error('Usage: generate-environment <description> <theme>');
  process.exit(1);
}

async function generateEnvironment() {
  try {
    const result = await generateEnvironmentSprites(description, { theme, save: true });
    console.log(`Environment sprites generated and saved to: ${result.metadata.filename}`);
  } catch (error) {
    console.error('Error generating environment sprites:', error);
  }
}

generateEnvironment();
```

By following this guide, you should be well-equipped to integrate and utilize the SpriteAI SDK in your projects, leveraging its powerful features to generate high-quality game assets programmatically.