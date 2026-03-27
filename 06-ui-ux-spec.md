# UI/UX Specification — Neighbors Screen & Book Tab Integration

## Book Tab Changes

### Current Book Tab Structure (5 sub-tabs)
```
[Book Tab Icon]
├── Home (house icon — rooms list)
├── Tools (wrench icon — cleaning tools/items)
├── Factory (factory icon — item catalog)
├── Chests (chest icon — chest collection tracker)
└── Star (star icon — currency/achievements)
```

### Option A — Add 6th Sub-Tab
```
[Book Tab Icon]
├── Home
├── Tools
├── Factory
├── Chests
├── Star
└── Neighbors       ← NEW (6th tab)
```

### Option B — Simplify to 2 Prominent Tabs
```
[Book Tab Icon]
├── Home            ← LARGER (absorbs Tools, Factory, Chests, Star as sub-sections)
└── Neighbors       ← LARGER (new, high-engagement)
```

**Rationale:** Option B creates a cleaner, more focused Book tab with two large, easy-to-tap icons. The current 5-tab bar uses small icons on mobile — reducing to 2 makes both tabs more prominent and accessible. Tools/Factory/Chests/Star content folds into the Home tab as scrollable sections. Recommend A/B testing both layouts.

### Bottom Navigation Bar (unchanged)
```
[Shop] [Trophy] [Home] [Team] [Book]
```

---

## Neighbors Screen Layout

### Main View — Collection Grid

```
┌─────────────────────────────────────────────┐
│  MY NEIGHBORHOOD          [6/12 Unlocked]   │
│  ─────────────────────────────────────────── │
│                                             │
│  ┌─────┐  ┌─────┐  ┌─────┐  ┌─────┐       │
│  │Marta│  │Felix│  │Otto │  │Rosa │       │
│  │ ✅  │  │ ✅  │  │ 🔒 │  │ 🔒 │       │
│  │ 10G │  │ 8E  │  │ ??? │  │ ??? │       │
│  └─────┘  └─────┘  └─────┘  └─────┘       │
│                                             │
│  ┌─────┐  ┌─────┐  ┌─────┐  ┌─────┐       │
│  │Elise│  │ Rex │  │Spark│  │Holly│       │
│  │ 🔒 │  │ 🔒 │  │ 🔒 │  │ 🔒 │       │
│  │ ??? │  │ ??? │  │ ??? │  │ ??? │       │
│  └─────┘  └─────┘  └─────┘  └─────┘       │
│                                             │
│  ┌─────┐  ┌─────┐  ┌─────┐  ┌─────┐       │
│  │Cupid│  │Jack │  │Auror│  │Niko │       │
│  │ 🔒 │  │ 🔒 │  │ 🔒 │  │ 🔒 │       │
│  │ ??? │  │ ??? │  │ ??? │  │ ??? │       │
│  └─────┘  └─────┘  └─────┘  └─────┘       │
│                                             │
│  ─────── Active Boosts ──────────────────── │
│  Max Energy: +4  │  Recharge: -5%  │  +0   │
└─────────────────────────────────────────────┘
```

### Card States

**Locked (not yet achievable):**
- Silhouette portrait (dark, no details)
- "???" for rewards
- Tap → shows unlock requirement + progress bar
- Rarity border color visible (gray/blue/purple outline)

**Locked (progress visible):**
- Silhouette portrait
- Progress bar below (e.g., "37/50 Orders")
- Tap → shows full unlock details + current progress

**Locked (seasonal, not available):**
- Silhouette portrait
- "Returns [Month Year]" label
- Tap → shows neighbor preview + "Available during [Event Name]"

**Locked (seasonal, IAP available):**
- Silhouette portrait with golden "!" badge
- "Limited Offer!" label with countdown timer
- Tap → shows IAP purchase option

**Unlocked (rewards available):**
- Full color portrait with glowing border
- Reward icon with collectible indicator (bouncing coin/energy/item)
- Tap → collect rewards (animation plays)
- Rarity border: Common (green), Rare (blue), Epic (purple)

**Unlocked (rewards collected):**
- Full color portrait, no glow
- "Collected" checkmark or dimmed reward icon
- Timer showing next reward availability: "Next reward: 14h 23m"
- Tap → shows neighbor detail card

