# Contributing to Sentiment Trading Analysis

First off, thank you for considering contributing to this project! 🎉

This project is part of an MSc AI thesis, but I welcome contributions that can improve or extend the research.

## 🤝 How Can I Contribute?

### Reporting Bugs

If you find a bug:

1. **Check existing issues** to avoid duplicates
2. **Open a new issue** with:
   - Clear title describing the bug
   - Steps to reproduce
   - Expected vs actual behavior
   - Your environment (OS, Python version, etc.)
   - Relevant error messages/logs

### Suggesting Enhancements

Have ideas for improvements?

1. **Open an issue** with tag `enhancement`
2. Describe:
   - What problem does it solve?
   - How would it work?
   - Why is it useful for this project?

### Code Contributions

#### Areas Welcome for Contribution

🎯 **High Priority:**
- [ ] LSTM/Transformer model implementations
- [ ] Real-time data streaming pipeline
- [ ] Additional sentiment sources (Discord, Telegram, LinkedIn)
- [ ] Cross-market validation (international stocks, crypto)
- [ ] Model ensemble methods
- [ ] Extended backtesting scenarios

🧪 **Medium Priority:**
- [ ] Unit tests for sentiment analysis
- [ ] More technical indicators (MACD, Bollinger Bands, etc.)
- [ ] Multi-timeframe analysis
- [ ] Risk management improvements
- [ ] Performance optimization

📚 **Documentation:**
- [ ] Video tutorial
- [ ] API documentation
- [ ] Jupyter notebook tutorials
- [ ] Blog post writeups

## 🔧 Development Process

### 1. Fork & Clone

```bash
git clone https://github.com/yourusername/sentiment-trading-analysis.git
cd sentiment-trading-analysis
```

### 2. Create Branch

```bash
git checkout -b feature/your-feature-name
# or
git checkout -b fix/bug-description
```

**Branch naming:**
- `feature/lstm-implementation`
- `fix/sentiment-calculation-bug`
- `docs/add-api-examples`
- `test/add-unit-tests`

### 3. Setup Development Environment

```bash
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
pip install -r requirements.txt
pip install -r requirements-dev.txt  # If we add dev dependencies
```

### 4. Make Changes

- Write clean, readable code
- Add comments for complex logic
- Follow existing code style
- Update documentation as needed

### 5. Test Your Changes

```bash
# Run the notebook to ensure it still works
jupyter notebook main_1.ipynb

# If adding code, test it works:
python -c "from your_module import your_function; your_function()"
```

### 6. Commit

```bash
git add .
git commit -m "Add: LSTM model for sentiment time-series"
```

**Commit message format:**
- `Add: New feature description`
- `Fix: Bug fix description`
- `Update: Documentation/code improvement`
- `Refactor: Code restructuring`
- `Test: Adding tests`

### 7. Push & Create Pull Request

```bash
git push origin feature/your-feature-name
```

Then on GitHub:
1. Click "Compare & pull request"
2. Fill in:
   - **Title**: Clear, descriptive
   - **Description**: What, why, how
   - **Related issues**: `Fixes #123` or `Addresses #456`
3. Submit!

## 📋 Pull Request Checklist

Before submitting a PR, ensure:

- [ ] Code runs without errors
- [ ] Existing functionality still works (notebook runs end-to-end)
- [ ] New dependencies added to `requirements.txt`
- [ ] Documentation updated (README, docstrings, comments)
- [ ] No API keys or secrets committed
- [ ] Code follows project style
- [ ] Commit messages are clear

## 💻 Code Style Guidelines

### Python

```python
# Good: Clear variable names, docstrings, type hints where helpful
def calculate_sentiment_score(texts: list[str], model_type: str = "vader") -> np.ndarray:
    """
    Calculate sentiment scores for a list of texts.
    
    Args:
        texts: List of text strings to analyze
        model_type: Sentiment model to use ("vader" or "finbert")
    
    Returns:
        numpy array of sentiment scores in range [-1, 1]
    """
    scores = []
    for text in texts:
        score = model.predict(text)
        scores.append(score)
    return np.array(scores)
```

```python
# Avoid: Unclear names, no documentation
def calc(t, m="v"):
    s = []
    for x in t:
        s.append(m.p(x))
    return np.array(s)
```

### Jupyter Notebooks

- Clear cell titles/comments
- Logical section ordering
- Remove debug/test cells before committing
- Clear output before committing (optional, but cleaner)

## 🧪 Testing Guidelines

When adding new features:

1. **Add examples** in docstrings
2. **Test edge cases**: empty inputs, invalid data, etc.
3. **Verify notebook still runs** end-to-end

Example:
```python
def preprocess_text(text: str) -> str:
    """
    Clean text for sentiment analysis.
    
    Examples:
        >>> preprocess_text("Check out https://example.com #stocks")
        'Check out  stocks'
        >>> preprocess_text("")
        ''
    """
    # Implementation
```

## 📖 Documentation Standards

### README Updates

When adding features:
- Update "Key Features" section
- Add to "Technology Stack" if new library
- Update "Usage" with examples
- Modify "Installation" if new dependencies

### Code Comments

```python
# Good: Explain WHY, not WHAT
# Multiply by 0.6 to weight FinBERT higher than VADER based on validation results
combined_score = 0.4 * vader + 0.6 * finbert

# Avoid: Obvious comments
# Multiply scores
combined_score = 0.4 * vader + 0.6 * finbert
```

## 🎨 Project Philosophy

This project aims to:

1. **Education First**: Code should be readable and teachable
2. **Research Quality**: Maintain academic rigor
3. **Practical Utility**: Should work in real scenarios
4. **Open Science**: Reproducible, transparent, accessible

## 🚫 What We Don't Accept

- Code that doesn't run or breaks existing functionality
- Uncommented complex algorithms
- API keys or secrets in commits
- Plagiarized code without attribution
- Changes that make the project harder to understand

## 🌟 Recognition

Contributors will be:
- Listed in README.md contributors section
- Mentioned in release notes
- Credited in any future publications using contributed code

## 📞 Questions?

- **Open an issue** with tag `question`
- **Email me** at [your email]
- **Discussion board** for general chat

## 📜 License

By contributing, you agree that your contributions will be licensed under the MIT License.

---

## 🎯 Suggested First Contributions

New to the project? Try these beginner-friendly issues:

1. **Add more sample phrases** to `sample_phrases` list for sentiment simulation
2. **Create visualization** of sentiment vs price for a new ticker
3. **Add exception handling** for API failures
4. **Write docstrings** for undocumented functions
5. **Add new technical indicator** (e.g., MACD)

Label: `good first issue`

---

**Thank you for helping improve this project! Every contribution matters.** 🚀
