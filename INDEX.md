# Magic Smuggler - Design Document Index

**Game:** Top-down management/adventure game — Papers Please meets Stardew Valley with Guy Ritchie tone
**Engine:** Unreal Engine 5 (GAS for magic, hybrid C++/Blueprint)
**Status:** Multi-year hobby project, design phase

---

## Quick Reference: Key Numbers

| Metric | Value |
|--------|-------|
| Starting Debt | 10,000 gold |
| Escape Fund Target | 5,000 gold (hidden) |
| Enclave Cut | 25% of visible earnings |
| Personal Mana (starting) | 100 (in staff) |
| Wagon Crystal (starting) | 50 charges |
| Wagon Compartments | 2 → 6 (across acts) |
| Starting Cargo Capacity | 8 slots |
| Strikes to Game Over | 3 |

---

## Start Here

| Document | What It Covers |
|----------|----------------|
| [[CLAUDE]] | Project context, working style, how to help |
| [[Gameplay/Overview]] | Core loop, mechanics summary, player goal |
| [[Worldbuilding/World Overview]] | Setting, factions, tone, themes |
| [[Unsorted_Ideas]] | Backlog of ideas and decisions pending |

---

## Core Systems (Decided)

These systems have concrete numbers and documented designs.

### Economy & Progression

| Document | Status | Summary |
|----------|--------|---------|
| [[Gameplay/Debt & Economy]] | ✅ Decided | 10k debt, 5k escape, 25% cut, two win conditions |
| [[Gameplay/Wealth/Wealth]] | ✅ Decided | Physical wealth items, return-trip risk, hiding from Enclave |

### Mana & Magic

| Document | Status | Summary |
|----------|--------|---------|
| [[Gameplay/Magic/Mana Economy]] | ✅ Decided | 100 mana, spell costs, budget planning |
| [[Gameplay/Magic/Mana Crystals]] | ✅ Decided | Crystal in staff, wagon crystal separate |
| [[Gameplay/Magic/How Magic Works]] | ✅ Documented | Mana forms, spell types, prohibition context |

### Inventory & Cargo

| Document | Status | Summary |
|----------|--------|---------|
| [[Gameplay/Inventory]] | ✅ Decided | Two-tier system (personal items vs bundles), loading costs |
| [[Gameplay/Wagon]] | ✅ Decided | Compartment system, 2→6 progression, slot-based capacity |

### Checkpoints & Smuggling

| Document | Status | Summary |
|----------|--------|---------|
| [[Gameplay/Smuggling/Checkpoints]] | ✅ Documented | Overview, links to subsystems |
| [[Gameplay/Smuggling/Checkpoint Encounters]] | ✅ Documented | Dialogue + interrupts, suspicion meter, Heat |
| [[Gameplay/Checks & Contests]] | ✅ Documented | M.A.G.I.C. stats, hybrid resolution, GAS mapping |
| [[Gameplay/Smuggling/Checkpoints/Guards]] | ✅ Documented | Ranks, occupations, traits |

### Player

| Document | Status | Summary |
|----------|--------|---------|
| [[Gameplay/Player Character]] | ✅ Documented | M.A.G.I.C. stats, equipment slots, staff/crystal |
| [[Gameplay/Goods/Contraband]] | ✅ Documented | Contraband levels 0-6, flavor labels |

---

## Worldbuilding

| Document | What It Covers |
|----------|----------------|
| [[Worldbuilding/World Overview]] | Full setting, prohibition history, factions, tone |
| [[Worldbuilding/Factions/Wizards Enclave]] | Your employer/creditor, how they operate |
| [[Worldbuilding/Factions/Kingdom]] | The governing authority |
| [[Worldbuilding/Factions/Undead]] | The faction that just wants to be left alone |
| [[Worldbuilding/Locations/Locations]] | All locations with vendors and features |

---

## Systems Needing Work

These have documents but need more design or are stubs.

