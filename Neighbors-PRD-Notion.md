# PRD: Neighbors

**Author:** Bobby
**Date:** March 26, 2026
**Status:** Draft
**Priority:** P1 (High)

---

# Overview

Neighbors is a **character collection system** inside the Book tab. Players unlock named NPC neighbors through gameplay achievements, event wins, and seasonal events. Each unlocked neighbor provides ongoing value — daily gold, energy, free items, and permanent gameplay boosts like increased max energy or cheaper container recharges.

The goal is threefold:

- **Engagement** — a new collectible layer that gives players goals beyond room completion
- **Retention** — daily and weekly rewards that pull players back to collect from their neighborhood
- **IAP potential** — seasonal neighbors tied to limited-time events with a purchase fallback for players who miss them

12 neighbors at launch across 3 rarity tiers (Common / Rare / Epic). Half are permanently earnable through gameplay, half are seasonal with a short IAP window if missed.

---

# User Stories

- As a **mid-game F2P player**, I want to unlock neighbors by hitting milestones so that I get useful daily bonuses
- As a **veteran player**, I want to collect all neighbors so that I have long-term goals beyond room completion
- As a **light spender**, I want to purchase seasonal neighbors I missed so that I don't lose collection progress
- As an **event-focused player**, I want my repeated event wins to count toward something permanent
- As a **daily player**, I want to tap my neighborhood each day to collect energy, gold, and items

---

# Book Tab Restructure

The Book tab gets reorganized into 3 main tabs:

```
┌───────────────────────────────────────────────┐
│                                               │
│   [ Rooms ]    [ Neighbourhood ]  [Collections]
│                     ▲                         │
│               (active tab)                    │
│                                               │
└───────────────────────────────────────────────┘
```

| Tab | Contents |
|-----|----------|
| **Rooms** | Room list (same as current Home tab) |
| **Neighbourhood** | Neighbors collection — the new feature |
| **Collections** | Sub-tabs for the old categories: Tools, Factory, Chests, Star |

---

# Neighbourhood Screen

A vertically scrollable page showing neighbor portraits. Unlocked neighbors are shown in full color on the left side. Locked neighbors appear as grayed-out silhouettes to the right, showing that there are more to collect.

```
┌───────────────────────────────────────────────┐
│  [ Rooms ]  [ Neighbourhood ]  [ Collections ]│
├───────────────────────────────────────────────┤
│                                               │
│  MY NEIGHBOURHOOD                  [Claim All]│
│                                               │
│  ┌────────────────────────────────────────┐   │
│  │                                        │   │
│  │  ┌──────┐ ┌──────┐ ┌──────┐ ┌──────┐  │   │
│  │  │Marta │ │Felix │ │ ░░░░ │ │ ░░░░ │  │   │
│  │  │  🟢  │ │  🟢  │ │  🔒  │ │  🔒  │  │   │
│  │  │ 10G  │ │  8E  │ │  ?   │ │  ?   │  │   │
│  │  │Common│ │Common│ │ Rare │ │ Rare │  │   │
│  │  └──────┘ └──────┘ └──────┘ └──────┘  │   │
│  │                                        │   │
│  │  ┌──────┐ ┌──────┐ ┌──────┐ ┌──────┐  │   │
│  │  │ ░░░░ │ │ ░░░░ │ │ ░░░░ │ │ ░░░░ │  │   │
│  │  │  🔒  │ │  🔒  │ │  🔒  │ │  🔒  │  │   │
│  │  │  ?   │ │  ?   │ │  ?   │ │  ?   │  │   │
│  │  │ Epic │ │ Epic │ │Common│ │Common│  │   │
│  │  └──────┘ └──────┘ └──────┘ └──────┘  │   │
│  │                                        │   │
│  │  ┌──────┐ ┌──────┐ ┌──────┐ ┌──────┐  │   │
│  │  │ ░░░░ │ │ ░░░░ │ │ ░░░░ │ │ ░░░░ │  │   │
│  │  │  🔒  │ │  🔒  │ │  🔒  │ │  🔒  │  │   │
│  │  │  ?   │ │  ?   │ │  ?   │ │  ?   │  │   │
│  │  │ Rare │ │ Rare │ │ Epic │ │ Epic │  │   │
│  │  └──────┘ └──────┘ └──────┘ └──────┘  │   │
│  │                                        │   │
│  └────────────────────────────────────────┘   │
│                                               │
│  ─── Active Boosts ────────────────────────── │
│  +4 Max Energy  ·  -5% Recharge  ·  +0 Amt   │
│                                               │
├───────────────────────────────────────────────┤
│  [Shop] [Trophy] [Home] [Team]       [Book]  │
└───────────────────────────────────────────────┘
```

