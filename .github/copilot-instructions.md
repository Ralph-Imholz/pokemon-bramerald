# Copilot Instructions for Pokemon Bramerald

## Project Overview

This is **Pokemon Bramerald**, a personalized Pokémon Emerald ROM hack based on **pokeemerald-expansion** by RHH (Rom Hacking Hideout). This project is a gift for **Bram**, who will be the main character in the game.

### Project Goals
- **Personalize the game for Bram** - The protagonist and story elements are customized for him
- **Include Bram's favorite Pokémon** - Featured prominently in the game
- **Add easter eggs and inside jokes** - Hidden references that Bram and friends will recognize
- **Transform NPCs into real people** - Friends and family members become characters in the game
- **Ralphie as a recurring NPC and final boss** - The project creator appears throughout the game and as the ultimate challenge

## Technology Stack

- **Language**: C, Assembly (ARM/Thumb for GBA)
- **Build System**: Make
- **Target Platform**: Game Boy Advance (GBA)
- **Base**: pokeemerald-expansion (decompilation of Pokémon Emerald)
- **Tools**: 
  - `porymap` - Map editing
  - `porytiles` - Metatile creation
  - `poryscript` - Scripting
  - Tilemap Studio - Tilemap editing

## Project Structure

### Key Directories
- `src/` - C source files for game logic, battle system, UI, etc.
- `data/` - Game data including scripts, maps, text, and tilesets
  - `data/scripts/` - Event scripts (.inc files)
  - `data/maps/` - Map-specific data and events
  - `data/text/` - Dialog and text strings
- `graphics/` - Sprites, tilesets, UI elements, and other graphics
  - `graphics/trainers/` - Trainer sprites
  - `graphics/pokemon/` - Pokémon sprites
  - `graphics/object_events/` - Overworld character sprites
- `include/` - Header files and configuration
  - `include/config/` - Game configuration files (battle, items, species, etc.)
- `constants/` - Game constants and definitions
- `asm/` - Assembly source files and macros
- `sound/` - Music and sound effects
- `tools/` - Build tools and utilities

### Important Configuration Files
- `include/config/battle.h` - Battle mechanics configuration
- `include/config/pokemon.h` - Pokémon data configuration
- `include/config/species_enabled.h` - Enable/disable specific Pokémon
- `include/config/general.h` - General game settings
- `include/config/debug.h` - Debug features

## Coding Guidelines

### C Code Style
- Use snake_case for function and variable names
- Use UPPER_CASE for constants and macros
- Follow existing pokeemerald-expansion code patterns
- Keep functions focused and modular
- Comment complex logic, especially for custom features

### Scripting (Poryscript/Event Scripts)
- Scripts are in `.inc` files in `data/scripts/`
- Map-specific scripts go in `data/maps/<MapName>/scripts.inc`
- Use meaningful label names for script sections
- Test scripts in-game using debug features

### Graphics
- Sprites must follow GBA color palette limitations (16 colors per palette)
- Use indexed PNG format for graphics
- Trainer sprites: 64x64 pixels
- Overworld sprites: 16x32 or 32x32 pixels depending on type

## Common Tasks

### Adding/Modifying NPCs
1. Create or modify sprite in `graphics/object_events/`
2. Add object event in the map's `events.inc` file
3. Create dialog script in the map's `scripts.inc`
4. Add any text strings to appropriate text files

### Creating Custom Trainers (for friends/family NPCs)
1. Add trainer sprite to `graphics/trainers/`
2. Define trainer data in trainer configuration files
3. Create trainer's team in the trainer party files
4. Add battle script and dialog

### Adding Easter Eggs
1. For item-based: Add hidden items to map events
2. For dialog-based: Add special text to NPC scripts
3. For encounter-based: Modify wild encounter tables
4. Consider using flags to track discovery

### Making Ralphie the Final Boss
1. Create custom trainer class and sprite
2. Design challenging team composition
3. Add special pre-battle and post-battle dialog
4. Consider unique battle mechanics or gimmicks

### Featuring Bram's Favorite Pokémon
1. Ensure species are enabled in `include/config/species_enabled.h`
2. Add to wild encounters in relevant routes
3. Consider giving to important NPCs/gift Pokémon
4. May feature in starter selection or early game

## Building the Project

```bash
# Basic build
make

# Parallel build (faster)
make -j$(nproc)

# Clean build
make clean && make

# Build with debug symbols
make debug
```

The compiled ROM will be output as `pokeemerald.gba`.

## Testing

- Use the debug menu (if enabled) to test features quickly
- Test on mGBA or other accurate GBA emulators
- Use save states for efficient testing of specific scenarios
- The project includes a test framework for automated testing

## Custom Content Tracking

When adding personalized content, consider documenting:
- Which NPCs have been converted to friends/family
- Location of easter eggs and inside jokes
- Bram's favorite Pokémon and where they appear
- Ralphie's appearances throughout the game
- Any modified story elements or dialog

## Resources

- [pokeemerald-expansion documentation](https://rh-hideout.github.io/pokeemerald-expansion/)
- [pret pokeemerald wiki](https://github.com/pret/pokeemerald/wiki)
- [RHH Discord](https://discord.gg/6CzjAG6GZk) for community support
- [Team Aqua's Asset Repo](https://github.com/Pawkkie/Team-Aquas-Asset-Repo/) for tutorials and assets

## Notes for AI Assistance

When helping with this project:
- Remember this is a **personalized gift for Bram**
- Maintain the fun, personal nature of modifications
- Preserve game balance while adding custom content
- Be mindful of GBA hardware limitations
- Follow pokeemerald-expansion coding conventions
- Test suggestions against the existing codebase structure