---

## Neighbor Detail Card (Tap on any neighbor)

```
┌─────────────────────────────────────────────┐
│                    [X]                       │
│         ┌───────────────┐                   │
│         │               │                   │
│         │   [Portrait]  │                   │
│         │               │                   │
│         └───────────────┘                   │
│                                             │
│         PROFESSOR OTTO                      │
│         ★★ Rare                             │
│         "Science is just organized          │
│          curiosity!"                        │
│                                             │
│  ─────── Rewards ────────────────────────── │
│  Daily: 15 Gold              [Collect]      │
│  Weekly: Rare Chest           3d 14h        │
│  Boost: +4 Max Energy         ACTIVE        │
│                                             │
│  ─────── How to Unlock ──────────────────── │
│  Complete Room 10                           │
│  [████████████░░░░░░] Room 7/10             │
└─────────────────────────────────────────────┘
```

---

## Active Boosts Bar

A persistent summary bar at the bottom of the Neighbors screen showing all currently active permanent boosts:

```
┌─────────────────────────────────────────────┐
│ ⚡ +4 Energy  │  🔄 -5% Recharge  │  📦 +0 │
└─────────────────────────────────────────────┘
```

- Updates live as neighbors are unlocked
- Tap any boost → tooltip showing which neighbors contribute
- Values are the SUM of all unlocked neighbors' boosts

---

## Notification System

### Book Tab Badge
- **Red dot** appears on Book tab icon when any daily or weekly reward is available to collect
- Badge shows count of collectible rewards (e.g., "3" if 3 neighbors have uncollected rewards)
- Clears when all rewards are collected

### Reward Reset Timing
- **Daily rewards:** Reset at server midnight UTC (same as Daily Tasks)
- **Weekly chests:** Available every 7 days from the moment the neighbor was unlocked (rolling, not fixed day)

### Push Notifications (Opt-In)

| Trigger | Message | Frequency |
|---------|---------|-----------|
| Daily rewards available | "Your neighbors have gifts! Tap to collect." | Once daily at reset |
| Weekly chest available | "[Neighbor Name] has a chest for you!" | Once per chest |
| Seasonal event starting | "A new neighbor is moving in! [Event] starts today." | Once per event |
| IAP fallback Day 2 | "Last chance to get [Neighbor]! Offer ends tomorrow." | Once |
| Near unlock (80% progress) | "Almost there! [X] more [action] to meet [Neighbor]!" | Once per neighbor |

---

## Unlock Celebration

### Animation Sequence (2-3 seconds)

1. Silhouette card glows with rarity color (green/blue/purple)
2. Card flips to reveal full-color portrait
3. Confetti burst + rarity-appropriate particle effects
4. Character name + tagline appear
5. "Rewards Unlocked!" banner
6. First reward auto-collected with fanfare
7. "View in Neighborhood" CTA button

### Seasonal Unlock (Extended)
Same as above, plus:
- Seasonal themed background (snowflakes for winter, hearts for Valentine's, etc.)
- Event-specific celebration music sting

---

## Collect Rewards Interaction

### Daily Reward Collection
1. Player taps unlocked neighbor with available reward
2. Reward icon (coin/energy/item) flies from neighbor portrait to resource bar
3. Satisfying "cha-ching" or "pop" sound effect
4. "Collected" state replaces the reward indicator
5. If multiple neighbors have rewards, player can tap each one (no "collect all" button — each tap is a micro-engagement moment)

### Weekly Chest Collection
1. Player taps neighbor with available weekly chest
2. Chest appears (Rare or Epic visual)
3. Chest opens with standard chest-opening animation
4. Items fly to board/inventory
5. Chest timer resets (7-day countdown visible)

---

## Accessibility Considerations

| Aspect | Implementation |
|--------|---------------|
| Color blindness | Rarity indicated by border pattern (solid/dashed/double) in addition to color |
| Text size | Neighbor names and reward amounts use minimum 14sp font |
| Tap targets | Each neighbor card is minimum 48dp × 48dp |
| Screen readers | Each card has descriptive content: "[Name], [Rarity], [Locked/Unlocked], [Reward status]" |
| Low-end devices | Portraits use compressed textures, celebration animations can be simplified |
