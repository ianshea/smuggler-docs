# Unsorted Ideas & TODO

**Last Updated:** Initial dump from design session

This file captures ideas, decisions, and details discussed but not yet fully documented or organized into the main docs.

---

## How to Use This Document

This is a backlog of design decisions that need to reach "decided" status. Not everything needs answering immediately - but everything here needs an answer before building that specific system.

**Priority items to resolve:**
- Mana Economy - the resource loop that drives tension
- Debt Numbers - the actual goal posts for the player
- Inventory/Wagon Design - how cargo management actually works (stub exists at [[Wagon]], details below)

**Recently decided (documented elsewhere):**
- Failure States → [[Overview#Failure & Consequences]], [[Smuggling#Success & Failure]]
- Checkpoint mechanics → [[Guards]], [[Smuggling]]
- Contraband levels → [[Contraband]]

---

## Spellbook as Consigliere (IDEA - NOT DECIDED)

The player's spellbook could have personality - acting as an advisor, companion, or sarcastic commentator. Think of it as a consigliere that:
- Gives advice (helpful or questionable)
- Manages your spell loadout
- Provides flavor/narrative commentary
- Maybe has its own agenda?

This could add character to what would otherwise be a menu screen. Fits the Guy Ritchie tone - a mouthy magical book that's seen some shit.

---

## Inventory & Wagon Design (UNRESOLVED)

Early thinking referenced Astroneer/Death Stranding style visual inventory - physical representation of cargo, tetris-like packing puzzles.

Current direction leans toward "the wagon" being the primary cargo container, but specifics are muddy:

**Open questions:**
- Is inventory management a puzzle (spatial packing) or just capacity limits (weight/slots)?
- How does the wagon interact with checkpoints? (Guards search it, hidden compartments, etc.)
- What's the relationship between personal inventory (player) and wagon inventory?
- Does the player physically load/unload, or is it abstracted?

**Previous ideas that may or may not apply:**
- Containers hold Packages hold Items (nesting structure)
- Backpacks equipped to provide personal inventory
- Pouches/Belts for quick-use items
- Visual representation of cargo

This needs actual design work before building.

---

## Regional Beverages & Substances

### Concept
Each location has cultural preferences for specific beverages/drugs that create natural smuggling opportunities:
- Legal in origin city, illegal/restricted elsewhere  
- Requires transport permits for legal movement
- Based on culture/geography/history, NOT race stereotypes
- Creates permit vs smuggling economic decisions

### Specific Items Discussed

**Fuzzy Leaf** (Capital/Kingsmoor production)
- Popular smoking substance (tobacco/cannabis analog)
- Legal to grow ONLY in capital region (controlled crop)
- Requires permits to transport to other regions
- High demand across kingdom
- Potential mechanics:
  - Consumable item with buffs/debuffs for player
  - Economic cargo (high value, moderate contraband without permit)
  - Could smuggle seeds? (very illegal to grow outside capital)
  - Different forms: dried leaf, processed products, seeds

**Goose** (Ashford Crossing desert moonshine)
- Local swill/moonshine from border town
- Terrible for drinking
- Valuable as alchemical reagent/solvent in certain circles
- Cheap in Ashford, expensive to alchemists elsewhere
- Player uses it as crafting ingredient (acquires, doesn't craft it)
- Questions:
  - What recipes use Goose specifically?
  - Cheap solvent for low-grade potions?
  - Dangerous reagent for unstable but powerful products?
  - Specialized use (poison base? corrosive?)?

**Snowmarch Alpine Beverages**
- High-end wines (premium vintages)
- Luxury cheeses (could have alcoholic varieties? cheese + wine culture)
- Status symbols, expensive
- Desired in other regions as luxury imports

**Riverton River Products**
- Beers (breweries along river)
- Questions:
  - Specific beer styles tied to river trade culture?
  - Different quality tiers?
  - Export specialties?

### Mushrooms (Riverton)
- Nutritional varieties (legal, food)
- "Fun" psychoactive varieties (restricted/illegal)
- Ghost Caps already in item list - from battlefields or Riverton forests?
- Potential for tiered contraband (food vs drugs)
- Questions:
  - Are "fun mushrooms" just recreational drugs or magical properties?
  - Do they have gameplay buffs/debuffs if consumed?
  - Different preparation methods affect legality?

### Other Regional Specialties Not Yet Defined
- Thornhaven (Enclave city) - what do they produce/prefer?
- Capital city culture beyond fuzzy leaf?
- Are there imported goods from outside the kingdom?

### Consumables & Player Use
- Beverages/substances should have player consumable mechanics
- Small buffs/debuffs depending on item
- Examples:
  - Fuzzy Leaf: relaxation buff, slight perception debuff?
  - Goose: temporary stamina boost, taste debuff?
  - Premium wine: charisma/persuasion buff in social contexts?
  - Fun mushrooms: perception changes, risk/reward?

---

## Vendor Details (Needs Documentation)

### Hidden Stock Mechanic
Vendors have two inventories:
- **Public/Front** - Anyone can shop, legal or mundane goods
- **Hidden Stock** - Requires faction reputation to unlock

Reputation unlocks through:
- Completing faction quests
- Building relationships via trades
- Story progression
- Specific unlock conditions per vendor

### Faction Progression Examples

**Independent Smugglers (Riverton)**
- Level 1: Riverside General hidden stock access
- Level 3: Three Crowns broker sells checkpoint intel
- Level 5: Warehouse space for storing goods between runs

**Rebels (Ashford + Riverton)**  
- Level 1: Rebel quartermaster hidden stock
- Level 3: Mercer's Metalworks back room access
- Level 5: Rebels tip you off about Enclave shipments to intercept

**Enclave (Thornhaven)**
- Level 1: Supply office hidden stock (debt-based)
- Level 3: Access confiscation warehouse  
- Level 5: Can "borrow" master formulas from Archive

### Individual Vendor Inventories (Need to Detail)

Each vendor needs:
- Public inventory list (what anyone can buy)
- Hidden inventory list (what unlocks at each faction level)
- Pricing structure (markup, regional differences)
- Restock mechanics (daily? weekly? quest-triggered?)
- Special services beyond selling (information, storage, introductions)

*See [[Locations]] for the current vendor list per location.*

---

## Item Properties for Craft/Unreal

### Fields Needed (Not Yet Defined)

**Basic Info:**
- Name
- Description (flavor text, lore)
- Icon/Visual representation

**Categorization:**
- Item Category (Arcane, Botanical, Mineral, Animal, Processed, Misc)
- Subcategories? (legal vs illegal botanical, etc.)

**GameplayTags:**
- Tag structure hierarchy
- How many tags per item?
- Required vs optional tags
- Export format to Unreal

**Physical Properties:**
- Weight (cargo capacity implications)
- Size/Volume (concealment mechanics)
- Stackable? Max stack size?

**Economic Properties:**
- Base value (gold cost)
- Regional price modifiers
- Vendor markup percentages
- Black market vs legal market pricing

**Contraband Properties:**
- Contraband level (0-6, see [[Contraband]])
- Detection methods (Physical.Suspicious, Magic.Aura, etc.)
- Concealment difficulty
- Penalty if caught

**Consumable Properties (if applicable):**
- Can player use/consume this?
- Buff/debuff effects
- Duration
- Cooldowns?

**Crafting Properties:**
- Is this a crafting ingredient?
- Is this a crafted product?
- Which stations can use/produce it?

**Relations in Craft:**
- How to link items to formulas (ingredients)
- How to link items to vendors (inventory)
- How to link items to locations (regional goods)

### Tag Structure to Formalize

Current thinking:
```
Item.Type.* (Material, Product, Equipment, Consumable)
Item.Contraband.* (Legal, Level.1-5)
Item.System.* (Crafting.Input, Crafting.Output, Spell.Component, Quest)
Detection.* (Physical.Suspicious, Magic.Aura, etc.)
Faction.* (Kingdom.Banned, Rebels.Valued, Enclave.Property)
```

Need to finalize:
- Complete tag hierarchy
- Required vs optional tags
- How to structure in CraftCMS (Categories vs native tags)
- Export mapping to Unreal GameplayTags

---

## Formula/Recipe Expansion

### Current Formulas Documented
- Health Potion (Basic)
- Health Potion (Premium)
- Speed Elixir
- Levitation Draught

### Additional Potion Types to Design

**Utility Potions:**
- Invisibility/Stealth enhancement
- Night vision
- Water breathing
- Strength/carrying capacity
- Luck/fortune (affects checkpoint rolls?)

**Magical Effects:**
- Mana restoration (for refilling crystals?)
- Spell power enhancement
- Magic resistance
- Dispel/counterspell potions

**Social/Interaction:**
- Persuasion/charisma boost
- Truth serum (interrogation)
- Memory enhancement/suppression
- Language comprehension

**Dangerous/Illegal:**
- Poisons (for tools, not murder)
- Hallucinogens (extreme contraband)
- Berserker rage
- Necromantic effects

**Economic/Practical:**
- Preservation potions (extend ingredient shelf life?)
- Cleaning/restoration (remove traces of magic?)
- Lock-breaking acids
- Forgery aids (fake documents, signatures)

### Spell Formulas
Similar structure to crafting, but:
- Loaded into spellbook instead of crafting station
- Consume mana (from wagon crystal) instead of physical ingredients
- Some may require components (expensive spells need catalysts?)

**Spell types needed:**
- Illusion (concealment, disguise)
- Utility (light, unlock, detect)
- Defense (shield, ward, protection from detection)
- Emergency (escape, teleport short distance, confusion)

**Spell complexity tiers:**
- Novice/Journeyman (player can learn)
- Master/Archmage (cargo only, too advanced)

### Formula Properties
- Name, description
- Type (Crafting/Spell/Enchanting)
- Inputs (ingredients, quantities)
- Outputs (products, quantities)
- Station required
- Contraband level of output
- Learnable by player? (yes/cargo only)
- Difficulty tier (affects unlock/availability)

---

## Crafting Stations Beyond Potion Distiller

### Already Mentioned
- **Potion Distiller** - Alchemical potions/elixirs
- **Spell Management Station** - Learn/prepare spells

### Potential Additional Stations

**Enchanting Table**
- Imbue items with magical properties
- Enchant equipment (player gear)
- Create magical artifacts
- Formulas: base item + magical components → enchanted version

**Smuggler's Workshop**
- Create concealment devices (false bottoms, hidden compartments)
- Forge documents/permits
- Craft tools (lockpicks, scanners)
- Modify wagon (upgrades, improvements)

**Transmutation Circle**
- Transform materials (lead to gold, mundane to magical)
- Refine raw ingredients into pure forms
- High-level/expensive operations
- Limited uses per cycle? (prevent abuse)

**Herbalist Garden** (Maybe?)
- Conflicts with "no gathering" principle
- But: could be maintaining imported plants?
- Or: processing raw botanicals into usable forms?
- Needs careful thought to avoid survival crafting feel

### Station Upgrades
- Expand recipe capacity (more formulas loaded at once)
- Improve efficiency (reduce ingredient costs, faster production)
- Unlock higher-tier recipes
- Add secondary functions (bulk crafting, quality improvements)

### Station Acquisition
- Start with basic Potion Distiller
- Purchase additional stations (expensive, debt increase)
- Or unlock through story progression
- Or steal/salvage from raids/quests

---

## Mana Economy Details

### Mana Crystal Mechanics

**Production:**
- Created at Tower using your daily mana pool
- Limited by personal mana capacity (forces rest/return cycle)
- Enclave owns tower = they "own" your mana supply
- Cost to create? (time, gold, other ingredients?)

**Usage:**
- Powers wagon (fuel for travel)
- Powers spells (consumed when casting)
- Finite charges per crystal

**Pressure Points:**
- Production vs field work tradeoff
- Spell casting depletes fuel to get home
- Running out mid-route = stranded/desperate choices

**Questions to Resolve:**
- How many charges per crystal?
- Travel cost per distance unit?
- Spell costs (cheap utility vs expensive combat)?
- Can you carry multiple crystals?
- Can you recharge depleted crystals or must create new?
- Black market for crystals? (buy instead of making?)

---

## Economic Systems & Balancing

### Price Dynamics (Not Yet Defined)

**Regional Price Differences:**
- Items cost more where they're rare
- Items cost less where they're produced
- Creates arbitrage opportunities
- Example: Goose cheap in Ashford, expensive to capital alchemists

**Supply & Demand:**
- Do prices fluctuate based on player actions?
- Can you crash a market by flooding it?
- Scarcity increases value
- War affects availability (salvage materials more plentiful during battles)

**Permit Costs vs Smuggling Profit:**
- Legal transport with permits = safe but lower profit margin
- Smuggling = risky but higher profit
- Need to balance risk/reward to make both viable choices
- Permit costs vary by item type, distance, destination?

### Debt Management

**Starting Debt:**
- How much do you owe the Enclave? (50,000 gold mentioned as example)
- Affects psychological weight, progression pacing

**Debt Increase:**
- Buying ingredients on credit
- Failing Enclave inspections (punishments)
- Station purchases
- Interest accrual?

**Debt Payment:**
- Enclave takes a cut of profits automatically?
- Or manual payment system (temptation to skip)?
- Minimum payments vs paying down principal?
- What happens if you default?

**Escape Fund:**
- How much wealth needed to buy freedom?
- Separate from debt payoff? (50k debt + 20k escape = 70k total?)
- Hidden wealth mechanics (what Enclave can't see)

---

## Faction Relationships

### Faction Rep Mechanics (Not Detailed)

**How Reputation Increases:**
- Completing faction-specific quests
- Trading specific goods they value
- Making choices that align with faction goals
- Information sharing (selling intel)

**How Reputation Decreases:**
- Working against faction interests
- Selling them out to rivals
- Breaking agreements/promises
- Getting caught by opposing factions

**Reputation Consequences:**
- Vendor access (hidden stock unlocks)
- Pricing (discounts at higher rep, markup at lower)
- Quest availability (some only available to trusted members)
- Safe passage (rebel checkpoints let you through if allied)
- Story branches (different endings based on faction loyalty?)

### Playing Factions Against Each Other

**Opportunities:**
- Rebels offer to help escape Enclave (for a price)
- Kingdom offers amnesty if you inform on Enclave
- Enclave offers debt forgiveness for betraying Rebels
- Double-agent gameplay (risky, high reward)

**Mutual Exclusivity:**
- Can you be allied with Rebels AND Enclave?
- Does Kingdom rep always conflict with Enclave rep?
- Independent Smugglers neutral ground?

**Betrayal Mechanics:**
- Can you switch sides mid-game?
- Consequences for burning bridges
- Point of no return decisions?

---

## Wagon & Travel Systems

### Wagon as Entity

**Persistent vs Temporary:**
- Wagon state (cargo, upgrades) persists between sessions
- Visual representation only exists during travel/encounters
- Hybrid architecture (data container + visual actor)

**Cargo Capacity:**
- Weight limit (items have weight)
- Volume limit (items have size)
- Special slots (hidden compartments require upgrades)
- Organization matters (concealment, access speed)

**Wagon Upgrades:**
- Hidden compartments (concealment capacity)
- Reinforced storage (protect fragile goods)
- Faster travel (speed vs fuel efficiency)
- Better suspension (rough terrain handling)
- Decoy cargo areas (misdirect inspections)

### Travel Mechanics

**Route Planning:**
- Multiple routes between locations (fast vs safe vs cheap)
- Checkpoint frequency varies by route
- Terrain affects fuel consumption
- Weather/time of day factors?

**Random Encounters:**
- Bandits (lose cargo or fight)
- Kingdom patrols (unplanned checkpoints)
- Broken wagon (repair costs, time delay)
- Opportunities (find caches, meet NPCs, unlock quests)

**Fuel Management:**
- Mana crystal charges deplete with distance
- Plan routes based on crystal capacity
- Emergency options if running out (call for help? abandon cargo?)

---

## Spell System Integration with GAS

### Spell Preparation

**Spellbook Capacity:**
- Limited number of prepared spells (5? 10?)
- Expanded through progression/upgrades
- Must choose loadout before leaving Tower

**Preparation Strategy:**
- Utility spells (concealment, unlock, light)
- Emergency spells (escape, confusion, shield)
- Loadout depends on anticipated challenges

**Swapping Spells:**
- Only at Tower's Spell Management Station
- Forces commitment to choices
- Wrong loadout = adapt or struggle

### Spell Casting Costs

**Mana Consumption:**
- All spells consume wagon crystal charges
- Cheap utility: 5-10 charges
- Moderate effects: 20-30 charges
- Expensive emergency: 50+ charges
- Tradeoff: casting vs fuel to get home

**Component Requirements (Maybe?):**
- Some powerful spells require consumed components
- Makes high-tier spells feel like crafting
- Example: Teleport needs rare catalyst
- Limits spam of powerful magic

### Spell Acquisition

**Formula Scrolls:**
- Physical items you find/buy/steal
- Load at Spell Management Station to learn
- Once learned, permanently in spellbook
- Preparation slots determine active spells

**Learnable vs Cargo:**
- Novice/Journeyman spells: player can learn
- Master/Archmage spells: too advanced, smuggle only
- Creates item tier for contraband trading
- High-level scrolls worth more but can't use them

---

## Items Not in Current Lists

### Tools & Equipment

**Smuggling Tools:**
- Lockpicks (bypass locks, open containers)
- Detection scanner (preview guard suspicion level?)
- Forgery kit (create fake documents)
- Concealment charms (single-use magic items)

**Personal Equipment:**
- Clothing/disguises (affect persuasion, detection)
- Bags/containers (affect carrying capacity)
- Lanterns/light sources
- Maps/compass (navigation aids)

### Quest Items

**MacGuffins:**
- Story-critical artifacts
- Unique items for specific missions
- High-value single-use goods
- Evidence (documents, letters, blackmail material)

**Keys & Access:**
- Physical keys to locations
- Access tokens for restricted areas
- Passwords/codes (data items, not physical)

### Currency & Valuables

**Gold/Money:**
- Standard currency for transactions
- Can be contraband if hidden from Enclave
- Different denominations?

**Gems/Treasure:**
- High value, low weight
- Perfect for hiding wealth
- Fungible vs unique items

**Faction Tokens:**
- Rebel scrip, Enclave credits
- Special currency for faction vendors
- Earn through faction quests

---

## Story & Quest Structure (Barely Touched)

### Main Story Arc
- Inciting incident (how you got indebted to Enclave)
- Rising action (debt accumulation, faction entanglements)
- Climax (decision point about freedom method)
- Resolution (escape, pay off, or other ending)

### Side Quests
- Vendor relationship quests (unlock hidden stock)
- Faction missions (build reputation)
- One-off smuggling contracts
- NPC personal stories

### Multiple Endings?
- Pay off debt legitimately (pure route)
- Escape with Rebel help (faction route)
- Betray everyone and run (chaos route)
- Other options?

---

## UI/UX Considerations (Not Designed)

### Inventory Management
- Wagon cargo view
- Personal inventory
- Tower storage
- Crafting station interfaces
- Vendor shopping

### Map & Travel
- Overworld navigation
- Route planning
- Checkpoint locations
- Fast travel unlocks?

### Crafting UI
- Recipe browsing
- Ingredient requirements
- Batch crafting options
- Queue management

### Faction & Reputation
- Rep tracking displays
- Quest log organization
- Vendor unlock indicators

---

## Technical Implementation Questions

### CraftCMS Structure
- Entry types needed (Items, Formulas, Locations, Vendors, Factions)
- Category groups for tags
- Matrix/table fields for complex data
- Relationships between entries
- Export format to Unreal (JSON structure)

### Unreal Data Tables
- Item data table structure
- Formula data table structure
- How to reference between tables
- Asset references (icons, models)

### Save System
- What needs to persist (wagon state, debt, faction rep, inventory)
- Session vs permanent data
- Cloud saves? Multiple save slots?

### Procedural vs Fixed
- Are checkpoint encounters scripted or procedural?
- Vendor inventory refresh mechanics
- Quest generation vs hand-crafted
- Balance between authored and systemic content

---

## Open Questions & Decisions Needed

### Gameplay
- Is there a time limit or is progression player-paced?
- How do checkpoint encounters play out mechanically? (turn-based? real-time? dialogue tree?)

### Economy
- Exact debt amount and escape fund target
- Pricing formulas for items
- Ingredient cost vs product value (profit margins)
- Inflation/deflation mechanics?

### Progression
- How do players unlock new stations?
- What gates access to new locations?
- Skill trees or flat progression?
- Respec options or permanent choices?

### Multiplayer/Social
- Single player only (assumed yes)
- Any async elements (leaderboards, shared market?)
- Or purely solo experience

### Scope Management
- Which systems are MVP (minimum viable product)?
- Which are stretch goals for later?
- What can be simplified for initial release?
- Multi-year hobby project means what scope?

---

## Ideas for Later Refinement

### Advanced Concealment
- Magical illusions on cargo
- Scent masking (for organic contraband)
- Temperature control (preserve delicate goods)
- Sound dampening (hide rattling vials)

### NPC Relationships
- Recurring characters with story arcs
- Romance options? (probably not priority)
- Rivalries with other smugglers
- Mentor figures, betrayals, alliances

### Dynamic World Events
- War intensity fluctuates (affects salvage availability)
- Kingdom crackdowns (increased checkpoints)
- Rebel uprisings (chaos opportunities)
- Seasonal effects (winter travel harder)

### Meta Progression
- New Game+ with carried-over knowledge
- Unlockable starting scenarios
- Challenge modes (higher debt, fewer resources)
- Achievement system

### Modding Support
- Custom items via CraftCMS
- New locations and vendors
- Formula creation tools
- Depends on technical feasibility in UE5

---

**End of Unsorted Ideas**

This document will grow as more design sessions happen. Periodically review and migrate solid ideas into proper documentation.
