# MTG Card Value Scoring Model

**Can data predict which Magic: The Gathering cards will rise in value?**

This project builds a composite **Value Score (0–100)** using real card attribute data from the Scryfall API to identify newly released MTG cards likely to appreciate in price — before the market catches on.

## Key Results
- **Random Forest model** achieves R² = 0.796 predicting card prices from attributes alone
- **Value Score algorithm** correlates r = 0.34 with actual market prices (strong for attribute-only prediction)
- **Top predictors:** EDHREC rank, Modern legality, rarity, reserved list status, game changer designation
- **1,904 cards** analyzed with real TCGPlayer pricing from Scryfall API

## Research Questions
1. Which card attributes most strongly correlate with high market prices?
2. How much does format legality, EDHREC demand, and rarity each contribute to value?
3. Can a machine learning model predict card prices from attributes alone?
4. Does the resulting Value Score validate against actual market prices?

## Tech Stack
| Tool | Purpose |
|---|---|
| Python 3.11 | Core analysis |
| pandas | Data manipulation |
| scikit-learn | Random Forest regression |
| matplotlib / seaborn | Visualizations |
| Scryfall API | Real card data + pricing |

## Project Structure
```
mtg-card-value-analysis/
├── data/
│   └── mtg_cards_raw.csv          # 1,904 real cards from Scryfall API
├── notebooks/
│   └── mtg_value_scoring_model.ipynb  # Full analysis notebook
├── images/
│   ├── 01_price_by_rarity.png
│   ├── 03_edhrec_vs_price.png
│   ├── 07_feature_importance.png
│   ├── 08_value_score_validation.png
│   └── 09_top20_value_score.png
├── output/
│   ├── cards_with_value_scores.csv    # All cards with computed scores
│   └── top20_value_cards.csv
└── README.md
```

## How to Run
```bash
git clone https://github.com/Clivesay1/mtg-card-value-analysis
cd mtg-card-value-analysis
pip install pandas scikit-learn matplotlib seaborn requests nbformat
jupyter notebook notebooks/mtg_value_scoring_model.ipynb
```

## Key Findings

| Driver | Score Weight | Finding |
|---|---|---|
| Rarity | 25 pts | Mythic rares have 8–12x higher median prices than rares |
| EDHREC Demand | 20 pts | Top-500 Commander cards command 3–5x price premium |
| Format Legality | 20 pts | Modern-legal cards are 4x more valuable than non-Modern |
| Reserved List | 10 pts | Cannot be reprinted — permanent scarcity signal |
| Game Changer | 8 pts | Wizards' official designation signals competitive power |

## Data Source
All data pulled live from the [Scryfall API](https://scryfall.com/docs/api) — the most comprehensive MTG card database, with real-time TCGPlayer pricing.

---
*Author: Chris Livesay | [LinkedIn](https://www.linkedin.com/in/christopher-livesay)*
<!-- 1043 -->
<!-- revision 5071 -->
