# Sentiment Analysis for Stock Market Prediction

**MSc AI Thesis Project | University of Essex | December 2025**

[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## 🚀 Project Overview

A **sentiment-driven trading system** that combines NLP techniques with technical analysis to predict stock market movements. The system processes social media data (Twitter, Reddit) and financial news to generate trading signals, achieving **49.91% returns** vs 24.71% benchmark on NVDA with a Sharpe ratio of 4.34.

### Key Results

| Stock | Strategy | Total Return | Benchmark Return | Sharpe Ratio | Max Drawdown |
|-------|----------|--------------|------------------|--------------|--------------|
| **NVDA** | Aggressive | **+49.91%** | 24.71% | **4.34** | -3.96% |
| **NVDA** | Moderate | +30.26% | 24.71% | 4.37 | -2.87% |
| **AAPL** | Aggressive | +11.91% | 36.39% | 1.34 | -5.86% |

## 🎯 Key Features

- **Multi-source Sentiment Analysis**: Combines VADER (lexicon-based) and FinBERT (transformer-based) for robust sentiment scoring
- **Hybrid Prediction Model**: Integrates sentiment indicators with technical analysis (MA, RSI, momentum indicators)
- **Risk-Managed Trading Strategies**: Three confidence thresholds (Conservative 65%, Moderate 60%, Aggressive 55%)
- **Explainable AI**: SHAP values for feature importance analysis
- **Real-time Processing**: Designed for live market data integration
- **Backtesting Framework**: Comprehensive strategy evaluation with performance metrics

## 📊 Architecture

```
Data Collection Layer
├── Social Media (Twitter/Reddit/StockTwits)
├── Financial News (NewsAPI)
└── Market Data (Yahoo Finance)
          ↓
Preprocessing & Feature Engineering
├── Text Cleaning & Tokenization
├── Sentiment Analysis (VADER + FinBERT)
└── Technical Indicators (MA5, RSI14, Returns)
          ↓
ML Model Layer
├── Logistic Regression (Probability Filter)
├── Signal Generator (Buy/Hold/Sell)
└── Confidence-Based Filtering
          ↓
Backtesting Engine
├── Strategy Execution
├── Performance Metrics
└── Risk Analysis
          ↓
Explainability Framework (SHAP)
```

## 🛠️ Technology Stack

**NLP & Sentiment Analysis:**
- VADER Sentiment Analysis
- FinBERT (yiyanghkust/finbert-tone)
- Hugging Face Transformers

**Machine Learning:**
- scikit-learn (Logistic Regression, classification metrics)
- SHAP (model explainability)

**Data Processing:**
- pandas, numpy
- yfinance (market data)
- Tweepy, PRAW, NewsAPI (social data)

**Visualization:**
- matplotlib, seaborn

## 📥 Installation

### Prerequisites
- Python 3.8 or higher
- pip package manager

### Setup

1. **Clone the repository**
```bash
git clone https://github.com/yourusername/sentiment-trading-analysis.git
cd sentiment-trading-analysis
```

2. **Create virtual environment** (recommended)
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. **Install dependencies**
```bash
pip install -r requirements.txt
```

4. **Configure API keys** (Optional - system uses simulated data if APIs not provided)
Edit the `API_KEYS` dictionary in the notebook:
```python
API_KEYS = {
    "twitter_bearer": "your_bearer_token",
    "reddit_client_id": "your_client_id",
    "reddit_client_secret": "your_secret",
    "newsapi_key": "your_newsapi_key"
}
```

## 🚀 Usage

### Basic Prediction

Run the main Jupyter notebook:
```bash
jupyter notebook main_1.ipynb
```

The notebook will:
1. Fetch market data for configured tickers (AAPL, TSLA, NVDA)
2. Collect/simulate social media sentiment
3. Engineer features combining sentiment + technical indicators
4. Train classification model
5. Generate trading signals
6. Backtest strategies
7. Display SHAP explainability analysis

### Customizing Tickers

Modify the configuration cell:
```python
TICKERS = ["AAPL", "TSLA", "NVDA"]  # Add your tickers
PULL_HISTORY_DAYS = 180
SENTIMENT_WINDOW_DAYS = 30
```

### Testing Different Strategies

Adjust confidence thresholds:
```python
strategies = {
    "Conservative": 0.65,  # 65% confidence required
    "Moderate": 0.60,
    "Aggressive": 0.55
}
```

## 📈 Model Performance

### Classification Metrics

| Ticker | Accuracy | Precision | Recall | F1-Score |
|--------|----------|-----------|--------|----------|
| AAPL   | 0.50     | 0.50      | 1.00   | 0.67     |
| TSLA   | 0.50     | 0.50      | 1.00   | 0.67     |
| NVDA   | 0.38     | 0.35      | 0.78   | 0.48     |

### Feature Importance (SHAP Analysis)

Top contributing features:
1. **MA5** (5-day Moving Average) - Primary trend indicator
2. **RSI14** (14-day Relative Strength Index) - Momentum signal
3. **ret1** (1-day returns) - Short-term momentum
4. **ret5** (5-day returns) - Medium-term momentum
5. **combined_sentiment** - Hybrid sentiment score

## 🔬 Research Methodology

### Data Collection
- **Market Data**: 125 trading days (Jun-Dec 2025) for AAPL, TSLA, NVDA
- **Sentiment Data**: 3,717 social media posts (real + simulated)
- **Timeframe**: 6-month window for short-term prediction

### Feature Engineering
**Technical Indicators:**
- Daily returns (ret1)
- 5-day returns (ret5)
- 5-day moving average (MA5)
- 14-day RSI (RSI14)

**Sentiment Features:**
- VADER mean/median sentiment
- FinBERT mean/median sentiment
- Combined weighted sentiment score
- Post volume (investor attention proxy)

### Model Pipeline
1. **Preprocessing**: Text cleaning, normalization
2. **Sentiment Analysis**: VADER + FinBERT parallel processing
3. **Feature Fusion**: Sentiment + technical indicators
4. **Classification**: Logistic Regression with probability calibration
5. **Signal Generation**: Confidence-filtered buy/hold decisions
6. **Backtesting**: Walk-forward validation

## 📚 Key Findings

### What Worked
✅ **Hybrid models** (sentiment + technical) outperform pure technical analysis by 10-22%  
✅ **Confidence filtering** significantly improves risk-adjusted returns  
✅ **Multi-source sentiment** reduces platform bias  
✅ **Aggressive strategy** on high-volatility stocks (NVDA) yields exceptional Sharpe ratios  

### Limitations
⚠️ **Linear model constraint**: Logistic Regression showed limited ability to capture non-linear sentiment effects (SHAP: combined_sentiment ≈ 0)  
⚠️ **Data scarcity**: Only 20 days of sentiment per ticker  
⚠️ **Linguistic complexity**: Sarcasm and informal language not fully handled  
⚠️ **Market manipulation risk**: Social media can be artificially influenced  

### Future Improvements
🔮 **Deep Learning**: Implement LSTM/Transformer architectures for temporal sentiment modeling  
🔮 **Multi-modal inputs**: Add images, emojis, video sentiment analysis  
🔮 **Real-time deployment**: Live data streaming with high-frequency execution  
🔮 **Cross-market validation**: Test on international markets and cryptocurrencies  
🔮 **Ensemble methods**: Combine multiple model architectures  

## 📖 Documentation

Full thesis documentation available in [`docs/CE-901_Report.pdf`](docs/CE-901_Report.pdf)

### Citation
```bibtex
@mastersthesis{victory2025sentiment,
  title={Sentiment Analysis for Trading Signals Using NLP and Social Media Data},
  author={Victory, Saviour},
  year={2025},
  school={University of Essex},
  type={MSc Thesis},
  department={School of Computer Science and Electronic Engineering}
}
```

## 🤝 Contributing

Contributions welcome! Areas for improvement:
- Additional sentiment sources (Discord, Telegram, LinkedIn)
- Alternative ML architectures (LSTM, GRU, Attention mechanisms)
- Extended backtesting on different time periods
- Real-time deployment scripts
- Additional technical indicators

## 📝 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 👤 Author

**Saviour Victory**  
MSc Artificial Intelligence and Machine Learning  
University of Essex  
Student ID: 2412275

📧 Email: [Your Email]  
🔗 LinkedIn: [Your LinkedIn]  
💻 GitHub: [Your GitHub]

---

## 🙏 Acknowledgments

- **Supervisor**: Dr. Junkyu Lee
- **University**: University of Essex, School of Computer Science and Electronic Engineering
- **Libraries**: Hugging Face Transformers, scikit-learn, VADER, yfinance
- **Community**: Thanks to the open-source NLP and quant finance communities

---

**⭐ If you find this project useful, please consider giving it a star!**

