# Wagon

Your wagon is your mobile operations center—transport, cargo storage, and enchantable platform for smuggling magic.

---

## Two-Crystal System

The wagon runs on a dedicated **Wagon Crystal** that powers locomotion only. This is separate from your **Personal Crystal**, which powers your spells.

| Crystal | Location | Powers | Recharge |
|---------|----------|--------|----------|
| Wagon Crystal | Mounted in wagon | Movement only | Tower (full efficiency) |
| Personal Crystal | Carried by wizard | All spellcasting, including smuggling enchantments | Tower only |

**Emergency Transfer:** If the wagon crystal runs dry in the field, you can transfer mana from your personal crystal to the wagon at a poor ratio. This gets you moving but depletes your spellcasting reserves—a desperation move, not a strategy.

The wagon crystal is essentially a specialized battery. Not everyone is a smuggler; most wagon owners just use theirs for transport. What makes yours special is what you do with magic on top of it.

---

## Cargo & Compartments

The wagon has compartments for storing cargo. These compartments are **enchantable**—you cast obscurement spells on them to hide contraband from checkpoint detection.

### Key Distinctions

- **Compartments are physical storage** - They hold bundles of goods, legal or otherwise
- **Obscurement is magical** - You cast spells to make compartment contents harder to detect
- **You power the magic** - Enchantments on compartments run off your personal crystal, not the wagon's
- **Spells have duration** - Obscurement isn't permanent; it's a countdown that can run out at bad times

This means smuggling isn't about mechanical hidden panels—it's about your wizard abilities. Detection at checkpoints is magical, and you're countering with magical concealment.

### Bundles, Not Loose Items

You don't smuggle individual potions — you smuggle **bundles** (crates, cases, wrapped packages). Bundles are the cargo unit that occupies wagon slots.

- Crafting automatically produces bundles (a batch of potions becomes a "crate of potions")
- 1 bundle = 1 slot (standard size)
- Bundles stay sealed until delivered — you don't break them open mid-run
- Personal consumables (potions you drink, scrolls you use) are separate from cargo bundles

See [[Inventory]] for full details on the item/bundle distinction and how loading works.

### Cargo Separation

Wagon cargo is separate from personal inventory:

- **Personal inventory** - Tools, consumables, your crystal, documents you're carrying
- **Wagon cargo** - Bulk goods, contraband, trade items

You can't hide contraband on your person and walk through a checkpoint. The wagon is where the goods go, and the wagon is what gets searched.

---

## Compartment System (DECIDED)

Cargo management uses a **compartment-based** model: the wagon has distinct compartments, each with slot/capacity limits. You choose *which compartment* holds what, but don't arrange items spatially within.

### Why This Model

- **Strategic, not mechanical.** The interesting decision is "what goes where and how do I conceal it?" not "how do I tetris these crates."
- **Fits checkpoint design.** Guards search compartments. Obscurement targets compartments. Stakes are clear: "open the rear storage" means you know exactly what's at risk.
- **Compartment specialization.** Different compartments have different properties—capacity, obscurement bonuses, storage requirements. Meaningful choice without spatial puzzles.
- **Scales with progression.** Upgrades add compartments, improve compartments, or unlock specialized storage. Clean upgrade path.

### Compartment Properties

Each compartment has:

| Property | Description |
|----------|-------------|
| **Capacity** | How many slots it holds (discrete units, no weight math) |
| **Visibility** | How obvious it is to guards (hidden floor vs open bed) |
| **Obscurement Bonus** | Base modifier when you cast concealment on this compartment |
| **Storage Type** | What it can hold — general only in Act I; specialized types (cold, reinforced, hazardous) introduced in Act II |
| **Search Priority** | How likely guards are to check this compartment first |

### Progression by Act

| Act | Compartments | What's New |
|-----|--------------|------------|
| **Act I** | 2 → 3 | Core system only. Learn loading, obscurement, checkpoint rhythm. All compartments are general storage. |
| **Act II** | 4 | Specialized storage introduced. Certain goods require specific compartment types (cold, reinforced, hazardous). |
| **Act III** | 5 → 6 | Final compartment mechanic (TBD). Full system mastery. |

