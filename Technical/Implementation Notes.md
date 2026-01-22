# Technical Implementation Notes

Implementation planning for Unreal Engine 5 and CraftCMS. This is **how to build it**, not **what the game is**—see the Gameplay docs for design.

---

## Item Data Structure

### Fields Needed

**Basic Info:**
- Name
- Description (flavor text, lore)
- Icon/Visual representation

**Categorization:**
- Item Category (Arcane, Botanical, Mineral, Animal, Processed, Misc)
- Subcategories (legal vs illegal botanical, etc.)

**Physical Properties:**
- Weight (cargo capacity implications)
- Size/Volume (concealment mechanics)
- Stackable? Max stack size?

**Economic Properties:**
- Base value (gold cost)
- Regional price modifiers
- Vendor markup percentages
- Black market vs legal market pricing

**Contraband Properties:**
- Contraband level (0-6, see [[Contraband]])
- Detection methods (Physical.Suspicious, Magic.Aura, etc.)
- Concealment difficulty
- Penalty if caught

**Consumable Properties (if applicable):**
- Can player use/consume this?
- Buff/debuff effects
- Duration
- Cooldowns?

**Crafting Properties:**
- Is this a crafting ingredient?
- Is this a crafted product?
- Which stations can use/produce it?

---

## GameplayTag Structure

### Proposed Hierarchy

```
Item.Type.*
    Item.Type.Material
    Item.Type.Product
    Item.Type.Equipment
    Item.Type.Consumable

Item.Contraband.*
    Item.Contraband.Legal
    Item.Contraband.Level.1
    Item.Contraband.Level.2
    ...
    Item.Contraband.Level.5

Item.System.*
    Item.System.Crafting.Input
    Item.System.Crafting.Output
    Item.System.Spell.Component
    Item.System.Quest

Detection.*
    Detection.Physical.Suspicious
    Detection.Physical.Odor
    Detection.Magic.Aura
    Detection.Magic.Residue

Faction.*
    Faction.Kingdom.Banned
    Faction.Rebels.Valued
    Faction.Enclave.Property
```

### Open Questions

- Required vs optional tags per item?
- How to structure in CraftCMS (Categories vs native tags)?
- Export mapping to Unreal GameplayTags
- How many tags per item is reasonable?

---

## CraftCMS Structure

### Entry Types Needed

| Entry Type | Purpose |
|------------|---------|
| **Item** | All game items (ingredients, products, equipment) |
| **Formula** | Crafting recipes and spell formulas |
| **Location** | Regions, cities, specific venues |
| **Vendor** | NPCs who buy/sell |
| **Faction** | Kingdom, Enclave, Rebels, etc. |

### Relationships

| From | To | Relationship |
|------|----|--------------|
| Formula | Item | Inputs (ingredients) |
| Formula | Item | Outputs (products) |
| Vendor | Item | Inventory (public + hidden) |
| Vendor | Location | Where they operate |
| Item | Location | Regional goods (where produced) |
| Item | Faction | Faction associations |

### Export Format

Target: JSON structure that Unreal can import into Data Tables.

```json
{
  "items": [
    {
      "id": "ghost_caps",
      "name": "Ghost Caps",
      "category": "Botanical",
      "contraband_level": 3,
      "base_value": 50,
      "tags": ["Item.Type.Material", "Detection.Magic.Aura"],
      ...
    }
  ]
}
```

---

## Unreal Data Tables

### Item Data Table

Maps to CraftCMS Item entries. Row structure:

| Field | Type | Notes |
|-------|------|-------|
| RowName | FName | Unique ID from CraftCMS |
| DisplayName | FText | Localized name |
| Description | FText | Flavor text |
| Icon | TSoftObjectPtr<UTexture2D> | Asset reference |
| Category | EItemCategory | Enum |
| ContrabandLevel | int32 | 0-6 |
| BaseValue | int32 | Gold |
| Weight | float | Cargo capacity |
| Tags | FGameplayTagContainer | From CraftCMS export |

### Formula Data Table

| Field | Type | Notes |
|-------|------|-------|
| RowName | FName | Unique ID |
| DisplayName | FText | |
| FormulaType | EFormulaType | Crafting/Spell/Enchanting |
| Inputs | TArray<FItemQuantity> | Ingredient list |
| Outputs | TArray<FItemQuantity> | Product list |
| StationRequired | EStationType | Which station |
| IsLearnable | bool | Player can learn vs cargo-only |

### Cross-Table References

Use RowName as foreign key between tables. Unreal's FDataTableRowHandle can reference rows in other tables.

---

## Save System

### What Persists

| Data | Storage | Notes |
|------|---------|-------|
| Wagon state | SaveGame | Cargo, upgrades, crystal charge |
| Player inventory | SaveGame | Personal items, gold |
| Debt amount | SaveGame | Current debt to Enclave |
| Hidden wealth | SaveGame | Escape fund progress |
| Faction reputation | SaveGame | Per-faction rep levels |
| Learned spells | SaveGame | Permanent unlocks |
| Prepared spells | SaveGame | Current loadout |
| Story flags | SaveGame | Quest progress, decisions |
| Calendar position | SaveGame | Current date/season |

### Session vs Permanent

| Session (resets on load) | Permanent (persists) |
|--------------------------|----------------------|
| Active spell durations | Learned spells |
| Current checkpoint state | Faction reputation |
| NPC conversation position | Completed quests |
| Temp buffs/debuffs | Debt/wealth |

### Architecture Notes

- Use UGameInstanceSubsystem for runtime state
- USaveGame subclass for serialization
- Consider async saves for large data
- Multiple save slots? Cloud saves?

---

## Procedural vs Authored Content

### Fixed/Authored

| Content | Why Fixed |
|---------|-----------|
| Main story beats | Narrative coherence |
| Key NPCs | Character development |
| Location layouts | Level design quality |
| Core item list | Balance testing |

### Procedural/Dynamic

| Content | Why Procedural |
|---------|----------------|
| Guard traits at checkpoints | Replayability |
| Vendor inventory refresh | Economy feels alive |
| Random encounter selection | Route variety |
| Price fluctuations | Market dynamics |

### Hybrid

| Content | Approach |
|---------|----------|
| Checkpoint encounters | Authored dialogue trees, procedural guard selection |
| Side quests | Authored quest templates, procedural targets/rewards |
| NPC schedules | Authored patterns, procedural variation |

---

## Open Technical Questions

- Checkpoint encounters: turn-based, real-time, or dialogue tree?
- How does CraftCMS export trigger? Manual, CI/CD, runtime fetch?
- Version control strategy for Data Tables vs CraftCMS as source of truth?
- Hot reload during development or restart required?

---

## Related

- [[CLAUDE]] — Project context
- [[INDEX]] — Design document structure
