# Neighbor Roster — Launch Set (12 Neighbors)

## Rarity Distribution

| Rarity | Count | F2P | Seasonal | Permanent Boosts? | Weekly Chest? |
|--------|-------|-----|----------|-------------------|---------------|
| Common | 4 | 2 | 2 | No | No |
| Rare | 4 | 2 | 2 | Yes (small) | Yes (Rare) |
| Epic | 4 | 2 | 2 | Yes (large) | Yes (Epic) |

---

## F2P Permanent Neighbors (6)

### 1. Marta the Baker (Common)
- **Theme:** Cheerful neighborhood baker, always has fresh pastries
- **Unlock:** Complete 50 customer orders
- **Daily Reward:** 10 gold (tap to collect)
- **Permanent Boost:** None
- **Weekly Chest:** None
- **Design Note:** First neighbor most players unlock. Teaches the collection mechanic.

### 2. Felix the Handyman (Common)
- **Theme:** Friendly fix-it guy with a toolbelt and a can-do attitude
- **Unlock:** Merge 500 items (lifetime)
- **Daily Reward:** 8 energy (tap to collect)
- **Permanent Boost:** None
- **Weekly Chest:** None
- **Design Note:** Rewards core loop engagement. ~Day 5-7 unlock for active players.

### 3. Professor Otto (Rare)
- **Theme:** Eccentric inventor neighbor with wild hair and a lab coat
- **Unlock:** Complete Room 10 (meta progression milestone)
- **Daily Reward:** 15 gold (tap to collect)
- **Permanent Boost:** +4 max energy
- **Weekly Chest:** Rare Neighbor Chest (see `03-reward-economy.md`)
- **Design Note:** First permanent boost. Rewards meta progression commitment.

### 4. Rosa the Gardener (Rare)
- **Theme:** Patient, green-thumbed neighbor who grows the best flowers
- **Unlock:** Win Merge League 3 times
- **Daily Reward:** 10 energy (tap to collect)
- **Permanent Boost:** 5% container recharge cost discount
- **Weekly Chest:** Rare Neighbor Chest
- **Design Note:** Rewards event mastery. Requires 3 separate Merge League participations (72h each), meaning minimum ~3 weeks of calendar time.

### 5. Grandma Elise (Epic)
- **Theme:** Wise matriarch neighbor who's lived on the street forever
- **Unlock:** Complete 15 rooms AND reach Level 25
- **Daily Reward:** 25 gold (tap to collect)
- **Permanent Boost:** +6 max energy, +1 container recharge amount
- **Weekly Chest:** Epic Neighbor Chest
- **Design Note:** Major chase target for veterans. Dual-condition ensures only committed players unlock.

### 6. Captain Rex (Epic)
- **Theme:** Retired adventurer neighbor with stories from around the world
- **Unlock:** Spend 100,000 coins lifetime AND complete 200 orders
- **Daily Reward:** Free daily item (rotating: Time Skipper L1, Merge Stone L1, Chain Breaker L1, Energy L2)
- **Permanent Boost:** +4 max energy, 5% container recharge cost discount
- **Weekly Chest:** Epic Neighbor Chest
- **Design Note:** Economy milestone neighbor. Rewards long-term resource investment.

---

## Seasonal Neighbors (6)

### 7. Sparky (Common) — Independence Day
- **Theme:** Patriotic neighbor with fireworks and a stars-and-stripes apron
- **Season:** July (4th of July event)
- **Unlock:** Complete the Independence Day event
- **IAP Fallback:** $2.99 (+ 50 energy + 100 gold sweetener)
- **Daily Reward:** 12 energy (tap to collect)
- **Permanent Boost:** None
- **Weekly Chest:** None
- **Returns:** Annually in July

### 8. Holly (Common) — Christmas
- **Theme:** Warm, jolly neighbor who decorates everything with lights
- **Season:** December (Christmas event)
- **Unlock:** Complete the Christmas event
- **IAP Fallback:** $2.99 (+ 50 energy + 100 gold sweetener)
- **Daily Reward:** 15 gold (tap to collect)
- **Permanent Boost:** None
- **Weekly Chest:** None
- **Returns:** Annually in December

