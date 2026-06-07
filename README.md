# DiceCraft | Bring D&D to your Minecraft Server

**DiceCraft** transforms your Paper server into a full tabletop RPG experience — d20 rolls, six D&D stats, 12 classes, 173 abilities, branching quests, dialogue NPCs, and more. Every system is modular and configurable, so you decide how deep the rabbit hole goes.

[![Discord](https://img.shields.io/discord/1369689692244803674?label=Discord&logo=discord&logoColor=white&color=7B2D8B&style=for-the-badge)](https://soystargaze.com/discord) ![Made with ❤️ by Stargaze](https://img.shields.io/badge/Made%20with-%E2%9D%A4%EF%B8%8F%20by%20stargaze-7B2D8B?style=for-the-badge)

![Banner](https://camo.githubusercontent.com/36e1eecbfcc0c395567b69f459962ba0225d2668b8083d4a2847caa9294c1644/68747470733a2f2f63646e2e6d6f6472696e74682e636f6d2f646174612f4d725238664b50692f696d616765732f626364623464346563333735363535313131386530313232346263393964613566323330666461622e706e67)

---

## ❖ Core Philosophy

- **Requires Minecraft 26.1.2** — built exclusively for modern Paper
- **Two modular game modes**: DM Mode and Turn Mode — enable only what you want
- **GUI-first workflow**: stat setup, class management, ability loadouts, quest tracking, and NPC editing all from in-game menus
- **SQL persistence**: SQLite out of the box, with MySQL/MariaDB/PostgreSQL support
- **Multi-language**: English and Spanish included; fully translatable via MiniMessage
- **12 config files**: fine-tune every dice value, mob AC, enchant bonus, and passive effect

---

## ➤ DM Mode — The Master Switch

DM Mode is the heart of DiceCraft. When **ON**, every combat roll, stat check, and resource matters. When **OFF**, players can still use abilities freely with no costs, no restrictions, and no required class unlock. Both modes coexist on the same server.

<details>
<summary>DM Mode ON — Full RPG Rules</summary>

- All attacks use **d20 + stat modifier vs. Armor Class**
- D&D attributes become effective (jump, speed, regen, trade prices…)
- Spell slots, Ki Points, and Rage uses are tracked and consumed
- XP and class leveling are active
- **Death Saving Throws** replace instant death (3 successes / 3 failures)
- Mob attacks roll d20 vs your AC
- Dialogue skill checks use your stats + affinity bonuses

</details>

<details>
<summary>DM Mode OFF — Casual Play</summary>

- Abilities can still be activated (configurable)
- No resource costs — free spell slots, Ki, and Rage
- No level requirements enforced
- Skill checks use plain d20 vs DC (no modifiers, no affinity bonus)
- Attribute passives only if `apply_without_dm_mode: true`

</details>

---

## ➤ Combat System

Every hit, miss, and crit is resolved with real dice mechanics.

<details>
<summary>Player Melee & Ranged Attacks</summary>

- **Roll**: d20 + weapon bonus + primary class stat modifier + enchantment bonuses + potion effects
- **vs. AC**: base armor per slot + shield bonus (+2, configurable) + enchantments
- **Natural 20** → critical hit (2× damage dice)
- **Natural 1** → critical failure (0 damage)
- **Damage dice by weapon**:
  - Wooden Sword: 1d4 · Golden Sword: 1d4+1 · Stone Sword: 1d6+1
  - Iron Sword: 1d8+2 · Diamond Sword: 1d10+3 · Netherite Sword: 1d12+4
  - Bow: 1d6+2 · Crossbow: 1d8+3 · Trident: 1d10+3

</details>

<details>
<summary>Mob Attacks</summary>

- ~25 mob types each with their own **damage dice and AC** (configured in `config.yml`)
- Examples: Zombie (1d6, AC 8) · Skeleton (1d6, AC 12) · Warden (1d30, AC 12) · Creeper (1d20, AC 8)
- **FairMode**: if player AC exceeds a threshold (15/20), mobs gain a flat attack bonus (+3/+5)
- Slimes and Magma Cubes scale dice by size (small/medium/large)

</details>

<details>
<summary>Enchantment & Potion Bonuses</summary>

Vanilla enchants and potions grant **flat dice bonuses** instead of percentages:
- Sharpness: +1 per level · Fire Aspect: +1 fire dmg + burn per level · Smite: +2 vs undead · Knockback: +0.4 force per level
- Power: +1 per level (bow) · Protection: -0.5 damage per total armor level (max 8 reduction) · Thorns: +1 reflect per level
- Strength: +2 · Weakness: -2 · Haste/Slowness: ±0.5 · Resistance: -1.5 per level (max 10 reduction)

</details>

<details>
<summary>Environmental & Indirect Damage</summary>

Fire, fall, poison, drowning and other hazards trigger a **d20 saving throw vs. DC 10** (configurable). Fail it, and you take the hit.

</details>

---

## ➤ Turn Mode — Initiative-Based Combat

Opt into D&D-style turn combat for tactical encounters.

<details>
<summary>Turn Mode Features</summary>

- **Auto-start**: entities within range (default 3 blocks) auto-join the session
- **BossBar**: shows current combatant, turn count, and initiative order
- **Movement range**: 10 blocks per turn (configurable)
- **Stealth system**: hold Shift for 3s → tactical invisibility; stealth attacks deal bonus damage (default 2d8+4)
- **Flee mechanic**: roll d20 vs escape DC to leave combat
- **Balance mode**: fighting multiple mobs? Get bonus attacks (per 2 mobs, configurable)
- **Glow highlight**: active combatant glows for clarity
- **Manual/auto turn advance**: pass manually or auto-advance on inactivity
- **Title & ActionBar** real-time combat feedback

</details>

---

## ➤ D&D Attribute System

Six classic stats shape everything from combat to trade prices.

<details>
<summary>The Six Stats (Point-Buy, 27 points, range 8–15)</summary>

- **STR — Strength**: jump height, knockback force, knockback resistance, block break speed
- **DEX — Dexterity**: stealth movement speed, attack speed, luck (loot), fall damage reduction
- **CON — Constitution**: max health bonus, oxygen capacity, burn time reduction, hunger drain resistance
- **INT — Intelligence**: enchanting cost reduction, anvil cost reduction, XP gain bonus
- **WIS — Wisdom**: potion effect duration, mob perception range, natural regen rate
- **CHA — Charisma**: villager trade discounts, pet health and damage bonuses

All values configurable per-modifier in `stats.yml`. Stats cap at 20 after ASI improvements.

</details>

<details>
<summary>Stat Configuration</summary>

- **GUI setup**: right-click a bookshelf on first login, or `/dc stats set`
- **Point-buy**: 27 points, range 8–15 per stat, real-time validation
- **Modifier formula**: `(stat - 10) / 2` (D&D standard)
- **ASI**: +2 to one stat or +1 to two stats, every 4 levels of the same class
- **Reset items**: Tome of Reincarnation, Scroll of Amnesia, Crystal of Rebirth (physical items, consumed on use)

</details>

---

## ➤ Class System — 12 D&D Classes

<details>
<summary>The 12 Classes</summary>

| Class | Primary Stat | Class Item | Abilities |
|-------|-------------|-----------|-----------|
| Fighter | Strength | Battle Order (Iron Sword) | 12 |
| Barbarian | Strength | Totem of Fury (Bone) | 14 |
| Monk | Dexterity | Staff of Ki (Stick) | 15 |
| Paladin | Strength | Holy Symbol (Golden Sword) | 14 |
| Rogue | Dexterity | Dagger of Shadows (Iron Sword) | 15 |
| Ranger | Dexterity | Hunter's Mark (Bow) | 15 |
| Bard | Charisma | Mystic Instrument (Music Disc) | 15 |
| Cleric | Wisdom | Divine Symbol (Life Totem) | 14 |
| Druid | Wisdom | Druidic Branch (Stick) | 15 |
| Wizard | Intelligence | Arcane Grimoire (Enchanted Book) | 14 |
| Warlock | Charisma | Pact Book (Book) | 15 |
| Sorcerer | Charisma | Elemental Staff (Blaze Rod) | 15 |

</details>

<details>
<summary>Progression & Multiclass</summary>

- **Level range**: 1–12 per class; configurable total cap (TOTAL/PER_CLASS/NONE modes)
- **XP formula**: configurable base + multiplier (`base=100, multiplier=1.5` by default)
- **Multiclass cost**: `100 × number of existing classes` XP to unlock each new class
- **ASI at level 4/8/12** of the same class: GUI auto-triggers, permanent stat improvement
- **Magical Secrets** (Bard lv5): pick one active ability from any other class

</details>

<details>
<summary>Resource Management</summary>

| Resource | Classes | Recovery |
|----------|---------|---------|
| Spell Slots (full caster) | Wizard, Sorcerer, Bard, Cleric, Druid | Long rest (sleep) |
| Spell Slots (half caster) | Paladin, Ranger | Long rest |
| Pact Magic | Warlock | Short or long rest |
| Ki Points | Monk | Short or long rest |
| Rage Uses | Barbarian | Long rest |

- `/dc class rest short|long` · Sleeping in bed auto-triggers long rest
- **ActionBar / Scoreboard** pips display (◆ filled / ◇ empty, configurable)

</details>

---

## ➤ 173 Abilities

Every class has a full roster of active and passive abilities, activated through a loadout system without opening your inventory.

<details>
<summary>Loadout System (4 slots per class)</summary>

| Input | Slot |
|-------|------|
| Right-click class item | Slot 1 |
| Left-click class item | Slot 2 |
| Shift + Right-click | Slot 3 (or open selector if empty) |
| Shift + Left-click | Slot 4 |

- **ActionBar** updates every second: class name, ability state (✓ ready or ⏱ Xs), resource count
- **Preparation**: Shift+Right-click → GUI ability picker filtered by level and available resources
- Persistent across sessions via database

</details>

<details>
<summary>Ability Highlights by Class</summary>

**Fighter**: Second Wind, Action Surge, Whirlwind Attack, Extra Attack, Great Weapon Master, Indomitable, Battle Magic…

**Barbarian**: Rage, Reckless Attack, Ground Slam, War Cry, Brutal Critical, Feral Instinct, Primal Champion…

**Monk**: Flurry of Blows, Ki Blast, Quivering Palm, Step of the Wind, Stunning Strike, Martial Arts, Blindsense…

**Paladin**: Divine Smite, Lay on Hands, Holy Avenger, Cleansing Touch, Aura of Protection, Aura of Courage…

**Rogue**: Sneak Attack, Smoke Bomb, Shadow Step, Cunning Action, Evasion, Assassinate, Elusive, Vanish…

**Ranger**: Hunter's Mark, Multi-shot, Volley, Ensnaring Shot, Favored Enemy, Hide in Plain Sight, Foe Slayer…

**Bard**: Vicious Mockery, Hypnotic Pattern, Healing Word, Inspiration, Cutting Words, Jack of All Trades, Magical Secrets…

**Cleric**: Healing Word, Turn Undead, Resurrection, Mass Cure, Beacon of Hope, Bless, Divine Intervention…

**Druid**: Entangling Roots, Call of the Pack, Wrath of Nature, Produce Flame, Spore Cloud, Tidal Wave, Thorn Armor…

**Wizard**: Fireball, Misty Step, Time Stop, Magic Missile, Counterspell, Disintegrate, Haste, Invisibility, Teleport…

**Warlock**: Eldritch Blast, Hex, Hunger of Hadar, Hellish Rebuke, Armor of Agathys, Pact Blade, Minions of Chaos…

**Sorcerer**: Chromatic Orb, Wild Magic Surge, Chaos Bolt, Dragon Wings, Quickened Spell, Twinned Spell, Bend Luck…

</details>

<details>
<summary>Damage Feedback (configurable)</summary>

- `FULL` — chat with per-die breakdown
- `SUMMARY` — chat with roll + total only
- `ACTIONBAR` — compact one-liner
- `OFF` — silent
- Failed rolls: `ZERO` (default for single-target) or `HALF` (default for AoE/saves), overridable per-ability

</details>

---

## ➤ Death Saving Throws

Death in DiceCraft is a dramatic moment, not a respawn screen.

<details>
<summary>How It Works</summary>

When HP reaches 0, the player enters a downed crawl state — incoming damage is negated, mobs cannot target them.

**Without DM Mode**: fixed countdown timer → auto d20 roll ≥ 10 to survive.

**With DM Mode (D&D rules)**:
- Automated d20 rolls every 10s
- 3 successes (≥10) → revive · 3 failures (<10) → permanent death
- Natural 20 → 2 successes · Natural 1 → 2 failures
- Scoreboard shows live: `Successes: N | Failures: N`

**Active while downed**:
- Hold Shift for 3s (player) → force a manual saving throw
- Ally within 2 blocks holds Shift for 3s → revive with ActionBar progress bar
- Cleric abilities `Resurrection` and `True Resurrection` can revive permanently dead players

</details>

---

## ➤ RPG Module — Dialogues, Quests, NPCs, Checks & Affinity

A full narrative and quest system built directly into the plugin.

<details>
<summary>Dialogue System (Paper Dialog API)</summary>

- **Graph-based nodes** with branching choices
- Per-node: body text (MiniMessage), multiple choices, conditions, d20 checks, actions
- **Conditions gate choices** (quest status, affinity tier, player flags, class level…)
- **D20 skill checks** inside dialogue (Persuasion, Deception, Intimidation…)
- **Actions on choice**: start quest, add affinity, give items, run commands, set flags, open trade…
- Per-player session tracking with back-stack navigation

</details>

<details>
<summary>18 Skill Check Types</summary>

Persuasion · Deception · Intimidation · Insight · Perception · Investigation · Stealth · Athletics · Acrobatics · Sleight of Hand · Arcana · History · Nature · Religion · Animal Handling · Medicine · Survival · Performance

Each check: `1d20 + stat modifier + affinity bonus vs. DC` (with DM Mode) or `plain 1d20 vs. DC` (without). Natural 20/1 auto-succeed/fail.

</details>

<details>
<summary>25+ Quest Objective Types</summary>

`kill_entity` · `kill_player` · `kill_boss` · `collect_item` · `deliver_item` · `consume_item` · `break_blocks` · `place_blocks` · `interact_block` · `craft_item` · `smelt_item` · `enchant_item` · `brew_item` · `fish_catch` · `reach_location` · `reach_dialogue_node` · `explore_biome` · `reach_level` · `gain_xp` · `deal_damage` · `take_damage` · `talk_to_npc` · `tame_mobs` · `breed_mobs` · `escort_npc` · `gain_affinity` · `learn_class` · `complete_quest` · `use_ability` · `pass_check` · `playtime` · `run_command_trigger` · `condition`

Quests support **multi-stage branching**, prerequisites, cooldowns, time limits, repeatable flags, and fully configurable rewards (XP, items, affinity, flags, commands, titles, sounds, particles).

</details>

<details>
<summary>NPC System (Native + Citizens soft-depend)</summary>

- **Native NPCs**: spawn any Minecraft entity at a configured location, invulnerable, no AI
- **Citizens NPCs**: full Citizens 2.x integration (soft-depend, degrades gracefully if absent)
- **Conditional dialogue routing**: per-binding conditions — first match wins, default fallback
- **Trade menu**: auto-injects a "Trade" button in dialogue; configurable pool from `trades.yml`
- **Affinity tiers**: HOSTILE / NEUTRAL / FRIENDLY / HONORED — affect dialogue branches, check bonuses, and trade prices

</details>

<details>
<summary>Affinity (Reputation) System</summary>

- Per-player, per-NPC reputation score
- Tiers: HOSTILE (≤-20, -2 to checks) · NEUTRAL · FRIENDLY (+20, +1) · HONORED (+50, +2)
- **Charisma bias**: CHA modifier influences affinity gains (DM Mode only, configurable)
- **Trade price scaling**: HOSTILE 1.25× → HONORED 0.70× cost multiplier
- Hostile players can be blocked from rare trade offers

</details>

<details>
<summary>In-Game Content Editors (GUI)</summary>

Full GUI editors for server staff — no external tools needed:
- **Dialogue editor**: create/edit nodes, choices, conditions, actions
- **Quest editor**: multi-stage creation, objective configuration, reward setup
- **NPC editor**: spawn location, provider type, dialogue bindings, trade config
- Content saved as hot-reloadable YAML (`/dc rpg reload`)

</details>

---

## ➤ Spell Scrolls

<details>
<summary>Scroll System</summary>

- **Single-use consumable items** — right-click to cast any ability
- **Scroll Infusion Altar**: crafted from Chest + Enchanting Table base + Amethyst pillars
- **Two tiers**:
  - *Lesser Scroll* (Lv1–5): Paper + 4 Blaze Powder + 1 Diamond
  - *Greater Scroll* (Lv1–12): Paper + 8 Blaze Powder + 4 Diamond + Nether Star
- **Casting stat**: Intelligence by default, configurable per scroll
- **Loot generation**: configurable 12% chest spawn chance, max level cap for found scrolls

</details>

---

## ➤ XP & Rewards

<details>
<summary>XP Sources (all configurable)</summary>

| Action | Default XP |
|--------|-----------|
| Kill mob | 50 |
| Kill player | 150 |
| Kill boss (Wither/Dragon or >100 HP mob) | 500 |
| Discover structure | 100 |
| Mine diamond ore | 10 |
| Mine ancient debris | 20 |
| Craft item | 5 |
| Catch fish | 15 |

</details>

---

## ➤ Commands & Permissions

<details>
<summary>Full Command Reference</summary>

| Command | Permission | Purpose |
|---------|-----------|---------|
| `/dc hub` | `dicecraft.use` | Open character hub GUI |
| `/dc roll <notation>` | `dicecraft.use` | Roll any dice (3d6+2, 1d20…) |
| `/dc dmmode set true\|false [player]` | `dicecraft.dmmode` | Toggle DM Mode |
| `/dc dmmode status` | `dicecraft.dmmode` | Check DM Mode status |
| `/dc turnmode start\|stop` | `dicecraft.turnmode` | Begin/end combat session |
| `/dc stats set [player]` | `dicecraft.stats.set` | Open attribute setup GUI |
| `/dc stats view [player]` | `dicecraft.stats.view` | Show stats in chat |
| `/dc stats reset [player]` | `dicecraft.stats.reset` | Reset stats (admin) |
| `/dc levelup [class]` | `dicecraft.levelup` | View/manage classes & XP |
| `/dc class menu` | `dicecraft.use` | Open ability selector |
| `/dc class set-secret <key>` | `dicecraft.use` | Set Bard Magical Secrets |
| `/dc class rest short\|long` | `dicecraft.use` | Recover spell slots/Ki/Rage |
| `/dc quests` | `dicecraft.use` | List active/completed quests |
| `/dc quests <id>` | `dicecraft.use` | View quest details |
| `/dc admin reset stats\|class\|all <player>` | `dicecraft.admin` | Force reset (no item required) |
| `/dc admin give-reset <type> <player>` | `dicecraft.admin` | Give reset item to player |
| `/dc rpg reload` | `dicecraft.admin` | Hot-reload all RPG content |
| `/dc rpg quest give <id> [player]` | `dicecraft.admin` | Grant quest to player |
| `/dc rpg edit` | `dicecraft.admin` | Open content editor hub |
| `/dc reload` | `dicecraft.admin` | Reload all config files |

</details>

---