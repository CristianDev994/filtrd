<div align="center">

# CV Forge

**Framework de generaciÃ³n de CVs bilingÃ¼es, compatibles con ATS y con diseÃ±o premium â€” impulsado por Claude AI + Astro**

[![License: MIT](https://img.shields.io/badge/Licencia-MIT-yellow.svg?style=flat-square)](LICENSE)
[![Built with Astro](https://img.shields.io/badge/Generado%20con-Astro-ff5d00?style=flat-square&logo=astro&logoColor=white)](https://astro.build)
[![Claude AI](https://img.shields.io/badge/Potenciado%20por-Claude%20AI-6b21a8?style=flat-square)](https://claude.ai)
[![Gratis](https://img.shields.io/badge/100%25-Gratuito-22c55e?style=flat-square)]()
[![ES / EN](https://img.shields.io/badge/Idioma-ES%20%7C%20EN-0ea5e9?style=flat-square)]()

**Leer en:** [EspaÃ±ol](#-quÃ©-es-CV Forge) Â· [English](#-what-is-CV Forge)

</div>

---

## EspaÃ±ol

### Â¿QuÃ© es CV Forge?

**CV Forge** es un framework de contexto + sistema de diseÃ±o que le indica a un agente de IA (Claude) cÃ³mo generar CVs profesionales, compatibles con sistemas ATS, como sitios web estÃ¡ticos en Astro.

En lugar de pelear con plantillas de Word o pagar suscripciones a generadores de CV, introduces tus datos una sola vez y obtienes:

- Un **CV bilingÃ¼e** (EspaÃ±ol + InglÃ©s) en un Ãºnico proyecto
- HTML **semÃ¡ntico y legible por ATS** que supera el filtro automatizado de selecciÃ³n
- Un **diseÃ±o visual premium** con UI glassmorphism, ideal para compartir como enlace
- **ExportaciÃ³n a PDF con un clic** vÃ­a impresiÃ³n del navegador (A4, CSS optimizado)
- **Variantes por oferta** que adaptan automÃ¡ticamente las palabras clave a cada empresa

> Este repositorio contiene los **archivos de contexto** que impulsan al agente â€” el sistema de diseÃ±o, las reglas CSS y las instrucciones de implementaciÃ³n paso a paso.
>
> **Es completamente gratuito. Ãšsalo, compÃ¡rtelo y adÃ¡ptalo libremente.**

---

### CaracterÃ­sticas

| CaracterÃ­stica | Detalle |
|---|---|
| **Compatible con ATS** | HTML semÃ¡ntico, flujo de texto lÃ³gico, sin tablas ni columnas que rompan los parsers |
| **BilingÃ¼e** | CV en EspaÃ±ol + InglÃ©s en un Ãºnico proyecto Astro con salto de pÃ¡gina entre versiones |
| **ExportaciÃ³n a PDF** | CSS optimizado para impresiÃ³n â€” gradientes, fuentes y layout sobreviven a `window.print()` |
| **Variantes por empresa** | PÃ¡ginas independientes por empresa/puesto con titulares adaptados y colores de acento |
| **DiseÃ±o premium** | UI glassmorphism Â· Fuente Inter Â· Cabecera degradada Ã­ndigo Â· Grid de dos columnas |
| **Colores por empresa** | AdaptaciÃ³n automÃ¡tica (morado Accenture, azul Endesa, etc.) |
| **OptimizaciÃ³n de espacio** | Sistema de 5 pasos para completar CVs escasos sin inventar contenido |
| **Reglas de IA** | 13 reglas estrictas â€” nunca inventa experiencia, siempre pasa el test ATS de copia-pega |

---

### CÃ³mo funciona

```
Tus datos profesionales
        â”‚
        â–¼
  [skill.md] â”€â”€â–º Agente IA (Claude) lee contexto.md
        â”‚
        â–¼
  Genera el proyecto Astro
  â”œâ”€â”€ src/pages/index.astro               â† CV base bilingÃ¼e (ES + EN)
  â”œâ”€â”€ src/pages/accenture-analista.astro  â† Variante empresa #1
  â”œâ”€â”€ src/pages/endesa-datos.astro        â† Variante empresa #2
  â””â”€â”€ src/styles/global.css              â† Todo el CSS personalizado
        â”‚
        â–¼
  npm run build â†’ Sitio estÃ¡tico
  Abrir en navegador â†’ Imprimir a PDF
```

El agente sigue un **flujo de 3 fases**:

1. **Recogida de datos** â€” Analiza tu experiencia, repositorios de GitHub, y crea `[nombre]-context.md`
2. **CV base bilingÃ¼e** â€” Construye el proyecto Astro completo con ambas versiones
3. **AdaptaciÃ³n a oferta** â€” Analiza cada descripciÃ³n de empleo, calcula el % de coincidencia y genera la variante

---

### CÃ³mo usarlo

#### 1. Copia los archivos de contexto a tu sesiÃ³n de Claude

Abre una conversaciÃ³n nueva en [claude.ai](https://claude.ai) y adjunta los dos archivos:
- `contexto.md` â€” el sistema de diseÃ±o y las reglas CSS
- `skill.md` â€” las instrucciones del agente

#### 2. Comparte tus datos profesionales

Comparte tu experiencia, formaciÃ³n, habilidades y cualquier enlace a GitHub. El agente harÃ¡ preguntas y generarÃ¡ un archivo `[nombre]-context.md` como fuente Ãºnica de verdad.

#### 3. Recibe tu proyecto Astro

El agente genera el proyecto completo. EjecÃºtalo en local:

```bash
npm install
npm run dev      # Vista previa en localhost:4321
npm run build    # Build de producciÃ³n
```

#### 4. Genera variantes por oferta

Pega una descripciÃ³n de empleo. El agente:
- Calcula un porcentaje de coincidencia
- Crea una nueva pÃ¡gina variante
- Adapta palabras clave, titular y colores de acento
- Verifica que sigue pasando el filtro ATS

#### 5. Exporta a PDF

Abre la pÃ¡gina en el navegador â†’ `Ctrl+P` â†’ Guardar como PDF. El CSS de impresiÃ³n garantiza:
- Formato A4 con mÃ¡rgenes correctos
- Fondo blanco (sin gasto de tinta)
- La barra lateral se convierte a formato lineal para los lectores ATS
- Una pÃ¡gina por idioma, sin pÃ¡ginas en blanco

---

### Estructura del proyecto

```
CV Forge/
â”œâ”€â”€ contexto.md     # Sistema de diseÃ±o, reglas CSS, paletas y especificaciones de layout
â””â”€â”€ skill.md        # Instrucciones del agente â€” flujo de 3 fases + 13 reglas de calidad
```

**`contexto.md` contiene:**
- Plantilla de datos â€” cÃ³mo estructurar informaciÃ³n personal, experiencia, educaciÃ³n, habilidades
- Sistema de diseÃ±o â€” tipografÃ­a (Inter), colores, grid, UI glassmorphism
- 8 reglas CSS obligatorias â€” los patrones exactos que hacen que los PDFs se vean correctamente
- Componente de lÃ­nea de tiempo â€” patrÃ³n cÃ­rculo + lÃ­nea con errores frecuentes de IA documentados
- OptimizaciÃ³n de espacio â€” sistema de 5 pasos para CVs escasos
- Variantes de color por empresa â€” Accenture, Endesa, y cÃ³mo aÃ±adir nuevas

**`skill.md` contiene:**
- Fase 0 â€” protocolo de recogida de datos y anÃ¡lisis de GitHub
- Fase 1 â€” generaciÃ³n del CV bilingÃ¼e con estructura de archivos Astro
- Fase 2 â€” adaptaciÃ³n a oferta de empleo y coincidencia de palabras clave
- 13 reglas absolutas â€” garantÃ­as de calidad que el agente no puede saltarse

---

### Stack tecnolÃ³gico (proyectos generados)

| Herramienta | FunciÃ³n |
|---|---|
| [Astro](https://astro.build) | Generador de sitios estÃ¡ticos â€” rÃ¡pido, sin JS por defecto |
| [Inter (Google Fonts)](https://fonts.google.com/specimen/Inter) | TipografÃ­a premium en todos los pesos |
| CSS Grid + `minmax(0, 1fr)` | Layout de dos columnas que sobrevive a la exportaciÃ³n PDF |
| CSS `@media print` | SeparaciÃ³n entre renderizado en pantalla y en PDF |
| `window.print()` | ExportaciÃ³n a PDF â€” sin dependencias externas |

---

### Â¿Por quÃ© no usar Word / Canva / Enhancv?

| | CV Forge | Word | Canva / Enhancv |
|---|:---:|:---:|:---:|
| HTML compatible con ATS | âœ… | âš ï¸ | âŒ |
| BilingÃ¼e en un solo proyecto | âœ… | âŒ | âŒ |
| Variantes por oferta | âœ… | Manual | De pago |
| UI web premium para compartir | âœ… | âŒ | âœ… |
| ExportaciÃ³n a PDF | âœ… | âœ… | âœ… |
| Completamente gratuito | âœ… | ðŸ’° | ðŸ’° |
| Contenido generado por IA | âœ… | âŒ | Parcial |

---

### Contribuir

Las contribuciones son bienvenidas, especialmente:

- Nuevas variantes de color para empresas en `contexto.md`
- Reglas CSS adicionales para casos especiales
- Patrones alternativos de lÃ­nea de tiempo
- Traducciones de `skill.md` a otros idiomas

Abre un issue o un PR describiendo el caso de uso.

---

---

## English

### What is CV Forge?

**CV Forge** is a prompt framework + design system that instructs an AI agent (Claude) to generate professional, ATS-compatible CVs as static Astro websites.

Instead of fighting with Word templates or paying for resume builders, you provide your data once and get:

- A **bilingual CV** (Spanish + English) in a single project
- Clean, **ATS-parseable HTML** that passes automated resume screening
- A **premium visual design** with glassmorphism UI, perfect for sharing as a link
- **One-click PDF export** via browser print (A4, print-optimized CSS)
- **Job-specific variants** that adapt keywords to each offer automatically

> This repository contains the **context files** that power the AI agent â€” the design bible, CSS rules, and step-by-step implementation instructions.
>
> **It is completely free. Use it, share it, and adapt it freely.**

---

### Features

| Feature | Details |
|---|---|
| **ATS Compliance** | Semantic HTML structure, logical text flow, no tables or columns that break parsers |
| **Bilingual Output** | Spanish + English CVs in a single Astro project with page-break separation |
| **PDF Export** | Print-optimized CSS â€” gradients, fonts, and layout survive `window.print()` |
| **Job Variants** | Separate pages per company/role with keyword-matched headlines and accent colors |
| **Premium Design** | Glassmorphism UI Â· Inter font Â· Indigo gradient header Â· Two-column grid |
| **Company Branding** | Automatic color adaptation (Accenture purple, Endesa blue, etc.) |
| **Space Optimization** | 5-step system to fill sparse CVs without inventing content |
| **AI Guardrails** | 13 strict rules â€” never invents experience, always runs ATS copy-paste test |

---

### How It Works

```
Your professional data
        â”‚
        â–¼
  [skill.md] â”€â”€â–º AI Agent (Claude) reads contexto.md
        â”‚
        â–¼
  Generates Astro project
  â”œâ”€â”€ src/pages/index.astro              â† Bilingual base CV (ES + EN)
  â”œâ”€â”€ src/pages/accenture-analyst.astro  â† Job variant #1
  â”œâ”€â”€ src/pages/endesa-data.astro        â† Job variant #2
  â””â”€â”€ src/styles/global.css             â† All custom CSS (no Tailwind)
        â”‚
        â–¼
  npm run build â†’ Static site
  Open in browser â†’ Print to PDF
```

The AI agent follows a **3-phase workflow**:

1. **Data Collection** â€” Parses your experience, analyzes GitHub repos, creates `[name]-context.md`
2. **Bilingual Base CV** â€” Builds the full Astro project with both language versions
3. **Job Offer Adaptation** â€” Analyzes each job description, calculates match %, creates variant page

---

### Usage

#### 1. Copy context files to your Claude session

Open a new conversation at [claude.ai](https://claude.ai) and attach both files:
- `contexto.md` â€” the design system and CSS rules
- `skill.md` â€” the agent instructions

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

Open the page in browser â†’ `Ctrl+P` â†’ Save as PDF. The print CSS ensures:
- A4 format with correct margins
- White background (no ink waste)
- Sidebar transforms inline for ATS scanners
- One page per language, no blank pages

---

### Project Structure

```
CV Forge/
â”œâ”€â”€ contexto.md     # Design system, CSS rules, color palettes, layout specs
â””â”€â”€ skill.md        # AI agent instructions â€” 3-phase workflow + 13 guardrail rules
```

**`contexto.md` contains:**
- Data template â€” how to structure personal info, experience, education, skills
- Design system â€” typography (Inter), colors, grid layout, glassmorphism UI
- 8 mandatory CSS rules â€” the exact patterns that make PDFs look correct
- Timeline component â€” circle + line pattern with documented AI error fixes
- Space optimization â€” 5-step system for sparse CVs
- Company color variants â€” Accenture, Endesa, and how to add new ones

**`skill.md` contains:**
- Phase 0 â€” data collection and GitHub analysis protocol
- Phase 1 â€” bilingual CV generation with Astro file structure
- Phase 2 â€” job offer adaptation and keyword matching
- 13 absolute rules â€” quality guardrails the agent must never break

---

### Tech Stack (Generated Projects)

| Tool | Role |
|---|---|
| [Astro](https://astro.build) | Static site generator â€” fast, zero-JS by default |
| [Inter (Google Fonts)](https://fonts.google.com/specimen/Inter) | Premium typography at all weights |
| CSS Grid + `minmax(0, 1fr)` | Two-column layout that survives PDF export |
| CSS `@media print` | Screen vs. PDF rendering split |
| `window.print()` | PDF export â€” no external dependencies |

---

### Why Not Just Use Word / Canva / Enhancv?

| | CV Forge | Word | Canva / Enhancv |
|---|:---:|:---:|:---:|
| ATS-compliant HTML | âœ… | âš ï¸ | âŒ |
| Bilingual in one project | âœ… | âŒ | âŒ |
| Job-specific variants | âœ… | Manual | Paid |
| Premium web UI to share | âœ… | âŒ | âœ… |
| PDF via browser print | âœ… | âœ… | âœ… |
| Completely free | âœ… | ðŸ’° | ðŸ’° |
| AI-generated content | âœ… | âŒ | Partial |

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

**Licencia MIT â€” Ãºsalo, compÃ¡rtelo y adÃ¡ptalo sin restricciones.**

**MIT License â€” use it, share it, and adapt it freely.**

Hecho con Claude AI Â· Para quienes se niegan a tener un CV mediocre

Made with Claude AI Â· For those who refuse to have a mediocre CV

---

Si te ha sido Ãºtil, deja una â­ â€” ayuda a que otros lo encuentren.

If this saved you time, leave a â­ â€” it helps others find it.

</div>

