# GitHub Setup Instructions

## 📋 Prerequisites

1. **GitHub Account** - If you don't have one: https://github.com/signup
2. **Git Installed** - Check by running `git --version` in terminal
   - If not installed: https://git-scm.com/downloads

---

## 🚀 Step-by-Step: Push to GitHub

### Step 1: Create New GitHub Repository

1. Go to https://github.com/new
2. Fill in:
   - **Repository name**: `sentiment-trading-analysis` (or your preferred name)
   - **Description**: "Sentiment-driven stock market prediction using NLP and ML | MSc AI Thesis"
   - **Visibility**: Public (recommended for portfolio) or Private
   - **DON'T** initialize with README, .gitignore, or license (we already have these)
3. Click "Create repository"

### Step 2: Initialize Local Git Repository

Open terminal in your project folder and run:

```bash
cd sentiment-trading-analysis  # Navigate to your project folder
git init
git add .
git commit -m "Initial commit: MSc AI thesis - Sentiment analysis for stock prediction"
```

### Step 3: Link to GitHub

Replace `yourusername` with your actual GitHub username:

```bash
git remote add origin https://github.com/yourusername/sentiment-trading-analysis.git
git branch -M main
git push -u origin main
```

**You'll be prompted for GitHub credentials:**
- Username: your GitHub username
- Password: Use a **Personal Access Token** (not your actual password)

### Step 4: Create Personal Access Token (if needed)

If you don't have a token:

1. Go to: https://github.com/settings/tokens
2. Click "Generate new token" → "Generate new token (classic)"
3. Give it a name: "Thesis Project"
4. Select scopes: ✅ `repo` (full control)
5. Click "Generate token"
6. **Copy the token immediately** (you won't see it again!)
7. Use this token as your password when pushing

---

## ✅ Verify Upload

1. Go to `https://github.com/yourusername/sentiment-trading-analysis`
2. You should see:
   - ✅ README.md with project overview
   - ✅ main_1.ipynb (your notebook)
   - ✅ requirements.txt
   - ✅ LICENSE
   - ✅ docs/ folder with thesis PDF
   - ✅ QUICK_START.md

---

## 🎨 Customize Your Repository

### Add Project to LinkedIn

1. On GitHub repo page, copy the URL
2. LinkedIn → Profile → Projects → Add Project
3. Title: "Sentiment Analysis for Stock Market Prediction"
4. Description: "Achieved 49.91% returns using NLP-driven trading system"
5. Project URL: Your GitHub link

### Make README Stand Out

Add a banner/logo:
1. Create a simple banner at https://www.canva.com (free)
2. Upload to GitHub repo: Add file → Upload files
3. Add to README: `![Banner](banner.png)` at the top

### Pin Repository

1. Go to your GitHub profile: `https://github.com/yourusername`
2. Find "Popular repositories" section
3. Click "Customize your pins"
4. Select this repository
5. Save changes

---

## 📝 Update README with Your Info

Edit `README.md` and replace placeholders:

```markdown
## 👤 Author

**Saviour Victory**  
MSc Artificial Intelligence and Machine Learning  
University of Essex

📧 Email: your.email@example.com
🔗 LinkedIn: https://linkedin.com/in/yourprofile
💻 GitHub: https://github.com/yourusername
```

Commit the change:
```bash
git add README.md
git commit -m "Update author contact information"
git push
```

---

## 🔄 Making Future Updates

When you modify code:

```bash
git add .
git commit -m "Description of your changes"
git push
```

Examples:
```bash
git commit -m "Add LSTM model implementation"
git commit -m "Improve sentiment preprocessing"
git commit -m "Update results with new backtesting data"
```

---

## 📊 Add GitHub Stats Badge (Optional but Cool!)

Add to README.md after the title:

```markdown
![GitHub stars](https://img.shields.io/github/stars/yourusername/sentiment-trading-analysis?style=social)
![GitHub forks](https://img.shields.io/github/forks/yourusername/sentiment-trading-analysis?style=social)
![GitHub watchers](https://img.shields.io/github/watchers/yourusername/sentiment-trading-analysis?style=social)
```

---

## 🎯 Add Topics/Tags to Repository

On GitHub repo page:
1. Click "⚙️ Settings" (gear icon next to About)
2. Add topics:
   - `machine-learning`
   - `nlp`
   - `sentiment-analysis`
   - `stock-prediction`
   - `fintech`
   - `deep-learning`
   - `trading`
   - `python`
   - `artificial-intelligence`
3. Save changes

These help people discover your project!

---

## 🐛 Common Issues

### "Permission denied (publickey)"
Use HTTPS instead of SSH:
```bash
git remote set-url origin https://github.com/yourusername/repo.git
```

### "Repository not found"
Check the URL:
```bash
git remote -v  # Should show correct GitHub URL
```

### Large files (>100MB)
GitHub has file size limits. If thesis PDF is too large:
```bash
git rm --cached docs/CE-901_Report__1_.pdf
```
Then host PDF elsewhere (Google Drive, Dropbox) and link in README.

### Forgot to add API key protection
If you accidentally committed API keys:
```bash
git filter-branch --force --index-filter \
  "git rm --cached --ignore-unmatch path/to/file" \
  --prune-empty --tag-name-filter cat -- --all
```
Then regenerate ALL exposed API keys immediately!

---

## ✨ Final Checklist

Before sharing your repository:

- [ ] README.md is complete and accurate
- [ ] requirements.txt includes all dependencies
- [ ] No API keys or secrets committed
- [ ] Thesis PDF is in docs/ folder
- [ ] Contact info updated
- [ ] Repository description set on GitHub
- [ ] Topics/tags added
- [ ] Repository pinned to profile

---

## 🎓 Pro Tips

1. **Star your own repo** - Shows confidence to employers
2. **Write good commit messages** - They show your development process
3. **Add a project demo video** - Record yourself running the notebook
4. **Create a GitHub Pages site** - Turn README into a website
5. **Contribute to related projects** - Shows community involvement

---

## 📞 Need Help?

- **Git basics**: https://docs.github.com/en/get-started
- **Git cheat sheet**: https://education.github.com/git-cheat-sheet-education.pdf
- **GitHub guides**: https://guides.github.com

---

**Once uploaded, share the link on LinkedIn and start applying! 🚀**
