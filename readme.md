# Spam Detection ML Pipeline

**"In the shadows of the internet, billions of messages flow every second.  
Hidden among them are unwanted advertisements, sophisticated scams, and sometimes much worse.  
Your mission — should you choose to accept it — is to build a detector smart enough to distinguish real messages from spam attempts… at very large scale."**

This notebook presents a complete, modern machine learning pipeline designed to solve a classic (yet still very relevant) spam detection challenge, in the spirit of a serious Kaggle competition.

## Dataset

- Training set: 600,000 samples  
- Test set: 540,000 samples  
- Features: 100 anonymized numerical features (`f0` → `f99`)  
- Target: binary (`0` / `1`) — almost perfectly balanced (~50.6% positive / 49.4% negative)

## What this notebook does (step by step)

1. Data loading & quick exploratory analysis  
2. Stratified train/validation split (80/20)  
3. Fast baseline model using LightGBM  
4. Serious Bayesian hyperparameter optimization with Optuna (50 trials)  
5. Final model training with the best found parameters  
6. Test set predictions + generation of submission file  
7. Clean visual summary of the entire experiment

## Typical Results (example from one run)

| Model                | AUC-ROC   | Approx. training time |
|----------------------|-----------|-----------------------|
| LightGBM Baseline    | 0.7414    | ~32 seconds           |
| Optimized model      | 0.7986    | variable              |
| **Improvement**      | **+5.72%**| —                     |

## Generated Files
submission.csv      → ready-to-submit file for Kaggle
results.png         → visual summary (Optuna progress, prediction distribution, top features, model comparison)

## Main Technologies

- Python 3.11+
- pandas & numpy
- scikit-learn
- LightGBM
- Optuna
- matplotlib

## Quick Start

```bash
# Recommended virtual environment
python -m venv venv
source venv/bin/activate          # Linux/macOS
# or
venv\Scripts\activate             # Windows

pip install pandas numpy scikit-learn lightgbm optuna matplotlib

# Then just open and run the notebook sequentially
ro tip: The Optuna optimization phase is the longest part.
Feel free to reduce the number of trials (n_trials=20 for example) during experimentation.
Happy spam hunting! 