### 9. Cupid (Rare) — Valentine's Day
- **Theme:** Romantic neighbor with hearts and roses everywhere
- **Season:** February (Valentine's event)
- **Unlock:** Complete the Valentine's event
- **IAP Fallback:** $4.99 (+ 100 energy + 250 gold sweetener)
- **Daily Reward:** Free daily booster (rotating: Time Skipper L1, Merge Stone L1)
- **Permanent Boost:** 5% container recharge cost discount
- **Weekly Chest:** Rare Neighbor Chest
- **Returns:** Annually in February

### 10. Jack O'Lantern (Rare) — Halloween
- **Theme:** Spooky-but-friendly pumpkin-headed neighbor
- **Season:** October (Halloween event)
- **Unlock:** Complete the Halloween event
- **IAP Fallback:** $4.99 (+ 100 energy + 250 gold sweetener)
- **Daily Reward:** 12 energy (tap to collect)
- **Permanent Boost:** +4 max energy
- **Weekly Chest:** Rare Neighbor Chest
- **Returns:** Annually in October

### 11. Aurora (Epic) — Spring Festival
- **Theme:** Ethereal, flower-crowned neighbor who brings spring
- **Season:** April (Spring Festival event)
- **Unlock:** Complete all milestones of the Spring Festival event
- **IAP Fallback:** $9.99 (+ 200 energy + 500 gold + Time Skipper L2 sweetener)
- **Daily Reward:** 20 gold (tap to collect)
- **Permanent Boost:** +1 container recharge amount, 5% container recharge cost discount
- **Weekly Chest:** Epic Neighbor Chest
- **Returns:** Annually in April

### 12. Nikolai (Epic) — Winter Holiday
- **Theme:** Warm, fur-coated neighbor from the north, brings gifts
- **Season:** December/January (Winter Holiday event — distinct from Christmas)
- **Unlock:** Complete all milestones of the Winter Holiday event
- **IAP Fallback:** $9.99 (+ 200 energy + 500 gold + Time Skipper L2 sweetener)
- **Daily Reward:** 15 energy (tap to collect)
- **Permanent Boost:** +4 max energy
- **Weekly Chest:** Epic Neighbor Chest
- **Returns:** Annually in January

---

## Permanent Boost Totals (All 12 Neighbors)

| Boost Type | Contributors | Individual | Total |
|------------|-------------|------------|-------|
| Max Energy | Otto (+4), Elise (+6), Rex (+4), Jack (+4), Nikolai (+4) | +4 to +6 | **+22** |
| Recharge Discount | Rosa (5%), Rex (5%), Cupid (5%), Aurora (5%) | 5% each | **20%** |
| Recharge Amount | Elise (+1), Aurora (+1) | +1 each | **+2** |

**Note:** Total max energy boost of +22 falls within the approved +15-20 moderate budget with slight overshoot. If needed, reduce Nikolai or Rex by 2 each to hit exactly +18. Recommend A/B testing the higher value first.

---

## Art Requirements

| Asset | Count | Notes |
|-------|-------|-------|
| Character portraits (full) | 12 | Used in Neighbors screen, unlock animation |
| Character icons (small) | 12 | Used in Book tab grid, notification badges |
| Silhouette/locked state | 12 | Shown before unlock with "?" overlay |
| Seasonal event banners | 6 | Shown during seasonal event announcing the neighbor |
| Unlock animation | 1 (reusable) | Celebration effect when a neighbor is unlocked |
| Reward collection VFX | 3 (per rarity) | Tap-to-collect effect, scales with rarity |

---

## Future Expansion Slots

The system is designed to accommodate new neighbors with each content update:
- **New seasonal events** → new seasonal neighbor
- **New rooms** → potential new F2P neighbor tied to room milestone
- **New event types** → potential new F2P neighbor tied to event mastery
- **Target:** 2-4 new neighbors per year (1 per quarter minimum)
