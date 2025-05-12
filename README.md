# AI Code Review with Google Gemini

**AI Code Review** is a GitHub Action that uses **Google Gemini** (formerly Bard) to provide intelligent feedback and code suggestions on your pull requests. This tool helps automate the review process, improve code quality, and save time during development.

---

## ✨ Features

- Reviews pull requests using **Google Gemini API**.
- Posts inline comments and suggestions directly on the PR.
- Filters out unnecessary files with customizable exclude patterns.
- Easily integrates with your GitHub workflows.

---

## 🚀 Getting Started

### Prerequisites

- A **Google Gemini API key**  
  ➤ Get access at [https://makersuite.google.com/app](https://makersuite.google.com/app)

---

### Installation Steps

1. **Fork or clone this repository.**

2. **Create a secret for your Gemini API key** in your GitHub repo:
   - Go to **Settings > Secrets > Actions**
   - Click **"New repository secret"**
   - Name it `GEMINI_API_KEY`
   - Paste your Google Gemini API key

3. **Add the GitHub Actions workflow:**

Create a file at `.github/workflows/ai-code-review.yml`:

```yaml
name: AI Code Review with Gemini

on:
  pull_request:
    types: [opened, synchronize]

permissions:
  contents: read
  pull-requests: write

jobs:
  review:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v3

      - name: Run Gemini Code Review
        uses: nagendra247/ai-code-review@main
        with:
          GEMINI_API_KEY: ${{ secrets.GEMINI_API_KEY }}
          exclude: "**/*.json, **/*.md"
