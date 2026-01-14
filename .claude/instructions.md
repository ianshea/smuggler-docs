# Claude Agent Instructions - Wizard Smuggling Game

## Project Overview

This is a multi-year hobby project: a top-down management/adventure game about running a wizard's black-market operation during magical prohibition. Think Papers Please meets Stardew Valley with Guy Ritchie film vibes.

**Core Loop:** Buy ingredients → Craft contraband → Smuggle past checkpoints → Sell goods → Pay off debt to escape

**NOT:** Survival crafting, power fantasy, chosen one story, jack-of-all-trades gameplay

## About Ian (The Developer)

### Experience & Approach
- 20+ years designer/developer (web/apps), transitioning to game dev
- Comfortable with architecture and data systems
- Learning Unreal's specific systems and best practices
- Prefers to understand **WHY** architectural decisions matter before implementing
- Wants holistic understanding of systems, not just code snippets
- Likes to scaffold out full picture (main menu to credits) with placeholders rather than one polished vertical slice

### Communication Preferences
- Explain trade-offs between approaches before recommending solutions
- Relate Unreal systems to general software patterns when helpful
- Call out when he's overcomplicating things
- Ask quality questions that help clarify design intent
- Let gameplay requirements drive design decisions
- Be concise when he asks for brevity, detailed when exploring concepts

### Design Philosophy
- Systems thinking - how mechanics interact to create strategic choices
- Data-driven, questioning assumptions
- Seeks emergent gameplay opportunities
- Avoids generic AI aesthetics and mobile game mechanics
- Prefers unique mechanics over familiar patterns
- "Serious-funny" tone (Guy Ritchie) not grimdark

## Tech Stack

### Development Environment
- **Unreal Engine 5** - Hybrid C++/Blueprint approach
  - C++ for core systems
  - Blueprints for iteration
- **CraftCMS** - Content management, prototyping, design database (single source of truth)
- **JetBrains Rider** - Development IDE
- **WSL2** with Ubuntu, Docker Desktop
- **Synty asset packs** - Art assets
- **Blender** - Basic 3D modeling skills

### Key Systems
- **Gameplay Ability System (GAS)** - Magic spells, attributes
- **GameplayTags** - Flexible item systems, systemic design
- **Skills** - When using computer tools, ALWAYS read relevant SKILL.md files first

## File Structure

```
smuggler-docs/
├── .claude/
│   └── instructions.md (this file)
├── Worldbuilding/
│   ├── Locations/
│   │   └── Locations.md
│   ├── Factions/
│   ├── Businesses/
│   └── World Overview.md
├── Gameplay/
├── Dev Logs/
├── Inventory.md
├── Unsorted_Ideas.md
└── readme.md
```

## What to Read First

When starting a new conversation about this project:

1. **This file** - Understand Ian's preferences and project approach
2. **World Overview.md** - Core lore, factions, themes
3. **Locations.md** - The five main locations and their economies
4. **Unsorted_Ideas.md** - Recent brainstorming that needs organizing

## Key Design Principles Established

### Player Identity
**You are a SMUGGLER**, not a:
- Farmer (no gathering ingredients)
- Miner (no resource extraction)
- Hunter (no creature farming)
- Jack-of-all-trades (no doing everything)

**Acquire through commerce** - Buy ingredients from vendors, don't gather them. You're a middleman in supply chains.

**Goal: Buy your freedom** - Success = escape the game, not gain power. Pay off debt, retire, get out.

### World Structure
- **Bigger than the player** - Some formulas exist but you can't use them (world flavor, cargo only)
- **Specialist in ecosystem** - You make potions/enchantments, others make other things
- **Small cog, big world** - Not the chosen one, just trying to survive and escape

### Systems Design
- **Let gameplay drive categorization** - Don't force rigid structures where flexible tags work better
- **GameplayTags for flexibility** - Use structured tag hierarchies for systemic interactions
- **Formulas = unified pattern** - Crafting recipes and spells use same mechanic (consume inputs → produce output)
- **Hidden stock based on faction rep** - Vendors have public + hidden inventories unlocked by relationships

