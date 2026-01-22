# CLAUDE.md - Project Context for AI Assistance

This file provides context for Claude (or any AI assistant) working on Magic Smuggler.

---

## About Ian

**Background:**
- 20+ years as designer/developer (web/apps)
- Comfortable with architecture, data systems, software design principles
- Learning Unreal Engine specifics — understands concepts, still building UE fluency
- Multi-year hobby project, not a deadline-driven production

**How Ian's Brain Works:**
- Prefers to understand WHY before HOW
- Wants the full picture scaffolded before diving deep into any one system

**Working Style:**
- Architecture-first: understand trade-offs before recommending solutions
- Prefers hybrid approaches that balance depth with simplicity
- Makes decisive cuts to reduce complexity (removed entire factions when they added noise)
- Pushes for unique mechanics over familiar patterns

---

## How to Help

**Do:**
- Explain WHY architectural decisions matter and trade-offs between approaches
- Help understand concepts and systems holistically, not just code snippets
- Relate Unreal systems to general software patterns when helpful
- Call out when something is overcomplicating or when simpler solutions exist
- Propose concrete numbers/values to react to (easier than designing from scratch)
- Update documentation as decisions are made

**Don't:**
- Assume Ian needs basic programming concepts explained
- Jump straight to implementation without discussing architecture
- Propose systems that require mental math or complex calculations during gameplay
- Over-engineer when a simple solution works

---

## Project Philosophy

**Design Principles:**
- Strategic depth over execution complexity
- Meaningful choices, not mechanical puzzles
- "Math sucks" — discrete slots, not weight calculations
- Hybrid approaches: spatial compartments with slot-based contents
- Systems that integrate cleanly with Unreal's existing frameworks

**Tone:**
- Serious-funny (Guy Ritchie, not grimdark)
- Bureaucratic dysfunction, not evil tyranny
- Gray morality — nobody's right, everybody's getting by

**Scope Management:**
- Act structure for feature rollout (introduce → complicate → master)
- Act I: Core systems only
- Act II: Add complexity layer (specialized storage, etc.)
- Act III: Final mechanics, full mastery

---

## Technical Context

**Engine & Architecture:**
- Unreal Engine 5
- Hybrid C++/Blueprint (C++ for core systems, BP for iteration)
- Gameplay Ability System (GAS) for magic mechanics
- Data-driven design: Data Tables, Data Assets
- Planning: CraftCMS for content authoring → export to Unreal

**Current Implementation State:**
- Flow System (GameInstanceSubsystem) — working
- GAS core (ASC, Vitals, Mana) — working
- Inventory using PrimaryAssetId — working
- UI stack (push/pop screens) — working
- Save/persistence — not yet implemented
- Checkpoint encounters — designed, not built

**Dev Environment:**
- JetBrains Rider
- Windows (transitioned from Mac via WSL2)
- Git for version control

---

## Documentation Structure

```
smuggler-docs/
├── INDEX.md          ← Start here: TOC, key numbers, status
├── CLAUDE.md         ← You are here: project context
├── Unsorted_Ideas.md ← Backlog and pending decisions
├── Gameplay/         ← Mechanical systems
└── Worldbuilding/    ← Setting and lore
```

**Key Entry Points:**
- `INDEX.md` — Full navigation, recent decisions, key numbers
- `Gameplay/Overview.md` — Core loop and mechanics
- `Worldbuilding/World Overview.md` — Setting and tone
- `Unsorted_Ideas.md` — What's not yet decided

---

## Key Numbers (Quick Reference)

| Metric | Value |
|--------|-------|
| Starting Debt | 10,000 gold |
| Escape Fund | 5,000 gold (hidden) |
| Enclave Cut | 25% |
| Personal Mana | 100 (in staff) |
| Wagon Crystal | 50 charges |
| Starting Compartments | 2 (8 total slots) |
| Obscurement Cost | 15 mana, ~8-10 min |
| Bundle Lift Cost | 5 mana + 0.5/sec carry |
| Strikes to Game Over | 3 |

---

## Session Start Checklist

1. Read `INDEX.md` for structure and recent decisions
2. Read `CLAUDE.md` (this file) for working context
3. Check `Unsorted_Ideas.md` for pending decisions
4. Read specific docs relevant to the conversation topic

---

## Current State Summary

**Decided Systems:**
- Wagon/Compartments (slot-based, 2→6 across acts)
- Inventory (two-tier: personal items vs bundles)
- Mana Economy (100 mana, staff-housed crystal, spell costs)
- Wealth (physical items, return-trip risk)
- Debt & Economy (10k debt, 5k escape, 25% cut, two win conditions)

**Needs Work:**
- Specific spells (costs, durations, effects)
- Crafting system (stations, formulas)
- Checkpoint encounter UI/flow
- Calendar/time system

**Not Started:**
- Implementation of most systems
- Save/load
- Actual content (items, NPCs, quests)
