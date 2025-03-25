# Troubleshooting Guide for SpriteAI

This guide aims to help you resolve common issues you might encounter while using SpriteAI. We'll cover API-related problems, image processing errors, and integration difficulties. You'll also find guidance on how to interpret error messages and steps for escalating issues that cannot be resolved.

## Table of Contents

1. [API-Related Issues](#api-related-issues)
2. [Image Processing Errors](#image-processing-errors)
3. [Integration Difficulties](#integration-difficulties)
4. [Interpreting Error Messages](#interpreting-error-messages)
5. [Escalating Unresolved Issues](#escalating-unresolved-issues)

## API-Related Issues

### Authentication Errors

If you're experiencing authentication issues:

1. Ensure you're using the correct API key.
2. Check that your API key has not expired.
3. Verify that you have the necessary permissions for the endpoints you're trying to access.

Example of proper API key usage:

```javascript
const openAiObject = new OpenAI();
```

### Rate Limiting

If you're encountering rate limit errors:

1. Review your API usage and ensure you're not exceeding the allowed requests per minute.
2. Implement proper error handling to catch rate limit errors and retry after a delay.

## Image Processing Errors

### Invalid Input Image

If you're getting errors related to invalid input images:

1. Ensure the image file exists at the specified path.
2. Check that the image format is supported (PNG, JPEG, etc.).
3. Verify that the image file is not corrupted.

Example of proper file path handling:

```javascript
const currentWorkingDirectory = process.cwd();
const filename = `${currentWorkingDirectory}${path.sep}assets${path.sep}${description.replace(/\s+/g, '_')}_spritesheet.png`;
```

### Background Removal Issues

If the background removal process is not working as expected:

1. Check that the target color is correctly specified (e.g., '#FFFFFF' for white).
2. Adjust the color threshold if necessary.
3. Ensure the input and output paths are correct.

Example of background removal function call:

```javascript
await removeBackgroundColor(
  tempInputPath, 
  tempOutputPath, 
  options.backgroundColor || '#FFFFFF', 
  options.colorThreshold || 0.1
);
```

## Integration Difficulties

### Module Import Issues

If you're having trouble importing SpriteAI modules:

1. Ensure you've installed all required dependencies (`openai`, `axios`, `sharp`, `jimp`).
2. Check that your import statements are correct:

```javascript
import OpenAI from "openai";
import axios from "axios";
import sharp from "sharp";
import Jimp from "jimp";
```

### Incompatible Versions

If you're experiencing compatibility issues:

1. Check the version of SpriteAI you're using.
2. Ensure all dependencies are up to date.
3. Review the changelog for any breaking changes in recent versions.

## Interpreting Error Messages

SpriteAI uses descriptive error messages to help you identify issues. Here are some common error messages and their meanings:

- "Invalid API key": Check your authentication credentials.
- "Rate limit exceeded": You've made too many requests in a short period. Implement rate limiting in your code.
- "Invalid image format": Ensure you're using a supported image format.
- "File not found": Check the file path and ensure the image exists.

## Escalating Unresolved Issues

If you've tried the troubleshooting steps and still can't resolve your issue:

1. Gather all relevant information, including:
   - Error messages
   - Code snippets
   - SpriteAI version
   - Node.js version
   - Operating system
2. Check the GitHub issues page to see if it's a known problem.
3. If it's not a known issue, create a new GitHub issue with all the gathered information.
4. For urgent matters, contact the SpriteAI support team directly.

Remember to always provide as much detail as possible when reporting issues. This helps the development team quickly identify and resolve the problem.