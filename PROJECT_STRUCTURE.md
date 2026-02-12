# Project Structure

```
sentiment-trading-analysis/
│
├── README.md                    # Main project documentation
├── QUICK_START.md              # Quick setup guide
├── GITHUB_SETUP.md             # GitHub upload instructions
├── LICENSE                      # MIT License
├── requirements.txt             # Python dependencies
├── .gitignore                  # Git ignore rules
│
├── main_1.ipynb                # Main Jupyter notebook with full pipeline
│
├── docs/                       # Documentation folder
│   └── CE-901_Report__1_.pdf  # Full MSc thesis (39 pages)
│
└── (future additions)
    ├── src/                    # Source code modules (when refactoring)
    │   ├── data_collection.py
    │   ├── sentiment_analysis.py
    │   ├── feature_engineering.py
    │   ├── model_training.py
    │   └── backtesting.py
    │
    ├── data/                   # Data storage (gitignored)
    │   ├── raw/
    │   └── processed/
    │
    ├── models/                 # Saved model checkpoints
    │
    ├── results/                # Output plots and metrics
    │
    └── tests/                  # Unit tests
        └── test_sentiment.py

```

## 📁 File Descriptions

### Root Files

- **README.md**: Comprehensive project overview with results, architecture, installation, and usage instructions
- **QUICK_START.md**: Fast-track guide to run the project in under 10 minutes
- **GITHUB_SETUP.md**: Step-by-step instructions for uploading to GitHub
- **LICENSE**: MIT License for open-source distribution
- **requirements.txt**: All Python package dependencies
- **.gitignore**: Files and directories to exclude from version control

### Main Code

- **main_1.ipynb**: Complete ML pipeline including:
  - Cell 1: Dependency installation
  - Cell 2: Imports and API configuration
  - Cell 3: Ticker configuration
  - Cell 4: FinBERT initialization
  - Cell 5: Helper functions (text cleaning, simulation)
  - Cell 6-15: Data collection and preprocessing
  - Cell 16-20: Feature engineering
  - Cell 21-25: Model training and evaluation
  - Cell 26-30: Backtesting framework
  - Cell 31-35: SHAP explainability
  - Cell 36-40: Visualization and results

### Documentation

- **docs/CE-901_Report__1_.pdf**: Full academic thesis (39 pages) including:
  - Literature review (27 citations)
  - Methodology
  - Results and analysis
  - Discussion
  - Conclusions
  - Appendices with detailed tables

## 🔄 Workflow Diagram

```
┌─────────────────────────────────────────────────────────┐
│                     DATA COLLECTION                      │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  │
│  │ Yahoo Finance│  │Social Media  │  │Financial News│  │
│  │  (yfinance)  │  │(Twitter/Reddit│  │  (NewsAPI)   │  │
│  └──────┬───────┘  └──────┬───────┘  └──────┬───────┘  │
└─────────┼──────────────────┼──────────────────┼─────────┘
          │                  │                  │
          v                  v                  v
┌─────────────────────────────────────────────────────────┐
│                   PREPROCESSING                          │
│  ┌────────────────────────────────────────────────────┐ │
│  │  • Text cleaning (URLs, mentions, hashtags)        │ │
│  │  • Tokenization                                    │ │
│  │  • Feature scaling and normalization               │ │
│  └────────────────────────────────────────────────────┘ │
└─────────────────────┬───────────────────────────────────┘
                      │
                      v
┌─────────────────────────────────────────────────────────┐
│                 FEATURE ENGINEERING                      │
│  ┌──────────────────────┐  ┌──────────────────────────┐│
│  │ Sentiment Analysis   │  │ Technical Indicators     ││
│  │ • VADER (lexicon)    │  │ • MA5 (moving avg)       ││
│  │ • FinBERT (DL)       │  │ • RSI14 (momentum)       ││
│  │ • Combined score     │  │ • ret1, ret5 (returns)   ││
│  └──────────┬───────────┘  └──────────┬───────────────┘│
│             └────────────┬─────────────┘                │
└──────────────────────────┼──────────────────────────────┘
                           │
                           v
┌─────────────────────────────────────────────────────────┐
│                    MODEL TRAINING                        │
│  ┌────────────────────────────────────────────────────┐ │
│  │  Logistic Regression                               │ │
│  │  • Input: Sentiment + Technical features          │ │
│  │  • Output: BUY (1) / HOLD (0) probabilities      │ │
│  │  • Walk-forward validation                         │ │
│  └────────────────────────────────────────────────────┘ │
└─────────────────────┬───────────────────────────────────┘
                      │
                      v
┌─────────────────────────────────────────────────────────┐
│                 SIGNAL GENERATION                        │
│  ┌────────────────────────────────────────────────────┐ │
│  │  Confidence-Based Filtering                        │ │
│  │  • Conservative: prob ≥ 0.65 → BUY                │ │
│  │  • Moderate: prob ≥ 0.60 → BUY                    │ │
│  │  • Aggressive: prob ≥ 0.55 → BUY                  │ │
│  └────────────────────────────────────────────────────┘ │
└─────────────────────┬───────────────────────────────────┘
                      │
                      v
┌─────────────────────────────────────────────────────────┐
│                    BACKTESTING                           │
│  ┌────────────────────────────────────────────────────┐ │
│  │  Strategy Execution & Evaluation                   │ │
│  │  • Returns: Total, Buy-and-Hold comparison        │ │
│  │  • Risk: Sharpe ratio, Max drawdown               │ │
│  │  • Trade analysis: Win rate, # of trades          │ │
│  └────────────────────────────────────────────────────┘ │
└─────────────────────┬───────────────────────────────────┘
                      │
                      v
┌─────────────────────────────────────────────────────────┐
│                  EXPLAINABILITY                          │
│  ┌────────────────────────────────────────────────────┐ │
│  │  SHAP (SHapley Additive exPlanations)             │ │
│  │  • Feature importance ranking                      │ │
│  │  • Individual prediction explanations             │ │
│  │  • Visualization of model decisions                │ │
│  └────────────────────────────────────────────────────┘ │
└─────────────────────────────────────────────────────────┘
```

