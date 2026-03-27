# Technical Specification — Data Model, Server, IAP & State Management

## Data Model

### Neighbor Definition (Server Config — Static)

```json
{
  "neighbor_id": "professor_otto",
  "display_name": "Professor Otto",
  "rarity": "rare",
  "type": "permanent",
  "tagline": "Science is just organized curiosity!",
  "unlock_conditions": [
    { "type": "rooms_completed", "threshold": 10 }
  ],
  "rewards": {
    "daily": { "type": "gold", "amount": 15 },
    "weekly_chest": { "chest_id": "neighbor_chest_rare" },
    "permanent_boosts": [
      { "type": "max_energy", "value": 4 }
    ]
  },
  "art_assets": {
    "portrait": "neighbors/otto_portrait.png",
    "icon": "neighbors/otto_icon.png",
    "silhouette": "neighbors/otto_silhouette.png"
  }
}
```

### Seasonal Neighbor Extension

```json
{
  "neighbor_id": "sparky",
  "type": "seasonal",
  "season": {
    "event_id": "independence_day_2026",
    "month": 7,
    "unlock_requirement": "event_completed",
    "iap_fallback": {
      "sku": "com.mergedom.neighbor.sparky.fallback",
      "price_usd": 2.99,
      "sweetener": { "energy": 50, "gold": 100 },
      "window_hours": 72
    },
    "returns_annually": true
  }
}
```

### Player Neighbor State (Server — Per Player)

```json
{
  "player_id": "abc123",
  "neighbors": {
    "marta": {
      "status": "unlocked",
      "unlocked_at": "2026-04-15T10:30:00Z",
      "daily_last_collected": "2026-04-20T00:00:00Z",
      "weekly_last_collected": null,
      "weekly_next_available": null
    },
    "professor_otto": {
      "status": "locked",
      "progress": {
        "rooms_completed": 7
      }
    },
    "sparky": {
      "status": "locked",
      "iap_fallback_active": false,
      "iap_fallback_expires": null
    }
  },
  "active_boosts": {
    "max_energy_bonus": 0,
    "recharge_discount_pct": 0,
    "recharge_amount_bonus": 0
  }
}
```

---

## Server Requirements

### New Endpoints

| Endpoint | Method | Purpose |
|----------|--------|---------|
| `GET /neighbors` | GET | Return all neighbor definitions + player state |
| `POST /neighbors/{id}/collect-daily` | POST | Collect daily reward, validate eligibility |
| `POST /neighbors/{id}/collect-weekly` | POST | Collect weekly chest, validate eligibility |
| `POST /neighbors/{id}/purchase-fallback` | POST | Process IAP fallback purchase |
| `GET /neighbors/boosts` | GET | Return current active boost totals |

### Existing Endpoint Modifications

| Endpoint | Change |
|----------|--------|
| Energy system | Apply `max_energy_bonus` to max capacity calculation |
| Container recharge | Apply `recharge_discount_pct` to coin recharge cost calculation |
| Container recharge | Apply `recharge_amount_bonus` to recharge capacity |
| Achievement counters | Expose `total_orders`, `total_merges`, `total_coins_spent` for progress tracking |
| Event completion | Trigger neighbor unlock check on event completion |

---

## Boost Application Logic

### Max Energy Bonus

```
effective_max_energy = base_max_energy + active_boosts.max_energy_bonus
```

Applied in:
- Energy bar display (UI)
- Energy regeneration cap check
- Coin refill amount calculation
- Energy overflow protection (energy from rewards can exceed max, but regen stops at max)

### Container Recharge Discount

```
effective_recharge_cost = base_recharge_cost × (1 - active_boosts.recharge_discount_pct / 100)
```

Applied in:
- Coin recharge cost calculation (all containers)
- Escalation still applies on discounted base: `(base × discount) → (base × discount × modifier)`
- Floor: minimum 1 coin per recharge (prevent free recharges at extreme discounts)

### Recharge Amount Bonus

```
effective_recharge_cap = base_recharge_cap + active_boosts.recharge_amount_bonus
```

Applied in:
- Coin recharge result (items spawned)
- RV recharge result (half of effective_recharge_cap)
- Hourglass recharge result (half of effective_recharge_cap)
- Does NOT affect time-based full capacity recharge

---

## IAP Integration

### SKU Registration