**Unlocked neighbors** show full color portrait, daily reward indicator, and a collectible badge when rewards are ready. **Locked neighbors** show a grayed silhouette with a lock icon and their rarity border.

Tapping a neighbor opens a detail card with their portrait, description, rewards breakdown, and unlock progress (if locked).

The **Claim All** button collects all available daily and weekly rewards in one tap.

---

# Neighbor Types

## Permanent Neighbors

Always available to unlock through gameplay. Conditions are based on achievements (merge X items, complete Y orders), meta progression (complete Room Z), event mastery (win Merge League X times), or economy milestones (spend X coins lifetime). Once unlocked, they stay forever.

## Seasonal Neighbors

Tied to limited-time seasonal events (Independence Day, Halloween, Christmas, etc.). Players earn them by completing the event. If they miss it:

- A **3-day IAP purchase window** opens after the event ends, bundled with some energy and gold as a sweetener
- If they miss that too, the neighbor **returns annually** with the same event next year
- Pricing is tiered by rarity: Common $2.99, Rare $4.99, Epic $9.99

This creates collectibility pressure and a natural IAP opportunity without being pay-to-win — every seasonal neighbor can be earned free the following year.

## Reward Types

Neighbors provide three categories of rewards:

**Daily Rewards** — Tap to collect (or Claim All). Small amounts of gold, energy, or a rotating free item (Time Skipper, Merge Stone, etc.). Resets at server midnight. Light supplement to existing income, not a replacement.

**Weekly Chests** — Available from Rare and Epic neighbors. A per-neighbor chest that refreshes every 7 days. Contains gold, boosters, and energy items. Quality scales with rarity.

**Permanent Boosts** — Passive, always active once the neighbor is unlocked. No interaction needed. Available from Rare and Epic neighbors. Three types:

| Boost | What It Does |
|-------|-------------|
| **+Max Energy** | Increases energy capacity (base: 100). More energy per recharge, longer sessions |
| **Recharge Discount** | Reduces coin cost of container recharges by a percentage |
| **+Recharge Amount** | Adds extra items when manually recharging containers (coins/RV/hourglass) |

Boosts **stack** across multiple neighbors. The more you collect, the stronger you get.

---

# Neighbor Roster & Rewards

## F2P Permanent Neighbors

| Neighbor | Rarity | Unlock Condition | Daily Reward | Permanent Boost | Weekly Chest |
|----------|--------|-----------------|-------------|-----------------|--------------|
| Marta the Baker | Common | Complete 50 orders | 10 gold | — | — |
| Felix the Handyman | Common | Merge 500 items | 8 energy | — | — |
| Professor Otto | Rare | Complete Room 10 | 15 gold | +4 max energy | Rare Chest |
| Rosa the Gardener | Rare | Win Merge League 3x | 10 energy | 5% recharge discount | Rare Chest |
| Grandma Elise | Epic | Complete 15 rooms + Level 25 | 25 gold | +6 max energy, +1 recharge amount | Epic Chest |
| Captain Rex | Epic | Spend 100K coins + 200 orders | Rotating item | +4 max energy, 5% recharge discount | Epic Chest |

## Seasonal Neighbors

