# Skill: ATS-Compatible CV Generation & Job Offer Adaptation

> **Complete step-by-step instructions** for an AI agent to generate professional web-based CVs (Astro) that pass ATS filters, export cleanly as PDF, and adapt to specific job offers. This file is generic and reusable for any candidate.

---

## MANDATORY PREREQUISITES

Before generating any CV, the agent **MUST**:

1. **Read `contexto.md`**: Contains the data template, the full Design System (colors, typography, CSS classes, print rules), the space optimization rule, and class naming conventions.
2. **Obtain the candidate's context**: The user must provide a `[name]-context.md` file with their data, or a PDF/text version of their current CV.
3. **Ask about projects/portfolio** before implementing anything:
   > "Do you have personal projects, GitHub repositories, or a portfolio website you'd like included in the CV? If so, share them (folder, link, or description) and I'll analyze them for integration."

---

## PHASE 0: CANDIDATE DATA COLLECTION

### Step 0.1 — Request Personal Information
If no context file exists, ask the user for information following the structure in `contexto.md`: contact details, professional profile, education, work experience, skills, languages, and awards.

### Step 0.2 — Research Candidate Projects (if applicable)
1. Read the `README.md` and analyze the source code of shared repositories.
2. Extract per project: name, short description, tech stack, and 2–3 bullets using the formula `Action verb + Task + Quantifiable result`.
3. Create a `PROJECTS-[NAME].md` file as the technical source of truth.

### Step 0.3 — Save Candidate Context
Create the file `[name]-context.md` at the project root. This file is the **single source of truth** throughout the entire process.

---

## PHASE 1: BILINGUAL BASE CV GENERATION

### Step 1.1 — Determine Section Order
- **Junior / Academic profiles:** Profile → Education → Experience → Skills → Languages.
- **Mid-Senior profiles:** Profile → Experience → Education → Skills → Certifications.

### Step 1.2 — Astro Project Structure

The CV is built as a static Astro site with the following structure:

```
astro-cv/
├── src/
│   ├── layouts/
│   │   └── Layout.astro        # Base layout: Inter font (300-700), <slot/>
│   ├── pages/
│   │   ├── index.astro         # Bilingual base CV (ES + EN)
│   │   └── [company]-[role].astro  # Job-specific variants
│   └── styles/
│       └── global.css          # @tailwind directives + :root resets
├── astro.config.mjs            # Tailwind as Vite plugin
└── package.json
```

**Layout.astro** — loads Inter from Google Fonts and accepts a `title` prop:
```astro
---
const { title } = Astro.props;
---
<html lang="es">
  <head>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <title>{title}</title>
  </head>
  <body><slot /></body>
</html>
```

**Bilingual structure rules:**
- Declare two sets of variables in the frontmatter: `const experiencia = [...]` and `const experienciaIngles = [...]` (and so on for every section).
- Create two `<article class="cv-hoja">` blocks: one in Spanish, the second with the additional class `pagina-salto` (`page-break-before: always`).
- **All variable names, class names, and functions must be in Spanish.**

### Step 1.3 — Premium Design & Visual Aesthetics (Mandatory)

Follow the Design System in `contexto.md` exactly.

**Decorative background wrapper:**
```html
<div class="fondo-decorativo min-h-screen bg-gradient-to-br from-slate-100 via-indigo-50 to-blue-100 py-12 px-4">
  <article class="cv-hoja max-w-[794px] mx-auto bg-white rounded-2xl shadow-2xl overflow-hidden">
    ...
  </article>
</div>
```

**Header (`.cabecera-cv`):** dark gradient `#0f172a → #1e293b → #312e81`, name in white 24px/700, headline in `#a5b4fc` 11px/500.

**Content grid (`.cuerpo-grid`):**
```css
display: grid;
grid-template-columns: minmax(0, 1fr) 200px;  /* CRITICAL */
```
Main column: padding `16px 20px 16px 28px`, right border `1px solid #e8ecf3`.
Sidebar: background `#fafbfd`, padding `16px 20px`.

**Section titles:** 9px, uppercase, `letter-spacing: 0.12em`, color `#4338ca` (indigo), bottom border `1px solid #e8ecf3`, margin-bottom 8px.

**Skills as pills** (screen) and inline comma-separated list (print) — see CSS in `contexto.md` section 5.

**Floating elements with Glassmorphism:**
```html
<!-- Print button -->
<button id="boton-imprimir" class="no-print fixed bottom-8 right-8 z-50
  bg-indigo-600 hover:bg-indigo-500 text-white text-xs font-medium
  rounded-full px-4 py-2 shadow-lg transition-colors flex items-center gap-2">
  <!-- SVG printer icon (24x24 viewBox, stroke-width 2.5) -->
  Export PDF
</button>
<script>
  document.getElementById('boton-imprimir').addEventListener('click', () => window.print());
</script>

<!-- Variant navigation panel -->
<nav class="no-print fixed top-8 left-8 z-50">
  <div class="bg-white/90 backdrop-blur-sm rounded-xl shadow-lg ring-1 ring-black/5 p-3 min-w-[160px]">
    <p class="text-[9px] font-semibold uppercase tracking-wider text-slate-400 mb-2">Tailored CVs</p>
    <!-- links with hover: arrow appears via opacity + translate-x transition -->
  </div>
</nav>
```

### Step 1.4 — Apply Mandatory CSS Rules (ATS & Print)

Apply **all** rules defined in `contexto.md` (section "Mandatory CSS Rules"):

