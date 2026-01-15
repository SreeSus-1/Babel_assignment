# Babel_assignment
Translation tool

# Babel Take-home Assignment - LunarTech

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
✅ Issues Identified & Fixes (As per LunarTech Task Requirements)
1) Mixed-language output (Chinese mixed with Hindi)

Issue: During EN → HI translation, the output sometimes contained Chinese characters mixed with Hindi, especially in headings and metadata sections.
Fix/Improvement: Updated translation prompt + extraction settings to ensure the output stays strictly Hindi and preserves proper nouns/technical tokens unchanged.
Result: Output is now consistently Hindi-only, without unwanted Chinese artifacts.

2) Missing translation (eleventh page not translated earlier)

Issue: Some pages (ex: page 11) were not being translated and remained in English or partially untranslated.
Fix/Improvement: Adjusted translation configuration and processing flags to ensure Babel captures and translates all layout regions correctly.
Result: The previously untranslated page(s) now translate completely with correct layout preservation.

3) Tables formatting → improved meaningful table headers

Issue: Table labels were unclear/untranslated.
Fix/Improvement: Enabled table-specific translation handling and improved output formatting so that table headers become clear + meaningful in hindi.
Result: Tables now render in a clean readable structure with meaningful Hindi table names/headers.

---
✅ Results

Screenshots and comparisons are available in /Assignment_1.pdf
