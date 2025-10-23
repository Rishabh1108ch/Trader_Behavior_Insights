# Trader Behavior Sentiment Classifier – XGBoost PnL Prediction

## Project Overview
This project predicts the **Closed Profit and Loss (PnL)** of trades using a combination of **sentiment**, **temporal**, and **behavioral** features. The model helps analyze how market sentiment dynamics influence trader profitability.

---

## Objectives
- Predict trader PnL using engineered features.
- Identify key features influencing trade profitability.
- Visualize predictions and interpret model performance.
- Build a portfolio-ready project demonstrating end-to-end ML workflow.

---

## Dataset
**Source:** [Kaggle – Trader Behavior Dataset](https://www.kaggle.com/datasets/rishabhchandrakar/trader-behavior-dataset)

**Files:**
- `trades.csv` – individual trades, comments, outcomes.
- `users.csv` – trader metadata, behavior patterns.

**Sample Columns:**
- `trade_id`, `user_id`, `comment`, `profit_loss`, `trade_type`, `Closed PnL`

---

## Tools & Technologies
- **Programming:** Python
- **Environment:** Google Colab
- **Libraries:** pandas, NumPy, matplotlib, seaborn, XGBoost, scikit-learn
- **Data Storage:** Kaggle Dataset, Google Drive
- **Visualization:** Matplotlib, Seaborn

---

## Feature Engineering
| Feature | Description |
|---------|-------------|
| `sentiment` | Raw sentiment score of trade comment |
| `sentiment_momentum` | Change in sentiment from previous trade |
| `regime_*` | One-hot encoded sentiment regimes (`Extreme Fear` → `Extreme Greed`) |
| `regime_duration` | Number of trades since last regime change |
| `rolling_win_rate` | Trader's recent win rate (window=20 trades) |
| `size_relative` | Trade size relative to trader's average |
| `side_encoded` | Buy=1, Sell=-1 |
| `hour`, `day_of_week` | Time features extracted from trade timestamp |

---

## Model Overview
- **Algorithm:** XGBoost Regressor
- **Target:** `Closed PnL`
- **Train/Test Split:** 80% Train – 20% Test (time-ordered)
- **Cross-Validation:** 5-fold TimeSeriesSplit
- **Model File:** `sentiment_pnl_model.h5`

---

## Performance Metrics

| Metric | Test Set |
|--------|----------|
| RMSE | 1128.35 |
| MAE  | 140.60 |
| R²   | -0.010 |

> Interpretation: The low R² indicates the model cannot accurately predict individual trade PnL but still provides insights into feature importance and regime trends.

---

## Feature Importance

| Rank | Feature | Gain | Insight |
|------|---------|------|--------|
| 1 | `sentiment_momentum` | 0.345 | Most influential feature; changes in sentiment strongly impact PnL |
| 2 | `regime_greed` | 0.164 | Trades in Greed regime correlate with large PnL deviations |
| 3 | `regime_extreme_fear` | 0.071 | Extreme fear events moderately impact profitability |
| 4 | `regime_duration` | 0.069 | Longer sentiment phases slightly influence outcomes |
| 5 | `day_of_week` | 0.057 | Day-of-week patterns affect trades |
| — | `side_encoded` | 0.000 | Buy/Sell direction not predictive |

---

## Visual Insights

1. **Feature Importance Plot:** Shows top predictors by Gain.  
2. **Actual vs Predicted PnL:** Predicted PnL smooths actual fluctuations; spikes/dips are underrepresented.  
3. **Regime-Specific Predictions:**

| Regime | Actual Mean PnL | Predicted Mean PnL | Number of Trades |
|--------|----------------|------------------|----------------|
| Extreme Fear | 38.00 | 6.61 | 3,172 |
| Fear         | 50.32 | 100.36 | 18,597 |
| Neutral      | 26.77 | 51.55 | 5,607 |
| Greed        | -14.11 | 61.42 | 14,868 |
| Extreme Greed| — | — | 0 |

> The model tends to overestimate PnL in Neutral and Greed regimes.

---

## Numerical Conclusion

**Dataset and Features**
- Total Trades: 211,218  
- Number of Features: 13  
- Target Variable: `Closed PnL`  

**Model Performance (Test Set)**
| Metric | Value | Interpretation |
|--------|-------|----------------|
| RMSE | 1128.35 | Avg deviation per trade |
| MAE | 140.60 | Mean absolute error per trade |
| R² | -0.010 | Worse than predicting mean PnL |

**Feature Importance (Top 5 by Gain)**
| Feature | Gain | Insight |
|---------|------|---------|
| `sentiment_momentum` | 0.345 | Strongest predictor; rapid sentiment changes matter |
| `regime_greed` | 0.164 | Positive/negative swings in Greed regime affect PnL |
| `regime_extreme_fear` | 0.071 | Extreme fear influences returns |
| `regime_duration` | 0.069 | Longer regimes slightly impact PnL |
| `day_of_week` | 0.057 | Minor effect on trading outcomes |

**Predicted vs Actual PnL by Regime**
| Regime | Actual (\$) | Predicted (\$) | Trades |
|--------|-------------|----------------|-------|
| Extreme Fear | 38.00 | 6.61 | 3,172 |
| Fear         | 50.32 | 100.36 | 18,597 |
| Neutral      | 26.77 | 51.55 | 5,607 |
| Greed        | -14.11 | 61.42 | 14,868 |
| Extreme Greed| — | — | 0 |

**Key Insights**
- Only ~13% of trades predicted within ±\$100 of actual PnL.  
- Sentiment momentum is the dominant predictor.  
- Model smooths volatility; extreme spikes/dips are missed.  
- Overestimation in Neutral and Greed regimes; underestimation in Extreme Fear.  

**Portfolio Takeaway**
- Effective for **trend-level insights** but **not for per-trade forecasting**.  
- Demonstrates ML workflow: feature engineering, time-series split, XGBoost modeling, evaluation, and interpretation.  

---

## Future Improvements
- Add volatility & technical indicators.  
- Explore classification models (Win/Loss) for stability.  
- Real-time dashboard deployment with Flask or Streamlit.  
- Expand dataset to include multi-lingual sentiment or market features.

---

## Conclusion
The XGBoost model highlights **sentiment-driven trends** in trader profitability, with **sentiment momentum and regime** as key drivers. While individual PnL prediction is inaccurate (R²=-0.010), the analysis demonstrates **feature importance, model evaluation, and data-driven insights**, making it a strong portfolio example for finance and AI analytics.
