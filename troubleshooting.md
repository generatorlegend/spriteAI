Here's the new documentation page content for troubleshooting.md:

<response>
---
title: Troubleshooting Guide
description: Common issues and solutions when using SpriteAI
---

# Troubleshooting Guide

This guide addresses common issues you might encounter when using SpriteAI and provides step-by-step solutions to resolve them.

## Table of Contents

1. [API Call Errors](#api-call-errors)
2. [Image Processing Issues](#image-processing-issues)
3. [File Handling Problems](#file-handling-problems)
4. [Error Message Interpretation](#error-message-interpretation)

## API Call Errors

### OpenAI API Authentication Failed

**Error Message:** "Authentication error: Invalid API key provided"

**Solution:**

1. Check that you have set up your OpenAI API key correctly.
2. Ensure the API key is valid and has not expired.
3. Verify that you're using the correct environment variable name (`OPENAI_API_KEY`).

Example of setting the API key:

```javascript
import OpenAI from "openai";

const openAiObject = new OpenAI({
  apiKey: process.env.OPENAI_API_KEY,
});
```

### Rate Limit Exceeded

**Error Message:** "Rate limit exceeded"

**Solution:**

1. Implement exponential backoff and retry logic in your API calls.
2. Consider upgrading your API plan if you consistently hit rate limits.

Example retry logic:

```javascript
async function callWithRetry(apiFunction, maxRetries = 3) {
  for (let i = 0; i < maxRetries; i++) {
    try {
      return await apiFunction();
    } catch (error) {
      if (error.message.includes("Rate limit exceeded") && i < maxRetries - 1) {
        await new Promise(resolve => setTimeout(resolve, 1000 * Math.pow(2, i)));
      } else {
        throw error;
      }
    }
  }
}
```

## Image Processing Issues

### Sharp Module Error

**Error Message:** "Error: Input file is missing"

**Solution:**

1. Ensure that the input file path is correct and the file exists.
2. Check file permissions to make sure the application can read the file.
3. Verify that the Sharp module is correctly installed (`npm install sharp`).

Example of using Sharp with error handling:

```javascript
import sharp from "sharp";
import fs from "fs";

async function processImage(inputPath, outputPath) {
  try {
    if (!fs.existsSync(inputPath)) {
      throw new Error("Input file does not exist");
    }
    await sharp(inputPath)
      .resize(300, 300)
      .toFile(outputPath);
    console.log("Image processed successfully");
  } catch (error) {
    console.error("Image processing error:", error.message);
  }
}
```

### Jimp Color Processing Error

**Error Message:** "Error: Invalid color"

**Solution:**

1. Ensure that you're passing a valid color format to Jimp functions.
2. Use Jimp's built-in color helpers for consistent results.

Example of correct color usage with Jimp:

```javascript
import Jimp from "jimp";

const colorToReplace = Jimp.cssColorToHex('#FFFFFF');
// Use colorToReplace in your image processing logic
```

## File Handling Problems

### Unable to Save Generated Spritesheet

**Error Message:** "ENOENT: no such file or directory, open '/path/to/assets/spritesheet.png'"

**Solution:**

1. Ensure that the target directory exists before saving the file.
2. Use `fs.promises.mkdir` with the `recursive` option to create nested directories.

Example of creating directories before saving:

```javascript
import fs from "fs/promises";
import path from "path";

async function saveSpritesheet(buffer, filename) {
  try {
    const dir = path.dirname(filename);
    await fs.mkdir(dir, { recursive: true });
    await fs.writeFile(filename, buffer);
    console.log("Spritesheet saved successfully");
  } catch (error) {
    console.error("Error saving spritesheet:", error.message);
  }
}
```

## Error Message Interpretation

Understanding error messages can help quickly identify and resolve issues. Here are some common error patterns and their meanings:

- **"ENOENT"**: This usually indicates a file or directory not found error. Check file paths and ensure all required directories exist.
- **"EACCES"**: This suggests a permissions issue. Verify that your application has the necessary read/write permissions for the files and directories it's trying to access.
- **"Invalid value"**: Often seen with API calls, this may indicate that you're passing an incorrect parameter type or value. Double-check the API documentation for the correct parameter format.

When encountering an error, always check the full error stack trace for additional context. Many errors will include specific file paths or line numbers that can help pinpoint the issue in your code.

If you encounter persistent issues not covered in this guide, please consult the SpriteAI documentation or reach out to our support team for assistance.
</response>---
title: Troubleshooting Guide
description: Common issues and solutions when using SpriteAI
---

# Troubleshooting Guide

This guide addresses common issues you might encounter when using SpriteAI and provides step-by-step solutions to resolve them.

## Table of Contents

1. [API Call Errors](#api-call-errors)
2. [Image Processing Issues](#image-processing-issues)
3. [File Handling Problems](#file-handling-problems)
4. [Error Message Interpretation](#error-message-interpretation)

## API Call Errors

### OpenAI API Authentication Failed

**Error Message:** "Authentication error: Invalid API key provided"

**Solution:**

1. Check that you have set up your OpenAI API key correctly.
2. Ensure the API key is valid and has not expired.
3. Verify that you're using the correct environment variable name (`OPENAI_API_KEY`).

Example of setting the API key:

```javascript
import OpenAI from "openai";

const openAiObject = new OpenAI({
  apiKey: process.env.OPENAI_API_KEY,
});
```

### Rate Limit Exceeded

**Error Message:** "Rate limit exceeded"

**Solution:**

1. Implement exponential backoff and retry logic in your API calls.
2. Consider upgrading your API plan if you consistently hit rate limits.

Example retry logic:

```javascript
async function callWithRetry(apiFunction, maxRetries = 3) {
  for (let i = 0; i < maxRetries; i++) {
    try {
      return await apiFunction();
    } catch (error) {
      if (error.message.includes("Rate limit exceeded") && i < maxRetries - 1) {
        await new Promise(resolve => setTimeout(resolve, 1000 * Math.pow(2, i)));
      } else {
        throw error;
      }
    }
  }
}
```

## Image Processing Issues

### Sharp Module Error

**Error Message:** "Error: Input file is missing"

**Solution:**

1. Ensure that the input file path is correct and the file exists.
2. Check file permissions to make sure the application can read the file.
3. Verify that the Sharp module is correctly installed (`npm install sharp`).

Example of using Sharp with error handling:

```javascript
import sharp from "sharp";
import fs from "fs";

async function processImage(inputPath, outputPath) {
  try {
    if (!fs.existsSync(inputPath)) {
      throw new Error("Input file does not exist");
    }
    await sharp(inputPath)
      .resize(300, 300)
      .toFile(outputPath);
    console.log("Image processed successfully");
  } catch (error) {
    console.error("Image processing error:", error.message);
  }
}
```

### Jimp Color Processing Error

**Error Message:** "Error: Invalid color"

**Solution:**

1. Ensure that you're passing a valid color format to Jimp functions.
2. Use Jimp's built-in color helpers for consistent results.

Example of correct color usage with Jimp:

```javascript
import Jimp from "jimp";

const colorToReplace = Jimp.cssColorToHex('#FFFFFF');
// Use colorToReplace in your image processing logic
```

## File Handling Problems

### Unable to Save Generated Spritesheet

**Error Message:** "ENOENT: no such file or directory, open '/path/to/assets/spritesheet.png'"

**Solution:**

1. Ensure that the target directory exists before saving the file.
2. Use `fs.promises.mkdir` with the `recursive` option to create nested directories.

Example of creating directories before saving:

```javascript
import fs from "fs/promises";
import path from "path";

async function saveSpritesheet(buffer, filename) {
  try {
    const dir = path.dirname(filename);
    await fs.mkdir(dir, { recursive: true });
    await fs.writeFile(filename, buffer);
    console.log("Spritesheet saved successfully");
  } catch (error) {
    console.error("Error saving spritesheet:", error.message);
  }
}
```

## Error Message Interpretation

Understanding error messages can help quickly identify and resolve issues. Here are some common error patterns and their meanings:

- **"ENOENT"**: This usually indicates a file or directory not found error. Check file paths and ensure all required directories exist.
- **"EACCES"**: This suggests a permissions issue. Verify that your application has the necessary read/write permissions for the files and directories it's trying to access.
- **"Invalid value"**: Often seen with API calls, this may indicate that you're passing an incorrect parameter type or value. Double-check the API documentation for the correct parameter format.

When encountering an error, always check the full error stack trace for additional context. Many errors will include specific file paths or line numbers that can help pinpoint the issue in your code.

If you encounter persistent issues not covered in this guide, please consult the SpriteAI documentation or reach out to our support team for assistance.