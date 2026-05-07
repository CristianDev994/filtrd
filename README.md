<div align="center">

# 👻 GhostPass

### Tu CV pasa los filtros ATS como un fantasma.
### *Your CV passes ATS filters like a ghost.*

**Framework de contexto para Claude AI que genera CVs bilingües, compatibles con ATS, con diseño premium — gratis y open source.**

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

### ¿Qué es GhostPass?

**GhostPass** es un framework de contexto + sistema de diseño que convierte a Claude AI en un agente especialista en CVs. Le das tus datos una sola vez y el agente genera un proyecto Astro completo con tu CV profesional.

El nombre lo dice todo: tu candidatura pasa por los sistemas ATS **como un fantasma** — invisible para los filtros automáticos, perfectamente legible para los reclutadores humanos.

**Lo que obtienes:**

- 🌐 **CV bilingüe** (Español + Inglés) en un único proyecto, listo para compartir como web
- ✅ **HTML semántico** que supera cualquier sistema ATS sin trucos ni hacks
- 🎨 **Diseño premium** con UI glassmorphism — parece una landing page de startup, no una plantilla de Word
- 📄 **PDF perfecto** con un clic, vía impresión del navegador (A4, CSS optimizado para print)
- 🎯 **Variantes por oferta** — el agente adapta tu CV a cada descripción de empleo automáticamente
- 💰 **Completamente gratuito** — sin suscripciones, sin límites, sin trampa

> Este repositorio contiene los **archivos de contexto** que le das a Claude: el sistema de diseño, las reglas CSS y las instrucciones paso a paso que convierten al agente en tu asistente personal de CV.

---

### El problema que resuelve

El 75% de los CVs nunca llegan a un reclutador humano. Los sistemas ATS (Applicant Tracking Systems) los filtran antes porque:

- Usan tablas, columnas o imágenes que los parsers no pueden leer
- No contienen las palabras clave exactas de la oferta
- Están en formato PDF sin capa de texto semántico

**GhostPass lo soluciona generando CVs como sitios web estáticos** — HTML puro, semántico, legible por cualquier máquina y con diseño que impresiona a cualquier humano.

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
  └── src/styles/global.css              ← Todo el CSS (sin Tailwind)
        │
        ▼
  npm run dev → Vista previa en navegador
  Ctrl+P → Exportar a PDF (A4, perfecto)
```

**Flujo en 3 fases:**

1. **Recogida de datos** — El agente analiza tu experiencia, tus repositorios de GitHub, y crea un archivo `[nombre]-context.md` como fuente única de verdad
2. **CV base bilingüe** — Construye el proyecto Astro completo con las versiones en español e inglés
3. **Variante por oferta** — Pega cualquier descripción de empleo y el agente calcula el % de coincidencia, adapta las palabras clave y crea una página nueva

---

### Cómo usarlo

#### Paso 1 — Abre Claude y adjunta los archivos

Ve a [claude.ai](https://claude.ai) (cuenta gratuita funciona), crea una conversación nueva y adjunta:
- `contexto.md`
- `skill.md`

#### Paso 2 — Comparte tus datos

Cuéntale al agente tu experiencia, formación, habilidades y enlaza tu GitHub si tienes. El agente hará preguntas y organizará todo en un archivo `[nombre]-context.md`.

#### Paso 3 — Recibe tu proyecto

El agente genera el código completo. Créalo en local:

```bash
npm create astro@latest mi-cv
# Copia los archivos generados
npm install
npm run dev      # Vista previa en localhost:4321
npm run build    # Build de producción
```

#### Paso 4 — Adapta a cada oferta

Pega la descripción del trabajo. El agente:
- Calcula % de coincidencia con tu perfil
- Crea una nueva página variante con las palabras clave de la oferta
- Adapta el color de acento al branding de la empresa
- Verifica que sigue pasando el filtro ATS

#### Paso 5 — Exporta a PDF

Navegador → `Ctrl+P` → Guardar como PDF. El CSS de impresión garantiza:
- Formato A4 con márgenes correctos
- Fondo blanco limpio
- La barra lateral se convierte a formato lineal para los parsers ATS
- Una página por idioma, sin páginas en blanco

---

### Qué hay en cada archivo

```
ghostpass/
├── contexto.md     # Sistema de diseño completo
└── skill.md        # Instrucciones del agente AI
```

**`contexto.md` — el sistema de diseño:**
- Plantilla de datos (información personal, experiencia, educación, habilidades)
- Tipografía (Inter), colores, grid de dos columnas, UI glassmorphism
- 8 reglas CSS obligatorias que hacen que los PDFs salgan perfectos
- Componente de línea de tiempo con los errores más comunes de IA documentados
- Sistema de optimización de espacio en 5 pasos para CVs con poco contenido
- Variantes de color por empresa (Accenture, Endesa, y cómo añadir más)

**`skill.md` — las instrucciones del agente:**
- Fase 0: protocolo de recogida de datos y análisis de GitHub
- Fase 1: generación del CV bilingüe con estructura de archivos Astro
- Fase 2: adaptación a oferta de empleo y análisis de palabras clave
- 13 reglas absolutas que el agente no puede saltarse (nunca inventa experiencia, siempre verifica el build, siempre pasa el test ATS de copia-pega)

---

### Stack del proyecto generado

| Herramienta | Función |
|---|---|
| [Astro](https://astro.build) | Sitio estático, rápido, sin JS innecesario |
| [Inter (Google Fonts)](https://fonts.google.com/specimen/Inter) | Tipografía premium en todos los pesos |
| CSS Grid + `minmax(0, 1fr)` | Layout de dos columnas que sobrevive al PDF |
| CSS `@media print` | Separación total entre pantalla y PDF |
| `window.print()` | Exportación a PDF sin dependencias externas |

---

### ¿Por qué no Word / Canva / Enhancv?

| | GhostPass | Word | Canva / Enhancv |
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
- Reglas CSS para casos especiales
- Patrones alternativos de layout
- Traducción de `skill.md` a otros idiomas

Abre un issue o PR describiendo el caso de uso.

---

---

## English

### What is GhostPass?

**GhostPass** is a context framework + design system that turns Claude AI into a specialized CV agent. Give it your data once and the agent generates a complete Astro project with your professional CV.

The name says it all: your application passes through ATS systems **like a ghost** — invisible to automated filters, perfectly readable to human recruiters.

**What you get:**

- 🌐 **Bilingual CV** (Spanish + English) in a single project, ready to share as a website
- ✅ **Semantic HTML** that passes any ATS without tricks or hacks
- 🎨 **Premium design** with glassmorphism UI — looks like a startup landing page, not a Word template
- 📄 **Perfect PDF** in one click, via browser print (A4, print-optimized CSS)
- 🎯 **Job-specific variants** — the agent adapts your CV to each job description automatically
- 💰 **Completely free** — no subscriptions, no limits, no catch

> This repository contains the **context files** you give to Claude: the design system, CSS rules, and step-by-step instructions that turn the agent into your personal CV assistant.

---

### The Problem It Solves

75% of CVs never reach a human recruiter. ATS (Applicant Tracking Systems) filter them out because:

- They use tables, columns, or images that parsers can't read
- They don't contain the exact keywords from the job listing
- They're PDF files without a semantic text layer

**GhostPass solves this by generating CVs as static websites** — pure, semantic HTML that any machine can read, with a design that impresses any human.

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
  └── src/styles/global.css             ← All CSS (no Tailwind)
        │
        ▼
  npm run dev → Preview in browser
  Ctrl+P → Export to PDF (A4, perfect)
```

