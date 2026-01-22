# Checkpoint Encounters

This document defines how checkpoint encounters play out—the structure, flow, and player options when you're stopped and inspected.

For the underlying check mechanics, see [[Checks & Contests]].
For guard stats and types, see [[Guards]].

---

## Encounter Model: Dialogue with Interrupts

Checkpoint encounters use a **dialogue-based system with multiple participants**.

### Core Structure

- **Lead Guard** — Your primary interaction point. Dialogue choices, main checks, negotiation.
- **Supporting Guards** — Generate **interrupts**: observations, findings, pressure that you must triage.
- **Interrupt Queue** — Secondary observations appear over time; you can address them or let them escalate.
- **Suspicion Meter** — Rises and falls based on checks and observations; determines encounter outcome.

### Why This Model

- Focused camera/UI (lead guard is anchor)
- Environmental tension without chaotic real-time action
- Multiple participants handled through dialogue UI, not 3D camera choreography
- Triaging interrupts creates decision-making under pressure
- Scalable complexity (more guards = more interrupts, not fundamentally different system)

---

## Encounter Flow

```
Approach Checkpoint
        │
        ▼
┌─────────────────┐
│ ENCOUNTER START │ ← Starting suspicion based on Heat, guard traits, events
└────────┬────────┘
         │
         ▼
┌─────────────────────────────────────────────────┐
│                CHECKPOINT ENCOUNTER              │
│                                                  │
│  Lead Guard presents checks based on occupation  │
│  Supporting guards generate interrupts           │
│  Player responds: dialogue, spells, bribes, etc. │
│  Suspicion rises/falls based on outcomes         │
│                                                  │
└────────┬────────────────────────────────────────┘
         │
         ▼
    Exit Condition
    ┌─────┴─────┐
    │           │
 PASS        CAUGHT
(or other outcomes)
```

---

## Suspicion Meter

Suspicion is an **encounter-level** resource that tracks how the interaction is going.

### Suspicion Levels

| Level | State | What's Happening |
|-------|-------|------------------|
| 0 | Clean | Waved through, minimal inspection |
| 1-3 | Low | Routine inspection, standard checks |
| 4-6 | Medium | Thorough inspection, more checks, guards paying attention |
| 7-9 | High | They're convinced something's wrong, backup called, very hard to recover |
| 10 | Caught | Contraband found, arrest, strike |

### What Raises Suspicion

| Event | Suspicion Change |
|-------|------------------|
| Failed check | +1 to +3 depending on severity |
| Unaddressed interrupt escalates | +1 to +2 |
| Suspicious cargo (even legal) | +1 at encounter start |
| Guard trait: High Strung | +1 at encounter start |
| Your Heat in this region | +1 per Heat level at encounter start |
| Caught in a lie (failed Cunning vs Intuition badly) | +2 |
| Attempted bribe on Loyal guard | +2 |

### What Lowers Suspicion

| Event | Suspicion Change |
|-------|------------------|
| Passed check | -1 |
| Successful bribe | -1 to -3 depending on guard |
| Good documents (valid permits) | -1 |
| Guard trait: Lazy | -1 at encounter start |
| Addressed interrupt successfully | -1 |
| Convincing explanation (Moxie vs Moxie) | -1 |

---

## Heat: The Persistent Layer

**Heat** is your regional notoriety—how much attention you've attracted over time.

| Heat Level | Effect |
|------------|--------|
| 0 | No reputation, clean slate |
| 1-2 | Minor attention; +1 starting suspicion |
| 3-4 | Known quantity; +2 starting suspicion, better guards assigned |
| 5+ | Actively hunted; +3 starting suspicion, Mage Breakers deployed, Enclave is aware |

### Heat Sources

- Barely escaping a checkpoint (high suspicion but got through)
- Violence (massive Heat spike—see below)
- Failed smuggling runs (getting caught)
- Witness reports ("someone matching your description...")
- Enclave assignments gone wrong

### Heat Decay

- Slow decay over time (days/weeks)
- Laying low (not running checkpoints) helps
- Some contacts might offer Heat reduction services
- Heat is **regional**—you might be hot in Ashford but unknown in Snowmarch

---

## The Interrupt Queue

Supporting guards generate **interrupts**—observations that demand attention.

### How Interrupts Work

1. Interrupt appears in UI ("Guard 2: There's residue on these crates...")
2. Interrupt has an **escalation timer** or **threshold**
3. If unaddressed, interrupt either:
   - **Fades** — Guard shrugs it off, no effect
   - **Escalates** — Becomes a formal check, or automatically raises suspicion
4. Player can spend an action to **address** the interrupt (explain, cast spell, etc.)
5. Addressing an interrupt triggers a check—pass and it's resolved, fail and it escalates anyway

### Interrupt Severity

| Severity | Examples | If Ignored |
|----------|----------|------------|
| Minor | "Wagon's riding low" / "You seem nervous" | Usually fades |
| Moderate | "This manifest doesn't match" / "What's this residue?" | Likely escalates to check |
| Severe | "I'm detecting magical concealment" / "Open that compartment" | Will escalate, high suspicion if failed |

### Intuition and Interrupts

High **Intuition** helps you:
- See which interrupts are about to escalate (vs. which will fade)
- Preview what check an interrupt will trigger if it escalates
- Prioritize what to address

---

## Player Options During Encounter

### Dialogue Choices

The core interaction with the lead guard. Options depend on context:

