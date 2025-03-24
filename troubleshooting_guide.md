# Troubleshooting Guide for SpriteAI

This guide addresses common issues you might encounter when using SpriteAI and provides solutions to help you resolve them quickly.

## Table of Contents

1. [Installation Issues](#installation-issues)
2. [Sprite Generation Problems](#sprite-generation-problems)
3. [Image Quality Concerns](#image-quality-concerns)
4. [Integration with Game Development Workflows](#integration-with-game-development-workflows)
5. [Getting Additional Support](#getting-additional-support)

## Installation Issues

### Error: Unable to install dependencies

If you encounter issues while installing SpriteAI dependencies, try the following:

1. Ensure you have the latest version of Node.js installed.
2. Clear your npm cache:
   ```
   npm cache clean --force
   ```
3. Retry the installation:
   ```
   npm install spriteai
   ```

### Error: Module not found

If you see a "Module not found" error when trying to use SpriteAI, make sure:

1. You've installed the package correctly.
2. You're importing the module correctly in your code:
   ```javascript
   import { generateCharacterSpritesheet, generateEnvironmentSprites } from 'spriteai';
   ```

## Sprite Generation Problems

### Error: OpenAI API key not found

If you encounter an error related to the OpenAI API key:

1. Ensure you've set up your OpenAI API key as an environment variable:
   ```
   export OPENAI_API_KEY='your-api-key-here'
   ```
2. Verify that the API key is correct and has the necessary permissions.

### Error: Invalid response from OpenAI API

If you receive an invalid response:

1. Check your internet connection.
2. Verify that your OpenAI API key has not expired or reached its usage limit.
3. Try regenerating the sprite with a different description or options.

## Image Quality Concerns

### Sprites appear blurry or low-resolution

If your generated sprites are not of the expected quality:

1. Ensure you're specifying a high-resolution size in the options:
   ```javascript
   const options = {
     size: '1024x1024',
     // other options...
   };
   ```
2. Try adjusting the `style` option to see if it improves the output:
   ```javascript
   const options = {
     style: 'pixel-art', // or try 'vector', '3d', etc.
     // other options...
   };
   ```

### Inconsistent character sizes across frames

If character sizes are inconsistent:

1. Make sure you're using a consistent `framesPerState` value across all states.
2. Try regenerating the spritesheet with more specific instructions in the description.

## Integration with Game Development Workflows

### Difficulty importing spritesheets into game engine

If you're having trouble importing the generated spritesheets:

1. Ensure you're saving the spritesheet correctly:
   ```javascript
   const result = await generateCharacterSpritesheet('character description', {
     save: true,
     // other options...
   });
   ```
2. Check the `assets` folder in your project directory for the saved PNG file.
3. Verify that your game engine supports the PNG format and the dimensions of the generated spritesheet.

### Animating sprites in-game

If you're struggling to animate the sprites in your game:

1. Use the `metadata` returned by the generation function to set up your animations:
   ```javascript
   const result = await generateCharacterSpritesheet('character description');
   console.log(result.metadata);
   ```
2. The `frameData` in the metadata provides information about each animation state, including start and end frames.

## Getting Additional Support

If you're still experiencing issues after trying these troubleshooting steps:

1. Check the [SpriteAI GitHub repository](https://github.com/yourusername/spriteai) for known issues or to report a new one.
2. Join our [Discord community](https://discord.gg/spriteai) for real-time support from developers and other users.
3. Contact our support team at support@spriteai.com with a detailed description of your problem, including any error messages and steps to reproduce the issue.

Remember to always use the latest version of SpriteAI to ensure you have the most up-to-date features and bug fixes.