1. `minmax(0, 1fr)` in `.cuerpo-grid` + `min-width: 0` on `.columna-principal` and `.columna-lateral`.
2. Internal `auto 1fr` grid on `.lista-idiomas li` with `.idioma-nivel { text-align: right; min-width: 0; }`.
3. `padding: 16px 6px 16px 18px !important` on `.columna-lateral` inside `@media print`.
4. `@page { size: A4; margin: 8mm; }` and background/shadow resets in `@media print`.
5. Header print transformation: white background, accent-color bottom border, dark text.
6. Skills print transformation: `display: inline`, no borders, separated by `content: ', '`.

**If the CV uses a timeline style (circle markers + vertical connector line):**
Follow the "Timeline Rule" in `contexto.md` exactly — do not improvise. Mandatory checklist:
- Line is on `.item:not(:last-child)::after`, **never** on the container.
- `left` of line = `left of circle + circle_width/2 − 0.5px` (centered on circle).
- `bottom` of line = `-(gap value)` — must match the flex `gap` on the list exactly.
- `position: relative` on every `.item-*` — missing this breaks everything.
- `z-index: 2` on circles, `z-index: 1` on lines.
- `overflow: hidden` is **never** set on `.lista-educacion` or `.lista-experiencia`.
- Section titles (`.seccion-titulo`) are **outside** the list — lines never pass through them.

### Step 1.5 — Space Optimization (Mandatory before marking done)

After drafting content, apply the **Space Optimization Rule** from `contexto.md`:

1. Preview the CV in browser (`npm run dev`) and estimate fill level visually.
2. If fill is **< 90%**, apply adjustments from the toolkit in `contexto.md` in order of invasiveness:
   - Expand bullets (always first).
   - Increase body text size and line-height within allowed range.
   - Increase inter-section and inter-item gaps proportionally.
   - Expand column paddings.
   - Redistribute sections between columns to balance visual height.
   - Rethink section order so fuller sections appear first.
3. Verify the page does **not** overflow A4 after any adjustment.

### Step 1.6 — Professional Writing

1. Start every bullet with an **action verb** (Developed, Led, Designed, Implemented...).
2. Describe the **concrete task** + **quantifiable result** when available.
3. **NEVER invent** data, experience, tools, or achievements.
4. Translate with technical precision into English.

### Step 1.7 — Build & Verification

After every significant change:
```bash
npm run build
```
Fix any errors before continuing.

Preview locally:
```bash
npm run dev
```

Mandatory checks before marking as complete:
- **Visual:** CV fills exactly 1 A4 page per language in print preview (`Ctrl+P`) with no large blank areas.
- **No clipping:** No text is cut off at the right or bottom edges.
- **ATS (Copy-Paste test):** Select all text in the PDF and paste into Notepad. Reading order must be logical (title → company → dates → bullets) with no unexpected column jumps.

---

## PHASE 2: JOB OFFER ADAPTATION

When the user provides a job listing URL or description:

### Step 2.1 — Offer Analysis & Match (%)

1. Read the job requirements (technologies, soft skills, keywords).
2. Cross-reference with the candidate's context (`[name]-context.md`).
3. Present the **Match Analysis** to the user before writing a single line of code:
   - ✅ **Strengths:** experience/skills with a direct match.
   - ⚠️ **Points to emphasize:** experience that can be reframed to appear more relevant.
   - ❌ **Gaps:** requirements the candidate does not meet (never invent).

### Step 2.2 — Create the Adapted Page

1. Create `src/pages/[company]-[role].astro`.
2. Copy the bilingual base structure from `index.astro`.
3. **Modify content** (never invent anything):
   - **Headline:** include exact keywords from the job posting.
   - **Professional Profile:** respond directly to the offer's mission and company values.
   - **Experience bullets:** reorder and reframe to prioritize what the offer demands.
   - **Skills:** reorder categories and individual skills by relevance to the offer.
   - **Accent colors:** derive from the company's corporate color (dark→light gradient in header, pastel for subtitle, mid tone for markers and print button).
4. **Apply the Space Optimization Rule** — adapted CVs often have fewer bullets than the base; fill the page proportionally before finalizing.

### Step 2.3 — Update Navigation

Add a link to the new variant in the `<nav>` panel in `index.astro`:
```html
<a href="/[company]-[role]" class="group flex items-center gap-1.5 text-[10px] font-medium text-slate-600 hover:text-[COMPANY_COLOR] transition-colors py-0.5">
  <span class="opacity-0 group-hover:opacity-100 -translate-x-1 group-hover:translate-x-0 transition-all">→</span>
  [Company] — [Role]
</a>
```

### Step 2.4 — Final Verification

```bash
npm run build
```
Verify print preview and ATS test for the new variant. Confirm the navigation panel in `index.astro` links to it correctly.

---

## ABSOLUTE AGENT RULES

1. **NEVER INVENT** experience, education, projects, certifications, or skills. Only reframe and prioritize existing information.
2. **ALWAYS ask** about projects/portfolio before starting.
3. **ALWAYS verify the build** (`npm run build`) after every significant change.
4. **ALWAYS apply all CSS rules** from `contexto.md` ("Mandatory CSS Rules") to every CV.
5. **ALWAYS create the bilingual version** (ES + EN) with `.pagina-salto` on the second sheet, unless the user explicitly says otherwise.
6. **ALWAYS present the Match Analysis (%)** before generating any adaptation.
7. **ALWAYS name variables, classes, and functions in Spanish.**
8. **ALWAYS run the Copy-Paste (ATS) test** before marking a CV as complete.
9. **NEVER delete any file** without explicit user approval.
10. **ALWAYS read `contexto.md`** before starting any CV-related task.
11. **ALWAYS transform skills to inline comma-separated in print** (see `contexto.md` section 5).
12. **ALWAYS include the print button and navigation panel** with `.no-print` so they are hidden in the PDF.
13. **ALWAYS apply the Space Optimization Rule** — the exported PDF must look intentionally dense, never half-empty. Adjust spacing, bullets, and layout proportionally to the amount of content available.
