# Checks & Contests

This document defines how contested checks work mechanically—the core system that powers checkpoint encounters, NPC interactions, and any situation where your stats are tested against opposition.

---

## Design Philosophy

- **Universal stats** - Players and NPCs use the same M.A.G.I.C. system
- **Hybrid resolution** - Stat comparison determines odds, dice add variance
- **Modifier stacking** - Spells, equipment, traits, and situation all contribute
- **D&D-inspired** - Familiar language (checks, contests, modifiers) mapped to video game systems
- **GAS-ready** - Designed to implement cleanly in Unreal's Gameplay Ability System

---

## M.A.G.I.C. Stats

| Stat | Meaning | Primary Uses |
|------|---------|--------------|
| **Moxie** | Confidence, Charisma, Nerve | Persuasion, intimidation resistance, bribe negotiations |
| **Arcana** | Magical Knowledge | Spell effectiveness, concealment vs. detection, mana efficiency |
| **Grit** | Toughness, Willpower | Resist spells, endure negative effects, mana regeneration |
| **Intuition** | Perception, Foresight | Detect lies, read situations, preview incoming checks |
| **Cunning** | Deception, Trickery | Stealth, hiding contraband, lying convincingly |

Both player and NPCs have these stats. Every contest pits one stat against another.

---

## Check Resolution (Hybrid Model)

Checks use a **hybrid** system: stat comparison determines your success chance, then a roll introduces variance.

### Step 1: Calculate Effective Stats

For both participants, calculate:

```
Effective Stat = Base Stat + Modifiers
```

Modifiers come from:
- Active spells (duration-based, costs mana)
- Equipment (passive, always-on while worn)
- Potions (consumable, temporary buff)
- Traits (NPC personality modifiers)
- Situational (weather, time of day, checkpoint events)

### Step 2: Determine Success Chance

Compare effective stats to get a **success chance** percentage:

| Difference (Your Stat - Their Stat) | Success Chance |
|-------------------------------------|----------------|
| +5 or more | 95% (near certain) |
| +4 | 90% |
| +3 | 80% |
| +2 | 70% |
| +1 | 60% |
| 0 (tied) | 50% |
| -1 | 40% |
| -2 | 30% |
| -3 | 20% |
| -4 | 10% |
| -5 or worse | 5% (near impossible) |

> **Note:** Exact curve is tunable. This is a starting point that gives meaningful variance without making stats feel pointless.

### Step 3: Roll

System rolls against the success chance. Player sees the result.

- **Pass:** You succeed at the check
- **Fail:** You fail the check

Checks are **binary**—no partial success. However, checkpoint encounters involve multiple checks, so the overall encounter has texture even with binary individual outcomes.

---

## Contest Types

| Situation | Your Stat | Their Stat | Example |
|-----------|-----------|------------|---------|
| Convincing someone | Moxie | Moxie | Talking your way past a guard |
| Negotiating a bribe | Moxie | Moxie (modified by traits) | How much will they take? |
| Magical concealment | Arcana | Arcana | Your obscurement vs. their detection |
| Resisting their spell | Grit | Arcana | Guard casts compulsion, you resist |
| Casting on them | Arcana | Grit | You cast charm, they resist |
| Lying convincingly | Cunning | Intuition | Your deception vs. their read |
| Hiding contraband | Cunning | Cunning | Your hiding spots vs. their search |
| Reading their intentions | Intuition | Cunning | Do you see the trap coming? |
| Anticipating checks | Intuition | — | Preview what inspection is coming |

---

## Modifier Sources

### Spells (Active)

Cast by the player, powered by personal mana crystal.

- Provide temporary stat bonuses or penalties (to self or target)
- Have **duration**—countdown that can expire at bad moments
- Cost mana—a limited resource per trip
- Some spells affect checks directly (Obscurement adds to Arcana for concealment)

### Equipment (Passive)

Worn items that provide constant effects while equipped.

- Stat bonuses (+1 Cunning from enchanted gloves)
- Special abilities (ring that grants one free re-roll per encounter)
- No ongoing cost, but limited slots

### Potions (Consumable)

Drink for temporary buff. Gone once used.

- Strong but temporary stat boosts
- Takes an action to use (or pre-encounter preparation)
- Limited inventory (belt quick slots)

### Traits (NPC)

Guard traits modify their effective stats or change check behavior.

**Exploitable:**
- *Greedy* — Bribe checks easier, lower cost
- *Lazy* — Fewer checks, lower Cunning for searches
- *Rookie* — Lower stats overall
- *Stressed* — Penalty to Intuition

**Challenging:**
- *Sharp* — Bonus to Intuition
- *Loyal* — Bribe checks much harder or impossible
- *Veteran* — Bonus across the board
- *Zealot* — Immune to bribery, high Grit

See [[Guards]] for full trait list.

### Situational

Environmental and contextual modifiers:

| Situation | Effect |
|-----------|--------|
| Night | Bonus to Cunning (concealment), penalty to Intuition (visibility) |
| Rain/Storm | Guards less thorough (Lazy-like effect), travel slower |
| Fog | Bonus to concealment checks |
| Crackdown event | Guards get bonuses, more checks triggered |
| Festival/Crowds | Distracted guards, fewer checks |
| Your Heat is high | Starting suspicion higher, tougher guards assigned |

---

## Pre-empt and React Windows

Not all checks are equal. Your build determines **when** you can act:

| Window | When It Triggers | What You Can Do |
|--------|------------------|-----------------|
| **Pre-empt** | Before a check resolves | Cast a spell, present a document, prepare for what's coming |
| **React** | After a check fails | Attempt a bribe, talk your way out, quick-cast to cover |
| **Passive** | Always on | High Intuition previews incoming checks |

These windows can be:
- Unlocked by stats (high Intuition grants pre-empt awareness)
- Granted by equipment (an item that gives a react window)
- Skill/ability choices (you pick which abilities fill your slots)

---

## GAS Implementation Notes

The M.A.G.I.C. system maps cleanly to GAS:

### Attributes

Each M.A.G.I.C. stat is a **Gameplay Attribute**:
- `Moxie`
- `Arcana`
- `Grit`
- `Intuition`
- `Cunning`

Both player and NPCs have an **Attribute Set** containing these.

### Modifiers via Gameplay Effects

Spells, equipment, potions, and situational modifiers are **Gameplay Effects** that modify attributes:

- **Spell:** Gameplay Effect with duration, applied on cast
- **Equipment:** Gameplay Effect applied on equip, removed on unequip
- **Potion:** Gameplay Effect with duration, applied on consume
- **Trait:** Gameplay Effect applied to NPC at spawn (or baked into their attribute defaults)
- **Situational:** Gameplay Effect applied based on world state (time, weather, events)

### Check Execution

When a check occurs:

1. Get player's effective stat (base + all active modifiers)
2. Get NPC's effective stat (base + all active modifiers)
3. Calculate success chance from difference
4. Roll (or use deterministic seed for replays/testing)
5. Return pass/fail
6. Trigger appropriate Gameplay Cue for feedback

### Gameplay Cues

Visual/audio feedback for:
- Check occurring (what's being tested)
- Check passed (relief, success indicator)
- Check failed (tension, danger indicator)
- Suspicion rising/falling
- Pre-empt/react window opening

---

## Related Systems

- [[Player Character]] — Your stats and equipment
- [[Guards]] — NPC stats, ranks, occupations, traits
- [[Checkpoint Encounters]] — Where most checks happen
- [[How Magic Works]] — Spells and mana economy
- [[Calendar]] — Situational modifiers from events and weather
