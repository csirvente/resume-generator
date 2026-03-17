# AI Resume Generator

A free, single-page web app that generates professional resumes using AI.
No signup, no server, no backend — just open it and go.

**Live demo:** https://YOUR-USERNAME.github.io/resume-generator

---

## What it does

- **Quick mode** — paste your LinkedIn profile text, an existing resume, or just describe your background. The AI extracts everything automatically.
- **Structured mode** — fill in a detailed form with work experience, education, skills, and expertise.
- Optionally paste a **target job description** to personalise the resume for a specific role.
- Preview the resume in your browser and **save as PDF** with one click (File → Print → Save as PDF).

The AI model used is `meta-llama/llama-3.3-70b-instruct` via OpenRouter (free tier).

---

## Getting your own free OpenRouter API key

The app includes a shared default key for convenience, but **it may hit rate limits during peak hours**. Getting your own free key takes 30 seconds:

1. Go to [openrouter.ai/keys](https://openrouter.ai/keys)
2. Sign in with Google or GitHub
3. Click **Create key**
4. Copy the key (starts with `sk-or-v1-`)
5. In the app, click **Advanced (API key)** and paste your key

Your key is free, never stored by this app, and only lives in your browser's memory for the session.

> **Note for site owners:** The shared key has a daily usage cap. If it stops working, users will see an error prompting them to use their own key.

---

## Setting up the default API key (for site owners)

1. Get a free key at [openrouter.ai/keys](https://openrouter.ai/keys)
2. Open `index.html` and find this section near the top of the `<script>` block:
   ```javascript
   const _a = 'sk-or-v1-';
   const _b = 'REPLACE_PART2';
   const _c = 'REPLACE_PART3';
   ```
3. Split your key after `sk-or-v1-` and fill in `_b` and `_c` with the two halves. Example:
   ```javascript
   const _a = 'sk-or-v1-';
   const _b = 'abcdef1234';
   const _c = '5678xyz_rest_of_key';
   ```
4. Save and deploy. The split is a light deterrent against scraping — it is not a security guarantee.

---

## Deploying to GitHub Pages

### Step 1 — Create the repository

1. Log in to [github.com](https://github.com) and click **New repository**
2. Name it `resume-generator`
3. Set visibility to **Public**
4. Do **not** initialise with a README (you'll add your own files)
5. Click **Create repository**

### Step 2 — Push the files

```bash
# From the folder containing index.html and README.md
git init
git add index.html README.md
git commit -m "Initial commit — AI Resume Generator"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/resume-generator.git
git push -u origin main
```

### Step 3 — Enable GitHub Pages

1. Go to your repository on GitHub
2. Click **Settings** → **Pages** (left sidebar)
3. Under **Source**, select `Deploy from a branch`
4. Set branch to `main`, folder to `/ (root)`
5. Click **Save**

GitHub will show a green banner with your live URL in about 30–60 seconds:
```
https://YOUR-USERNAME.github.io/resume-generator
```

### Step 4 — Verify

1. Open the live URL in an **incognito window**
2. Paste a short bio and click Generate Resume
3. Confirm the resume preview appears and the PDF download works

---

## Tech stack

| What | How |
|------|-----|
| UI | Vanilla HTML + CSS + JS — zero dependencies |
| AI | OpenRouter API → `meta-llama/llama-3.3-70b-instruct` |
| PDF | Browser print (`Ctrl+P` / `Cmd+P` → Save as PDF) |
| Hosting | GitHub Pages (free static hosting) |

---

## Customising the model

To use a different model, change this line in `index.html`:

```javascript
model: 'meta-llama/llama-3.3-70b-instruct',
```

Other good free options on OpenRouter:
- `google/gemma-3-27b-it` — strong at instruction following
- `mistralai/mistral-7b-instruct` — fast and lightweight
- `deepseek/deepseek-r1-distill-llama-70b` — excellent reasoning

---

## Privacy

- All resume data is sent only to OpenRouter's API to generate the resume.
- No data is stored by this app — everything lives in your browser tab.
- API keys are held in memory only and cleared when you close the tab.
- See [OpenRouter's privacy policy](https://openrouter.ai/privacy) for how they handle data.
