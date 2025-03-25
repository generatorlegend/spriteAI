# Landscape Sprite Generation Guide

This guide provides detailed information on using the `generateLandscapeSprite` function to create custom landscape sprites for your game or application. The function allows you to generate pixel-art style landscapes with various customization options.

## Function Overview

The `generateLandscapeSprite` function generates a landscape sprite based on a given description and optional parameters. It uses AI-powered image generation to create detailed, customizable landscapes suitable for game backgrounds or other graphical applications.

### Basic Usage

```javascript
import { generateLandscapeSprite } from './path/to/module';

const landscape = await generateLandscapeSprite('A lush forest with a winding river');
```

## Function Parameters

The function accepts two parameters:

1. `description` (string): A detailed description of the landscape you want to generate.
2. `options` (object): An optional object to customize various aspects of the generated landscape.

### Available Options

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| size | string | '1024x1024' | Output size of the image |
| style | string | 'pixel-art' | Art style of the landscape |
| timeOfDay | string | 'day' | Time of day setting |
| weather | string | 'clear' | Weather conditions |
| perspective | string | 'side-scrolling' | Perspective of the landscape |
| save | boolean | false | Whether to save the generated image |
| removeBackground | boolean | false | Option to remove the background |
| backgroundColor | string | '#FFFFFF' | Background color to remove (if removeBackground is true) |
| colorThreshold | number | 0.1 | Threshold for background color removal |

## Customizing Landscape Generation

### Time of Day

You can set the time of day for your landscape using the `timeOfDay` option. Available options include:

- 'day'
- 'night'
- 'sunset'
- 'dawn'

Example:

```javascript
const nightForest = await generateLandscapeSprite('A mysterious forest', {
  timeOfDay: 'night'
});
```

### Weather Conditions

Customize the weather in your landscape using the `weather` option. Available options include:

- 'clear'
- 'rainy'
- 'foggy'
- 'snowy'

Example:

```javascript
const snowyMountain = await generateLandscapeSprite('A tall mountain peak', {
  weather: 'snowy'
});
```

### Perspective

Change the viewpoint of your landscape using the `perspective` option. Available options include:

- 'side-scrolling'
- 'top-down'
- 'isometric'

Example:

```javascript
const isometricCity = await generateLandscapeSprite('A bustling cityscape', {
  perspective: 'isometric'
});
```

## Advanced Usage

### Saving Generated Images

To automatically save the generated landscape image, use the `save` option:

```javascript
const savedLandscape = await generateLandscapeSprite('A serene beach at sunset', {
  save: true,
  timeOfDay: 'sunset'
});
```

The image will be saved in the `assets` directory of your project with a filename based on the description.

### Removing Background

If you need a transparent background for your landscape sprite, use the `removeBackground` option:

```javascript
const transparentLandscape = await generateLandscapeSprite('A dense jungle', {
  removeBackground: true,
  backgroundColor: '#FFFFFF',
  colorThreshold: 0.1
});
```

This will remove the white background from the generated image, making it suitable for overlaying on other graphics.

## Return Value

The `generateLandscapeSprite` function returns an object with the following properties:

- `original`: URL of the originally generated image
- `landscape`: Base64-encoded string of the processed image (can be used directly in img src)
- `metadata`: Object containing details about the generated landscape

Example of accessing the return value:

```javascript
const result = await generateLandscapeSprite('A medieval castle on a hill');
console.log(result.metadata);
// Use result.landscape for the image data
```

## Best Practices

1. Be specific in your landscape descriptions for best results.
2. Experiment with different time of day and weather combinations to achieve desired atmospheres.
3. Consider the perspective that best suits your game or application design.
4. Use the `removeBackground` option when you need to layer landscapes with other graphics.
5. Save generated landscapes that you plan to reuse to avoid unnecessary API calls.

By leveraging the `generateLandscapeSprite` function, you can quickly create diverse and detailed landscape sprites for your projects, saving time and enhancing the visual appeal of your games or applications.