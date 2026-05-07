# CV Context Template - [Candidate Name]

## Personal Information
- **Name:** [Full Name]
- **Location:** [City, Country]
- **Phone:** [Number with international prefix]
- **Email:** [Professional email address]
- **LinkedIn:** [Profile URL]
- **GitHub / Portfolio:** [URL if applicable]

## Professional Profile / About Me

*Sector-Specific Version (English):*
[3–4 line paragraph summarizing experience, key knowledge, and career objective focused on a specific sector].

*General Version (Spanish):*
[3–4 line paragraph summarizing the overall profile, highlighting soft skills and the type of opportunities sought].

## Work Experience

### [Job Title] – [Company] | [Location] | [Contract Type]
*[Month Year] – [Month Year / Present]*
- [Main achievement or task using action verbs, detailing the magnitude of impact].
- [Problem-solving, tools used, or teamwork].
- [Soft or technical skill developed in this role].

*(Repeat structure for each relevant experience, reverse chronological order)*

## Education

### [Name of Academic Institution]
*[Degree obtained or in progress]*
*[Start Year] – [End Year or Expected]*
- **Relevant:** [Key subjects, honours, or projects].

*(Repeat for exchanges, complementary training, or other degrees)*

## Technical Skills & Competencies

### Hard Skills
- **[Category 1, e.g. Programming Languages]:** [Skill 1], [Skill 2]...
- **[Category 2, e.g. Tools & Data]:** [Skill 1], [Skill 2]...
- **[Category 3, e.g. Sector Competencies]:** [Skill 1], [Skill 2]...

### Soft Skills
- [Soft skill 1]
- [Soft skill 2]
- [Soft skill 3]

## Languages
- **[Language 1]:** [Level — e.g. Native]
- **[Language 2]:** [Level — e.g. C1 / Advanced]

## Awards, Activities & Interests
- **[Activity or Award Title] ([Year]):** [Brief description of values developed or context].

---

## Design System & Visual Aesthetics

The project follows a **premium, modern, and highly professional** design orientation, combining high-end consulting aesthetics with a live web interface. Any derivative or new CV must respect this Look & Feel.

### 1. Typography & Scale (Inter — All Weights)

| Element | Size | Weight | Notes |
|---|---|---|---|
| Name | 24px | 700 | `letter-spacing: -0.02em` |
| Headline/Subtitle | 11px | 500 | `letter-spacing: 0.03em` |
| Section titles | 9px | 700 | Uppercase, `letter-spacing: 0.12em` |
| Item title | 10px | 600 | — |
| Body text | 9.5–10px | 400 | `line-height: 1.45–1.5` |
| Dates | 8.5px | 400 | Italic, grey |
| Skills (pills) | 8px | 400 | — |
| Secondary text | 8–8.5px | 400 | — |

Font loaded from Google Fonts: weights `300,400,500,600,700`.

### 2. Color Palette

#### Base CV (Indigo)
- **Header gradient:** `#0f172a → #1e293b → #312e81`
- **Name:** white `#ffffff`
- **Headline:** `#a5b4fc` (indigo-300)
- **Section accent:** `#4338ca` (indigo-700)
- **Primary text:** `#334155` (slate-700)
- **Secondary text:** `#475569` (slate-500)
- **Dates / details:** `#64748b` (slate-400)
- **Sidebar background:** `#fafbfd`
- **Sidebar border:** `#e8ecf3`
- **Bullet markers:** `#a5b4fc`

#### Company Variants (reference examples)
- **Accenture / Cybersecurity:** Purple gradient (`#4c1d95 → #6b21a8`), subtitle `#e9d5ff`, accent `#6b21a8`, markers `#c084fc`
- **Endesa / Digital:** Blue gradient (`#00548f → #007bc0`), subtitle `#bae6fd`, accent `#007bc0`, markers `#38bdf8`

When creating a new variant: extract the company's corporate color and derive the gradient (dark→light), subtitle (pastel tint), and bullet markers (mid tone).

### 3. Layout: Floating A4 Sheet (Glassmorphism)

The web page (`body`) uses a soft gradient background (`from-slate-100 via-indigo-50 to-blue-100`).

The CV is an `<article class="cv-hoja">` with:
- `max-width: 794px` (A4 width at 96dpi)
- `background: white`
- `border-radius: 16px` (`rounded-2xl`)
- `box-shadow: 0 25px 50px -12px rgba(0,0,0,.25)` (`shadow-2xl`)

