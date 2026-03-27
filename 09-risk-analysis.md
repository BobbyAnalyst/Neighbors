# Risk Analysis

## Risk Matrix

| # | Risk | Likelihood | Impact | Category | Mitigation |
|---|------|-----------|--------|----------|------------|
| 1 | Permanent boosts disrupt energy economy balance | Medium | High | Economy | A/B test conservative vs moderate boost values. Feature flag `neighbors_boost_multiplier` allows live tuning. Monitor coin refill frequency and session length deltas. Cap total boosts server-side regardless of future neighbor additions |
| 2 | Seasonal FOMO generates player backlash ("pay to win") | Medium | High | Sentiment | Ensure seasonal neighbors have identical reward types (not exclusive ones) to F2P neighbors. Annual return guarantee. Half the roster is permanently F2P. Accessible price points ($2.99-$9.99). Monitor app store reviews and support tickets weekly |
| 3 | Art production bottleneck delays launch | High | Medium | Production | 12 character portraits + icons + silhouettes = significant art workload. Prioritize F2P neighbors first (Phase 1). Seasonal art can follow on Phase 2 timeline. Consider outsourcing portrait art if internal team is capacity-constrained |
| 4 | Counter backfill for existing players creates mass instant-unlocks, devaluing the collection | Medium | Medium | Design | Expected behavior — veterans SHOULD unlock 3-5 neighbors instantly. This rewards loyalty. Include a "Welcome to the Neighborhood" bonus chest to celebrate. The long-tail chase (Epic neighbors, seasonal collection) sustains engagement |
| 5 | Players don't return to Book tab daily to collect rewards | Medium | Medium | Engagement | Push notifications (opt-in) for daily rewards. Badge indicator on Book tab. Rewards are light but consistent — low friction to collect. NO "collect all" button (each tap is a micro-engagement). Consider A/B testing a pop-up reminder on main screen |
| 6 | Container recharge discount makes containers too easy to sustain | Low | Medium | Economy | 20% discount on base costs is modest (saving 4-8 coins per recharge). Escalation modifier still applies on the discounted base. Monitor container recharge frequency in A/B test. Feature flag allows instant adjustment |
| 7 | Seasonal events are complex to build and maintain | Medium | Medium | Engineering | Design seasonal event framework with reusable components. First 1-2 seasonal events require full build; subsequent ones should leverage the framework. Template: milestone track + themed items + neighbor unlock trigger |
| 8 | IAP fallback conversion is too low to justify the feature complexity | Medium | Low | Revenue | The feature's primary value is retention, not direct revenue. IAP is a bonus. If conversion is <1%, consider lowering prices or extending the window. The FOMO model's value is primarily in driving event participation, not IAP sales |
| 9 | Low-end Android performance issues | Low | High | Technical | Lazy-load portraits, compress textures, simplify animations on low-tier devices. Test on Carry1st's target device list (budget Android phones). Book tab is static content — should be lighter than merge board |
| 10 | Players expect neighbor interaction/social features beyond collection | Low | Low | Expectations | PRD scope is collection + rewards only. No chat, no visiting, no co-op. If demand emerges, consider Phase 2 social expansion (neighbor gifting, neighbor challenges). Keep initial scope tight |

---

## Economy Risk Deep Dive

### Scenario: Player Unlocks All 12 Neighbors

**Daily income increase:**
- +85 gold/day (+1.8% vs Merge Fever baseline)
- +57 energy/day (equivalent to ~2.3 extra RV watches)
- +2 free items/day

**Weekly income increase:**
- +560 gold from chests (~80/day)
- +12 boosters (Time Skippers, Merge Stones)

**Permanent boost impact:**
- +22 max energy → ~15-25% more energy capacity
- 20% recharge discount → ~200-400 coins saved per Merge Fever cycle
- +2 recharge amount → ~5-8% more production efficiency

**Total monthly economy impact:** ~5-6% increase in total resource income. This is within safe bounds — the five cascading progression gates remain intact:
1. Energy depletion → Still happens, just delayed by 22 taps
2. Container depletion → Still happens, slightly cheaper to recharge
3. Board space → Unchanged
4. Item scarcity → Unchanged
5. Star + Coin costs → Unchanged (coin income increase is marginal)

**Verdict:** Economy impact is carefully contained. The feature improves quality of life without removing any progression gates.

---

## Competitive Risk Assessment

| Competitor | Collection Feature? | Risk to Mergedom |
|------------|-------------------|-----------------|
| Gossip Harbor | Character-driven story progression | Different model — Mergedom's collection is additive, not story-gated |
| Travel Town | No collection system | Mergedom gains differentiation advantage |
| Seaside Escape | Limited collectibles | Mergedom's deeper system could be a competitive edge |
| Merge Mansion | Story characters but no collection rewards | Mergedom's rewards-based model is more gameplay-integrated |

**Conclusion:** No major competitor has a collection system with passive permanent boosts. This positions Mergedom as an innovator in the merge-2 genre for this feature type.

---

## Worst-Case Scenarios

### Scenario A: Economy Disruption
- **Trigger:** A/B test shows >10% coin inflation or >15% decrease in container recharge spend
- **Response:** Set `neighbors_boost_multiplier` to 0.5 immediately. Halves all permanent boosts. Analyze which specific boost is causing the disruption. Adjust individual neighbor rewards and re-test

### Scenario B: Negative Sentiment Spike
- **Trigger:** App store rating drops by 0.1+ points, or >5% of new reviews mention "pay wall" or "unfair"
- **Response:** Pause seasonal IAP rollout. Post community update explaining the annual return guarantee. Consider making one seasonal neighbor permanently earnable (convert to F2P). Adjust pricing downward

### Scenario C: Low Engagement
- **Trigger:** <15% Book tab open rate after 2 weeks, <30% daily reward collection rate
- **Response:** Add main screen pop-up reminder for uncollected rewards. Increase daily reward amounts (set `neighbors_daily_multiplier` to 1.5). Add a "streak bonus" for consecutive daily collections. Consider animated visitor on merge board (rejected in planning but viable as engagement rescue)

### Scenario D: Art Production Delay
- **Trigger:** Character art not ready for planned launch
- **Response:** Launch with placeholder art (stylized silhouettes with rarity borders). Replace with final art in hot-fix update. This is the least risky scenario — players will engage with the mechanic even with placeholder art

---

## Open Questions

- [ ] **Max energy base value:** What is the current fixed max energy capacity? Needed to calculate the exact % impact of +22 bonus. (Check balancing spreadsheet or client code)
- [ ] **Merge League "win" definition:** Is it top 1, top 3, or completing the event? Needed for Rosa's unlock condition
- [ ] **Seasonal event calendar:** Are there existing seasonal events planned, or does the Neighbors feature require building new seasonal events from scratch?
- [ ] **Book tab Chests removal:** Confirm with design team that removing the Chests sub-tab is acceptable. Alternative: add Neighbors as a 5th sub-tab
- [ ] **Offline reward collection:** Can rewards be collected offline and synced later, or must they require server validation? (Impacts offline play, which is a Mergedom differentiator)
- [ ] **Team/social integration:** Should neighbor count be visible on leaderboards or team profiles? Would create social proof pressure for collection