## 🎯 Key Components

### 1. Data Collection Module
- **Purpose**: Fetch market prices and social sentiment
- **Technologies**: yfinance, tweepy, praw, NewsAPI
- **Output**: Pandas DataFrames with timestamps

### 2. Sentiment Analysis Module
- **Purpose**: Score text sentiment from -1 (negative) to +1 (positive)
- **Technologies**: VADER (rule-based), FinBERT (transformer-based)
- **Output**: Aggregated sentiment scores per day per ticker

### 3. Feature Engineering Module
- **Purpose**: Create predictive features combining sentiment + technical indicators
- **Technologies**: pandas, numpy
- **Output**: Feature matrix for ML model

### 4. Model Training Module
- **Purpose**: Train classifier to predict next-day price movements
- **Technologies**: scikit-learn (LogisticRegression)
- **Output**: Trained model with probability outputs

### 5. Backtesting Module
- **Purpose**: Simulate historical trading to evaluate strategy
- **Technologies**: Custom Python implementation
- **Output**: Performance metrics (returns, Sharpe, drawdown)

### 6. Explainability Module
- **Purpose**: Understand which features drive predictions
- **Technologies**: SHAP
- **Output**: Feature importance plots and values

## 📊 Data Flow

```
Raw Data → Cleaned Data → Engineered Features → Model → Predictions → Backtested Returns
   ↓                                               ↓
Sentiment                                      SHAP Values
(text → score)                              (interpretability)
```

## 🔧 Future Modularization Plan

When refactoring notebook into production code:

```python
# Example modular structure
from src.data_collection import fetch_market_data, fetch_social_sentiment
from src.sentiment_analysis import analyze_vader, analyze_finbert, combine_sentiment
from src.feature_engineering import create_technical_indicators, merge_features
from src.model_training import train_classifier, generate_signals
from src.backtesting import backtest_strategy, calculate_metrics
from src.explainability import explain_predictions

# Main pipeline
market_data = fetch_market_data(tickers=['AAPL', 'TSLA'], days=180)
sentiment_data = fetch_social_sentiment(tickers=['AAPL', 'TSLA'], days=30)
features = merge_features(market_data, sentiment_data)
model = train_classifier(features)
signals = generate_signals(model, features)
results = backtest_strategy(signals, market_data)
explanations = explain_predictions(model, features)
```

## 💡 Usage Patterns

### Quick Experimentation
```bash
jupyter notebook main_1.ipynb
# Modify parameters in-notebook, run cells
```

### Automated Backtesting
```bash
# Future: CLI tool
python run_backtest.py --tickers AAPL TSLA NVDA --days 180 --strategy aggressive
```

### Live Trading (Future)
```bash
# Future: Real-time deployment
python live_trading.py --config config.yaml
```

## 📈 Performance Benchmarks

**Current Setup:**
- Training time: ~2-5 minutes (depending on data volume)
- Inference: <1 second per prediction
- Memory usage: ~500MB (with FinBERT loaded)
- Disk space: ~1GB (model cache + data)

---

**This structure is designed for clarity, reproducibility, and future scalability.** 🚀
