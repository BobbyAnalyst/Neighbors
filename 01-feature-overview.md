# PRD: Neighbors — Collection & Passive Rewards System

**Author:** Bobby
**Date:** 2026-03-26
**Status:** Draft
**Priority:** P1 (High)

---

## 1. Overview

### Problem Statement

Mergedom acquires well — 15M+ downloads, 450K/month, 4.6★ rating — but converts poorly. At ~$70K/month US revenue, it sits **1,600x below the genre leader** (Gossip Harbor, ~$677M lifetime). The gap isn't acquisition; it's what happens after onboarding:

1. **Finite endgame.** The core loop (merge → orders → stars → rooms) terminates at ~4,432 stars across 27 rooms. No parallel progression exists to keep veterans engaged once rooms run dry.
2. **No collectible layer.** Gossip Harbor, Travel Town, and Seaside Escape all have character/narrative systems that sustain long-term play. Mergedom has zero — no characters to collect, no personalities to invest in, no social hooks.
3. **Content drought is the #3 player complaint.** Players love the merge loop but run out of reasons to return. New rooms are expensive to produce; the game needs a content vector that scales without requiring new environments.

The result: strong top-of-funnel, weak mid-to-late-game retention and monetization. Neighbors directly attacks this gap.

### Opportunity

| Lever | What Neighbors Delivers | Why It Matters |
|-------|------------------------|----------------|
| **Retention** | Daily collectible rewards + weekly chests create a tap-to-collect ritual | Adds a daily pull beyond energy regen — targets the D7→D30 retention drop-off |
| **Monetization** | 6 seasonal neighbors/year with 3-day IAP fallback ($2.99–$9.99) | New revenue stream at Carry1st-friendly price points; every seasonal neighbor is also earnable free the next year, protecting F2P trust |
| **Differentiation** | First character collection system in a merge-2 game | Competitors have narrative but not collectible character rosters with stacking passive boosts |
| **Content velocity** | Each seasonal event auto-generates a new neighbor | Scales the content pipeline without building new rooms — 6 new neighbors/year at minimal marginal cost |
| **Veteran engagement** | Unlock conditions tied to event mastery, economy milestones, meta progression | Gives endgame players a reason to re-engage with events and push past the room ceiling |

### Target Audience

| Segment | Why They Care | What They Get |
|---------|--------------|---------------|
| **Mid-game** (L10-20) | Hit the first real energy wall; need power progression beyond rooms | Permanent boosts (+max energy, recharge discounts) that compound as they collect |
| **Endgame veterans** (L25+, 15+ rooms) | Running out of rooms; nothing to chase | Collection completionism + weekly chests + daily income — an evergreen goal layer |
| **Light spenders** ($2.99–$9.99) | Want value, not whale packs | Seasonal IAP bundles with immediate tangible rewards at Carry1st-friendly price points |
| **F2P players** | Need to feel progression is possible without paying | 6 permanently earnable neighbors — half the roster — with real gameplay impact |
| **Event grinders** | Repeated event play currently has no cumulative payoff | Event mastery unlocks (win Merge League 3x, etc.) turn grind into permanent collection progress |

---

## 2. Success Metrics

| Metric | Current Baseline | Target (90 days post-launch) | Measurement |
|--------|-----------------|------------------------------|-------------|
| D7 Retention | Baseline TBD | +3-5% lift | Firebase/Adjust cohort analysis |
| D30 Retention | Baseline TBD | +5-8% lift | Firebase/Adjust cohort analysis |
| Daily Session Count | Baseline TBD | +0.5 sessions/day (driven by daily reward collection) | Average sessions per DAU |
| Event Participation Rate | Baseline TBD | +10-15% lift (players pursuing neighbor unlocks) | Event completion tracking |
| Seasonal IAP Conversion | N/A (new) | 3-5% of eligible players purchase fallback | IAP transaction tracking |
| ARPDAU | Baseline TBD | +8-12% lift (seasonal IAP + increased engagement) | Revenue / DAU |
| Neighbor Collection Rate | N/A (new) | Avg 4-5 neighbors unlocked at D30 | Server-side collection state |
| Book Tab Open Rate | Baseline TBD | 40%+ DAU visit Neighbors tab daily | UI event tracking |

---

## 3. User Stories

- As a **mid-game F2P player**, I want to unlock neighbors by hitting milestones so that I feel rewarded for my progress and get useful daily bonuses.
- As a **veteran player**, I want to collect all neighbors so that I have long-term goals beyond room completion and maximize my permanent boosts.
- As a **light spender**, I want to purchase seasonal neighbors I missed so that I don't lose out on collection progress and unique rewards.
- As an **event-focused player**, I want my repeated event wins to count toward something permanent so that engaging with events feels rewarding beyond the event itself.
- As a **daily player**, I want to tap my neighborhood each day to collect energy, gold, and items so that I have a satisfying daily ritual.

---

## 4. Feature Summary

The Neighbors system is a **character collection** housed in the Book tab. Players unlock named NPC neighbors through gameplay achievements, event mastery, meta progression, and seasonal events. Each neighbor provides a combination of:

1. **Permanent passive boosts** — max energy increases, container recharge discounts, recharge amount bonuses (always active, no interaction needed)
2. **Daily collectible rewards** — energy, gold, or rotating free items (tap to collect in the Neighbors screen)
3. **Weekly chests** — per-neighbor chests from Rare and Epic neighbors (tap to collect)

The roster launches with **12 neighbors** across 3 rarity tiers (Common/Rare/Epic), split evenly between **6 permanently earnable F2P neighbors** and **6 seasonal/limited-time neighbors** with a 3-day IAP fallback window after the event ends.

See individual spec documents (02-09) for detailed mechanics, economy, and rollout.