**Floating UI elements** (navigation, print button) use Glassmorphism:
- `background: rgba(255,255,255,0.9)` + `backdrop-filter: blur(8px)`
- Subtle `box-shadow` + `border: 1px solid rgba(0,0,0,0.05)`
- Tailwind class: `bg-white/90 backdrop-blur-sm`

### 4. Two-Column Grid

```css
.cuerpo-grid {
  display: grid;
  grid-template-columns: minmax(0, 1fr) 200px;  /* CRITICAL */
  border-top: 1px solid #e8ecf3;
}

.columna-principal {
  padding: 16px 20px 16px 28px;
  border-right: 1px solid #e8ecf3;
  min-width: 0;
}

.columna-lateral {
  background: #fafbfd;
  padding: 16px 20px;
  min-width: 0;
}
```

### 5. Skills Components (Pills)

**Screen — flex-wrap pills:**
```css
.lista-habilidades { display: flex; flex-wrap: wrap; gap: 3px; }
.lista-habilidades li {
  display: inline-block;
  background: white;
  border: 1px solid #e2e8f0;
  border-radius: 4px;
  padding: 1.5px 5px;
  font-size: 8px;
  color: #475569;
}
```

**Print — inline comma-separated list:**
```css
@media print {
  .lista-habilidades { display: inline !important; }
  .lista-habilidades li { display: inline !important; background: none; border: none; padding: 0; }
  .lista-habilidades li::after { content: ', '; }
  .lista-habilidades li:last-child::after { content: ''; }
}
```

### 6. Floating UI: Print Button & Navigation Panel

**IMPORTANTE: NO usar clases de Tailwind.** Este proyecto NO tiene Tailwind instalado. Toda la UI flotante usa clases CSS definidas en `global.css`.

**Print button (bottom-right):**
```html
<div class="no-print boton-flotante-contenedor">
  <button id="boton-imprimir" class="boton-exportar">
    <!-- SVG icon + texto -->
    Exportar PDF
  </button>
</div>
<script>document.getElementById('boton-imprimir').addEventListener('click',()=>window.print())</script>
```

**Panel de navegación entre variantes (top-left, glassmorphism):**
```html
<nav class="no-print panel-navegacion">
  <div class="panel-navegacion-interior">
    <p class="panel-navegacion-titulo">
      <svg><!-- icono documento --></svg>
      Versiones del CV
    </p>
    <div class="panel-navegacion-lista">
      <a href="/" class="panel-navegacion-enlace activo">
        <span class="enlace-icono"><svg><!-- icono --></svg></span>
        <span class="enlace-info">
          <span class="enlace-nombre">CV Base (General)</span>
          <span class="enlace-descripcion">Perfil profesional completo</span>
        </span>
      </a>
      <!-- Más enlaces de variantes -->
    </div>
  </div>
</nav>
```

La clase `.activo` marca la página actual con un indicador lateral animado.

Hide on print:
```css
.no-print, #boton-imprimir, [class*="no-print"] { display: none !important; }
```

---

## Mandatory CSS Rules for Print/PDF (apply to ALL CVs)

### Rule 1: `minmax(0, 1fr)` instead of `1fr`

**Symptom without this rule:** long text in the main column pushes the sidebar beyond A4 width; `overflow: hidden` clips it in the PDF export.

**Fix:**
```css
.cuerpo-grid { grid-template-columns: minmax(0, 1fr) 200px; }
.columna-principal { min-width: 0; }
.columna-lateral   { min-width: 0; }
```

`minmax(0, 1fr)` allows the track to shrink below its `min-content`. Without `min-width: 0` on **both** children the layout can still break.

### Rule 2: Internal grid in `.lista-idiomas li`

Ensures the language level aligns to the right and wraps correctly:
```css
.lista-idiomas li {
  display: grid;
  grid-template-columns: auto 1fr;
  gap: 4px;
  align-items: baseline;
}
.idioma-nivel {
  text-align: right;
  min-width: 0;
  overflow-wrap: break-word;
  word-break: break-word;
}
```

### Rule 3: Minimum `padding-right` in sidebar at `@media print`

Italic glyphs overhang their box; `overflow: hidden` clips the last character.

```css
@media print {
  .columna-lateral { padding: 16px 6px 16px 18px !important; }
}
```

