<response>

---
title: Landscape Sprite Generation Guide
description: Learn how to create game-ready landscape sprites using SpriteAI
---

# Landscape Sprite Generation Guide

## Introduction

This guide will walk you through the process of creating landscape sprites for your game environments using SpriteAI. With the `generateLandscapeSprite` function, you can quickly generate high-quality, customizable background images for various game scenarios.

## Basic Usage

To generate a landscape sprite, use the `generateLandscapeSprite` function. Here's a basic example:

```javascript
import { generateLandscapeSprite } from 'spriteAI';

const description = 'A lush forest with a winding river';
const result = await generateLandscapeSprite(description);
```

This will generate a default landscape sprite based on your description.

## Customization Options

The `generateLandscapeSprite` function accepts an options object as its second parameter, allowing you to customize various aspects of the generated sprite:

```javascript
const options = {
  size: '1024x1024',
  style: 'pixel-art',
  timeOfDay: 'sunset',
  weather: 'clear',
  perspective: 'side-scrolling',
  save: true
};

const result = await generateLandscapeSprite(description, options);
```

### Available Options

- `size`: Output size of the sprite (default: '1024x1024')
- `style`: Art style (default: 'pixel-art')
- `timeOfDay`: Time setting (options: 'day', 'night', 'sunset', 'dawn')
- `weather`: Weather conditions (options: 'clear', 'rainy', 'foggy', 'snowy')
- `perspective`: View perspective (options: 'side-scrolling', 'top-down', 'isometric')
- `save`: Whether to save the generated image locally (default: false)

## Advanced Features

### Background Removal

You can automatically remove the background from your generated landscape sprite:

```javascript
const options = {
  removeBackground: true,
  backgroundColor: '#FFFFFF',
  colorThreshold: 0.1
};

const result = await generateLandscapeSprite(description, options);
```

This is particularly useful for creating sprites that blend seamlessly with your game's existing art style.

## Best Practices

1. **Be Specific**: Provide detailed descriptions for more accurate results.
2. **Consistent Style**: Keep the art style consistent with your game's overall aesthetic.
3. **Experiment**: Try different combinations of time of day, weather, and perspective for varied environments.
4. **Optimize Size**: Choose an appropriate size based on your game's resolution and performance requirements.
5. **Post-Processing**: Consider using the background removal feature for further customization.

## Example Scenarios

### Forest Side-Scroller

```javascript
const forestDescription = 'Dense pine forest with a misty atmosphere';
const forestOptions = {
  style: 'pixel-art',
  timeOfDay: 'dawn',
  weather: 'foggy',
  perspective: 'side-scrolling'
};

const forestSprite = await generateLandscapeSprite(forestDescription, forestOptions);
```

### Desert Top-Down View

```javascript
const desertDescription = 'Vast desert with sand dunes and an oasis';
const desertOptions = {
  style: 'pixel-art',
  timeOfDay: 'day',
  weather: 'clear',
  perspective: 'top-down'
};

const desertSprite = await generateLandscapeSprite(desertDescription, desertOptions);
```

## Conclusion

With SpriteAI's `generateLandscapeSprite` function, you can rapidly create diverse and high-quality background sprites for your game environments. Experiment with different descriptions and options to achieve the perfect look for your game's landscapes.

</response>---
title: Landscape Sprite Generation Guide
description: Learn how to create game-ready landscape sprites using SpriteAI
---

# Landscape Sprite Generation Guide

## Introduction

This guide will walk you through the process of creating landscape sprites for your game environments using SpriteAI. With the `generateLandscapeSprite` function, you can quickly generate high-quality, customizable background images for various game scenarios.

## Basic Usage

To generate a landscape sprite, use the `generateLandscapeSprite` function. Here's a basic example:

```javascript
import { generateLandscapeSprite } from 'spriteAI';

const description = 'A lush forest with a winding river';
const result = await generateLandscapeSprite(description);
```

This will generate a default landscape sprite based on your description.

## Customization Options

The `generateLandscapeSprite` function accepts an options object as its second parameter, allowing you to customize various aspects of the generated sprite:

```javascript
const options = {
  size: '1024x1024',
  style: 'pixel-art',
  timeOfDay: 'sunset',
  weather: 'clear',
  perspective: 'side-scrolling',
  save: true
};

const result = await generateLandscapeSprite(description, options);
```

### Available Options

- `size`: Output size of the sprite (default: '1024x1024')
- `style`: Art style (default: 'pixel-art')
- `timeOfDay`: Time setting (options: 'day', 'night', 'sunset', 'dawn')
- `weather`: Weather conditions (options: 'clear', 'rainy', 'foggy', 'snowy')
- `perspective`: View perspective (options: 'side-scrolling', 'top-down', 'isometric')
- `save`: Whether to save the generated image locally (default: false)

## Advanced Features

### Background Removal

You can automatically remove the background from your generated landscape sprite:

```javascript
const options = {
  removeBackground: true,
  backgroundColor: '#FFFFFF',
  colorThreshold: 0.1
};

const result = await generateLandscapeSprite(description, options);
```

This is particularly useful for creating sprites that blend seamlessly with your game's existing art style.

## Best Practices

1. **Be Specific**: Provide detailed descriptions for more accurate results.
2. **Consistent Style**: Keep the art style consistent with your game's overall aesthetic.
3. **Experiment**: Try different combinations of time of day, weather, and perspective for varied environments.
4. **Optimize Size**: Choose an appropriate size based on your game's resolution and performance requirements.
5. **Post-Processing**: Consider using the background removal feature for further customization.

## Example Scenarios

### Forest Side-Scroller

```javascript
const forestDescription = 'Dense pine forest with a misty atmosphere';
const forestOptions = {
  style: 'pixel-art',
  timeOfDay: 'dawn',
  weather: 'foggy',
  perspective: 'side-scrolling'
};

const forestSprite = await generateLandscapeSprite(forestDescription, forestOptions);
```

### Desert Top-Down View

```javascript
const desertDescription = 'Vast desert with sand dunes and an oasis';
const desertOptions = {
  style: 'pixel-art',
  timeOfDay: 'day',
  weather: 'clear',
  perspective: 'top-down'
};

const desertSprite = await generateLandscapeSprite(desertDescription, desertOptions);
```

## Conclusion

With SpriteAI's `generateLandscapeSprite` function, you can rapidly create diverse and high-quality background sprites for your game environments. Experiment with different descriptions and options to achieve the perfect look for your game's landscapes.