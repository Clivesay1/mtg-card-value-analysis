# Data Notes

## Included Snapshot

`mtg_cards_raw.csv` is the project snapshot used by the consolidated analysis notebook. It contains **2,139 records** (plus the header row) exported from the Scryfall API. The project notebook identifies the source snapshot as **April 2025**.

Market-price fields should be interpreted as an observed snapshot rather than a historical price series. Prices, legality, and EDHREC-related fields may have changed since collection.

## Reproducing the Analysis

1. Create a virtual environment and install the packages in the repository root with `pip install -r requirements.txt`.
2. Launch `jupyter notebook notebooks/mtg_value_scoring_model.ipynb` from the repository root.
3. Run cells in order. The notebook reads the committed CSV snapshot and writes derived outputs to `output/`.

## Source

The raw card attributes and price fields originate from the [Scryfall API](https://scryfall.com/docs/api). Any future refresh should record the retrieval date, API endpoint, and any field-mapping changes before replacing the committed snapshot.