| Document | Status | What's Needed |
|----------|--------|---------------|
| [[Gameplay/Magic/Spells]] | 🔶 In Progress | Spell categories, Spellbook concept, acquisition |
| [[Gameplay/Magic/Potions]] | Stub | Specific potions, effects, crafting |
| [[Gameplay/Magic/Scrolls]] | Stub | Scroll mechanics |
| [[Gameplay/Magic/Enchantments]] | Stub | Enchantment system |
| [[Gameplay/Crafting/*]] | Stubs | Stations, formulas, recipes |
| [[Gameplay/Contacts/Contacts]] | 🔶 In Progress | Vendor system, hidden stock, faction unlocks |
| [[Gameplay/Calendar]] | Stub | Time system, events |
| [[Gameplay/Wealth/Gold]] | Empty | Could merge into Wealth |
| [[Gameplay/Wealth/Gems]] | Empty | Could merge into Wealth |

---

## Technical

| Document | What It Covers |
|----------|----------------|
| [[Technical/Implementation Notes]] | CraftCMS structure, Unreal Data Tables, GameplayTags, Save System |

---

## File Structure

```
smuggler-docs/
├── INDEX.md                    ← Table of contents, key numbers
├── CLAUDE.md                   ← Project context for AI assistance
├── Unsorted_Ideas.md           ← Backlog and pending decisions
├── Conversation Engine.md      ← Dialogue system notes
│
├── Dev Logs/                   ← Development journal
│   └── YYYY-MM-DD.md
│
├── Technical/                  ← Implementation planning
│   └── Implementation Notes.md
│
├── Gameplay/                   ← Mechanical systems
│   ├── Overview.md             ← Start here for mechanics
│   ├── Player Character.md
│   ├── Inventory.md
│   ├── Wagon.md
│   ├── Checks & Contests.md
│   ├── Debt & Economy.md
│   ├── Calendar.md
│   │
│   ├── Magic/
│   │   ├── How Magic Works.md
│   │   ├── Mana.md
│   │   ├── Mana Crystals.md
│   │   ├── Mana Economy.md     ← Key numbers
│   │   ├── Spells.md
│   │   ├── Potions.md
│   │   ├── Scrolls.md
│   │   └── Enchantments.md
│   │
│   ├── Smuggling/
│   │   ├── Smuggling.md
│   │   ├── Checkpoints.md
│   │   ├── Checkpoint Encounters.md
│   │   └── Checkpoints/
│   │       ├── Guards.md
│   │       ├── Documents.md
│   │       ├── Inspections.md
│   │       ├── Checkpoint Devices.md
│   │       └── Checkpoint Fail.md
│   │
│   ├── Goods/
│   │   ├── Contraband.md
│   │   └── Legal Goods.md
│   │
│   ├── Wealth/
│   │   ├── Wealth.md           ← Key doc
│   │   ├── Gold.md
│   │   └── Gems.md
│   │
│   ├── Crafting/
│   │   ├── Artifacts.md
│   │   ├── Knowledge.md
│   │   ├── Resources.md
│   │   └── Tools.md
│   │
│   ├── Contacts/
│   │   └── Contacts.md
│   │
│   └── Resources/
│       └── Resource.md
│
└── Worldbuilding/              ← Setting and lore
    ├── World Overview.md       ← Start here for setting
    │
    ├── Factions/
    │   ├── Kingdom.md
    │   ├── Wizards Enclave.md
    │   ├── Undead.md
    │   └── Races/
    │       └── [race].md
    │
    ├── Locations/
    │   └── Locations.md
    │
    └── Businesses/
        ├── Legal/
        ├── Illegal/
        └── Faction Fronts/
```

---

## Recent Decisions (This Session)

| System | Decision |
|--------|----------|
| Wagon Cargo | Compartment-based, slot capacity (not spatial tetris) |
| Compartment Progression | 2 → 3 (Act I) → 4 (Act II) → 5-6 (Act III) |
| Inventory | Two-tier: personal items vs bundles |
| Bundle Loading | Costs mana (5 to lift, 0.5/sec while carrying) |
| Mana Crystal Location | In staff (staff upgrade = capacity upgrade) |
| Personal Mana | 100 starting, upgrades via staff |
| Wagon Crystal | 50 charges, separate pool |
| Obscurement | 15 mana, ~8-10 min real-time duration |
| Starting Debt | 10,000 gold |
| Escape Fund | 5,000 gold (hidden wealth) |
| Enclave Cut | 25% of visible earnings |
| Win Conditions | Two paths: pay off debt OR escape with hidden wealth |

---

## How to Use These Docs

**Starting a new conversation:**
1. Read this INDEX.md for structure and key numbers
2. Check [[Unsorted_Ideas]] for pending decisions
3. Read specific docs relevant to the topic

**For context on core loop:** [[Gameplay/Overview]]

**For setting/tone:** [[Worldbuilding/World Overview]]

**For specific systems:** Use the tables above to find the right doc

---

## Technical Context

- **Engine:** Unreal Engine 5
- **Architecture:** Hybrid C++/Blueprint, GAS for magic
- **Data:** Data-driven design, planning CraftCMS → Unreal export
- **Current Focus:** Design documentation before implementation
