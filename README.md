# Advanced Time Series Forecasting With Prophet and Hyperpaeameter Optimization:

# 1. Dataset Generation:  
      - A synthetic dataset was generated covering daily data from 2020-01-01 to 2023-12-31 (1461 days).  
   - Components included:  
      - Trend: Linear increase from 50 to 150.  
      - Yearly seasonality: Sinusoidal pattern with amplitude 20.  
      - Weekly seasonality: Sinusoidal pattern with amplitude 10.  
      - Noise: Gaussian random noise with mean 0 and standard deviation 5.  
      - Outliers: Random spikes (+50 or -50) with 2% probability.  
      - This ensured realistic complexity with multiple seasonalities and irregularities.

- # 2. Baseline Forecasting Model:
       - Data split: last 180 days held out for testing.  
       - Baseline model: Prophet with default settings.  
       - Metrics on test set:  
          - RMSE = 6.27  
          - MAE = 4.39  
          - MAPE = 3.48%

 # 3. Hyperparameter Optimization with Optuna:
      - Optuna used to tune Prophet parameters:  
      - changepointpriorscale  
      - seasonalitypriorscale  
      - holidayspriorscale  
      - seasonality_mode (additive/multiplicative)  
      - Objective: minimize RMSE via Prophet’s cross-validation.

# 4. Optimization Process:  
     - Optuna executed with multiple trials (demonstrated with 20).  
     - Best parameters identified:  
     - changepointpriorscale ≈ 0.00126  
     - seasonalitypriorscale ≈ 0.915  
     - holidayspriorscale ≈ 2.34 (example from trial)  
     - seasonality_mode = additive

# 5. Final Comparison (Baseline vs Optimized):
    | Metric | Baseline | Optimized |
    |--------|----------|-----------|
    | RMSE   | 6.27     | 6.29      |
    | MAE    | 4.39     | 4.39      |
    | MAPE   | 3.48%    | 3.49%     |
 
- The optimized model did not significantly outperform the baseline.  
- This suggests Prophet’s default settings were already well-suited for the synthetic dataset.  
- However, the optimization framework is valuable for real-world datasets, where tuning often yields larger improvements.

# Conclusion:

     This project successfully demonstrated the end-to-end workflow of time series forecasting: dataset generation, baseline modeling, hyperparameter optimization, and performance comparison. While optimization did not improve results significantly on synthetic data, the methodology provides a strong foundation for applying Prophet with Optuna to real-world forecasting problems.
