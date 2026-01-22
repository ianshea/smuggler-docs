# Inventory

Inventory in Magic Smuggler operates on two tiers: **personal items** you carry and use, and **bundles** you smuggle as cargo. These are distinct systems with different rules.

---

## Two-Tier System

| Tier | What It Is | Where It Lives | How You Interact |
|------|------------|----------------|------------------|
| **Personal Items** | Individual objects for your use | Personal inventory (on your person) | Carry, equip, consume from quick slots |
| **Bundles** | Packaged cargo for smuggling | Wagon compartments | Magically lift and load |

You don't smuggle loose items — you smuggle bundles. You don't consume bundles — you deliver them.

---

## Personal Items

Things you carry on your person for use during runs.

### Examples
- **Consumables** — Potions you drink, scrolls you cast, food
- **Tools** — Lockpicks, detection devices, forgery kits
- **Documents** — Permits, papers, forgeries you present at checkpoints
- **Equipment** — Worn items (hat, robe, belt, staff, accessories)
- **Your Personal Crystal** — Mana source for spellcasting

### Capacity

Personal inventory is limited by equipment:
- **Belt** determines quick slot count (consumables accessible mid-encounter)
- Other capacity limits TBD (likely slot-based, small numbers)

### Key Rule

**Personal inventory cannot hold contraband bundles.** You can't stuff a crate of illegal potions in your pocket and walk through a checkpoint. Contraband goes in the wagon.

You *can* carry personal consumables that might be suspicious (a potion of invisibility, a questionable scroll), but these are individual items subject to different rules than bulk cargo.

---

## Bundles

Packaged cargo units for smuggling. This is what you're hauling through checkpoints.

### How Bundles Work

- **Crafting produces bundles automatically** — A batch of potions becomes a "crate of potions"
- **1 bundle = 1 wagon slot** (standard size)
- **Bundles stay sealed** — You don't break them open or access contents mid-run
- **Bundles have value** — What you get paid on delivery
- **Bundles have contraband level** — Determines risk if found (see [[Contraband]])

### Bundle Examples

| Bundle | Contents | Contraband Level |
|--------|----------|------------------|
| Crate of Health Potions | 12 potions | Level 2 (Restricted) |
| Case of Spell Scrolls | 6 scrolls | Level 3 (Prohibited) |
| Fuzzy Leaf Bale | Processed leaf | Level 2 without permit, Level 0 with |
| Necromantic Components | Bone dust, distillate | Level 5 (Capital Offense) |

### Large Items (Act II+)

Standard bundles are 1 slot. In later acts, you may encounter **large items** that take 2+ slots:

- Higher lift cost (more mana to move)
- May not fit smaller compartments
- Harder to obscure (size penalty)
- Draw guard attention

Large items create different risk/reward calculations. Usually tied to special quests or high-value opportunities.

---

## Loading the Wagon

Loading cargo isn't free — you're a wizard, and moving things costs mana.

### The Loading Process

```
Bundle exists at crafting station (or acquired from vendor)
        ↓
Cast telekinesis to lift bundle (flat mana cost)
        ↓
Carry to wagon (mana drains while holding)
        ↓
Place in chosen compartment
        ↓
Repeat for additional bundles
        ↓
Cast obscurement on compartments with contraband (mana cost per spell)
        ↓
Depart with remaining mana
```

### Mana Costs

| Action | Mana Cost |
|--------|----------|
| Lift bundle | 5 mana (flat) |
| Holding bundle | 0.5 mana/sec (drain while carrying) |
| Obscurement spell | 15 mana (per compartment, see [[Spells]]) |

See [[Mana Economy]] for full budget planning.

### Why This Matters

Every bundle you load costs mana. Every obscurement spell costs mana. The more cargo you haul, the less mana you have for:
- Emergency spells on the road
- Refreshing obscurement if it's about to expire
- Dealing with unexpected checkpoint complications

**Preparation has a cost.** A fully-loaded wagon with every compartment obscured might leave you dangerously low on mana before you even depart.

### Efficiency

Since you carry **one bundle at a time**, tower layout can matter:
- Stations closer to wagon = less drain while carrying
- Efficient pathing = more mana preserved

(Tower layout details TBD — see [[Unsorted_Ideas]] for current thinking)

---

## Summary

| Aspect | Personal Items | Bundles |
|--------|----------------|---------|
| Purpose | Use during runs | Deliver for profit |
| Location | Personal inventory | Wagon compartments |
| Interaction | Carry, equip, consume | Magically lift and load |
| Size | Individual | 1 slot (standard) or 2+ (large) |
| Contraband? | Usually no (some exceptions) | Yes — this is what you're smuggling |
| Mana cost? | No (already on your person) | Yes (lifting and carrying) |

---

## Related Systems

- [[Wagon]] - Compartments and cargo management
- [[Player Character]] - Personal inventory slots and equipment
- [[Contraband]] - Risk levels for illegal goods
- [[How Magic Works]] - Mana economy and spellcasting
- [[Crafting]] - How bundles are produced