**3-phase workflow:**

1. **Data Collection** — Agent parses your experience, GitHub repos, and creates `[name]-context.md` as single source of truth
2. **Bilingual Base CV** — Builds the full Astro project with Spanish and English versions
3. **Job Variant** — Paste any job description and the agent calculates match %, adapts keywords, and creates a new page

---

### Usage

#### Step 1 — Open Claude and attach the files

Go to [claude.ai](https://claude.ai) (free account works), create a new conversation and attach:
- `contexto.md`
- `skill.md`

#### Step 2 — Share your data

Tell the agent your experience, education, skills, and link your GitHub if you have one. The agent will ask questions and organize everything into a `[name]-context.md` file.

#### Step 3 — Receive your project

The agent generates the full code. Run it locally:

```bash
npm create astro@latest my-cv
# Copy the generated files
npm install
npm run dev      # Preview at localhost:4321
npm run build    # Production build
```

#### Step 4 — Adapt to each job offer

Paste the job description. The agent:
- Calculates match % with your profile
- Creates a new variant page with the offer's keywords
- Adapts the accent color to the company's branding
- Verifies it still passes ATS

#### Step 5 — Export to PDF

Browser → `Ctrl+P` → Save as PDF. The print CSS ensures:
- A4 format with correct margins
- Clean white background
- Sidebar converts to inline format for ATS parsers
- One page per language, no blank pages

---

### What's in each file

```
ghostpass/
├── contexto.md     # Full design system
└── skill.md        # AI agent instructions
```

**`contexto.md` — the design system:**
- Data template (personal info, experience, education, skills)
- Typography (Inter), colors, two-column grid, glassmorphism UI
- 8 mandatory CSS rules that make PDFs come out perfect
- Timeline component with the most common AI errors documented
- 5-step space optimization system for sparse CVs
- Company color variants (Accenture, Endesa, and how to add more)

**`skill.md` — agent instructions:**
- Phase 0: data collection protocol and GitHub analysis
- Phase 1: bilingual CV generation with Astro file structure
- Phase 2: job offer adaptation and keyword analysis
- 13 absolute rules the agent cannot break (never invents experience, always verifies the build, always runs ATS copy-paste test)

---

### Generated Project Tech Stack

| Tool | Role |
|---|---|
| [Astro](https://astro.build) | Static site, fast, no unnecessary JS |
| [Inter (Google Fonts)](https://fonts.google.com/specimen/Inter) | Premium typography at all weights |
| CSS Grid + `minmax(0, 1fr)` | Two-column layout that survives PDF export |
| CSS `@media print` | Complete separation between screen and PDF rendering |
| `window.print()` | PDF export with no external dependencies |

---

### Why Not Word / Canva / Enhancv?

| | GhostPass | Word | Canva / Enhancv |
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
- CSS rules for special cases
- Alternative layout patterns
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
