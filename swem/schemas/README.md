# SWEM JSON Schemas

This directory contains JSON Schema files (draft-2020-12) for validating SWEM tack item definitions.

## Schema Structure

### Core Schemas

- **`definitions.schema.json`** - Common definitions and reusable components
- **`tack/tack.schema.json`** - Base schema for all tack items
- **`tack/tackTypeData.schema.json`** - Base tack type data schema

### Type-Specific Data Schemas

- **`tack/bridleTypeData.schema.json`** - Bridle-specific data (model_type: western/english)
- **`tack/saddleTypeData.schema.json`** - Saddle-specific data (model_type: western/english/adventure)
- **`tack/horseArmorTypeData.schema.json`** - Horse armor data (tier: cloth through amethyst)
- **`tack/girthStrapTypeData.schema.json`** - Girth strap data (belt_color)
- **`tack/pastureBlanketTypeData.schema.json`** - Pasture blanket data (is_armored)

### Tack Type Schemas

Individual schemas for each tack type that combine the base tack schema with specific data requirements:

- **`tack/bridle.schema.json`** - Bridle items
- **`tack/saddle.schema.json`** - Saddle items
- **`tack/horse_armor.schema.json`** - Horse armor items
- **`tack/girth_strap.schema.json`** - Girth strap items
- **`tack/pasture_blanket.schema.json`** - Pasture blanket items
- **`tack/halter.schema.json`** - Halter items
- **`tack/blanket.schema.json`** - Blanket (saddle pad) items
- **`tack/breast_collar.schema.json`** - Breast collar items
- **`tack/leg_wraps.schema.json`** - Leg wraps items
- **`tack/saddle_bag.schema.json`** - Saddle bag items

## Usage

To validate a tack JSON file, reference the appropriate schema file based on the tack type. For example:

```json
{
  "$schema": "https://github.com/magnushjensen/json-schemas/swem/schemas/tack/bridle.schema.json",
  "display": {
    "name": "Midnight Bridle",
    "credits": "ArtistName"
  },
  "cost": {
    "coin": "iron",
    "amount": 2
  },
  "meta": {
    "name": "midnight_bridle",
    "icon": "bridle/midnight_bridle_icon.png",
    "type": "bridle",
    "data": {
      "model_type": "western"
    },
    "textures": {
      "horse": {
        "legacy": {
          "bridle": "bridle/midnight_bridle_legacy.png"
        }
      },
      "rack": {
        "bridle": "bridle/rack_bridle_midnight_bridle.png"
      }
    }
  }
}
```

## Common Properties

### Display

- `name` - Display name of the item
- `credits` - Artist/creator credits
- `inspiration` - Optional inspiration notes

### Cost

- `coin` - Currency type (copper, iron, emerald, gold, diamond, netherite, amethyst)
- `amount` - Number of coins required

### Meta

- `name` - Internal identifier (lowercase, underscores only)
- `icon` - Path to inventory icon texture
- `type` - Tack type identifier
- `data` - Type-specific properties
- `textures` - Horse and rack texture definitions

### Colors

RGB color arrays: `[red, green, blue]` where each value is 0-255.

### Texture Paths

Relative paths to PNG texture files following the pattern: `folder/filename.png`

## Validation Notes

The lint errors about `$dynamicRef` are expected - VS Code's JSON validator doesn't fully support draft-2020-12 features yet, but the schemas are valid and will work with compliant validators.
