# Guards

Guards staff checkpoints and conduct inspections. They're the primary obstacle between you and successful smuggling.

---

## Guard Stats (M.A.G.I.C.)

Guards use the same stat system as the player. Every contest is your stat vs their stat.

| Stat | What It Means for Guards | Contest Against Player |
|------|--------------------------|------------------------|
| **Moxie** | Confidence, authority, ability to intimidate | Your Moxie (who controls the interaction, bribe negotiations) |
| **Arcana** | Magical detection ability, dispelling obfuscation | Your Arcana (your concealment spells vs their detection) |
| **Grit** | Mental toughness, resistance to manipulation | Your Grit (your charm/sleep spells vs their willpower) |
| **Intuition** | Reading people, noticing nervousness, spotting inconsistencies | Your Cunning (they read you, you deceive them) |
| **Cunning** | Thoroughness, tactical thinking, not easily tricked | Your Cunning (their search tactics vs your hiding tactics) |

---

## What Makes a Guard

Guards are built from **Rank** (stat scaling) + **Occupation** (what they do) + **Traits** (personality modifiers).

### Ranks

Rank determines baseline stat values. Higher rank = higher stats.

| Tier | Ranks | Typical Location |
|------|-------|------------------|
| Low | Watchman, Constable | Riverton, Ashford |
| Mid | Corporal, Sergeant | Most checkpoints |
| High | Lieutenant, Marshal | Snowmarch, Capital gates |
| Elite | Knight-Lieutenant, High Marshal | Thornhaven, special encounters |

**Rank Variants:**
- Watchman → Watch Captain
- Constable → Law Keeper  
- Corporal → Captain
- Sergeant → Sergeant-at-Arms
- Lieutenant → Knight-Lieutenant
- Marshal → High Marshal

### Occupations

Occupation determines what checks the guard performs during inspection.

| Occupation | Focus | What They Do |
|------------|-------|--------------|
| **Guardsman** | Generic | Basic inspection, not that invested, prefers fighting to paperwork |
| **Inspector** | Detection | Thorough cargo search, checks manifests |
| **Customs Officer** | Payment | Requires fees/permits, handles taxes |
| **Detective** | Investigation | Focused on finding something specific, follows leads |
| **Interrogator** | Questioning | Asks lots of questions, reads responses |
| **Mage Breaker** | Magic | Specialized in detecting magical concealment |
| **Informant** | Intelligence | Works for another faction, may have alternate agendas |
| **Pursuer** | Enforcement | Will chase if you run, combat-focused |

### Traits

Traits are buffs/debuffs that modify a guard's behavior and create exploitable weaknesses.

**Exploitable (Work in Your Favor):**
- **Greedy** - More likely to accept bribes, lower bribe cost
- **Lazy** - Skips inspection steps, less thorough
- **Disloyal** - May have faction sympathies you can exploit
- **Desperate** - Needs money, very bribable
- **Rookie** - Inexperienced, easier to deceive
- **Stressed** - Distracted, misses things
- **Dumb** - Low Intuition/Cunning effectiveness
- **Really Dumb** - Very low effectiveness, easily confused

**Challenging (Work Against You):**
- **Sharp** - Bonus to Intuition checks
- **Cunning** - Bonus to search thoroughness
- **Brilliant** - High across the board
- **Loyal** - Won't take bribes, reports everything
- **Veteran** - Experienced, hard to fool
- **Zealot** - Fanatically dedicated, immune to bribery
- **High Strung** - Paranoid, extra inspection steps
- **Curious** - Keeps digging, won't let things go

**Neutral/Situational:**
- **Chatty** - Talks a lot, might reveal information
- **Too Friendly** - Disarming, but might be a trap
- **Irritating** - Annoying, might provoke you into mistakes
- **Connected** - Knows people, information travels fast
- **Smart** - Balanced and competent

---

## Example Guards

### Easy Mark
> **Watchman Greely** (Riverton Checkpoint)
> - **Rank:** Watchman (low stats)
> - **Occupation:** Guardsman
> - **Stats:** Moxie 3 | Arcana 2 | Grit 4 | Intuition 3 | Cunning 2
> - **Traits:** Greedy, Lazy, Rookie
> 
> *Will take a bribe, won't look too hard. Barely wants to be here.*

### Typical Checkpoint
> **Corporal Vance** (Ashford Checkpoint)
> - **Rank:** Corporal (mid stats)
> - **Occupation:** Inspector
> - **Stats:** Moxie 5 | Arcana 4 | Grit 5 | Intuition 5 | Cunning 5
> - **Traits:** Stressed, Veteran
> 
> *Knows his job but overworked. Might miss something if you're careful.*

### Serious Trouble
> **Sergeant Hollis** (Snowmarch Checkpoint)
> - **Rank:** Sergeant (high stats)
> - **Occupation:** Inspector
> - **Stats:** Moxie 6 | Arcana 5 | Grit 7 | Intuition 6 | Cunning 6
> - **Traits:** Loyal, Sharp, Veteran
> 
> *By the book, thorough, won't take a bribe. You need magic or perfect concealment.*

### Nightmare Scenario
> **Knight-Lieutenant Ashworth** (Thornhaven Gate)
> - **Rank:** Knight-Lieutenant (elite stats)
> - **Occupation:** Mage Breaker
> - **Stats:** Moxie 7 | Arcana 8 | Grit 7 | Intuition 7 | Cunning 7
> - **Traits:** Zealot, Brilliant, Curious
> 
> *Specializes in catching smugglers like you. Avoid if possible.*

---

## Checkpoint Contests

When you encounter a guard, various contests may occur based on their occupation and the situation:

| Situation | Your Stat | Their Stat | What's Happening |
|-----------|-----------|------------|------------------|
| Talking your way through | Moxie | Moxie | Social contest, convincing them to let you pass |
| Negotiating a bribe | Moxie | Moxie (modified by Greedy/Loyal traits) | Offering money, reading how much they'll take |
| Hiding magical items | Arcana | Arcana | Your concealment vs their detection |
| Casting on them (Charm, Sleep) | Grit | Grit | Your spell strength vs their resistance |
| Lying about your cargo | Cunning | Intuition | Your deception vs their read on you |
| Items hidden in wagon | Cunning | Cunning | Your hiding spots vs their search thoroughness |

---

## Design Notes

- Universal M.A.G.I.C. stats mean one system for everyone - simpler to balance and implement in GAS
- Traits create personality without needing more stats
- Occupation determines *what* checks happen, stats determine *how well*
- Rank is the easy scaling lever - same guard types at different checkpoints just have different ranks
- Example guards show the range from pushover to nightmare
