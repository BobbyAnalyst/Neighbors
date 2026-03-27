# Rollout Plan — Phases, A/B Tests, KPIs & Success Criteria

## Phased Rollout

### Phase 0: Internal QA (2 weeks)

| Activity | Duration | Owner |
|----------|----------|-------|
| Feature build + unit tests | 4-6 weeks (pre-rollout) | Dev team |
| Internal QA testing | 2 weeks | QA team |
| Art asset finalization | Concurrent with build | Art team |
| Economy simulation | 1 week | Game design |

**Exit Criteria:**
- [ ] All 12 neighbor cards display correctly (locked/unlocked states)
- [ ] All unlock conditions trigger correctly
- [ ] Daily and weekly rewards collect and reset properly
- [ ] Permanent boosts apply correctly to energy, recharge cost, recharge amount
- [ ] IAP purchase flow works on Android + iOS test environments
- [ ] IAP fallback timer activates and expires correctly
- [ ] Book tab navigation is smooth on low-end Android devices (target: <500ms load)
- [ ] Counter backfill runs correctly for test accounts with history
- [ ] No P0 or P1 bugs

---

### Phase 1: Soft Launch — F2P Neighbors Only (3 weeks)

**Audience:** 10% of DAU (random, stratified by level and payer status)
**Markets:** Southeast Asia + Africa (Carry1st core markets) — price-sensitive, Android-heavy

**What's included:**
- 6 F2P permanent neighbors only (no seasonal)
- Full unlock conditions, daily rewards, weekly chests
- All permanent boosts active
- Book tab with Neighbors sub-tab
- Counter backfill for existing players

**What's excluded:**
- Seasonal events and seasonal neighbors
- IAP fallback flow

**KPIs to monitor:**

| Metric | Target | Red Flag |
|--------|--------|----------|
| D7 retention (treatment vs control) | +2% lift | <0% (negative retention impact) |
| Daily session count | +0.3 sessions/day | No change |
| Book tab open rate | 30%+ DAU | <15% |
| Avg neighbors unlocked (D7) | 2-3 | <1 (unlock conditions too hard) |
| Avg neighbors unlocked (D21) | 3-5 | <2 |
| Daily reward collection rate | 60%+ of eligible | <30% (players forget) |
| Energy economy impact | <3% change in coin refill frequency | >10% (boosts too strong) |
| Container recharge spend | <5% decrease | >15% decrease (discount too generous) |
| Client performance (Book tab load) | <500ms P95 | >1s P95 |
| Crash rate | No increase | Any increase |

**Decision gate (end of Week 3):**
- **GO:** Retention lift ≥ +1%, no economy red flags, performance stable → proceed to Phase 2
- **ITERATE:** Retention flat but engagement positive → adjust reward numbers, extend Phase 1 by 2 weeks
- **STOP:** Negative retention, economy disruption, or performance issues → diagnose and redesign

---

### Phase 2: Seasonal Integration Test (4-6 weeks)

**Audience:** 25% of DAU (includes Phase 1 cohort)
**Timing:** Align with next seasonal event on the calendar

**What's added:**
- 1-2 seasonal neighbors tied to the upcoming event
- Full IAP fallback flow
- Push notifications (opt-in)
- Event → unlock → IAP offer → expiry pipeline

**KPIs to monitor:**

| Metric | Target | Red Flag |
|--------|--------|----------|
| Event participation rate (treatment vs control) | +10% lift | No change (feature not motivating event play) |
| Event completion rate | Within expected range per rarity | >20% deviation from target |
| IAP fallback conversion (of eligible) | 3-5% | <1% (price too high or value unclear) |
| IAP fallback revenue | $0.05-0.10 ARPDAU lift during window | Negligible |
| FOMO sentiment | Neutral-positive in reviews/support | Negative spike in reviews mentioning "pay wall" |
| Seasonal neighbor daily engagement | Same as F2P neighbors (60%+ collection rate) | Significantly lower (seasonal feels less valuable) |

