Here's the new documentation page content for "spriteai_best_practices.md":

<response>
# SpriteAI Best Practices

This guide provides a set of best practices for using SpriteAI effectively. Whether you're generating character spritesheets, environment sprites, or landscape scenes, these tips will help you optimize your workflow and achieve the best results.

## Crafting Effective Sprite Descriptions

The quality of your generated sprites largely depends on the descriptions you provide. Here are some tips for crafting effective descriptions:

1. Be specific and detailed: Instead of "a warrior", try "a muscular orc warrior with green skin, wearing plate armor and wielding a battle axe".

2. Include visual style information: Mention the desired art style, such as "pixel art", "hand-drawn", or "3D rendered".

3. Describe key features: Focus on distinctive elements that define the character or environment.

4. Consider context: If the sprite is for a specific game or setting, include relevant details.

Example:
```javascript
const description = "A steampunk-inspired robotic cat with brass gears visible through its translucent skin, glowing green eyes, and a top hat";
```

## Optimizing Generation Options

### For Character Spritesheets

1. Choose appropriate animation states:
   ```javascript
   const options = {
     states: ['idle', 'walk', 'run', 'attack', 'jump'],
     framesPerState: 8
   };
   ```

2. Adjust frame count based on animation complexity:
   - Simple animations (e.g., idle): 4-6 frames
   - Complex animations (e.g., attack): 8-12 frames

3. Set the correct direction:
   ```javascript
   const options = {
     direction: 'right' // or 'left' depending on your game's needs
   };
   ```

### For Environment Sprites

1. Specify the number of elements based on your needs:
   ```javascript
   const options = {
     elements: 6, // Adjust based on the variety of environmental pieces needed
     theme: 'fantasy'
   };
   ```

2. Choose an appropriate style that matches your character sprites:
   ```javascript
   const options = {
     style: 'pixel-art' // Ensure consistency across all game assets
   };
   ```

### For Landscape Sprites

1. Define time of day and weather for atmospheric effects:
   ```javascript
   const options = {
     timeOfDay: 'sunset',
     weather: 'foggy'
   };
   ```

2. Specify the perspective to match your game's viewpoint:
   ```javascript
   const options = {
     perspective: 'side-scrolling' // or 'top-down', 'isometric'
   };
   ```

## Efficiently Managing Generated Assets

1. Use descriptive filenames:
   ```javascript
   const description = "forest_elf_archer";
   const options = {
     save: true // This will save the file with a descriptive name
   };
   ```

2. Organize assets by type:
   - Create separate directories for characters, environments, and landscapes.
   - Within these, consider sub-directories for different themes or game levels.

3. Version control your assets:
   - Use Git LFS (Large File Storage) for efficient management of large image files.
   - Include metadata files with each asset detailing its generation parameters.

4. Implement a naming convention:
   ```
   [asset_type]_[description]_[variant].[extension]
   ```
   Example: `character_forest_elf_archer_v2.png`

## Real-World Scenarios and Examples

### Scenario 1: Creating a Consistent Game World

When developing a game with a specific theme, maintain consistency across all generated assets:

```javascript
const commonOptions = {
  style: 'pixel-art',
  theme: 'cyberpunk'
};

// Character generation
const characterDescription = "A cybernetic bounty hunter with neon-lit tattoos and a retractable arm blade";
await generateCharacterSpritesheet(characterDescription, { ...commonOptions, states: ['idle', 'run', 'attack'] });

// Environment generation
const environmentDescription = "A neon-lit alleyway with holographic advertisements and steam vents";
await generateEnvironmentSprites(environmentDescription, { ...commonOptions, elements: 8 });

// Landscape generation
const landscapeDescription = "A sprawling megacity with towering skyscrapers and flying vehicles";
await generateLandscapeSprite(landscapeDescription, { ...commonOptions, timeOfDay: 'night', weather: 'rainy' });
```

### Scenario 2: Iterative Asset Refinement

Sometimes, you may need to refine your assets through multiple generations:

1. Start with a basic description:
   ```javascript
   let description = "A magical wizard";
   let result = await generateCharacterSpritesheet(description);
   ```

2. Analyze the result and refine the description:
   ```javascript
   description = "An elderly wizard with a long white beard, wearing star-patterned blue robes and a pointed hat";
   result = await generateCharacterSpritesheet(description);
   ```

3. Further refine based on the new result:
   ```javascript
   description = "An elderly wizard with a long white beard, wearing star-patterned blue robes and a pointed hat, holding a gnarled wooden staff with a glowing crystal";
   result = await generateCharacterSpritesheet(description);
   ```

By following these best practices, you'll be able to leverage SpriteAI more effectively, creating high-quality and consistent game assets efficiently. Remember to experiment and iterate on your descriptions and options to achieve the best results for your specific project needs.
</response>