### Rule 4: Page setup at `@media print`

```css
@media print {
  @page { size: A4; margin: 8mm; }
  body { background: white !important; padding: 0 !important; margin: 0 !important; }
  .fondo-decorativo { background: white !important; padding: 0 !important; min-height: unset !important; }
  .cv-hoja { max-width: unset !important; width: 100% !important; box-shadow: none !important; border-radius: 0 !important; }
}
```

### Rule 5: Header transformation at `@media print`

The gradient disappears on print; replaced by a bottom border in the accent color:
```css
@media print {
  .cabecera-cv {
    background: white !important;
    color: #0f172a !important;
    border-bottom: 2px solid [ACCENT_COLOR] !important;
    padding: 0 0 12px 0 !important;
  }
}
```

### General rule
Any `1fr` track in a grid containing text must be declared `minmax(0, 1fr)`. Every child of a grid in narrow columns (≤200 px) must carry `min-width: 0`. Without **both**, the browser will not respect the page width when printing.

### Rule 6: Page Break — Evitar páginas en blanco

**Síntoma:** Al imprimir, aparecen páginas en blanco intercaladas o al final del documento.

**Causas comunes:**
1. `page-break-after: always` aplicado al **último** `.cv-hoja` genera una página vacía al final.
2. `height` fija en `.cv-hoja` (ej: `296mm`) que excede el área imprimible (297mm - márgenes). Con `@page { margin: 8mm }`, el espacio útil es ~281mm. Un `height: 296mm` desborda 15mm al siguiente folio.

**Fix obligatorio:**
```css
@media print {
  .cv-hoja {
    height: auto !important;
    max-height: none !important;
    min-height: 0 !important;
    overflow: visible !important;
    page-break-after: always;
  }
  /* Cancelar page-break en el último CV */
  .cv-hoja:last-of-type {
    page-break-after: avoid !important;
    break-after: avoid !important;
  }
}
```

### Rule 7: Especificidad CSS en variantes de empresa

**Síntoma:** La cabecera de una variante (ej: Accenture) conserva el gradiente de color en la impresión PDF, cuando debería ser blanca.

**Causa:** Cada variante usa un `<style>` scoped con `!important` para sobrescribir el gradiente de la cabecera:
```css
.cabecera-cv { background: linear-gradient(...) !important; }
```
Este `!important` **gana en cascada** al `background: white !important` del bloque `@media print` de `global.css`, porque los estilos del componente se cargan **después** del CSS global.

**Fix obligatorio:** Cada variante DEBE incluir en su propio `@media print` las reglas de reset de la cabecera:
```css
@media print {
  .cabecera-cv {
    background: white !important;
    color: #0f172a !important;
    border-bottom: 2px solid [ACCENT_COLOR] !important;
  }
  .cabecera-cv::before, .cabecera-cv::after { display: none !important; }
  .cabecera-cv h1 { color: #0f172a !important; }
  .cabecera-cv h2 { color: [ACCENT_COLOR] !important; }
  .cabecera-linea-decorativa { display: none !important; }
  .contacto-item { color: #334155 !important; }
  .contacto-icono svg { stroke: [ACCENT_COLOR] !important; }
}
```

**Regla de oro:** Cualquier `!important` fuera de `@media print` que afecte a la cabecera DEBE tener su contrapartida dentro del `@media print` del mismo componente.

### Rule 8: No usar Tailwind CSS

**Este proyecto NO tiene Tailwind instalado.** Usar clases de Tailwind (como `bg-white/90`, `backdrop-blur-sm`, `text-[9px]`, etc.) no producirá ningún efecto visual. Toda la UI debe usar las clases CSS definidas en `global.css`.

Clases del panel de navegación: `.panel-navegacion`, `.panel-navegacion-interior`, `.panel-navegacion-titulo`, `.panel-navegacion-lista`, `.panel-navegacion-enlace`, `.enlace-icono`, `.enlace-info`, `.enlace-nombre`, `.enlace-descripcion`.

---

## Timeline Rule: Circle Markers & Vertical Connector Line

When a CV variant uses a vertical timeline style (hollow circles on the left of each item connected by a thin line), this pattern has a precise implementation that AI agents commonly get wrong. The following is the **only correct approach** — any deviation produces broken lines, gaps, or misaligned circles.

