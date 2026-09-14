# Flame Prophet — Wildfire Risk Prediction System

An end-to-end AI system that predicts wildfire risk by combining satellite image classification with temperature time-series forecasting, surfaced on an interactive risk map.

## Course Context
- **Course:** Artificial Intelligence (COMP6853004)
- **Type:** Group Final Project
- **My Role:** Model Evaluation — implemented walk-forward time-series cross-validation and computed final performance metrics for both models.

## Problem Statement
Wildfires are difficult to anticipate because risk depends on both visual fire/smoke signatures in satellite imagery and short-term weather trends (especially temperature). This project combines both signal types into a single risk-scoring pipeline instead of relying on either alone.

## Approach
- **CNN (MobileNetV2, transfer learning)** — classifies satellite image tiles for fire/smoke presence.
  - Accuracy: **96.6%**
- **LSTM (transfer learning)** — forecasts short-term temperature trends as a leading indicator of fire risk.
  - Data sourced from the **NASA POWER API** (2019–2024 daily weather: temperature, humidity, wind, pressure, precipitation, solar radiation).
  - An LSTM encoder is **pretrained** on a corpus of 25 nearby grid locations around the target area, then **fine-tuned** on the target location using **Keras Tuner (Hyperband)** for hyperparameter search.
  - After tuning, the top encoder layers are unfrozen for a final fine-tuning pass.
  - RMSE: **0.36°C**
- Outputs from both models are combined and visualized on an interactive risk map.

## Model Evaluation (my contribution)
- Implemented **walk-forward (time-series) cross-validation** (`TimeSeriesSplit`, 5 folds) on the target-location data to avoid data leakage across time.
- CNN metrics: Accuracy, Precision, Recall, F1-score
- LSTM metrics: MSE, RMSE, MAE (computed after inverse-scaling predictions back to °C)

## Tech Stack
| Layer | Technology |
|---|---|
| Frontend | Next.js / React |
| Backend | Flask |
| ML/DL | TensorFlow / Keras |
| Models | MobileNetV2 (CNN), LSTM |

## Team Repository
This was a group project. The full source code (frontend, backend, and AI models) is hosted in the team repository: **github.com/bit-loi/Flame-Prophet**. This repo focuses on documenting the project and my specific contribution (model evaluation).

## This Repository
This repo documents the project and hosts my individual contribution:
```
flame-prophet-wildfire-prediction/
├── notebooks/
│   └── aol-artificial-intelligence-lstm.ipynb   # LSTM transfer-learning training & evaluation
└── README.md
```
For the complete, deployed application (frontend + backend + trained models), see the team repository linked above.

## Getting Started
This repo only contains the evaluation notebook. To run the full application (frontend + backend), see the setup instructions in the team repository: github.com/bit-loi/Flame-Prophet

## Team
Group final project — Artificial Intelligence course, BINUS University.

## License
This project was built for academic purposes as part of a university course.