| Neighbor | Rarity | Event | Daily Reward | Permanent Boost | Weekly Chest | IAP Fallback |
|----------|--------|-------|-------------|-----------------|--------------|-------------|
| Sparky | Common | Independence Day (Jul) | 12 energy | — | — | $2.99 |
| Holly | Common | Christmas (Dec) | 15 gold | — | — | $2.99 |
| Cupid | Rare | Valentine's (Feb) | Rotating booster | 5% recharge discount | Rare Chest | $4.99 |
| Jack O'Lantern | Rare | Halloween (Oct) | 12 energy | +4 max energy | Rare Chest | $4.99 |
| Aurora | Epic | Spring Festival (Apr) | 20 gold | +1 recharge amount, 5% recharge discount | Epic Chest | $9.99 |
| Nikolai | Epic | Winter Holiday (Jan) | 15 energy | +4 max energy | Epic Chest | $9.99 |

## Aggregate Totals (All 12 Neighbors Unlocked)

| Category | Total |
|----------|-------|
| **Daily gold** | 85 coins/day |
| **Daily energy** | 57 energy/day |
| **Daily items** | 2 rotating items/day |
| **Weekly chests** | 8 chests/week (4 Rare + 4 Epic) |
| **Max energy boost** | +22 (100 → 122, +22%) |
| **Recharge discount** | 20% off coin recharge costs |
| **Recharge amount** | +2 extra items per manual recharge |

---

# Seasonal Calendar

| Month | Event | Neighbor | Rarity | IAP |
|-------|-------|----------|--------|-----|
| January | Winter Holiday | Nikolai | Epic | $9.99 |
| February | Valentine's Day | Cupid | Rare | $4.99 |
| April | Spring Festival | Aurora | Epic | $9.99 |
| July | Independence Day | Sparky | Common | $2.99 |
| October | Halloween | Jack O'Lantern | Rare | $4.99 |
| December | Christmas | Holly | Common | $2.99 |

6 seasonal events per year. Miss the event → 3-day IAP window → or wait for next year.

---

# IAP Fallback Bundles

| Rarity | Price | Sweetener |
|--------|-------|-----------|
| Common | $2.99 | + 50 energy + 100 gold |
| Rare | $4.99 | + 100 energy + 250 gold |
| Epic | $9.99 | + 200 energy + 500 gold + Time Skipper L2 |

---

# Weekly Chest Drop Tables

## Rare Neighbor Chest (6 items, opens instantly)

| Drop | Chance |
|------|--------|
| Gold L1 (5 coins) | 40% |
| Gold L2 (15 coins) | 25% |
| Time Skipper L1 | 15% |
| Energy L2 (6 energy) | 10% |
| Merge Stone L1 | 8% |
| Gold L3 (40 coins) | 2% |

## Epic Neighbor Chest (8 items, opens instantly)

| Drop | Chance |
|------|--------|
| Gold L2 (15 coins) | 30% |
| Gold L3 (40 coins) | 20% |
| Time Skipper L1 | 15% |
| Time Skipper L2 | 12% |
| Energy L2 (6 energy) | 10% |
| Merge Stone L1 | 8% |
| Merge Stone L2 | 3% |
| Gold L4 (100 coins) | 2% |

---

# Rollout Plan

## Phase 1: Soft Launch — F2P Only (3 weeks)

10% of DAU. 6 F2P neighbors only, no seasonal. Southeast Asia + Africa markets.

## Phase 2: Seasonal Test (4-6 weeks)

25% of DAU. Add 1-2 seasonal neighbors + IAP fallback. Aligned with next seasonal event.

## Phase 3: Global Launch

100% of DAU. All 12 neighbors, full IAP, app store update.

---

# Open Questions

- [ ] Merge League "win" definition — top 1, top 3, or completing the event?
- [ ] Are seasonal events already planned, or do they need to be built from scratch?
- [ ] Can rewards be collected offline and synced later?
- [ ] Should neighbor count be visible on leaderboards or team profiles?
