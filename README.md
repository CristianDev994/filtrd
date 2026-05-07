<div align="center">

# Context-ATS

**Framework de generación de CVs bilingües, compatibles con ATS y con diseño premium — impulsado por Claude AI + Astro**

[![License: MIT](https://img.shields.io/badge/Licencia-MIT-yellow.svg?style=flat-square)](LICENSE)
[![Built with Astro](https://img.shields.io/badge/Generado%20con-Astro-ff5d00?style=flat-square&logo=astro&logoColor=white)](https://astro.build)
[![Claude AI](https://img.shields.io/badge/Potenciado%20por-Claude%20AI-6b21a8?style=flat-square)](https://claude.ai)
[![Gratis](https://img.shields.io/badge/100%25-Gratuito-22c55e?style=flat-square)]()
[![ES / EN](https://img.shields.io/badge/Idioma-ES%20%7C%20EN-0ea5e9?style=flat-square)]()

**Leer en:** [Español](#-qué-es-context-ats) · [English](#-what-is-context-ats)

</div>

---

## Español

### ¿Qué es Context-ATS?

**Context-ATS** es un framework de contexto + sistema de diseño que le indica a un agente de IA (Claude) cómo generar CVs profesionales, compatibles con sistemas ATS, como sitios web estáticos en Astro.

En lugar de pelear con plantillas de Word o pagar suscripciones a generadores de CV, introduces tus datos una sola vez y obtienes:

- Un **CV bilingüe** (Español + Inglés) en un único proyecto
- HTML **semántico y legible por ATS** que supera el filtro automatizado de selección
- Un **diseño visual premium** con UI glassmorphism, ideal para compartir como enlace
- **Exportación a PDF con un clic** vía impresión del navegador (A4, CSS optimizado)
- **Variantes por oferta** que adaptan automáticamente las palabras clave a cada empresa

> Este repositorio contiene los **archivos de contexto** que impulsan al agente — el sistema de diseño, las reglas CSS y las instrucciones de implementación paso a paso.
>
> **Es completamente gratuito. Úsalo, compártelo y adáptalo libremente.**

---

### Características

| Característica | Detalle |
|---|---|
| **Compatible con ATS** | HTML semántico, flujo de texto lógico, sin tablas ni columnas que rompan los parsers |
| **Bilingüe** | CV en Español + Inglés en un único proyecto Astro con salto de página entre versiones |
| **Exportación a PDF** | CSS optimizado para impresión — gradientes, fuentes y layout sobreviven a `window.print()` |
| **Variantes por empresa** | Páginas independientes por empresa/puesto con titulares adaptados y colores de acento |
| **Diseño premium** | UI glassmorphism · Fuente Inter · Cabecera degradada índigo · Grid de dos columnas |
| **Colores por empresa** | Adaptación automática (morado Accenture, azul Endesa, etc.) |
| **Optimización de espacio** | Sistema de 5 pasos para completar CVs escasos sin inventar contenido |
| **Reglas de IA** | 13 reglas estrictas — nunca inventa experiencia, siempre pasa el test ATS de copia-pega |

---

### Cómo funciona

```
Tus datos profesionales
        │
        ▼
  [skill.md] ──► Agente IA (Claude) lee contexto.md
        │
        ▼
  Genera el proyecto Astro
  ├── src/pages/index.astro               ← CV base bilingüe (ES + EN)
  ├── src/pages/accenture-analista.astro  ← Variante empresa #1
  ├── src/pages/endesa-datos.astro        ← Variante empresa #2
  └── src/styles/global.css              ← Todo el CSS personalizado
        │
        ▼
  npm run build → Sitio estático
  Abrir en navegador → Imprimir a PDF
```

El agente sigue un **flujo de 3 fases**:

1. **Recogida de datos** — Analiza tu experiencia, repositorios de GitHub, y crea `[nombre]-context.md`
2. **CV base bilingüe** — Construye el proyecto Astro completo con ambas versiones
3. **Adaptación a oferta** — Analiza cada descripción de empleo, calcula el % de coincidencia y genera la variante

---

### Cómo usarlo

#### 1. Copia los archivos de contexto a tu sesión de Claude

Abre una conversación nueva en [claude.ai](https://claude.ai) y adjunta los dos archivos:
- `contexto.md` — el sistema de diseño y las reglas CSS
- `skill.md` — las instrucciones del agente

#### 2. Comparte tus datos profesionales

Comparte tu experiencia, formación, habilidades y cualquier enlace a GitHub. El agente hará preguntas y generará un archivo `[nombre]-context.md` como fuente única de verdad.

#### 3. Recibe tu proyecto Astro

El agente genera el proyecto completo. Ejecútalo en local:

```bash
npm install
npm run dev      # Vista previa en localhost:4321
npm run build    # Build de producción
```

#### 4. Genera variantes por oferta

Pega una descripción de empleo. El agente:
- Calcula un porcentaje de coincidencia
- Crea una nueva página variante
- Adapta palabras clave, titular y colores de acento
- Verifica que sigue pasando el filtro ATS

#### 5. Exporta a PDF

Abre la página en el navegador → `Ctrl+P` → Guardar como PDF. El CSS de impresión garantiza:
- Formato A4 con márgenes correctos
- Fondo blanco (sin gasto de tinta)
- La barra lateral se convierte a formato lineal para los lectores ATS
- Una página por idioma, sin páginas en blanco

---

### Estructura del proyecto

```
Context-ATS/
├── contexto.md     # Sistema de diseño, reglas CSS, paletas y especificaciones de layout
└── skill.md        # Instrucciones del agente — flujo de 3 fases + 13 reglas de calidad
```

**`contexto.md` contiene:**
- Plantilla de datos — cómo estructurar información personal, experiencia, educación, habilidades
- Sistema de diseño — tipografía (Inter), colores, grid, UI glassmorphism
- 8 reglas CSS obligatorias — los patrones exactos que hacen que los PDFs se vean correctamente
- Componente de línea de tiempo — patrón círculo + línea con errores frecuentes de IA documentados
- Optimización de espacio — sistema de 5 pasos para CVs escasos
- Variantes de color por empresa — Accenture, Endesa, y cómo añadir nuevas

**`skill.md` contiene:**
- Fase 0 — protocolo de recogida de datos y análisis de GitHub
- Fase 1 — generación del CV bilingüe con estructura de archivos Astro
- Fase 2 — adaptación a oferta de empleo y coincidencia de palabras clave
- 13 reglas absolutas — garantías de calidad que el agente no puede saltarse

---

### Stack tecnológico (proyectos generados)

| Herramienta | Función |
|---|---|
| [Astro](https://astro.build) | Generador de sitios estáticos — rápido, sin JS por defecto |
| [Inter (Google Fonts)](https://fonts.google.com/specimen/Inter) | Tipografía premium en todos los pesos |
| CSS Grid + `minmax(0, 1fr)` | Layout de dos columnas que sobrevive a la exportación PDF |
| CSS `@media print` | Separación entre renderizado en pantalla y en PDF |
| `window.print()` | Exportación a PDF — sin dependencias externas |

---

### ¿Por qué no usar Word / Canva / Enhancv?

| | Context-ATS | Word | Canva / Enhancv |
|---|:---:|:---:|:---:|
| HTML compatible con ATS | ✅ | ⚠️ | ❌ |
| Bilingüe en un solo proyecto | ✅ | ❌ | ❌ |
| Variantes por oferta | ✅ | Manual | De pago |
| UI web premium para compartir | ✅ | ❌ | ✅ |
| Exportación a PDF | ✅ | ✅ | ✅ |
| Completamente gratuito | ✅ | 💰 | 💰 |
| Contenido generado por IA | ✅ | ❌ | Parcial |

---

### Contribuir

Las contribuciones son bienvenidas, especialmente:

- Nuevas variantes de color para empresas en `contexto.md`
- Reglas CSS adicionales para casos especiales
- Patrones alternativos de línea de tiempo
- Traducciones de `skill.md` a otros idiomas

Abre un issue o un PR describiendo el caso de uso.

---

---

## English

### What is Context-ATS?

**Context-ATS** is a prompt framework + design system that instructs an AI agent (Claude) to generate professional, ATS-compatible CVs as static Astro websites.

Instead of fighting with Word templates or paying for resume builders, you provide your data once and get:

- A **bilingual CV** (Spanish + English) in a single project
- Clean, **ATS-parseable HTML** that passes automated resume screening
- A **premium visual design** with glassmorphism UI, perfect for sharing as a link
- **One-click PDF export** via browser print (A4, print-optimized CSS)
- **Job-specific variants** that adapt keywords to each offer automatically

> This repository contains the **context files** that power the AI agent — the design bible, CSS rules, and step-by-step implementation instructions.
>
> **It is completely free. Use it, share it, and adapt it freely.**

---

### Features

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

### How It Works

```
Your professional data
        │
        ▼
  [skill.md] ──► AI Agent (Claude) reads contexto.md
        │
        ▼
  Generates Astro project
  ├── src/pages/index.astro              ← Bilingual base CV (ES + EN)
  ├── src/pages/accenture-analyst.astro  ← Job variant #1
  ├── src/pages/endesa-data.astro        ← Job variant #2
  └── src/styles/global.css             ← All custom CSS (no Tailwind)
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

### Usage

#### 1. Copy context files to your Claude session

Open a new conversation at [claude.ai](https://claude.ai) and attach both files:
- `contexto.md` — the design system and CSS rules
- `skill.md` — the agent instructions

#### 2. Provide your professional data

Share your experience, education, skills, and any GitHub links. The agent will ask clarifying questions and generate a `[name]-context.md` file as the single source of truth.

#### 3. Get your Astro project

The agent scaffolds the full Astro project. Run it locally:

```bash
npm install
npm run dev      # Preview at localhost:4321
npm run build    # Production build
```

#### 4. Generate job variants

Paste a job description. The agent will:
- Calculate a match percentage
- Create a new variant page
- Adapt keywords, headline, and accent colors
- Verify it still passes ATS

#### 5. Export PDF

Open the page in browser → `Ctrl+P` → Save as PDF. The print CSS ensures:
- A4 format with correct margins
- White background (no ink waste)
- Sidebar transforms inline for ATS scanners
- One page per language, no blank pages

---

### Project Structure

```
Context-ATS/
├── contexto.md     # Design system, CSS rules, color palettes, layout specs
└── skill.md        # AI agent instructions — 3-phase workflow + 13 guardrail rules
```

**`contexto.md` contains:**
- Data template — how to structure personal info, experience, education, skills
- Design system — typography (Inter), colors, grid layout, glassmorphism UI
- 8 mandatory CSS rules — the exact patterns that make PDFs look correct
- Timeline component — circle + line pattern with documented AI error fixes
- Space optimization — 5-step system for sparse CVs
- Company color variants — Accenture, Endesa, and how to add new ones

**`skill.md` contains:**
- Phase 0 — data collection and GitHub analysis protocol
- Phase 1 — bilingual CV generation with Astro file structure
- Phase 2 — job offer adaptation and keyword matching
- 13 absolute rules — quality guardrails the agent must never break

---

### Tech Stack (Generated Projects)

| Tool | Role |
|---|---|
| [Astro](https://astro.build) | Static site generator — fast, zero-JS by default |
| [Inter (Google Fonts)](https://fonts.google.com/specimen/Inter) | Premium typography at all weights |
| CSS Grid + `minmax(0, 1fr)` | Two-column layout that survives PDF export |
| CSS `@media print` | Screen vs. PDF rendering split |
| `window.print()` | PDF export — no external dependencies |

---

### Why Not Just Use Word / Canva / Enhancv?

| | Context-ATS | Word | Canva / Enhancv |
|---|:---:|:---:|:---:|
| ATS-compliant HTML | ✅ | ⚠️ | ❌ |
| Bilingual in one project | ✅ | ❌ | ❌ |
| Job-specific variants | ✅ | Manual | Paid |
| Premium web UI to share | ✅ | ❌ | ✅ |
| PDF via browser print | ✅ | ✅ | ✅ |
| Completely free | ✅ | 💰 | 💰 |
| AI-generated content | ✅ | ❌ | Partial |

---

### Contributing

Contributions are welcome, especially:

- New company color variants for `contexto.md`
- Additional CSS rules for edge cases
- Alternative timeline patterns
- Translations of `skill.md` to other languages

Open an issue or PR and describe the use case.

---

<div align="center">

**Licencia MIT — úsalo, compártelo y adáptalo sin restricciones.**

**MIT License — use it, share it, and adapt it freely.**

Hecho con Claude AI · Para quienes se niegan a tener un CV mediocre

Made with Claude AI · For those who refuse to have a mediocre CV

---

Si te ha sido útil, deja una ⭐ — ayuda a que otros lo encuentren.

If this saved you time, leave a ⭐ — it helps others find it.

</div>