### Visual structure
```
  ○  ←── circle (.item::before, z-index 2, white fill)
  │  ←── connector line (.item:not(:last-child)::after, z-index 1)
  │
  ○
  │
  │
  ○       ←── last circle: no line below (":last-child::after" hidden)
```

### Anatomy of key measurements

Given these base values (adjust proportionally for other sizes):
- `padding-left` on the list: **18px** (space reserved for circle + breathing room)
- Circle diameter: **9px**
- Circle `top` offset: **3px** (aligns circle center with the cap-height of the first text line)
- Gap between list items: **8px**
- Line width: **1px**

Then:
- Circle `left` = `-18px` (flush with the list's left edge, outside the content area)
- Line `left` = `-18px + 9px/2 - 1px/2` = **`-14px`** (centered on the circle)
- Line `top` = `3px + 9px` = **`12px`** (starts at the bottom edge of the circle)
- Line `bottom` = **`-8px`** (extends 8px below the item's bottom edge, into the flex gap, so it reaches the next circle)

### Correct implementation

```css
/* ── List container ─────────────────────────────────────── */
.lista-educacion,
.lista-experiencia {
  display: flex;
  flex-direction: column;
  gap: 8px;
  padding-left: 18px;
  /* NEVER set overflow: hidden — it clips the negative bottom extension */
}

/* ── Each item must be the positioning context ──────────── */
.item-educacion,
.item-experiencia {
  position: relative;   /* MANDATORY — circles/lines are absolute children */
  break-inside: avoid;
}

/* ── Circle marker ──────────────────────────────────────── */
.item-educacion::before,
.item-experiencia::before {
  content: '';
  position: absolute;
  left: -18px;          /* flush with list's left padding edge */
  top: 3px;             /* aligns with text cap-height */
  width: 9px;
  height: 9px;
  border-radius: 50%;
  border: 1.5px solid #cbd5e1;
  background: white;    /* white fill masks any line overshoot */
  box-sizing: border-box;
  z-index: 2;           /* above the connector line */
}

/* ── Connector line (all items EXCEPT the last) ─────────── */
.item-educacion:not(:last-child)::after,
.item-experiencia:not(:last-child)::after {
  content: '';
  position: absolute;
  left: -14px;          /* = -18 + 9/2 - 1/2  → centered on circle */
  top: 12px;            /* = circle top (3px) + circle height (9px) */
  bottom: -8px;         /* = -(gap value) → extends into the flex gap */
  width: 1px;
  background: #e2e8f0;
  z-index: 1;           /* below circles */
}
```

### Why this works

1. The line is on **each item's `::after`**, not on the container — so the line is always exactly as long as the distance between two consecutive circles, regardless of item height.
2. `:not(:last-child)` removes the line after the final item automatically.
3. `bottom: -8px` (negative gap) bridges the flex gap between items. The gap value must match the `gap` on the container exactly.
4. The **white-filled circle (`::before`) sits at `z-index: 2`** and physically covers the top end of the line below it, masking any 1–2 px misalignment at the meeting point.
5. `overflow: hidden` is **never** set on the list container — it would clip the `bottom: -8px` extension and create visible gaps between circles.

### The 7 errors AI agents commonly make

| # | Error | Symptom |
|---|---|---|
| 1 | Line on the `ul` container `::before` with `height: 100%` | Line spans from list top to list bottom — overshoots first and last circles |
| 2 | Line on each `li::after` but using `height: 100%` instead of `bottom: -gap` | Line ends at the item's own bottom edge, leaving a visible gap before each next circle |
| 3 | `left` of line ≠ `left + width/2` of circle | Circle and line are horizontally offset — the line doesn't pass through the circle center |
| 4 | `position: relative` missing on `.item-*` | Circle and line are positioned relative to a distant ancestor — they appear in the wrong place entirely |
| 5 | `z-index` missing or reversed | Line renders on top of circles, making circles appear as broken dashes |
| 6 | `overflow: hidden` on the list container | `bottom: -gap` is clipped — gaps appear between every pair of circles |
| 7 | Using `:last-child::after { display: none }` instead of `:not(:last-child)::after` | Both achieve the same result, but `:not(:last-child)` is preferred because it requires no override rule and avoids specificity conflicts |

### Adapting colors for company variants

In print, change the circle border and line color to a tint of the accent:
```css
@media print {
  .item-educacion::before,
  .item-experiencia::before {
    border-color: [ACCENT_COLOR_LIGHT];  /* e.g. #c4b5fd for purple variant */
  }
  .item-educacion:not(:last-child)::after,
  .item-experiencia:not(:last-child)::after {
    background: [ACCENT_COLOR_LIGHTEST]; /* e.g. #ede9fe */
  }
}
```

The base indigo variant uses `border-color: #c7d2fe` and line `background: #e0e7ff`.

### Section-level icons (graduation cap, briefcase)

The section title row (`.seccion-titulo`) sits **outside** the list container — it is never part of the timeline. Do not extend the connector line into or through the section title. Each `<section>` contains one `<h2 class="seccion-titulo">` and one `.lista-*` independently; lines are scoped strictly inside `.lista-*`.

---

## Space Optimization Rule (Proportional Filling)

**Problem:** When a CV has less content than the base (fewer jobs, shorter profile, fewer skills), the fixed paddings and gaps leave large blank areas in the exported PDF. The goal is always a fully filled A4 — no half-empty pages.

### Diagnosis before adjusting
Mentally (or visually in `npm run dev`) estimate how much of the page is filled:
- **> 90% filled:** no action needed.
- **75–90% filled:** light adjustments — increase line-height, expand bullet points within truthful bounds.
- **< 75% filled:** structural adjustments required — redistribute content, increase spacing, rethink section order.

### Adjustment toolkit (ordered from least to most invasive)

**1. Expand bullet points** *(always first)*
Add a second or third bullet to each experience entry if the real context allows it. Never invent — rephrase a detail mentioned elsewhere in the candidate's context.

**2. Increase body text size and line-height**
Within the allowed range: push body text to `10px` and `line-height: 1.55` across both columns.

**3. Increase inter-section gap**
Default gap between sections is `12px`. Scale up to `16–20px` when content is sparse.

**4. Increase item spacing**
Default gap between items within a section is `8px`. Scale up to `10–14px` proportionally.

**5. Expand column paddings**
Increase `.columna-principal` padding from `16px 20px 16px 28px` to `20px 24px 20px 32px` and `.columna-lateral` from `16px 20px` to `20px 22px`.

**6. Redistribute sections between columns**
If the sidebar is significantly shorter than the main column, move the **Languages** or **Awards** section to the bottom of the main column and promote a smaller sidebar section upward. Keep the grid visually balanced.

**7. Rethink section order**
If the candidate has strong education but little experience, move the Education section above Work Experience. Fuller sections go first.

### Hard constraints
- **Never invent content** to fill space. Adjust spacing and layout only.
- **Never exceed one A4 page per language.** If adjustments overflow the page, reverse them.
- **Always verify in print preview** (`Ctrl+P`) after any spacing change.
- The goal is a page that looks intentionally dense, not artificially padded.

---

## CSS Class Naming (Spanish — mandatory)

| Element | Class |
|---|---|
| A4 sheet | `.cv-hoja` |
| Main grid | `.cuerpo-grid` |
| Left column | `.columna-principal` |
| Right column | `.columna-lateral` |
| Decorative background | `.fondo-decorativo` |
| Header | `.cabecera-cv` |
| Name | `.nombre-cv` |
| Headline | `.titular-cv` |
| Contact line | `.contacto-linea` |
| Separator | `.separador` |
| Section title | `.seccion-titulo` / `.seccion-titulo-lateral` |
| Profile text | `.texto-perfil` |
| Education list | `.lista-educacion` |
| Experience list | `.lista-experiencia` |
| Education item | `.item-educacion` |
| Experience item | `.item-experiencia` |
| Title + date row | `.fila-titulo` |
| Item title | `.titulo-item` |
| Date | `.fecha-item` |
| Institution / company | `.institucion-item` |
| Contextual note | `.nota-item` |
| Detail / description | `.detalle-item` |
| Bullet list | `.lista-viñetas` |
| Skills (pills) | `.lista-habilidades` |
| Skills group | `.lista-habilidades-grupo` |
| Category label | `.categoria-habilidad` |
| Languages list | `.lista-idiomas` |
| Language name | `.idioma-nombre` |
| Language level | `.idioma-nivel` |
| Awards list | `.lista-logros` |
| Award title | `.titulo-logro` |
| Award description | `.desc-logro` |
| Second page | `.pagina-salto` |
| Hide on print | `.no-print` |
