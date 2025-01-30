Here's the complete file in a directly copyable format (without the code block markers around it):

# Cyberpunk 2077 Modding Guide
## Basic Concepts for YAML Tweaks

### Prerequisites
- TweakXL
- RED4ext 
- Visual Studio Code (or another text editor)
- Basic understanding of YAML format

### Core Concepts

#### 1. YAML Structure
YAML tweaks require strict indentation (2 spaces recommended, avoid tabs). Basic structure:

```yaml
RecordName:
  property1: value1
  property2: 
    - subvalue1
    - subvalue2
```

#### 2. Record Types
- **Records**: Unique containers grouping multiple properties
- **Flats**: Simple values (numbers, text, booleans)
- **Inlines**: Records nested directly within other records

#### 3. Common Operations

**Adding to Vendors:**
```yaml
Vendors.vendor_id:
  itemStock:
    - !append
      $type: VendorItem
      item: Items.YourItemID
      quantity: [Vendors.Always_Present]
```

**Modifying Items:**
```yaml
Items.item_id:
  statModifiers:
    - !append Quality.IconicItem
```

**Changing NPCs:**
```yaml
npc_id:
  displayName: "New Name"
  archetypeData: "ArchetypeData.TypeHere"
  affiliation: "Factions.FACTION_NAME"
```

### Best Practices

1. **Never use `inlineX` records** as base for your items - they can change with game updates
2. **Test thoroughly** - vendor changes require 24h game time to take effect
3. **Keep backups** of your mod files
4. **Use proper indentation** - YAML is very sensitive to formatting
5. **Research existing examples** in the game files before making changes

### File Structure
```
your_mod/
  ├── r6/
  │   └── tweaks/
  │       └── your_mod.yaml
  └── info.json
```

### Common Issues
- Incorrect indentation will break the mod
- Changes to vendor inventory require waiting/sleeping 24h in-game
- Some changes may require game restart
- Always check for conflicts with other mods

### Resources
- [TweakXL Documentation](https://github.com/psiberx/cp2077-tweak-xl)
- [Cyberpunk 2077 Modding Wiki](https://wiki.redmodding.org/)
- YAMLlint for validation

This guide covers basic concepts - refer to the modding wiki for detailed tutorials and advanced techniques.
