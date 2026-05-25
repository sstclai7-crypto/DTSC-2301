# Masters Tournament Cut Prediction Model

A machine learning project that predicts which golfers will make the cut at the Masters Tournament using player performance statistics.

## Overview

This project uses 2025 Masters Tournament data to train classification models and applies them to 2026 tournament data to predict cut outcomes. The final model correctly identified 52 of 54 players who made the 2026 cut.

## Dataset

The dataset (`masters_avg_dataset_cleaned.csv`) contains averaged round-by-round statistics for each player, including:

- **Strokes Gained:** Putting (`sg_putt`), Around the Green (`sg_arg`), Approach (`sg_app`), Off the Tee (`sg_ott`), Tee to Green (`sg_t2g`)
- **Traditional Stats:** Driving distance, fairway accuracy, greens in regulation (GIR), proximity to fairway
- **Target variable:** `made_cut` (1 = made cut, 0 = missed cut)

## Models

Three classification models were tested:

| Model | Accuracy |
|---|---|
| Logistic Regression | 89.5% |
| Random Forest | 84.2% |
| XGBoost | 84.2% |

Logistic regression performed best and was used for final predictions.

## Methodology

1. Average Round 1 and Round 2 statistics per player into a single dataset
2. Train models on 2025 tournament data with an 80/20 train/test split
3. Identify a minimum statline from 2025 cut-makers
4. Apply that minimum statline to 2026 player data to predict cut outcomes

## Requirements

Run `pip install -r requirements.txt`

## Results

The minimum statline a player needed to meet across all nine features to make the cut was derived from the lowest-performing 2025 cut-maker. Applied to 2026 data, the model predicted **52 out of 54** players who actually made the cut.