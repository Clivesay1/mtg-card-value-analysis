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

## Model Evaluation — April 29, 2026
Current model metrics on holdout set: RMSE: $4.21, MAE: $2.87, R²: 0.68. The model handles mid-range cards ($1-$20) well but underestimates reserved list cards. Adding a reserved list flag as a hard override.

## Price Trend Observation — April 30, 2026
Revisiting the relationship between set rotation and price spikes. Cards that see sudden spikes in EDHREC rank (Commander demand) often precede price increases by 2-4 weeks. Building a lag-feature to capture this signal.

## Keyword Synergy Scoring — May 01, 2026
Cards with 3+ keywords that appear together frequently in Commander decks show a 2.1x price premium over single-keyword cards of the same rarity. Building a keyword co-occurrence matrix from EDHREC deck data to capture synergy effects in the scoring model.

## Set Rotation Study — May 02, 2026

Examining how Standard rotation affects card prices. Cards rotating out of Standard drop an average of 62% in value, while cards entering Commander-legal sets see a sustained floor. This confirms that format legality is one of the strongest long-term price drivers in the dataset.


## Value Score Calibration — May 07, 2026
Recalibrating the 0-100 value score scale using the full dataset. Current distribution is right-skewed — most cards score below 30. Applying a log transformation to the price component normalizes the distribution and improves score interpretability.

## 2026-05-08 11:40

Segmented the card dataset by primary type (Creature, Instant, Sorcery, Enchantment, Artifact, Land, Planeswalker). Creatures and Instants show highest price volatility; Lands show lowest.

## 2026-05-10 11:46

Investigated Commander demand as a price driver. EDHREC rank shows a -0.41 Spearman correlation with price — stronger than rarity alone. Adding EDHREC rank as a primary feature in the next model iteration.

## Set Type Price Stratification — May 16, 2026
Comparing average card prices across set types: Masters sets show highest average price ($8.40), followed by Commander precons ($4.20) and Standard sets ($2.10). Masters set reprints cause immediate 40-60% price drops but recover within 18 months for staples.

## Model Validation on Recent Sets — May 19, 2026
Applied the trained model to cards from the last 3 set releases. Predicted vs. actual prices after 90 days: Mean absolute error = $1.83, within acceptable range for a portfolio tool. Model overestimates prices for bulk commons (predicts $0.30, actual $0.10) and underestimates for breakout Commander staples. Adding a post-release demand signal would improve accuracy.

### Update: May 25, 2026

Added foil multiplier analysis by set era. Pre-2015 foils show a 2.3x average premium vs. 1.4x for modern foils. Encoding era as a categorical feature improved model R² by 0.03.

---

## Data Quality Notes

- Scryfall API returns foil and non-foil prices separately — using non-foil as baseline
- Some promo cards have null EDHREC ranks — imputed with median rank by card type
- Set type 'masterpiece' cards excluded from main model (too few, too extreme)
- Double-faced cards counted as single entries using front face attributes

## Buylist vs Market Price Spread — June 19, 2026
The spread between buylist price (what stores pay) and market price (what players pay) averages 45% for bulk, 30% for mid-range, and 15% for high-end staples. Narrow spreads indicate high liquidity and market confidence. Using spread_ratio as a liquidity proxy in the value scoring algorithm.

---
## Model Refinement — June 22, 2026
Adjusted weighting for eternal format legality (Legacy/Vintage) in the value score. Cards legal in older formats command a 15-25% premium over their Modern-only equivalents. Updated coefficient from 0.08 to 0.12 for the format_legality_count feature.
