# Babel_assignment
Translation tool

# Babel Take-home Assignment – LunarTech (AI Engineering Apprentice)

This repository contains my work for the Babel take-home assignment for LunarTech.

I focused on:
- setting up the Babel project locally
- running PDF translations (English → Hindi)
- comparing output quality with the original document
- identifying formatting/layout issues (tables, overlay, boxed regions)
- documenting reproducible steps and findings

> Note: No source code changes were made yet. This repo currently contains reproducible setup, commands, and issue analysis.

---

## ✅ Environment

- OS: Windows 11
- Python: 3.10+ (as used by Babel project)
- Package manager: `uv`
- Translator: OpenAI (gpt-4o-mini)

---

## ✅ Setup Instructions

```powershell
# Create / activate venv if needed
uv venv
.venv\Scripts\activate

# Install dependencies
uv sync