**Decision gate (end of seasonal event + 2 weeks):**
- **GO:** IAP conversion ≥ 2%, no negative sentiment spike → proceed to Global Launch
- **ITERATE:** Low conversion → adjust pricing or sweetener, test again next season
- **STOP:** Significant backlash → redesign seasonal model

---

### Phase 3: Global Launch (Week 10-12)

**Audience:** 100% of DAU
**Timing:** Coincide with a content update or version bump for maximum visibility

**Includes:**
- All 12 neighbors (6 F2P + 6 seasonal)
- Full IAP flow
- All push notifications
- Counter backfill for all existing players
- App Store / Play Store listing update mentioning "Neighbors" feature
- In-game banner for 7 days post-launch

**Post-launch monitoring (90 days):**

| Metric | 30-Day Target | 90-Day Target |
|--------|--------------|---------------|
| D7 retention lift | +3% | +3-5% (sustained) |
| D30 retention lift | +3% | +5-8% |
| ARPDAU lift | +5% | +8-12% |
| Avg neighbors unlocked | 4-5 | 6-8 |
| Monthly seasonal IAP revenue | — | $2K-5K incremental |
| Book tab DAU penetration | 35% | 40%+ |
| Player sentiment (reviews) | Neutral-positive | Positive mentions of Neighbors feature |

---

## A/B Testing Plan

### Test 1: Boost Magnitude (Phase 1)

| Variant | Max Energy Boost | Recharge Discount | Recharge Amount |
|---------|-----------------|-------------------|-----------------|
| Control | No Neighbors feature | — | — |
| Treatment A (Conservative) | +14 total | 10% | +1 |
| Treatment B (Moderate — default) | +22 total | 20% | +2 |

**Sample size:** 5% per variant, 3 weeks
**Primary metric:** D7 retention
**Secondary:** Coin refill frequency, session length, container recharge spend

### Test 2: Daily Reward Level (Phase 1)

| Variant | Gold/Neighbor/Day | Energy/Neighbor/Day |
|---------|------------------|---------------------|
| Control A (Light) | 5-15 (current plan) | 5-10 |
| Control B (Higher) | 10-30 | 10-20 |

**Primary metric:** Daily reward collection rate, session count
**Hypothesis:** Higher rewards = higher collection rate but may devalue existing economy

### Test 3: IAP Pricing (Phase 2)

| Variant | Common | Rare | Epic |
|---------|--------|------|------|
| Price A (current plan) | $2.99 | $4.99 | $9.99 |
| Price B (lower) | $1.99 | $3.99 | $7.99 |

**Primary metric:** IAP conversion rate × revenue (optimize for total revenue, not just conversion)
**Market note:** Lower prices may convert better in Carry1st's emerging markets

### Test 4: IAP Window Duration (Phase 2)

| Variant | Window |
|---------|--------|
| A (current plan) | 3 days |
| B (shorter) | 24 hours |
| C (longer) | 7 days |

**Primary metric:** Conversion rate
**Hypothesis:** Shorter window = more urgency but higher frustration. 3 days is the hypothesized sweet spot.

---

## Feature Flags

| Flag | Default | Purpose |
|------|---------|---------|
| `neighbors_enabled` | `false` → `true` at launch | Master kill switch |
| `neighbors_seasonal_enabled` | `false` | Enable seasonal neighbors independently |
| `neighbors_iap_enabled` | `false` | Enable IAP fallback independently |
| `neighbors_push_enabled` | `false` | Enable push notifications independently |
| `neighbors_boost_multiplier` | `1.0` | Scale all permanent boosts (0.5 = half, 2.0 = double) |
| `neighbors_daily_multiplier` | `1.0` | Scale all daily rewards |
| `neighbors_rollout_pct` | `0` → `100` | Gradual percentage rollout |

---

## Risk-Gated Rollout

If at any point during rollout:
- Coin economy inflates by >10% → reduce `neighbors_daily_multiplier` to 0.5
- Energy economy disrupted → reduce `neighbors_boost_multiplier` to 0.5
- Crash rate increases → disable `neighbors_enabled` immediately
- Negative review spike → pause rollout, investigate sentiment
