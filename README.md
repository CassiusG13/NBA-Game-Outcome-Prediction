# NBA-Game-Outcome-Prediction
Machine Learning Project
# NBA Game Outcome Prediction

A machine learning project that predicts NBA regular-season game outcomes using advanced team statistics.

## Project Overview

This project develops and evaluates multiple machine learning models to predict NBA game winners based on team-level efficiency metrics. Using 8,290 games across 7 seasons (2018-2024), the models achieve **68-69% prediction accuracy**, significantly outperforming a baseline home-team predictor.

## Key Results

- **Best Model Accuracy:** 68.7% (RBF SVM)
- **Baseline Comparison:** +13 percentage points over home-team predictor (55.7%)
- **Dataset Size:** 8,290 games from 2018-2024 seasons
- **Models Evaluated:** Logistic Regression, Linear SVM, RBF SVM, Random Forest

## Technologies Used

- **Python 3.x**
- **Libraries:**
  - `pandas` - Data manipulation and analysis
  - `numpy` - Numerical computations
  - `scikit-learn` - Machine learning models and evaluation
  - `matplotlib` - Data visualization
  - `jupyter` - Interactive development environment

## Features

### Advanced Team Statistics (Basketball Reference)
- **ORtg** (Offensive Rating) - Points scored per 100 possessions
- **DRtg** (Defensive Rating) - Points allowed per 100 possessions
- **NRtg** (Net Rating) - Point differential per 100 possessions
- **SRS** (Simple Rating System) - Team strength rating
- **Pace** - Possessions per 48 minutes
- **TOV%** (Turnover Percentage)
- **TS%** (True Shooting Percentage)

All features are calculated as **difference metrics** (Home Team - Away Team) to capture matchup dynamics.

## Methodology

### Data Collection
- Game results from [Fixture Download](https://fixturedownload.com/results/)
- Advanced team statistics from Basketball Reference
- Seasons: 2018-2019 through 2024-2025

### Train/Test Split
- **Training Set:** 2018-2022 seasons (5,828 games)
- **Test Set:** 2023-2024 seasons (2,462 games)
- Split by season to prevent data leakage and ensure temporal validity

### Models Implemented

| Model | Test Accuracy | AUC |
|-------|--------------|-----|
| Home Team Baseline | 55.7% | - |
| Logistic Regression | 68.4% | 0.754 |
| Linear SVM | 68.4% | 0.754 |
| RBF SVM | **68.7%** | 0.732 |
| Random Forest | 68.6% | 0.753 |

### Feature Importance (Random Forest)
1. **SRS_diff** (30.9%) - Most predictive feature
2. **NRtg_diff** (26.5%)
3. **ORtg_diff** (16.4%)
4. **DRtg_diff** (11.9%)
5. **TS_diff** (9.1%)

## Project Structure

```
nba-game-prediction/
│
├── FinalProject.ipynb          # Main Jupyter notebook with full analysis
├── README.md                    # This file
├── data/                        # Data files (not included in repo)
│   ├── nba-2018-*.csv
│   ├── 18-19 Advanced Stats.csv
│   └── ...
└── outputs/
    └── nba_games_2018_2024_clean.csv
```

## Getting Started

### Prerequisites
```bash
pip install pandas numpy scikit-learn matplotlib jupyter
```

### Running the Analysis
1. Clone this repository
```bash
git clone https://github.com/yourusername/nba-game-prediction.git
cd nba-game-prediction
```

2. Download the required data files:
   - Game results from [Fixture Download](https://fixturedownload.com/results/)
   - Advanced stats from Basketball Reference

3. Open and run the Jupyter notebook
```bash
jupyter notebook FinalProject.ipynb
```

## Visualizations

The project includes:
- **ROC Curves** comparing all models
- **Feature Importance** bar chart showing predictive power of each statistic
- **Confusion Matrix** for classification performance analysis

## 🎓 Key Insights

### What Works
✅ **Team efficiency metrics** (Net Rating, SRS) are highly predictive  
✅ **Simple linear models** perform comparably to complex models  
✅ **Proper train/test splitting** ensures robust evaluation  
✅ **Feature engineering** (difference metrics) captures matchup dynamics

### Limitations
⚠️ Season-aggregated stats don't capture:
- Injuries and lineup changes
- Game-to-game momentum shifts
- Back-to-back games and travel fatigue
- Short-term hot/cold streaks

## Model Evaluation

### Confusion Matrix (Logistic Regression)
|  | Predicted Loss | Predicted Win |
|---|----------------|---------------|
| **Actual Loss** | 640 | 484 |
| **Actual Win** | 295 | 1,043 |

### Classification Metrics
- **Precision (Home Win):** 0.68
- **Recall (Home Win):** 0.78
- **F1-Score (Home Win):** 0.73

