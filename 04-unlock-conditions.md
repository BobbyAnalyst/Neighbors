# Unlock Conditions Matrix

## Overview

Neighbors unlock through **progressive difficulty tiers** using a mix of achievement-based, event mastery, meta progression, and economy milestones. Seasonal neighbors additionally require completing their tied seasonal event OR purchasing the IAP fallback.

---

## F2P Permanent Unlock Matrix

| # | Neighbor | Rarity | Condition Type | Unlock Requirement | Est. Time to Unlock | Level Gate |
|---|----------|--------|---------------|-------------------|---------------------|-----------|
| 1 | Marta the Baker | Common | Achievement | Complete 50 customer orders | ~3-5 days | Level 3+ |
| 2 | Felix the Handyman | Common | Achievement | Merge 500 items (lifetime) | ~5-7 days | Level 4+ |
| 3 | Professor Otto | Rare | Meta Progression | Complete Room 10 | ~4-8 weeks | Level 12+ |
| 4 | Rosa the Gardener | Rare | Event Mastery | Win Merge League 3 times | ~3-9 weeks (calendar) | Level 5+ |
| 5 | Grandma Elise | Epic | Meta + Level | Complete 15 rooms AND reach Level 25 | ~3-6 months | Level 25 |
| 6 | Captain Rex | Epic | Economy + Achievement | Spend 100,000 coins lifetime AND complete 200 orders | ~2-4 months | Level 15+ |

## Seasonal Unlock Matrix

| # | Neighbor | Rarity | Event | Unlock Requirement | IAP Fallback | Fallback Window |
|---|----------|--------|-------|-------------------|-------------|-----------------|
| 7 | Sparky | Common | Independence Day (July) | Complete the event | $2.99 + 50E + 100G | 3 days post-event |
| 8 | Holly | Common | Christmas (Dec) | Complete the event | $2.99 + 50E + 100G | 3 days post-event |
| 9 | Cupid | Rare | Valentine's Day (Feb) | Complete the event | $4.99 + 100E + 250G | 3 days post-event |
| 10 | Jack O'Lantern | Rare | Halloween (Oct) | Complete the event | $4.99 + 100E + 250G | 3 days post-event |
| 11 | Aurora | Epic | Spring Festival (Apr) | Complete ALL milestones | $9.99 + 200E + 500G + TS L2 | 3 days post-event |
| 12 | Nikolai | Epic | Winter Holiday (Jan) | Complete ALL milestones | $9.99 + 200E + 500G + TS L2 | 3 days post-event |

---

## Unlock Progression Timeline (Typical F2P Player)

```
Week 1-2:     Marta (50 orders) → Felix (500 merges)
              ├── Player learns the Neighbors system with 2 Commons
              └── Daily income: 10 gold + 8 energy

Week 3-9:     Rosa (win Merge League 3x, calendar-dependent)
              ├── First Rare unlock, first permanent boost (5% recharge discount)
              └── First weekly chest

Week 4-8:     Professor Otto (complete Room 10)
              ├── First max energy boost (+4)
              └── Second weekly chest

Month 2-4:    Captain Rex (100K coins + 200 orders)
              ├── First Epic unlock, daily item rotation
              └── Major permanent boosts (+4 max energy, 5% recharge discount)

Month 3-6:    Grandma Elise (15 rooms + Level 25)
              ├── Hardest F2P unlock, biggest rewards
              └── +6 max energy, +1 recharge amount, Epic weekly chest
```

---

## Tracking Requirements

### Achievement Counters (Server-Side)

| Counter | Description | Persistence |
|---------|------------|-------------|
| `total_orders_completed` | Lifetime customer orders completed | Permanent |
| `total_items_merged` | Lifetime merge actions | Permanent |
| `total_coins_spent` | Lifetime coins spent on any sink | Permanent |
| `rooms_completed` | Count of fully decorated rooms | Permanent |
| `player_level` | Current XP level | Permanent |
| `merge_league_wins` | Times player finished in winning position | Permanent |

### Seasonal Event Flags

| Flag | Description | Persistence |
|------|------------|-------------|
| `event_{event_id}_completed` | Player completed the seasonal event | Permanent |
| `event_{event_id}_all_milestones` | Player completed ALL milestones (Epic requirement) | Permanent |
| `neighbor_{id}_iap_offered` | IAP fallback window active | 3-day TTL |
| `neighbor_{id}_iap_purchased` | Player purchased the IAP fallback | Permanent |

---

## Unlock Notification Flow

1. **Progress tracking:** Book tab shows progress bars for locked neighbors (e.g., "Orders: 37/50")
2. **Near-completion nudge:** At 80% progress, show a subtle notification: "Almost there! 5 more orders to unlock Marta"
3. **Unlock moment:** Full-screen celebration animation with neighbor portrait reveal
4. **First reward:** Immediate first daily reward available after unlock
5. **Seasonal IAP:** Pop-up offer appears 1 hour after event ends, persists for 3 days with countdown timer

---

## Edge Cases

| Scenario | Resolution |
|----------|-----------|
| Player reaches unlock condition during offline play | Unlock triggers on next app open, rewards retroactively available |
| Player buys seasonal IAP but also completes the event | IAP is not offered if event was completed. If purchased before event completion, no refund (they already have the neighbor) |
| Player uninstalls and reinstalls | Server-side state preserves all unlocks and counters (requires account linking) |
| Counter reaches threshold during event that also has a seasonal neighbor | Both unlock simultaneously if conditions met. Celebrate both |
| Merge League "win" definition | Top 3 in league tier. Defined by existing Merge League leaderboard logic |
