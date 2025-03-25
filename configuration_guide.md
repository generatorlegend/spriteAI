# Configuration Guide for SpriteAI

## Introduction

This guide will walk you through the process of configuring SpriteAI for optimal use. We'll cover setting up API keys, customizing output options, and best practices for managing different environments and securing sensitive information.

## Setting Up API Keys

SpriteAI uses the OpenAI API to generate images. To use this functionality, you'll need to set up an API key:

1. Sign up for an OpenAI account at https://openai.com/
2. Navigate to the API section and create a new API key
3. Copy the API key

To securely store your API key, create a `.env` file in the root directory of your project:

```
OPENAI_API_KEY=your_api_key_here
```

Make sure to add `.env` to your `.gitignore` file to prevent accidentally committing sensitive information.

## Customizing Output Options

SpriteAI offers various customization options for both character spritesheets and landscape sprites. Here are some key options you can configure:

### Character Spritesheets

When calling `generateCharacterSpritesheet`, you can pass an options object to customize the output:

```javascript
const options = {
  states: ['idle', 'walk', 'run', 'attack'],
  framesPerState: 6,
  size: '1024x1024',
  style: 'pixel-art',
  padding: 1,
  direction: 'right',
  save: true
};

const result = await generateCharacterSpritesheet('a medieval knight', options);
```

### Landscape Sprites

For `generateLandscapeSprite`, you can customize the following options:

```javascript
const options = {
  size: '1024x1024',
  style: 'pixel-art',
  timeOfDay: 'day',
  weather: 'clear',
  perspective: 'side-scrolling',
  save: true,
  removeBackground: true,
  backgroundColor: '#FFFFFF',
  colorThreshold: 0.1
};

const result = await generateLandscapeSprite('a lush forest', options);
```

## Managing Different Environments

When working with SpriteAI across different environments (development, staging, production), it's important to manage your configuration appropriately:

1. Use separate `.env` files for each environment (e.g., `.env.development`, `.env.production`)
2. Set up a configuration management system to load the correct environment variables based on the current environment

Example of loading environment-specific variables:

```javascript
import dotenv from 'dotenv';
import path from 'path';

const environment = process.env.NODE_ENV || 'development';
dotenv.config({ path: path.resolve(process.cwd(), `.env.${environment}`) });
```

## Securing Sensitive Information

To ensure the security of your API keys and other sensitive information:

1. Never commit `.env` files or API keys to version control
2. Use environment variables to store sensitive information
3. Implement proper access controls and user authentication in your application
4. Regularly rotate your API keys
5. Monitor API usage for any suspicious activity

## Best Practices

1. **Version Control**: Keep your SpriteAI configuration files (excluding `.env`) in version control to track changes and collaborate with team members.

2. **Documentation**: Maintain clear documentation of your configuration options and any custom scripts or workflows you develop around SpriteAI.

3. **Error Handling**: Implement robust error handling in your application to gracefully handle API failures or configuration issues.

4. **Performance Optimization**: Consider caching generated sprites to reduce API calls and improve application performance.

5. **Regular Updates**: Keep your SpriteAI package and dependencies up to date to ensure you have the latest features and security patches.

By following these configuration guidelines and best practices, you'll be well-equipped to use SpriteAI effectively and securely in your projects.