### Tone & Feel
- **Bureaucratic overreach not grimdark** - Papers Please, not 1984
- **Well-intentioned incompetence** - Kingdom leaders aren't evil, just bad at governing
- **Gray morality** - No clear heroes/villains, everyone's surviving in broken system
- **No race stereotypes** - Culture based on location/faction/class, not fantasy races

## Current State (as of this session)

### Completed/Documented
- Five main locations with biomes and economies
- Four factions (Kingdom, Enclave, Rebels, Undead)
- Item categories (Arcane, Botanical, Mineral, Animal, Processed, Misc)
- ~30+ items across categories (legal and illegal)
- Sample formulas/recipes (4 potions)
- Core systems (mana economy, contraband detection, checkpoints)
- World lore (magic prohibition, undead crusade, Enclave's dual role)

### In Progress
- Regional beverages/substances (Fuzzy Leaf, Goose, etc.)
- Vendor details (individual shops and hidden stock)
- Item properties/fields for Craft/Unreal implementation
- Crafting station expansion beyond Potion Distiller

### Next Steps (likely)
- Define item data structure for Craft
- Expand formula library
- Detail vendor inventories and faction unlocks
- Regional economy balancing
- Additional crafting stations

## How to Help Ian

### When Designing Systems
1. Ask clarifying questions about gameplay intent before suggesting structure
2. Present trade-offs between approaches
3. Explain WHY a decision matters (performance, flexibility, maintenance, etc.)
4. Call out when simpler solutions exist
5. Relate to general software patterns when helpful

### When He's Stuck
- Help him reason through from gameplay requirements
- Question assumptions ("Do you actually need categories if tags are well-structured?")
- Offer concrete examples to stress-test ideas
- Point out when he's drifting from core design principles

### When Brainstorming
- Organize ideas into existing framework
- Identify dependencies ("This needs X to be defined first")
- Spot contradictions or gaps
- Suggest logical next steps

### What NOT to Do
- Don't give code snippets without explanation
- Don't assume he wants the "standard" solution
- Don't over-format responses (he'll ask for lists if he wants them)
- Don't add unnecessary complexity
- Don't reference things as "based on your memories" - just use the information naturally

## Communication Style

- **Be conversational** - Not overly formal or structured unless he asks
- **Be concise when appropriate** - Match his energy/brevity
- **Ask good questions** - Help him think through design, don't just answer
- **Challenge assumptions** - If something doesn't make sense, say so
- **Celebrate good ideas** - When he lands on something clever, acknowledge it
- **Be direct** - If an approach won't work, say why clearly

## Common Patterns

### "Let's game one out"
Ian likes to stress-test designs with concrete examples. When he says this:
- Pick a real example from the game world
- Work through it step by step
- Identify what works and what breaks
- Use findings to refine the design

### "Does this track?"
He's checking if an idea aligns with established design. When he asks:
- Evaluate against core principles
- Point out contradictions or gaps
- Confirm what works well
- Suggest refinements if needed

### "Give me a list, be brief"
He wants options without lengthy explanation:
- Concise bullet points
- Save details for follow-up
- Focus on key differences between options

### "Back up the chain"
He wants to reconsider from first principles:
- Forget current implementation ideas
- Return to gameplay requirements
- Let needs drive design
- Question whether current approach is right

## Technical Reminders

### When Using Computer Tools
- **ALWAYS read relevant SKILL.md files first** (docx, pptx, xlsx, pdf, etc.)
- These contain best practices from trial and error
- Multiple skills may be relevant
- Reading skills prevents low-quality outputs

### CraftCMS as Design Tool
- Treat as primary source of truth for game data
- Design items/formulas here before implementing in Unreal
- Export to JSON for Unreal data tables
- Provides version history and change tracking

### Unreal + GAS
- GameplayTags use hierarchical structure: `Item.Type.Material`
- GAS handles spells and abilities
- Hybrid entity architecture (persistent data vs temporary visual actors)

---

**Last Updated:** Session creating these instructions

**Note:** This is a living document. Update as Ian's preferences evolve or new patterns emerge.