- **Answer questions** — Truthfully or lying (Cunning vs Intuition)
- **Show documents** — Present permits, manifests, forgeries
- **Deflect** — Change subject, stall, buy time
- **Stay silent** — Sometimes safe, sometimes suspicious

### Pre-empt Actions

Available **before** a check resolves (requires pre-empt window, often from high Intuition or abilities):

- **Quick-cast spell** — Boost a stat, enhance concealment, affect the guard
- **Present document proactively** — "Here's my permit for that" before they ask
- **Warn the lead guard** — "Your man back there is mistaken" (address interrupt before it escalates)

### React Actions

Available **after** a check fails (requires react window, often from abilities or equipment):

- **Bribe** — Offer money to make the problem go away (Moxie vs Moxie, modified by Greedy/Loyal)
- **Talk your way out** — Moxie vs Moxie to reframe, explain, recover
- **Quick-cast** — Emergency spell to cover the failure
- **Produce document** — "Wait, I have a permit for that" (if you actually do)
- **Abandon cargo** — Let them confiscate something to protect the rest

### Desperate Actions

Available when things are going very badly:

- **Abandon cargo** — Sacrifice goods to reduce suspicion and escape
- **Flee** — Attempt to run (triggers pursuit, raises Heat significantly)
- **Violence** — The nuclear option (see below)

---

## Exit Conditions

### Satisfied (Pass)

Suspicion is low enough after all checks complete. Guard waves you through.
- No consequences
- Proceed to destination

### Bribed/Convinced (Pass)

You paid them off or talked your way through despite suspicion.
- Cost: gold (bribe) or nothing (pure Moxie)
- May still raise Heat slightly if suspicion was high

### Caught (Fail)

Suspicion hit 10, or contraband was found and you couldn't recover.
- Arrest
- Strike from Enclave (see [[Gameplay Overview#Failure & Consequences]])
- Contraband confiscated
- Possible fine or prison time (Enclave bails you out)

### Fled (Partial Fail)

You ran before getting caught.
- Keep your contraband (if they didn't find it yet)
- Significant Heat increase
- Pursuit encounter may trigger
- Can't use this checkpoint for a while

### Violence (Catastrophic)

You used lethal magic to escape.
- You survive (probably)
- Massive consequences (see below)

---

## Violence: The Nuclear Option

You're a wizard. You have combat magic. At any point during a checkpoint encounter, you can choose violence.

**This is always available. It is never advisable.**

### Immediate Effects

- Guards die (you're powerful enough to kill checkpoint guards)
- You escape with your cargo
- Encounter ends

### Consequences

| Category | Effect |
|----------|--------|
| **Physical** | Permanent stat penalties. Possibly lost limbs (equipment slots disabled). Visible scarring. Using forbidden magic damages you. |
| **Heat** | Maximum Heat in the region. Possibly all regions. You're now a cop-killer. |
| **Enclave** | They do not protect murderers. This may count as a strike—or they may cut you loose entirely. Your debt doesn't disappear; your protection does. |
| **Psychological** | Your character is shaken. Temporary debuffs. Dialogue changes. NPCs react differently to you. |
| **Witnesses** | Anyone who saw you is a problem. Do you hunt them down? Let them spread word? |
| **Kingdom Response** | Detectives, Mage Breakers, military resources. You're not facing checkpoint guards anymore. |

### Design Intent

Violence is the desperate "I have nothing left to lose" option. It's there so the player always has agency—you're never truly trapped. But choosing it should feel like a tragedy, not a strategy.

The fantasy: everything has gone wrong, you're about to get your third strike, and you think... "I could just kill them all."

The game says: "Yes, you can. Here's what it costs."

---

## Example Encounter

> **Ashford Checkpoint — Corporal Vance (Inspector), 2 supporting guards**
> 
> Starting suspicion: 2 (your Heat is 1, normal checkpoint)
> 
> **Phase 1: Documents**
> Vance: "Papers. What's your business in Ashford?"
> - You show valid merchant permit → Suspicion -1 (now 1)
> - You lie about destination (Cunning 6 vs his Intuition 5) → 60% chance
>   - Pass: Suspicion unchanged
>   - Fail: Suspicion +1
> 
> **Interrupt appears:** Guard 2: "This crate's heavier than the manifest says."
> - Minor severity, will escalate in 2 phases if unaddressed
> 
> **Phase 2: Cargo Inspection**
> Vance: "Mind if we take a look?"
> - Cargo check: Your Arcana (concealment) vs his Arcana (detection)
> - Your Arcana 7 (5 base + 2 from Obscurement spell) vs his Arcana 4
> - +3 difference = 80% success chance
>   - Pass: "Everything looks in order." Suspicion -1
>   - Fail: "What's this?" Suspicion +2, react window opens
> 
> **Interrupt escalates:** Guard 2's observation becomes a formal check
> - Weight discrepancy check: Cunning vs Cunning
> - Fail: They find the hidden compartment
> 
> **Phase 3: Resolution**
> - If suspicion ≤ 3: "Move along." You pass.
> - If suspicion 4-6: More questions, another check or two
> - If suspicion 7+: They're calling for backup, things are bad
> - If they found contraband: React window—bribe, talk, or worse

---

## Related Systems

- [[Checks & Contests]] — The underlying check mechanics
- [[Guards]] — NPC stats, occupations, traits
- [[Wagon]] — Your cargo and concealment
- [[How Magic Works]] — Spells you can cast during encounters
- [[Calendar]] — Events that modify checkpoint difficulty
- [[Contraband]] — What you're hiding
- [[Documents]] — Permits, forgeries, papers
