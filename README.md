# Flame Prophet 🔥 — Wildfire Risk Prediction System

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
- **LSTM** — forecasts short-term temperature trends from historical time-series data as a leading indicator of fire risk.
  - RMSE: **0.36°C**
- Outputs from both models are combined and visualized on an interactive risk map.

## Model Evaluation (my contribution)
- Implemented **walk-forward (time-series) cross-validation** to avoid data leakage across time.
- CNN metrics: Accuracy, Precision, Recall, F1-score
- LSTM metrics: MSE, RMSE, MAE

## Tech Stack
| Layer | Technology |
|---|---|
| Frontend | Next.js / React |
| Backend | Flask |
| ML/DL | TensorFlow / Keras |
| Models | MobileNetV2 (CNN), LSTM |

## Project Structure
```
flame-prophet-wildfire-prediction/
├── frontend/        # Next.js/React app (risk map UI)
├── backend/         # Flask API serving model predictions
├── models/          # Trained CNN & LSTM models
├── notebooks/       # Training & evaluation notebooks
└── README.md
```

## Getting Started
```bash
# Backend
cd backend
pip install -r requirements.txt
python app.py

# Frontend
cd frontend
npm install
npm run dev
```

## Team
Group final project — Artificial Intelligence course, BINUS University.

## License
This project was built for academic purposes as part of a university course.
