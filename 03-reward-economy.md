# Reward Economy — Detailed Numbers & Impact Analysis

## Daily Reward Budget

### Per-Neighbor Daily Rewards

| Neighbor | Rarity | Daily Type | Amount | $ Equivalent |
|----------|--------|-----------|--------|-------------|
| Marta | Common | Gold | 10 | $0.0099 |
| Felix | Common | Energy | 8 | $0.026 |
| Prof. Otto | Rare | Gold | 15 | $0.015 |
| Rosa | Rare | Energy | 10 | $0.033 |
| Grandma Elise | Epic | Gold | 25 | $0.025 |
| Captain Rex | Epic | Item | ~$0.03-0.05 value | Varies |
| Sparky | Common | Energy | 12 | $0.040 |
| Holly | Common | Gold | 15 | $0.015 |
| Cupid | Rare | Item | ~$0.03 value | Varies |
| Jack | Rare | Energy | 12 | $0.040 |
| Aurora | Epic | Gold | 20 | $0.020 |
| Nikolai | Epic | Energy | 15 | $0.050 |

### Aggregate Daily Income (All 12 Unlocked)

| Resource | Total Daily | Context vs Existing Sources |
|----------|------------|---------------------------|
| **Gold** | 85 coins/day | ~1.8% of Merge Fever daily (4,700/day). Negligible economy impact |
| **Energy** | 57 energy/day | ~1.9 coin refills saved (at 250 coins each). Equivalent to ~$0.19 IAP |
| **Items** | 2 rotating items/day | ~1 Time Skipper L1 + 1 Merge Stone L1 average. Minor supplement |

**Conclusion:** Daily rewards are a **light supplement** — meaningful enough to drive daily visits, but nowhere near disrupting the existing economy. Merge Fever remains the dominant gold source by >50x.

---

## Weekly Chest Rewards

### Rare Neighbor Chest (from each Rare neighbor)
- **Capacity:** 6 items
- **Drop Table:**
  - 40% Gold L1 (5 coins)
  - 25% Gold L2 (15 coins)
  - 15% Time Skipper L1
  - 10% Energy L2 (6 energy)
  - 8% Merge Stone L1
  - 2% Gold L3 (40 coins)
- **Expected value:** ~35-45 coins equivalent + 1 booster
- **Opens instantly** (no timer)

### Epic Neighbor Chest (from each Epic neighbor)
- **Capacity:** 8 items
- **Drop Table:**
  - 30% Gold L2 (15 coins)
  - 20% Gold L3 (40 coins)
  - 15% Time Skipper L1
  - 12% Time Skipper L2
  - 10% Energy L2 (6 energy)
  - 8% Merge Stone L1
  - 3% Merge Stone L2
  - 2% Gold L4 (100 coins)
- **Expected value:** ~80-120 coins equivalent + 2 boosters
- **Opens instantly** (no timer)

### Aggregate Weekly Chest Income (All 12 Unlocked)

| Source | Count/Week | Est. Value/Week |
|--------|-----------|----------------|
| Rare Neighbor Chests | 4 chests (Otto, Rosa, Cupid, Jack) | ~160 coins + 4 boosters |
| Epic Neighbor Chests | 4 chests (Elise, Rex, Aurora, Nikolai) | ~400 coins + 8 boosters |
| **Total** | 8 chests/week | **~560 coins + 12 boosters/week** |

**Context:** 560 coins/week = ~80 coins/day additional ≈ 1.7% of Merge Fever income. Boosters are the real value — 12 free Time Skippers and Merge Stones per week is a solid quality-of-life boost.

---

## Permanent Boost Economy Impact

### +22 Max Energy (Base: 100)

| Metric | Before | After | Impact |
|--------|--------|-------|--------|
| Max energy capacity | 100 | 122 | +22% increase |
| Full recharge time | 200 min | 244 min | +44 minutes to full recharge |
| Coin refill value | 100 energy for 250 coins | 122 energy for 250 coins | 22% more energy per refill |
| Session length potential | 100 taps | 122 taps | 22 more actions before depletion |

**Analysis:** A 22% capacity increase is the most impactful boost. Players get more energy per natural recharge cycle AND more value per coin refill. However, it does NOT change the regeneration rate (still 1/2min), so time-gating remains intact. The impact is strongest for players who play in burst sessions.