This structure follows "introduce, complicate, master" — each act adds depth, not just capacity.

### Starting Wagon (Act I)

A basic wagon has 2 compartments:

| Compartment | Capacity | Visibility | Obscurement Bonus | Storage Type | Search Priority |
|-------------|----------|------------|-------------------|--------------|----------------|
| **Main Bed** | 6 slots | High | +0 | General | 1 (searched first) |
| **Underseat Storage** | 2 slots | Medium | +1 | General | 3 (searched later) |

**Total starting capacity: 8 slots**

### Act I Upgrade: Third Compartment

Mid-Act I, player can add:

| Compartment | Capacity | Visibility | Obscurement Bonus | Storage Type | Search Priority |
|-------------|----------|------------|-------------------|--------------|----------------|
| **Hidden Floor Compartment** | 3 slots | Low | +2 | General | 5 (rarely searched) |

**Total Act I capacity: 11 slots**

### Example Upgraded Wagon (Act II+)

After progression, with specialized storage (4 compartments at start of Act II, 5-6 by Act III):

| Compartment | Capacity | Visibility | Obscurement Bonus | Storage Type | Search Priority |
|-------------|----------|------------|-------------------|--------------|----------------|
| **Main Bed** | 8 slots | High | +0 | General | 1 |
| **Underseat Storage** | 2 slots | Medium | +1 | General | 3 |
| **Hidden Floor Compartment** | 4 slots | Low | +2 | General | 5 |
| **Reinforced Lockbox** | 2 slots | Medium | +0 | Fragile/Volatile | 2 |
| **Cold Storage** | 2 slots | High | +0 | Perishable | 4 |

**Example Act II capacity: 18 slots** (but now constrained by storage types)

### Gameplay Flow

1. **At Tower:** Load cargo into compartments. Cast obscurement spells on compartments holding contraband. Note spell durations.
2. **Travel:** Spells tick down. Distance consumes wagon crystal mana.
3. **At Checkpoint:** Guards may search specific compartments. Your obscurement contests their detection. Compartment properties modify the contest.
4. **Decisions:** Do you spread contraband across compartments (harder to lose everything, more spells to maintain)? Concentrate it in your best-hidden compartment (one spell, but all eggs in one basket)? Mix legal and illegal goods as cover?

---

## Upgrades

Wagon upgrades fall into categories:

| Category | Examples | Effect |
|----------|----------|--------|
| **Capacity** | Larger bed, additional compartments | More cargo space |
| **Compartment quality** | Reinforced compartments, specialized storage | Better base for enchantments, certain goods require certain storage |
| **Crystal efficiency** | Improved wagon crystal mounting | Better mana-to-distance ratio |
| **Speed/Durability** | Wheels, axles, frame | Travel time, wear and tear |

Progression isn't just "bigger wagon"—it's improving the platform you're casting magic on.

> **TODO:** Define specific upgrades and costs.

---

## Wagon at Checkpoints

When you reach a checkpoint, the wagon is what guards inspect. The encounter becomes a contest between:

- **Their detection** - Spells, devices, trained inspection
- **Your obscurement** - Enchantments you've cast on compartments

Factors that matter:
- Quality/power of your obscurement spell
- Time remaining on the spell (did you cast it fresh, or is it about to expire?)
- Guard thoroughness (varies by checkpoint, events, bribes)
- What you're hiding (some contraband is harder to obscure than others?)

> **TODO:** Define the actual checkpoint mechanics—stat check? Interactive? See [[Checkpoints]].

---

## Related Systems

- [[How Magic Works]] - Mana, crystals, spellcasting
- [[Checkpoints]] - Where wagon inspections happen
- [[Contraband]] - What you're hiding
- [[Inventory]] - Item tiers, bundles, and loading
