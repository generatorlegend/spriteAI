<response>

# Troubleshooting and FAQ

This guide addresses common issues that may arise when using SpriteAI and provides answers to frequently asked questions about the library's capabilities and limitations.

## Troubleshooting

### Image Quality Issues

#### Problem: Generated sprites appear blurry or pixelated

**Possible causes:**
- Incorrect size parameter
- Incompatible style selection

**Solutions:**
1. Ensure you're using an appropriate size for your sprites. For pixel art, try using smaller dimensions like 256x256 or 512x512.
2. Double-check that the style parameter matches your desired output (e.g., 'pixel-art' for pixel art sprites).

Example:
```javascript
const result = await generateCharacterSpritesheet('warrior', {
  size: '512x512',
  style: 'pixel-art'
});
```

#### Problem: Inconsistent character size across frames

**Possible causes:**
- Limitations in AI-generated content

**Solutions:**
1. Try regenerating the spritesheet with a more specific character description.
2. Use image editing tools to manually adjust inconsistent frames if necessary.

### Unexpected Results

#### Problem: Generated sprites don't match the description

**Possible causes:**
- Ambiguous or complex descriptions
- AI model limitations

**Solutions:**
1. Provide more specific and detailed descriptions.
2. Break down complex characters into simpler elements.

Example:
```javascript
const result = await generateCharacterSpritesheet('tall, muscular warrior with long red hair and silver armor');
```

#### Problem: Missing or incorrect animation states

**Possible causes:**
- Unsupported animation states
- Incorrect state names in options

**Solutions:**
1. Check the available animation states using the `fetchAvailableAnimationStates()` function.
2. Ensure you're using correct state names in the `states` option.

Example:
```javascript
const availableStates = await fetchAvailableAnimationStates();
console.log(availableStates);

const result = await generateCharacterSpritesheet('wizard', {
  states: ['idle', 'walk', 'cast']
});
```

### Technical Issues

#### Problem: Error when saving generated sprites

**Possible causes:**
- Insufficient permissions
- Invalid file path

**Solutions:**
1. Ensure your application has write permissions for the target directory.
2. Check that the file path is correct and the directory exists.

Example:
```javascript
const result = await generateCharacterSpritesheet('rogue', {
  save: true
});
```

## Frequently Asked Questions

### Q: What image formats does SpriteAI support?
A: SpriteAI generates images in PNG format, which is widely supported and maintains transparency.

### Q: Can I generate sprites for specific game engines or frameworks?
A: SpriteAI generates generic spritesheets that can be used with most game engines and frameworks. You may need to process the spritesheet further to match specific engine requirements.

### Q: How many sprites can I generate in one API call?
A: Currently, SpriteAI generates one spritesheet per API call. Each spritesheet can contain multiple animation states and frames.

### Q: Can I modify the generated sprites programmatically?
A: Yes, you can use image processing libraries like Sharp or Jimp to further modify the generated sprites. SpriteAI returns the sprite data in a format that's easy to work with.

### Q: Are there any limitations on sprite complexity or detail?
A: While SpriteAI can generate a wide range of sprites, extremely complex or highly detailed sprites may not render perfectly. It's best to start with simpler designs and gradually increase complexity as needed.

### Q: How can I ensure consistent style across multiple sprite generations?
A: Use consistent description keywords and style parameters across your API calls. You can also use the `fetchAvailableSpriteStyles()` function to see available style options.

Example:
```javascript
const availableStyles = await fetchAvailableSpriteStyles();
console.log(availableStyles);

const result = await generateCharacterSpritesheet('elf archer', {
  style: 'pixel-art'
});
```

### Q: Can I generate environment sprites or tilesets?
A: Yes, you can use the `generateEnvironmentSprites()` function to create environment sprites and tilesets.

Example:
```javascript
const result = await generateEnvironmentSprites('forest', {
  elements: 6,
  theme: 'fantasy'
});
```

If you encounter any issues not covered in this guide or have additional questions, please refer to the API documentation or contact our support team for further assistance.

</response>