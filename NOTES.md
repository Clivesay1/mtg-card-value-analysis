<!-- revision 3548 -->
<!-- update 9281 -->
## Insight — April 19, 2026
Cards with 'Flash' keyword show 18% higher average price than non-Flash cards at same rarity tier. Interaction potential appears to be a significant value driver.

## Keyword Synergy Analysis — April 25, 2026

Exploring whether certain keyword combinations predict higher prices better than individual keywords. Preliminary findings:
- Flash + Instant speed interaction: +22% average price premium
- Haste + ETB effect: +18% premium in aggressive formats
- Draw + Low CMC: strongest predictor in Commander (EDHREC rank correlation: -0.41)

Next step: encode keyword pairs as interaction features in the model and re-run feature importance analysis.

---

### Update: April 26, 2026

## Methodology Notes

The value scoring algorithm uses a weighted combination of price volatility, set rarity distribution, and tournament demand signals. Cards with high EDH Commander demand consistently outperform pure rarity-based predictions.

### Key Observations
- Foil multipliers vary significantly by set era (pre-2015 foils command higher premiums)
- Reserved List cards show price floor behavior not captured by standard regression
- Promo variants require separate treatment in the model
