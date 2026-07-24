# Analysis Notes — mtg-card-value-analysis

Ongoing notes and observations from the analysis.

<!-- 2026-06-01 15:43 -->
> Expand notes on edhrec rank as price predictor.


## Update July 07, 2026

- CMC analysis: cards with CMC 2-3 dominate competitive formats; CMC 4+ cards rely on Commander demand
- Promo treatment premium: borderless and full-art versions average 2.4x regular frame prices
- New Bloomburrow set analysis: creature type synergy cards showing early price spikes

## 2026-07-16 15:39

**Update feature importance observations**

Random forest feature importances: rarity (0.31), edhrec_rank (0.24), reserved_list (0.18), legal_formats (0.14), cmc (0.08), other (0.05).

## July 19, 2026
**Keyword analysis update:** Cards with 'Ward', 'Cascade', or 'Companion' keywords show above-average price retention. Mechanic complexity correlates positively with Commander playability. Added keyword_complexity_score as a derived feature — counts high-value keywords per card.

## July 24, 2026
**Set type analysis:** Supplemental products (Commander precons, Secret Lairs) introduce new cards at artificially high initial prices. Tracking 90-day post-release price trajectories — most supplemental cards settle 20-40% below release price. Filtering supplemental-only printings from baseline price analysis.
