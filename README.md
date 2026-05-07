# Context-ATS — AI-Powered ATS-Proof CV Framework

<div align="center">

![Context-ATS Banner](https://img.shields.io/badge/Context--ATS-CV%20Framework-6366f1?style=for-the-badge&logo=files&logoColor=white)

**Generate bilingual, ATS-compliant CVs with a premium web UI — powered by Claude AI + Astro**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](LICENSE)
[![Built with Astro](https://img.shields.io/badge/Built%20with-Astro-ff5d00?style=flat-square&logo=astro&logoColor=white)](https://astro.build)
[![Claude AI](https://img.shields.io/badge/Powered%20by-Claude%20AI-6b21a8?style=flat-square)](https://claude.ai)
[![Language: ES/EN](https://img.shields.io/badge/Language-ES%20%7C%20EN-0ea5e9?style=flat-square)]()

[Overview](#-what-is-context-ats) · [Features](#-features) · [How It Works](#-how-it-works) · [Usage](#-usage) · [Structure](#-project-structure) · [Contributing](#-contributing)

</div>

---

## What is Context-ATS?

**Context-ATS** is a structured prompt framework + design system that instructs an AI agent (Claude) to generate professional, ATS-compatible CVs as static Astro websites.

Instead of fighting with Word templates or paying for resume builders, you feed your professional data once and get:

- A **bilingual CV** (Spanish + English) on a single page
- Clean, **ATS-parseable HTML** that passes automated resume screening
- A **premium visual design** with glassmorphism UI, perfect for sharing as a link
- **One-click PDF export** via browser print (A4, print-optimized CSS)
- **Job-specific variants** that adapt keywords to each offer automatically

> This repo contains the **context files** that power the AI agent — the design bible, CSS rules, and step-by-step implementation instructions.

---

## Features

| Feature | Details |
|---|---|
| **ATS Compliance** | Semantic HTML structure, logical text flow, no tables or columns that break parsers |
| **Bilingual Output** | Spanish + English CVs in a single Astro project with page-break separation |
| **PDF Export** | Print-optimized CSS — gradients, fonts, and layout survive `window.print()` |
| **Job Variants** | Separate pages per company/role with keyword-matched headlines and accent colors |
| **Premium Design** | Glassmorphism UI · Inter font · Indigo gradient header · Two-column grid |
| **Company Branding** | Automatic color adaptation (Accenture purple, Endesa blue, etc.) |
| **Space Optimization** | 5-step system to fill sparse CVs without inventing content |
| **AI Guardrails** | 13 strict rules — never invents experience, always runs ATS copy-paste test |

---

## How It Works

```
Your professional data
        │
        ▼
  [skill.md] ──► AI Agent (Claude) reads contexto.md
        │
        ▼
  Generates Astro project
  ├── src/pages/index.astro         ← Bilingual base CV (ES + EN)
  ├── src/pages/accenture-analyst.astro  ← Job variant #1
  ├── src/pages/endesa-data.astro        ← Job variant #2
  └── src/styles/global.css        ← All custom CSS (no Tailwind)
        │
        ▼
  npm run build → Static site
  Open in browser → Print to PDF
```

The AI agent follows a **3-phase workflow**:

1. **Data Collection** — Parses your experience, analyzes GitHub repos, creates `[name]-context.md`
2. **Bilingual Base CV** — Builds the full Astro project with both language versions
3. **Job Offer Adaptation** — Analyzes each job description, calculates match %, creates variant page

---

## Usage

### 1. Copy context files to your Claude session

Open a new Claude conversation and attach both files:
- `contexto.md` — the design system and CSS rules
- `skill.md` — the agent instructions

### 2. Provide your professional data

Share your experience, education, skills, and any GitHub links. The agent will ask clarifying questions and generate a `[name]-context.md` file as the single source of truth.

### 3. Get your Astro project

The agent scaffolds the full Astro project. Run it locally:

```bash
npm install
npm run dev      # Preview at localhost:4321
npm run build    # Production build
```

### 4. Generate job variants

Paste a job description. The agent will:
- Calculate a match percentage
- Create a new variant page
- Adapt keywords, headline, and accent colors
- Verify it still passes ATS

### 5. Export PDF

Open the page in browser → `Ctrl+P` → Save as PDF. The print CSS ensures:
- A4 format with correct margins
- White background (no ink waste)
- Sidebar transforms inline for ATS scanners
- One page per language, no blank pages

---

## Project Structure

```
Context-ATS/
├── contexto.md     # Design system, CSS rules, color palettes, layout specs
└── skill.md        # AI agent instructions — 3-phase workflow + 13 guardrail rules
```

### What lives in `contexto.md`

- **Data template** — How to structure personal info, experience, education, skills
- **Design system** — Typography (Inter), colors, grid layout, glassmorphism UI
- **8 mandatory CSS rules** — The exact patterns that make PDFs look correct
- **Timeline component** — Circle + line pattern with documented AI error fixes
- **Space optimization** — 5-step system for sparse CVs
- **Company color variants** — Accenture, Endesa, and how to add new ones

### What lives in `skill.md`

- **Phase 0** — Data collection and GitHub analysis protocol
- **Phase 1** — Bilingual CV generation with Astro file structure
- **Phase 2** — Job offer adaptation and keyword matching
- **13 absolute rules** — Quality guardrails the agent must never break

---

## Tech Stack (Generated Projects)

| Tool | Role |
|---|---|
| [Astro](https://astro.build) | Static site generator — fast, zero-JS by default |
| [Inter (Google Fonts)](https://fonts.google.com/specimen/Inter) | Premium typography at all weights |
| CSS Grid + `minmax(0, 1fr)` | Two-column layout that survives PDF export |
| CSS `@media print` | Screen vs. PDF rendering split |
| `window.print()` | PDF export — no external dependencies |

---

## Why Not Just Use Word / Canva / Enhancv?

| | Context-ATS | Word | Canva / Enhancv |
|---|:---:|:---:|:---:|
| ATS-compliant HTML | ✅ | ⚠️ | ❌ |
| Bilingual in one project | ✅ | ❌ | ❌ |
| Job-specific variants | ✅ | Manual | Paid |
| Premium web UI to share | ✅ | ❌ | ✅ |
| PDF via browser print | ✅ | ✅ | ✅ |
| Free | ✅ | 💰 | 💰 |
| AI-generated content | ✅ | ❌ | Partial |

---

## Contributing

Contributions are welcome — especially:

- New company color variants for `contexto.md`
- Additional CSS rules for edge cases
- Alternative timeline patterns
- Translations of `skill.md` to other languages

Open an issue or PR and describe the use case.

---

## License

MIT © 2025 [CristianDev994](https://github.com/CristianDev994)

---

<div align="center">

**If this saved you time, leave a ⭐ — it helps others find it.**

Made with Claude AI · Built for job seekers who refuse mediocre CVs

</div>