**Risk level:** Moderate. Monitor session lengths and coin refill frequency in A/B test.

### 20% Container Recharge Cost Discount

| Container | Base Recharge Cost | After 20% Discount | Savings |
|-----------|-------------------|--------------------|---------|
| Cleaning Set T5 | 18 coins | 14 coins | 4 coins |
| Cleaning Set T10 | 40 coins | 32 coins | 8 coins |
| Kitchen Cabinet T8 | 36 coins | 29 coins | 7 coins |

**Analysis:** At base recharge costs, savings are modest (4-8 coins per recharge). At escalated costs (after multiple recharges), savings compound:
- T10 max escalated cost: 600 coins → 480 coins (120 coins saved)
- Over a typical 4-day Merge Fever cycle with heavy recharging, estimated savings: 200-400 coins total

**Risk level:** Low. Savings are proportional and don't break any ceiling.

### +2 Container Recharge Amount

| Container | Base Recharge Cap | After +2 | % Increase |
|-----------|------------------|----------|------------|
| Cleaning Set T5 | 24 items | 26 items | +8.3% |
| Cleaning Set T10 | 39 items | 41 items | +5.1% |
| Kitchen Cabinet T8 | 27 items | 29 items | +7.4% |

**Analysis:** +2 items per manual recharge is a small but consistent quality-of-life improvement. At 18-40 coins per recharge, getting 2 extra items means ~5-8% more production efficiency per coin spent on recharges.

**Risk level:** Very low. Negligible economy impact.

---

## Combined Economy Impact Summary

| Source | Daily Value | Weekly Value | Monthly Value | % of Merge Fever Income |
|--------|-----------|-------------|---------------|------------------------|
| Daily gold | 85 coins | 595 coins | 2,550 coins | 1.8% |
| Daily energy | 57 energy | 399 energy | 1,710 energy | N/A (different currency) |
| Weekly chests | ~80 coins/day | 560 coins | 2,400 coins | 1.7% |
| Recharge savings | ~50-100 coins/day | 350-700 coins | 1,500-3,000 coins | 1.1-2.1% |
| **Total coin equivalent** | ~215-265 coins/day | ~1,505-1,855/week | ~6,450-7,950/month | ~4.6-5.6% |

**Verdict:** The Neighbors system adds approximately **5% to a player's total coin income** when fully unlocked. This is deliberately conservative — enough to feel rewarding but not enough to undermine existing monetization or disrupt the five cascading progression gates.

---

## Seasonal IAP Fallback Value Analysis

| Tier | Price | Neighbor Value (daily over 30 days) | Sweetener | Total 30-Day Value | Value Ratio |
|------|-------|-------------------------------------|-----------|-------------------|-------------|
| Common | $2.99 | ~$0.60-1.20 | 50E + 100G = $0.26 | ~$0.86-1.46 | 0.3-0.5x |
| Rare | $4.99 | ~$1.50-2.50 | 100E + 250G = $0.58 | ~$2.08-3.08 | 0.4-0.6x |
| Epic | $9.99 | ~$3.00-5.00 | 200E + 500G + TS = $1.16 | ~$4.16-6.16 | 0.4-0.6x |

**Note:** Value ratio is intentionally <1x in pure economy terms because the primary value proposition is **permanent collection progress + FOMO avoidance**, not raw resource efficiency. Players buy to complete their collection, not to min-max gold income.

---

## Captain Rex Daily Item Rotation

| Day | Item | Quantity | Estimated Value |
|-----|------|----------|----------------|
| Monday | Time Skipper L1 (203_01) | 1 | ~$0.03 |
| Tuesday | Merge Stone L1 (201_01) | 1 | ~$0.05 |
| Wednesday | Chain Breaker L1 (202_01) | 1 | ~$0.03 |
| Thursday | Energy L2 (4_02) | 1 (6 energy) | ~$0.02 |
| Friday | Time Skipper L1 | 1 | ~$0.03 |
| Saturday | Merge Stone L1 | 1 | ~$0.05 |
| Sunday | Gold L2 (5_02) | 1 (15 coins) | ~$0.015 |

## Cupid Daily Booster Rotation

| Day | Item | Quantity |
|-----|------|----------|
| Mon/Wed/Fri/Sun | Time Skipper L1 (203_01) | 1 |
| Tue/Thu/Sat | Merge Stone L1 (201_01) | 1 |
