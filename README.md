<div align="center">

# Filtrd

### ATS filters candidates. You filter through ATS.
### *El ATS filtra candidatos. Tú lo atraviesas.*

**Framework de contexto para Claude AI que genera CVs bilingües compatibles con ATS, con diseño premium. Gratis y open source.**

---

[![License: MIT](https://img.shields.io/badge/Licencia-MIT-yellow.svg?style=flat-square)](LICENSE)
[![Claude AI](https://img.shields.io/badge/Powered%20by-Claude%20AI-6b21a8?style=flat-square)](https://claude.ai)
[![Astro](https://img.shields.io/badge/Output-Astro-ff5d00?style=flat-square&logo=astro&logoColor=white)](https://astro.build)
[![100% Gratis](https://img.shields.io/badge/100%25-Gratuito-22c55e?style=flat-square)]()
[![ES / EN](https://img.shields.io/badge/Idioma-ES%20%7C%20EN-0ea5e9?style=flat-square)]()

**Leer en:** [Español](#español) · [English](#english)

</div>

---

## Español

### ¿Qué es Filtrd?

Cada vez que envías un CV, pasa por un sistema ATS (Applicant Tracking System) antes de llegar a cualquier humano. **El 75% de los CVs son descartados automáticamente** por estos filtros, aunque el candidato esté perfectamente cualificado.

**Filtrd existe para invertir eso.**

Es un framework de contexto + sistema de diseño que convierte a Claude AI en un agente especialista en CVs. Le das tus datos profesionales una sola vez y el agente genera un proyecto Astro completo: un CV que los sistemas ATS leen perfectamente y que los reclutadores recuerdan.

**Lo que obtienes:**

- 🌐 **CV bilingüe** (Español + Inglés) en un único proyecto, listo para compartir como web
- ✅ **HTML semántico** que supera cualquier filtro ATS sin trucos ni hacks
- 🎨 **Diseño premium** con UI glassmorphism — parece una web de startup, no una plantilla de Word
- 📄 **PDF perfecto con un clic** vía impresión del navegador (A4, CSS optimizado para print)
- 🎯 **Variantes por oferta** — el agente adapta tu CV a cada descripción de empleo automáticamente
- 💰 **Completamente gratuito** — sin suscripciones, sin límites, sin trampa

> Este repositorio contiene los **archivos de contexto** que le das a Claude: el sistema de diseño, las reglas CSS y las instrucciones paso a paso que convierten al agente en tu asistente personal de CV.

---

### Por qué los CVs fallan en ATS

Los sistemas ATS rechazan CVs por razones técnicas, no de contenido:

| Problema | Consecuencia |
|---|---|
| Columnas y tablas en Word o Canva | El parser lee el texto en orden incorrecto |
| PDFs con imágenes o fuentes no estándar | El texto no es extraíble |
| Palabras clave no coinciden con la oferta | El sistema puntúa bajo y descarta |
| Formato propietario (.docx con macros) | Algunos ATS directamente lo ignoran |

**Filtrd lo soluciona generando CVs como sitios web estáticos** — HTML puro, semántico, legible por cualquier máquina, con diseño que impresiona a cualquier persona.

---

### Cómo funciona

```
Tus datos profesionales
        │
        ▼
  Abres Claude AI y adjuntas:
  ├── contexto.md   ← sistema de diseño y reglas CSS
  └── skill.md      ← instrucciones del agente
        │
        ▼
  El agente genera tu proyecto Astro
  ├── src/pages/index.astro               ← CV bilingüe (ES + EN)
  ├── src/pages/accenture-analista.astro  ← Variante por empresa #1
  ├── src/pages/endesa-datos.astro        ← Variante por empresa #2
  └── src/styles/global.css              ← CSS personalizado (sin Tailwind)
        │
        ▼
  npm run dev → Vista previa local
  Ctrl+P → PDF perfecto en A4
```

**El agente trabaja en 3 fases:**

1. **Recogida de datos** — Analiza tu experiencia, tus repositorios de GitHub si los tienes, y crea `[nombre]-context.md` como fuente única de verdad
2. **CV base bilingüe** — Construye el proyecto Astro completo con las versiones en español e inglés
3. **Variante por oferta** — Pega una descripción de empleo: el agente calcula el % de coincidencia, adapta palabras clave y genera una página nueva

---

### Cómo usarlo

#### 1. Abre Claude y adjunta los dos archivos

Ve a [claude.ai](https://claude.ai) (la cuenta gratuita funciona perfectamente), crea una conversación nueva y adjunta:
- `contexto.md`
- `skill.md`

#### 2. Comparte tus datos profesionales

Cuéntale tu experiencia, formación, habilidades, y enlaza tu GitHub si tienes. El agente hará preguntas y guardará todo en un archivo `[nombre]-context.md`.

#### 3. Recibe el proyecto Astro completo

El agente genera todo el código. Para ejecutarlo:

```bash
npm create astro@latest mi-cv
# Sustituye los archivos generados por los del agente
npm install
npm run dev      # Vista previa en localhost:4321
npm run build    # Build de producción
```

#### 4. Genera variantes para cada oferta de empleo

Pega la descripción del trabajo en Claude. El agente:
- Calcula un % de coincidencia con tu perfil
- Crea una nueva página con las palabras clave de la oferta integradas
- Adapta el color de acento al branding de la empresa
- Verifica que el resultado sigue pasando el filtro ATS

#### 5. Exporta a PDF

Navegador → `Ctrl+P` → Guardar como PDF. El CSS de impresión garantiza:
- Formato A4 con márgenes correctos
- Fondo blanco limpio (sin gasto de tinta)
- La barra lateral se convierte en lista lineal para los parsers ATS
- Una página por idioma, sin páginas en blanco entre versiones

---

### Qué hay en cada archivo

```
filtrd/
├── contexto.md     # Sistema de diseño completo
└── skill.md        # Instrucciones del agente AI
```

**`contexto.md` — el sistema de diseño:**
- Plantilla de datos (información personal, experiencia, educación, habilidades)
- Tipografía Inter, paleta de colores, grid de dos columnas, UI glassmorphism
- 8 reglas CSS obligatorias que hacen que los PDFs salgan perfectos
- Componente de línea de tiempo con los errores más comunes de IA documentados y corregidos
- Sistema de optimización de espacio en 5 pasos para CVs con poco contenido
- Variantes de color por empresa (Accenture, Endesa, y cómo añadir más)

**`skill.md` — las instrucciones del agente:**
- Fase 0: protocolo de recogida de datos y análisis de GitHub
- Fase 1: generación del CV bilingüe con estructura de archivos Astro
- Fase 2: adaptación a oferta de empleo y análisis de palabras clave
- 13 reglas absolutas (nunca inventa experiencia, siempre verifica el build, siempre pasa el test ATS de copia-pega)

---

### Stack del proyecto generado

| Herramienta | Función |
|---|---|
| [Astro](https://astro.build) | Sitio estático, rápido, cero JS innecesario |
| [Inter — Google Fonts](https://fonts.google.com/specimen/Inter) | Tipografía premium en todos los pesos |
| CSS Grid + `minmax(0, 1fr)` | Layout de dos columnas que sobrevive a la exportación PDF |
| CSS `@media print` | Separación total entre renderizado en pantalla y en PDF |
| `window.print()` | Exportación a PDF sin ninguna dependencia externa |

---

### ¿Por qué no Word / Canva / Enhancv?

| | Filtrd | Word | Canva / Enhancv |
|---|:---:|:---:|:---:|
| HTML semántico compatible con ATS | ✅ | ⚠️ | ❌ |
| Bilingüe en un solo proyecto | ✅ | ❌ | ❌ |
| Variantes automáticas por oferta | ✅ | Manual | De pago |
| Web premium para compartir | ✅ | ❌ | ✅ |
| Exportación a PDF | ✅ | ✅ | ✅ |
| Completamente gratuito | ✅ | 💰 | 💰 |
| Contenido adaptado por IA | ✅ | ❌ | Parcial |

---

### Contribuir

Las contribuciones son bienvenidas:

- Variantes de color para más empresas en `contexto.md`
- Reglas CSS para casos especiales de layout
- Patrones alternativos de componentes
- Traducción de `skill.md` a otros idiomas

Abre un issue o PR describiendo el caso de uso.

---

---

## English

### What is Filtrd?

Every time you submit a CV, it goes through an ATS (Applicant Tracking System) before reaching any human. **75% of CVs are automatically rejected** by these filters, even when the candidate is a perfect fit.

**Filtrd exists to flip that.**

It's a context framework + design system that turns Claude AI into a specialized CV agent. Give it your professional data once and the agent generates a complete Astro project: a CV that ATS systems read perfectly and that recruiters remember.

**What you get:**

- 🌐 **Bilingual CV** (Spanish + English) in a single project, ready to share as a website
- ✅ **Semantic HTML** that passes any ATS without tricks or hacks
- 🎨 **Premium design** with glassmorphism UI — looks like a startup website, not a Word template
- 📄 **Perfect PDF in one click** via browser print (A4, print-optimized CSS)
- 🎯 **Job-specific variants** — the agent adapts your CV to each job description automatically
- 💰 **Completely free** — no subscriptions, no limits, no catch

> This repository contains the **context files** you give to Claude: the design system, CSS rules, and step-by-step instructions that turn the agent into your personal CV assistant.

---

### Why CVs Fail ATS

ATS systems reject CVs for technical reasons, not content ones:

| Problem | Consequence |
|---|---|
| Columns and tables in Word or Canva | Parser reads text in wrong order |
| PDFs with images or non-standard fonts | Text cannot be extracted |
| Keywords don't match the job listing | System scores low and discards |
| Proprietary formats (.docx with macros) | Some ATS systems ignore it entirely |

**Filtrd solves this by generating CVs as static websites** — pure semantic HTML that any machine can read, with a design that impresses any human.

---

### How It Works

```
Your professional data
        │
        ▼
  Open Claude AI and attach:
  ├── contexto.md   ← design system and CSS rules
  └── skill.md      ← agent instructions
        │
        ▼
  Agent generates your Astro project
  ├── src/pages/index.astro              ← Bilingual CV (ES + EN)
  ├── src/pages/accenture-analyst.astro  ← Company variant #1
  ├── src/pages/endesa-data.astro        ← Company variant #2
  └── src/styles/global.css             ← Custom CSS (no Tailwind)
        │
        ▼
  npm run dev → Local preview
  Ctrl+P → Perfect A4 PDF
```

**The agent works in 3 phases:**

1. **Data Collection** — Parses your experience, GitHub repos if available, and creates `[name]-context.md` as single source of truth
2. **Bilingual Base CV** — Builds the full Astro project with Spanish and English versions
3. **Job Variant** — Paste a job description: the agent calculates match %, adapts keywords, and creates a new page

---

### Usage

#### 1. Open Claude and attach both files

Go to [claude.ai](https://claude.ai) (free account works perfectly), start a new conversation and attach:
- `contexto.md`
- `skill.md`

#### 2. Share your professional data

Tell the agent your experience, education, skills, and link your GitHub if you have one. The agent will ask questions and store everything in a `[name]-context.md` file.

#### 3. Receive the full Astro project

The agent generates all the code. To run it:

```bash
npm create astro@latest my-cv
# Replace files with the ones generated by the agent
npm install
npm run dev      # Preview at localhost:4321
npm run build    # Production build
```

#### 4. Generate variants for each job offer

Paste the job description into Claude. The agent:
- Calculates a match % with your profile
- Creates a new page with the offer's keywords integrated naturally
- Adapts the accent color to the company's branding
- Verifies the result still passes ATS

#### 5. Export to PDF

Browser → `Ctrl+P` → Save as PDF. The print CSS ensures:
- A4 format with correct margins
- Clean white background (no ink waste)
- Sidebar converts to inline list for ATS parsers
- One page per language, no blank pages between versions

---

### What's in Each File

```
filtrd/
├── contexto.md     # Full design system
└── skill.md        # AI agent instructions
```

**`contexto.md` — the design system:**
- Data template (personal info, experience, education, skills)
- Inter typography, color palette, two-column grid, glassmorphism UI
- 8 mandatory CSS rules that make PDFs come out perfect
- Timeline component with the most common AI errors documented and fixed
- 5-step space optimization system for sparse CVs
- Company color variants (Accenture, Endesa, and how to add more)

**`skill.md` — agent instructions:**
- Phase 0: data collection protocol and GitHub analysis
- Phase 1: bilingual CV generation with Astro file structure
- Phase 2: job offer adaptation and keyword analysis
- 13 absolute rules (never invents experience, always verifies the build, always runs ATS copy-paste test)

---

### Generated Project Tech Stack

| Tool | Role |
|---|---|
| [Astro](https://astro.build) | Static site, fast, zero unnecessary JS |
| [Inter — Google Fonts](https://fonts.google.com/specimen/Inter) | Premium typography at all weights |
| CSS Grid + `minmax(0, 1fr)` | Two-column layout that survives PDF export |
| CSS `@media print` | Complete separation between screen and PDF rendering |
| `window.print()` | PDF export with no external dependencies |

---

### Why Not Word / Canva / Enhancv?

| | Filtrd | Word | Canva / Enhancv |
|---|:---:|:---:|:---:|
| ATS-compliant semantic HTML | ✅ | ⚠️ | ❌ |
| Bilingual in one project | ✅ | ❌ | ❌ |
| Automatic job-specific variants | ✅ | Manual | Paid |
| Premium web version to share | ✅ | ❌ | ✅ |
| PDF export | ✅ | ✅ | ✅ |
| Completely free | ✅ | 💰 | 💰 |
| AI-adapted content | ✅ | ❌ | Partial |

---

### Contributing

Contributions are welcome:

- Color variants for more companies in `contexto.md`
- CSS rules for special layout cases
- Alternative component patterns
- Translations of `skill.md` to other languages

Open an issue or PR describing the use case.

---

<div align="center">

**Licencia MIT — úsalo, compártelo y adáptalo sin restricciones.**

**MIT License — use it, share it, and adapt it freely.**

---

Hecho con Claude AI · Para candidatos que se niegan a ser filtrados por una máquina

Made with Claude AI · For candidates who refuse to be filtered out by a machine

---

Si te ha sido útil, deja una ⭐ — ayuda a que otros lo encuentren.

If this helped you, leave a ⭐ — it helps others find it.

</div>
