# Peer-to-Peer Lending Default Prediction

Project 2 for [FIN410-001], NJIT.
Author: Kendrick Moreira

## Project summary

This project predicts whether a peer-to-peer (P2P) loan will default (Charged Off) or be fully paid (Fully Paid), using only information that is available when the loan application is submitted. A model like this could support a lender's approve or deny decision.

**Goal:** predict loan default from application-time information.

**Success metrics:**
- AUC-ROC, compared against a logistic regression baseline
- Precision and recall on the default class, since missed defaults are costly for lenders

## Data

- **Source:** Lending Club quarterly loan data, Q1 2016 to Q2 2020, merged into one dataset
- **Access:** Mendeley Data, DOI [10.17632/mvvd3dnfyz.1](https://data.mendeley.com/datasets/mvvd3dnfyz/1)
- **Location in repo:** `data/raw/` (not committed; see setup below)

Columns that are only known after a loan ends (for example, total payments or recoveries) are excluded from the model to avoid data leakage.

## Repository layout

```
p2p-lending-project2/
├── README.md
├── requirements.txt
├── .gitignore
├── data/
│   ├── raw/          # downloaded data (not committed)
│   └── processed/    # cleaned data (not committed)
├── src/              # cleaning, modeling, and evaluation code
├── results/          # saved metrics and charts
├── prompt_log.md     # AI agent prompt log
└── report/           # short report and final slides
```

## Setup

Requires Python 3.10 or newer.

```bash
git clone https://github.com/<MuffinMan132>/p2p-lending-project2.git
cd p2p-lending-project2
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

## Getting the data

1. Go to https://data.mendeley.com/datasets/mvvd3dnfyz/1
2. Download the dataset.
3. Unzip it and place the CSV file(s) in `data/raw/`.

## Running the project

Run these steps in order:

```bash
python src/clean.py       # clean raw data and remove leakage columns
python src/baseline.py    # logistic regression baseline
python src/model.py       # second model and comparison
```

Results are saved to `results/`.

*Note: the scripts above are planned. This section will be updated as each script is added.*

## Reproducing results

The results should reproduce from a fresh clone by following the setup and run steps above. Random seeds are fixed in the code so that repeated runs produce the same numbers.

## AI agent use

This project was built with an AI coding agent (Claude Code). The full prompt log is in `prompt_log.md`.

## License

For course use only.
