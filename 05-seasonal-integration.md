# Seasonal Integration — Event Calendar, IAP Fallback & FOMO Mechanics

## Seasonal Event Calendar

### Year 1 Launch Schedule

| Month | Event | Neighbor | Rarity | IAP Price |
|-------|-------|----------|--------|-----------|
| January | Winter Holiday | Nikolai | Epic | $9.99 |
| February | Valentine's Day | Cupid | Rare | $4.99 |
| April | Spring Festival | Aurora | Epic | $9.99 |
| July | Independence Day | Sparky | Common | $2.99 |
| October | Halloween | Jack O'Lantern | Rare | $4.99 |
| December | Christmas | Holly | Common | $2.99 |

**Cadence:** 6 seasonal events per year = 1 new neighbor opportunity every 2 months on average.

### Concurrent Event Compatibility

Seasonal neighbor events run **alongside** existing events:
- Merge Fever continues its 96h cycle uninterrupted
- Daily Tasks and Star Cup continue as normal
- Seasonal event occupies its own UI space (banner + event screen)
- **No conflicts** with Merge League or Gift Rush scheduling — seasonal events should avoid overlapping with these to prevent attention split

---

## Seasonal Event Flow

### Pre-Event (3-7 days before)

1. **Teaser in Neighbors screen:** Locked neighbor silhouette gets a "Coming Soon" badge with countdown
2. **Push notification (opt-in):** "A new neighbor is moving in! [Event Name] starts in 3 days"
3. **Book tab badge:** Pulsing indicator on the Neighbors sub-tab

### During Event (Event Duration: 3-7 days, varies by event)

1. **Event screen:** Standard seasonal event UI with milestones/tasks
2. **Neighbor preview:** Full character portrait visible in event screen with "Complete to unlock!" label
3. **Progress tracking:** Book tab shows event completion progress on the neighbor's card
4. **Event mechanics:** Each seasonal event defines its own gameplay (e.g., collect themed items, complete special orders)

### Event Completion

**If player completes the event:**
1. Immediate unlock celebration (full-screen animation)
2. Neighbor moves to "Unlocked" state in Book tab
3. First daily reward available immediately
4. Permanent boosts activate instantly (if Rare/Epic)

**If player does NOT complete the event (Common/Rare unlock requirement):**
→ See IAP Fallback Flow below

**If player does NOT complete ALL milestones (Epic unlock requirement):**
- Partial completion does not count
- Must complete every milestone to unlock Epic seasonal neighbors
- IAP Fallback Flow activates

---

## IAP Fallback Flow (Miss → Buy → Wait)

### Timeline

```
Event Ends
    │
    ├── Hour 0: Event results screen shows
    │   └── If NOT unlocked: "You missed [Neighbor]!"
    │
    ├── Hour 1: IAP Offer Pop-up
    │   ├── Full neighbor portrait + reward preview
    │   ├── "Get [Neighbor] now!" CTA
    │   ├── Price + sweetener bundle displayed
    │   ├── 3-day countdown timer
    │   └── "Or earn them next [Month] during [Event Name]"
    │
    ├── Day 1-3: Offer persists
    │   ├── Book tab shows "Limited Offer!" badge on neighbor
    │   ├── Reminder push notification on Day 2 (opt-in)
    │   └── "Last chance!" banner on Day 3
    │
    └── Day 4: Offer expires
        ├── Neighbor card shows "Returns [Month Year]"
        ├── Silhouette remains visible in collection
        └── No purchase option until next year
```

### IAP Bundle Contents

| Rarity | Price | Neighbor | Energy | Gold | Bonus Item | Total IAP Value |
|--------|-------|----------|--------|------|------------|----------------|
| Common | $2.99 | Yes | 50 | 100 | — | Neighbor + $0.26 resources |
| Rare | $4.99 | Yes | 100 | 250 | — | Neighbor + $0.58 resources |
| Epic | $9.99 | Yes | 200 | 500 | Time Skipper L2 | Neighbor + $1.16 resources |

### IAP SKU Naming Convention

```
com.mergedom.neighbor.sparky.fallback       // $2.99
com.mergedom.neighbor.holly.fallback        // $2.99
com.mergedom.neighbor.cupid.fallback        // $4.99
com.mergedom.neighbor.jack.fallback         // $4.99
com.mergedom.neighbor.aurora.fallback       // $9.99
com.mergedom.neighbor.nikolai.fallback      // $9.99
```

---

## FOMO Mechanics

### Why This Works

1. **Scarcity:** 3-day window is short enough to create urgency
2. **Loss aversion:** Player can see the locked silhouette in their collection permanently — visible incomplete collection
3. **Annual return:** "Next year" is long enough to feel painful but fair enough to avoid backlash
4. **Social proof:** If leaderboards or friend lists show neighbor counts, players see others who have more
5. **Stacking pressure:** Each missed season = another gap in the collection, compounding FOMO

### Anti-Backlash Guardrails

| Concern | Mitigation |
|---------|-----------|
| "Pay to win" perception | Seasonal neighbors have the same reward tiers as F2P neighbors. No exclusive boost types |
| "Unfair to new players" | New players who join mid-year can earn F2P neighbors immediately. Seasonal ones return annually |
| "Too expensive" | $2.99-$9.99 is accessible, especially with energy/gold sweetener. No $19.99+ neighbors |
| "Forced to pay" | Annual return gives a guaranteed free path. IAP is acceleration, not exclusivity |
| "Collection is impossible" | 6 F2P neighbors are always available. A 50% collection is achievable by any player |

---

## Seasonal Event Design Requirements

Each seasonal event needs:

| Component | Description |
|-----------|------------|
| **Event mechanic** | Unique gameplay (collect themed items, complete themed orders, etc.) |
| **Milestone track** | 10-15 milestones with standard rewards + neighbor unlock as final milestone |
| **Epic milestone track** | Extended track (20-25 milestones) for Epic seasonal neighbors |
| **Event duration** | 3-5 days for Common/Rare events, 5-7 days for Epic events |
| **Themed visuals** | Event banner, themed items on merge board, celebration effects |
| **Difficulty tuning** | Common event: ~80% of active players should complete. Rare: ~50%. Epic: ~25% |

### Completion Rate Targets

| Rarity | Target Completion Rate | Design Implication |
|--------|----------------------|-------------------|
| Common | 75-85% of active players | Easy event, most players unlock for free |
| Rare | 45-55% of active players | Moderate challenge, meaningful IAP conversion from the other 45-55% |
| Epic | 20-30% of active players | Hard event, high FOMO, strong IAP conversion expected |

---

## Annual Returning Event Protocol

When a seasonal event returns the following year:

1. **Players who already have the neighbor:** Event still runs but neighbor reward is replaced with a bonus chest (Epic Neighbor Chest equivalent)
2. **Players who don't have the neighbor:** Same unlock opportunity as first year
3. **IAP fallback:** Same 3-day window, same price
4. **Event refreshes:** Consider updating the event mechanic or milestones slightly to keep it fresh for returning players
5. **New seasonal neighbor potential:** Future years could add a SECOND neighbor to the same event (e.g., Halloween Year 2 adds a new Rare neighbor alongside Jack)
