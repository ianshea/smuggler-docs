# Mana Economy

The mana economy is the resource tension at the heart of every smuggling run. You have a finite pool; every action costs something; running out means vulnerability.

---

## The Core Loop

```
Tower (full mana)
    ↓
Load cargo (costs mana to lift/carry)
    ↓
Cast obscurement (costs mana, starts duration timer)
    ↓
Travel outbound (wagon crystal, separate pool)
    ↓
Checkpoint (may spend mana on spells)
    ↓
Deliver cargo, receive payment (wealth = items)
    ↓
Travel return (wagon crystal)
    ↓
Checkpoint (may spend mana; now carrying wealth)
    ↓
Tower (recharge, unload wealth)
```

**Key insight:** Risk exists in both directions. Outbound you're hiding contraband. Return you're hiding wealth. Mana fuels your ability to handle both.

---

## Resource Pools

### Personal Crystal (in Staff)

Your spellcasting reserve. Housed in your equipped staff.

| Stat | Act I Starting | Notes |
|------|----------------|-------|
| **Capacity** | 100 mana | Upgrades via better staff |
| **Recharge** | Tower only | Cannot recharge mid-run |
| **Multiple crystals?** | No | One staff, one crystal |

### Wagon Crystal

Powers wagon movement. Separate from personal pool.

| Stat | Act I Starting | Notes |
|------|----------------|-------|
| **Capacity** | 50 charges | Upgrades available |
| **Travel cost** | ~10-15 per leg | Round trip = 20-30 |
| **Recharge** | Tower only | Same as personal |

### Emergency Transfer

If wagon crystal runs dry mid-field, you can drain personal mana into it.

| Ratio | Effect |
|-------|--------|
| **3:1** | 3 personal mana → 1 wagon charge |

This is a desperation move. It gets you moving but guts your spellcasting reserve.

---

## Mana Costs

### Loading (At Tower)

| Action | Cost | Notes |
|--------|------|-------|
| **Lift bundle** | 5 mana | Flat per bundle |
| **Carry bundle** | 0.5 mana/sec | Drain while holding |

Efficient tower layout = less carry time = more mana preserved.

### Spells

| Category | Cost Range | Examples |
|----------|------------|----------|
| **Utility** | 5-10 mana | Light, minor detection, small tricks |
| **Obscurement** | 15 mana | Per compartment, ~8-10 min duration |
| **Moderate** | 20-30 mana | Charm, enhanced concealment |
| **Emergency** | 25-40 mana | Combat, escape, major intervention |

### Obscurement Duration

Obscurement spells are **real-time countdowns**, not permanent.

| Spell Tier | Duration | Notes |
|------------|----------|-------|
| **Basic Obscurement** | ~8-10 minutes | Act I standard |
| **Enhanced (later)** | Longer | Upgrades/better spells |

**Why real-time?** Creates genuine tension. If you're stuck in a checkpoint line, your spell is ticking down. Do you recast (costs mana) or gamble it holds?

---

## Budget Example: Tight But Successful Run

Starting: **100 mana**

**LOADING**
- Lift bundle 1: -5 (95)
- Carry 5 sec: -2.5 (92.5)
- Lift bundle 2: -5 (87.5)
- Carry 5 sec: -2.5 (85)
- Obscurement on Underseat: -15 (70)

**CHECKPOINT (OUTBOUND)**
- Utility spell: -10 (60)

**DELIVERY**
- No cost
- Receive payment: gems + gold (now in wagon)

**CHECKPOINT (RETURN)**
- Greedy guard eyes your wealth
- Charm spell: -15 (45)

**ARRIVE TOWER**
- 45 mana remaining ✓
- Comfortable buffer

---

## Budget Example: Things Go Wrong

Starting: **100 mana**

**LOADING** (same as above)
- After loading + obscurement: 70 mana

**CHECKPOINT (OUTBOUND)**
- Guard suspicious, obscurement about to fail
- Recast obscurement: -15 (55)
- Utility charm: -10 (45)
- Guard persists, emergency spell: -30 (15)

**DELIVERY**
- Made it, but burned
- 15 mana remaining

**CHECKPOINT (RETURN)**
- Greedy guard, you're carrying gold
- Can't afford another big spell
- Bribe with gold instead? Or risk it?

**ARRIVE TOWER**
- Sweating, but alive
- Lesson learned

---

## Strategic Implications

### Preparation vs Field Reserves

Every bundle you load costs mana. Every obscurement spell costs mana. Heavy preparation = less buffer for surprises.

**Trade-off:** Do you load light and keep reserves? Or load heavy and hope nothing goes wrong?

### Obscurement Timing

Cast too early → might expire during checkpoint
Cast too late → scrambling at the last minute

Experienced players learn to time casts based on travel distance and expected checkpoint wait.

### Return Trip Matters

You're not safe after delivery. Wealth is also cargo. Greedy guards exist. Plan mana for both directions.

### Staff Upgrades = Strategic Flexibility

More mana capacity means more margin for error. Staff upgrades are high-priority progression.

---

## Related Systems

- [[Mana Crystals]] - Crystal mechanics and staff housing
- [[How Magic Works]] - Full magic system
- [[Inventory]] - Bundle lifting costs
- [[Wagon]] - Compartments and obscurement
- [[Wealth]] - Return trip risk
- [[Checkpoints]] - Where mana gets spent