| SKU | Price | Platform |
|-----|-------|----------|
| `com.mergedom.neighbor.sparky.fallback` | $2.99 | Android + iOS |
| `com.mergedom.neighbor.holly.fallback` | $2.99 | Android + iOS |
| `com.mergedom.neighbor.cupid.fallback` | $4.99 | Android + iOS |
| `com.mergedom.neighbor.jack.fallback` | $4.99 | Android + iOS |
| `com.mergedom.neighbor.aurora.fallback` | $9.99 | Android + iOS |
| `com.mergedom.neighbor.nikolai.fallback` | $9.99 | Android + iOS |

### Purchase Flow

1. Player taps "Get [Neighbor]" in IAP offer
2. Client sends purchase request to platform (Google Play / App Store)
3. Platform returns receipt
4. Client sends receipt to server for validation
5. Server validates receipt with platform API
6. Server unlocks neighbor + grants sweetener resources
7. Server updates `active_boosts` if applicable
8. Client receives updated state + plays unlock animation
9. Purchase logged for analytics

### Refund Handling

If a player refunds the IAP:
- Neighbor remains unlocked (do NOT revoke — bad player experience)
- Flag account for monitoring (potential abuse)
- If repeated refund pattern: escalate to support

---

## State Management

### Daily Reward Reset
- **Reset time:** Server midnight UTC (aligned with Daily Tasks)
- **Logic:** `daily_last_collected < today_midnight_utc` → reward available
- **Edge case:** If player hasn't opened the app in 3 days, only ONE daily reward is available (no accumulation)

### Weekly Chest Reset
- **Cycle:** 7 days from last collection (rolling, per neighbor)
- **Logic:** `now > weekly_next_available` → chest available
- **Edge case:** If player misses weeks, only ONE chest is available at a time (no accumulation)

### Boost Recalculation
- Recalculate `active_boosts` on:
  - Neighbor unlock
  - App startup
  - Server reconciliation
- Cache the computed values client-side for performance
- Server is authoritative — client values are for display only

---

## Analytics Events

| Event | Payload | Purpose |
|-------|---------|---------|
| `neighbor_unlocked` | `neighbor_id, rarity, method (gameplay/iap), time_to_unlock` | Track unlock rates and paths |
| `neighbor_daily_collected` | `neighbor_id, reward_type, reward_amount` | Track daily engagement |
| `neighbor_weekly_collected` | `neighbor_id, chest_contents` | Track weekly engagement |
| `neighbor_iap_offered` | `neighbor_id, price` | Track IAP funnel |
| `neighbor_iap_purchased` | `neighbor_id, price, sweetener` | Track IAP conversion |
| `neighbor_iap_expired` | `neighbor_id, price` | Track missed conversions |
| `neighbor_tab_opened` | `total_unlocked, total_collectible` | Track tab engagement |
| `neighbor_boost_applied` | `boost_type, total_value` | Track boost accumulation |

---

## Performance Considerations

| Aspect | Approach |
|--------|----------|
| **Memory** | Neighbor portraits lazy-loaded (only visible cards load full art). Silhouettes are low-res |
| **Network** | Neighbor state bundled with existing session sync (no separate API call on every app open) |
| **Storage** | ~2KB per player for neighbor state. Negligible |
| **Battery** | No background timers. Reward availability calculated on-demand when tab is opened |
| **Low-end Android** | Celebration animations have a "lite" variant (fewer particles, simpler effects) based on device tier |
| **Offline** | Player can VIEW neighbors offline. Collection requires server validation (queued if offline, synced on reconnect) |

---

## Migration & Backwards Compatibility

### For Existing Players at Feature Launch

1. **Counter backfill:** Server calculates existing `total_orders`, `total_merges`, `rooms_completed`, `total_coins_spent`, `merge_league_wins` from historical data
2. **Instant unlocks:** Any neighbor whose conditions are already met unlocks immediately on first app open post-update
3. **Welcome flow:** First time opening Book tab after update → brief tutorial overlay explaining Neighbors
4. **Retroactive rewards:** Players who auto-unlock 3+ neighbors on update get a bonus "Welcome to the Neighborhood" chest

### Book Tab Change

- Chests sub-tab removed
- Chest information accessible via long-press on chests on the merge board (tooltip)
- No player data lost — chests themselves are board items, not affected
