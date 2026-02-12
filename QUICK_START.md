# Quick Start Guide

Get the sentiment trading analysis running in under 10 minutes!

## 🚀 Speed Run (3 Steps)

### 1. Install Dependencies
```bash
pip install -r requirements.txt
```

### 2. Launch Jupyter
```bash
jupyter notebook main_1.ipynb
```

### 3. Run All Cells
Click "Cell" → "Run All" or press `Shift + Enter` through each cell.

**That's it!** The system will:
- ✅ Download market data for AAPL, TSLA, NVDA (last 180 days)
- ✅ Simulate social media sentiment (or use real APIs if configured)
- ✅ Train the prediction model
- ✅ Backtest trading strategies
- ✅ Display results with SHAP explainability

---

## ⚙️ Configuration (Optional)

### Change Stocks
In Cell 3, modify:
```python
TICKERS = ["MSFT", "GOOGL", "AMZN"]  # Any valid ticker symbols
```

### Add Real Social Media Data
In Cell 2, add your API keys:
```python
API_KEYS = {
    "twitter_bearer": "YOUR_BEARER_TOKEN",
    "reddit_client_id": "YOUR_CLIENT_ID",
    "reddit_client_secret": "YOUR_SECRET",
    "newsapi_key": "YOUR_NEWSAPI_KEY"
}
```

**Don't have API keys?** No problem! The system works with simulated data.

---

## 📊 Expected Outputs

You'll see:

1. **Market Data Summary** - Price history for your tickers
2. **Sentiment Analysis** - VADER & FinBERT scores
3. **Feature Engineering** - Technical indicators (MA, RSI, returns)
4. **Model Training** - Classification report per stock
5. **Backtesting Results** - Returns, Sharpe ratios, drawdowns
6. **SHAP Plots** - Feature importance visualization

### Sample Output:
```
=== FINAL BACKTESTING SUMMARY ===
Strategy        Total Return (%)  Sharpe Ratio  Max Drawdown (%)
NVDA Aggressive       +49.91           4.34           -3.96
AAPL Aggressive       +11.91           1.34           -5.86
```

---

## 🐛 Troubleshooting

### "Module not found" errors
```bash
pip install --upgrade -r requirements.txt
```

### Jupyter not opening
```bash
pip install jupyter
jupyter notebook
```

### FinBERT download slow?
First run downloads the model (~400MB). Subsequent runs use cached version.

### Out of memory?
Reduce `PULL_HISTORY_DAYS` to 90 or 60 days.

---

## 🎯 What's Next?

After running the basic setup:

1. **Experiment with different stocks** - Try crypto-related tickers (COIN, MSTR)
2. **Adjust risk levels** - Modify confidence thresholds (55% → 70%)
3. **Add custom features** - Include more technical indicators
4. **Test different time periods** - Change `PULL_HISTORY_DAYS`

---

## 💡 Pro Tips

- **Faster iteration**: Use `SENTIMENT_WINDOW_DAYS = 10` instead of 30
- **More reliable signals**: Increase confidence to 70% (fewer but better trades)
- **Test on volatile stocks**: TSLA, NVDA typically show stronger sentiment effects
- **Compare with buy-and-hold**: Benchmark column shows passive strategy returns

---

## 📝 Key Metrics Explained

- **Total Return**: Percentage gain/loss over the period
- **Sharpe Ratio**: Risk-adjusted returns (>1 is good, >2 is excellent)
- **Max Drawdown**: Largest peak-to-trough decline
- **Accuracy**: % of correctly predicted price movements
- **Precision**: Of predicted BUY signals, % that were correct
- **Recall**: Of actual price rises, % that model caught

---

## 🆘 Need Help?

- **Check the main [README.md](README.md)** for detailed documentation
- **Review the thesis PDF** in `docs/` folder for methodology
- **Open an issue** on GitHub if you find bugs

---

**Happy Trading! 📈🚀**

*Disclaimer: This is a research project for educational purposes. Not financial advice.*
