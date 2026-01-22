# Dialogue System

How NPCs talk to you—the philosophy, structure, and framework for creating conversations that feel alive without relying on AI generation.

For checkpoint-specific dialogue mechanics, see [[Checkpoint Encounters]].

---

## Design Philosophy

Most game dialogue lacks depth. Players love building relationships, but NPCs often feel like vending machines with voice lines.

**Goal:** Create a system where conversations feel contextual and personal, using structured data and state variables—not procedural AI.

**Core Principle:** A vendor who remembers what you bought last time, comments on the weather, and gradually warms up to you feels more real than one with 50 generic voice lines.

---

## Context Variables

Every conversation pulls from global and personal state to select appropriate dialogue.

### Global Context

| Variable | Example Values | Effect on Dialogue |
|----------|----------------|-------------------|
| **Time of Day** | Morning, Afternoon, Evening, Night | Greetings, energy level, availability |
| **Weather** | Clear, Rain, Storm, Snow | Mood, small talk topics, complaints |
| **Season** | Spring, Summer, Autumn, Winter | Seasonal references, stock availability |
| **Recent Events** | Kingdom crackdown, festival, battle | What's on everyone's mind |

### Personal Context (Per NPC)

| Variable | Example Values | Effect on Dialogue |
|----------|----------------|-------------------|
| **Relationship Level** | Stranger, Acquaintance, Regular, Friend | Formality, trust, what they'll share |
| **Interaction Count** | 0, 1-3, 4-10, 10+ | Greeting length, recognition |
| **Last Purchase** | Mushrooms, Herbs, Nothing | "More of the usual?" prompts |
| **Time Since Last Visit** | Hours, Days, Weeks | "Haven't seen you in a while" |
| **Faction Standing** | Your rep with their faction | Hidden stock access, pricing, trust |

---

## Greeting System

### Greeting Selection

When you approach an NPC, the system selects a greeting based on context. Example for a vendor:

**Kenneth (Mushroom Vendor, Riverton)**

| Conditions | Greeting Pool |
|------------|---------------|
| First meeting | "Don't think I've seen you before. Looking for mushrooms?" |
| Rain + Afternoon + Bought mushrooms before | "Afternoon mate, shite weather to be out in. Looking for more mushrooms?" |
| Rain + Afternoon + Bought herbs before | "Rainy afternoon friend, need some more herbs?" |
| Regular customer + Morning | "Early start today! The usual?" |
| Haven't visited in weeks | "Thought you'd forgotten about old Kenneth!" |

### Greeting Length Degradation

Repeated interactions in a short time should get shorter:

| Visit # (same day) | Greeting Style |
|--------------------|----------------|
| 1st | Full contextual greeting |
| 2nd | Shorter acknowledgment ("Back again?") |
| 3rd+ | Minimal or skip ("*nods*") |

This prevents repetitive dialogue when players are doing multiple transactions.

---

## Regional Voice

Different regions have distinct speech patterns, vocabulary, and tone.

### Voice Elements

| Element | Description |
|---------|-------------|
| **Formality** | How proper vs casual |
| **Slang/Idioms** | Region-specific expressions |
| **Terms of Address** | How they refer to strangers vs friends |
| **Attitude** | Default disposition toward outsiders |

### Regional Examples (TBD)

| Region | Tone | Sample Address Terms |
|--------|------|---------------------|
| **Riverton** | Working-class, friendly | Mate, friend, pal |
| **Capital/Kingsmoor** | Formal, guarded | Sir, madam, traveler |
| **Ashford Crossing** | Rough, direct | Stranger, you, (none) |
| **Snowmarch** | Reserved, polite | Good sir, visitor |
| **Thornhaven** | Bureaucratic, cold | Citizen, debtor, contractor |

---

## Relationship Progression

### Relationship Levels

| Level | Interactions | NPC Behavior |
|-------|--------------|--------------|
| **Stranger** | 0 | Generic greetings, no personal references |
| **Acquaintance** | 1-3 | Remembers your face, maybe your trade |
| **Regular** | 4-10 | Knows your name, preferences, small talk |
| **Friend** | 10+ | Personal conversations, favors, tips |

### What Builds Relationship

- Repeated transactions
- Completing requests/favors
- Dialogue choices (asking about them, being polite)
- Faction reputation with their group
- Story events

### Relationship Benefits

| Level | Unlocks |
|-------|---------|
| Acquaintance | Name recognition, slightly better prices |
| Regular | Purchase history shortcuts, gossip/tips |
| Friend | Hidden stock hints, quest opportunities, warnings |

---

## Conversation Structure

### Standard NPC Interaction

```
[Greeting - contextual]
    │
    ├── Talk → Conversation options
    │         ├── Ask about [topic]
    │         ├── Small talk
    │         └── [Quest/Narrative if available]
    │
    ├── Trade → Transaction screen
    │         (Pre-populated with last purchase if Regular+)
    │
    └── Leave → Exit dialogue
```

### Conversation Options

**Talk** branches can unlock:
- Information about the region/events
- Hints about opportunities
- Relationship building
- Quest hooks
- Lore/worldbuilding flavor

Not every NPC needs deep conversation trees. Vendors might just have 2-3 talk options. Key story NPCs have more.

---

## Writer Framework

### Dialogue Entry Structure

For each NPC, writers create:

```
NPC: Kenneth
Location: Riverton
Role: Mushroom Vendor
Voice: Working-class, friendly, complainer

GREETINGS:
- [default]: "Looking for mushrooms today?"
- [first_meeting]: "Don't think I've seen you before. Looking for mushrooms?"
- [rain]: "Shite weather, innit? At least the mushrooms love it."
- [rain + returning_customer]: "Afternoon mate, shite weather to be out in. Looking for more mushrooms?"
- [morning]: "Early bird! Best caps are still fresh."
- [repeat_same_day]: "Back again?"
- [repeat_same_day_2+]: "*nods*"
- [long_absence]: "Thought you'd forgotten about old Kenneth!"

TALK_OPTIONS:
- "How's business?": [relationship >= acquaintance]
    - [default]: "Can't complain. Well, I can, but who's listening?"
    - [rain]: "Slow day. Everyone's hiding from the wet."
- "Heard any rumors?": [relationship >= regular]
    - [varies by current_events]

TRADE_PROMPT:
- [last_purchase exists]: "More [last_purchase]? Or something different?"
- [default]: "What can I get you?"
```

### Condition Tags

Writers use standardized tags that map to game state:

| Tag | Meaning |
|-----|---------|
| `[rain]` | Weather is rainy |
| `[morning]` | Time is morning |
| `[first_meeting]` | Interaction count = 0 |
| `[returning_customer]` | Has purchased before |
| `[repeat_same_day]` | Already talked today |
| `[long_absence]` | 7+ days since last interaction |
| `[relationship >= X]` | Relationship at or above level |
| `[faction.rebels >= 3]` | Faction rep requirement |

---

## Open Questions

- How many greeting variations per NPC? (Diminishing returns vs repetition)
- Do we need a "mood" system for NPCs? (Bad day = grumpy regardless of relationship)
- How do we handle NPCs with multiple roles? (Vendor who's also a quest giver)
- Should relationship decay over time without interaction?
- How does this integrate with the Spellbook-as-Consigliere concept? (Does it comment on NPCs?)

---

## Related Systems

- [[Checkpoint Encounters]] — Dialogue during inspections (more mechanical)
- [[Contacts]] — Vendor relationships and hidden stock
- [[Locations]] — Where NPCs live, regional flavor
- [[Calendar]] — Time/season that affects dialogue
