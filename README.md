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

---

## ✅ API KEY SETUP
$env:OPENAI_API_KEY="YOUR_KEY_HERE"

---
## ✅ Translation Command
uv run babeldoc --openai --openai-api-key $env:OPENAI_API_KEY --openai-model "gpt-4o-mini" `
  --lang-in en --lang-out hi `
  --skip-curve-render `
  --translate-table-text `
  --disable-rich-text-translate --no-auto-extract-glossary `
  --custom-system-prompt "You are a professional translator. Translate ONLY the given text from English to Hindi. Output plain Hindi text only. Do NOT add headings, markdown, bullet points, hashtags, or extra explanations. Do NOT rewrite or summarize. Preserve punctuation and spacing. Keep person names, affiliations, emails, URLs, citations EXACTLY unchanged. Do NOT translate code/JSON blocks; keep them exactly as-is." `
  --files "C:\Users\ramya\Downloads\babel\test\Redmoon\Documents Original\DESIGN AND FABRICATION OF JET ENGINE USING.pdf" `
  --output ".\Outputs"

---
✅ Observed Issues
1) Table/Box overlay issue

Translated text appears behind table bounding boxes

Borders missing in some configurations

Some table text is not translated unless --translate-table-text is enabled

2) Shape rendering affecting readability

When curves/graphic elements are rendered, text positioning becomes incorrect

Workaround tested: --skip-curve-render / --disable-graphic-element-process


