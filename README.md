<div align="center">

# Filtrd

### ATS filters candidates. You filter through ATS.
### *El ATS filtra candidatos. Tú lo atraviesas.*

**Framework de contexto para agentes de IA que genera CVs bilingües compatibles con ATS, con diseño premium. Gratis y open source.**

---

[![License: MIT](https://img.shields.io/badge/Licencia-MIT-yellow.svg?style=flat-square)](LICENSE)
[![Claude AI](https://img.shields.io/badge/Claude-compatible-6b21a8?style=flat-square)](https://claude.ai)
[![ChatGPT](https://img.shields.io/badge/ChatGPT-compatible-10a37f?style=flat-square)](https://chatgpt.com)
[![Gemini](https://img.shields.io/badge/Gemini-compatible-4285F4?style=flat-square)](https://gemini.google.com)
[![Cursor](https://img.shields.io/badge/Cursor-compatible-000000?style=flat-square)](https://cursor.com)
[![Astro](https://img.shields.io/badge/Output-Astro-ff5d00?style=flat-square&logo=astro&logoColor=white)](https://astro.build)
[![100% Gratis](https://img.shields.io/badge/100%25-Gratuito-22c55e?style=flat-square)]()

**Leer en:** [Español](#español) · [English](#english)

</div>

---

## Español

### ¿Qué es Filtrd?

Cada vez que envías un CV, pasa por un sistema ATS (Applicant Tracking System) antes de llegar a cualquier humano. **El 75% de los CVs son descartados automáticamente** por estos filtros, aunque el candidato esté perfectamente cualificado.

**Filtrd invierte eso.**

Son dos archivos de contexto que convierten cualquier agente de IA en un especialista en CVs. Le das tus datos una sola vez y el agente genera un proyecto Astro completo: un CV que los sistemas ATS leen perfectamente y que los reclutadores recuerdan.

---

### Agentes compatibles y cómo usarlo con cada uno

Filtrd funciona con **cualquier agente de IA** que soporte archivos de contexto o system prompts. Adjuntas `contexto.md` y `skill.md` y el agente sabe exactamente qué hacer.

---

#### Ranking para este caso de uso

| Posición | Agente | Por qué |
|:---:|---|---|
| 🥇 | **Claude (Anthropic)** | Mejor seguimiento de instrucciones largas, ventana de 200K tokens, más preciso con CSS y código Astro |
| 🥈 | **Cursor** | Integración directa con el IDE, referencia archivos con `@`, genera y prueba el código en el mismo entorno |
| 🥉 | **Windsurf** | Similar a Cursor, más barato, buena gestión de contexto largo |
| 4 | **ChatGPT + Codex** | Muy capaz pero menos consistente con instrucciones de más de 10K tokens |
| 5 | **Gemini 2.5 Pro** | Contexto muy largo (1M tokens), buena alternativa gratuita |
| 6 | **GitHub Copilot** | Orientado a autocompletado, menos eficiente como agente de tareas largas |

---

#### Claude — el más recomendado

El agente que mejores resultados da con `contexto.md` y `skill.md`. Su ventana de contexto de 200K tokens procesa los dos archivos completos sin perder información.

**Opciones para usar Claude:**

**A) Claude.ai en el navegador (más sencillo)**

1. Ve a [claude.ai](https://claude.ai)
2. Crea una conversación nueva
3. Adjunta `contexto.md` y `skill.md` con el botón de archivo
4. Comparte tus datos profesionales y deja que el agente trabaje

**B) Claude Code — extensión para VS Code / terminal**

Claude Code es la CLI oficial de Anthropic. Se instala como extensión de VS Code o se usa desde el terminal:

```bash
npm install -g @anthropic-ai/claude-code
claude   # Inicia el agente en el directorio actual
```

Con la extensión de VS Code, puedes hacer referencia a los archivos directamente desde el editor.
Requiere plan **Pro o superior** (no funciona con cuenta gratuita en terminal).

**C) Cline — extensión gratuita para VS Code con tu propia API key**

[Cline](https://github.com/cline/cline) es una extensión open source para VS Code que usa la API de Claude directamente. Pagas solo por los tokens que consumes, sin suscripción mensual.

```
VS Code → Extensions → busca "Cline" → instala → configura tu API key de Anthropic
```

**Precios de Claude:**

| Plan | Precio | Incluye | ¿Sirve para Filtrd? |
|---|---|---|---|
| Free | Gratis | Claude.ai web, límite de mensajes diarios | ✅ Sí, con límites |
| Pro | $20/mes | Claude.ai sin límites, Claude Code CLI/VSCode | ✅ Recomendado |
| Max | $100–200/mes | Uso intensivo, API priorizada | ✅ Para uso profesional |
| API (pago por uso) | $3–25 / 1M tokens | Acceso directo sin suscripción | ✅ Con Cline o Continue |

---

#### ChatGPT + Codex (OpenAI)

ChatGPT puede usar `contexto.md` y `skill.md` adjuntando los archivos en la conversación. Codex CLI es el agente de terminal de OpenAI, incluido en los planes de ChatGPT.

**Cómo usarlo:**

1. Ve a [chatgpt.com](https://chatgpt.com) (o instala Codex CLI)
2. Adjunta `contexto.md` y `skill.md` usando el botón de archivos
3. Indica que quiere seguir el flujo descrito en `skill.md`

**Codex CLI (terminal):**

```bash
npm install -g @openai/codex
codex   # Agente en el terminal, similar a Claude Code
```

**Precios de ChatGPT / Codex:**

| Plan | Precio | Acceso a Codex | ¿Sirve para Filtrd? |
|---|---|---|---|
| Free | Gratis | Acceso limitado de prueba | ⚠️ Limitado |
| Plus | $20/mes | Sí, acceso completo | ✅ Funciona bien |
| Pro | $200/mes | Sí, con GPT-5 y mayor límite | ✅ Para uso intensivo |
| API (pago por uso) | $1.50–30 / 1M tokens | Solo via API key | ✅ Con Cline u otros |

---

#### Cursor — mejor opción para IDE

Cursor es un editor de código (fork de VS Code) con agente integrado. La ventaja para Filtrd es que puedes adjuntar `contexto.md` y `skill.md` con `@archivo` y el agente genera el proyecto Astro directamente en el editor, lo ejecuta y ves el resultado en tiempo real.

**Cómo usarlo:**

1. Descarga [Cursor](https://cursor.com) (reemplaza VS Code, misma interfaz)
2. Abre la carpeta del proyecto
3. En el chat del agente escribe: `@contexto.md @skill.md` y comparte tus datos
4. El agente genera los archivos Astro dentro del mismo editor

**Precios de Cursor:**

| Plan | Precio | Límite de agente | ¿Sirve para Filtrd? |
|---|---|---|---|
| Hobby (gratis) | Gratis | 50 peticiones premium/mes | ⚠️ Para probar |
| Pro | $20/mes | Sin límite (Auto mode) | ✅ Recomendado |
| Business | $40/usuario/mes | Sin límite + administración | ✅ Para equipos |

---

#### Windsurf — alternativa más barata a Cursor

Windsurf es otro editor basado en VS Code con agente integrado (Cascade). Misma mecánica que Cursor pero más económico.

**Precios de Windsurf:**

| Plan | Precio | Créditos/mes | ¿Sirve para Filtrd? |
|---|---|---|---|
| Free | Gratis | 25 créditos | ⚠️ Muy limitado |
| Pro | $15/mes | 500 créditos | ✅ Funciona bien |
| Teams | $30/usuario/mes | 500 créditos por miembro | ✅ Para equipos |

---

#### Gemini (Google)

Gemini 2.5 Pro tiene una ventana de contexto de 1M de tokens (la mayor del mercado) y funciona bien con los archivos de Filtrd. Google AI Studio es completamente gratuito para pruebas.

**Cómo usarlo:**

1. Ve a [aistudio.google.com](https://aistudio.google.com) (gratis)
2. Crea un prompt nuevo y pega el contenido de `contexto.md` y `skill.md` en el system prompt
3. Inicia la conversación con tus datos profesionales

**Precios de Gemini:**

| Opción | Precio | Límite | ¿Sirve para Filtrd? |
|---|---|---|---|
| Google AI Studio | Gratis | Rate limits (RPM) | ✅ Buena opción gratuita |
| Gemini Advanced (Google One AI Pro) | $19.99/mes | Sin límites en web | ✅ Funciona |
| API Gemini 2.5 Pro | $1.25–2.50 / 1M tokens | Pago por uso | ✅ Con Cline u otros |
| API Gemini Flash | $0.10 / 1M tokens | Pago por uso | ⚠️ Menor calidad |

---

#### GitHub Copilot — extensión para VS Code / JetBrains

Copilot está integrado en VS Code y JetBrains. Para Filtrd, la forma más eficaz es usar Copilot Chat con los archivos adjuntos. No es la opción más potente como agente de tareas largas, pero funciona.

**Cómo usarlo en VS Code:**

1. Instala la extensión GitHub Copilot desde el marketplace de VS Code
2. Abre Copilot Chat (`Ctrl+Shift+I`)
3. Usa `#contexto.md` y `#skill.md` para adjuntar los archivos al chat
4. Sigue el flujo de `skill.md`

**Precios de GitHub Copilot:**

| Plan | Precio | Acceso | ¿Sirve para Filtrd? |
|---|---|---|---|
| Free | Gratis | 2.000 sugerencias/mes, chat limitado | ⚠️ Muy limitado para esto |
| Pro | $10/mes | Chat sin límites, agente en la nube | ✅ Funciona |
| Pro+ | $39/mes | Todos los modelos frontier | ✅ Mejor rendimiento |

---

#### Otras extensiones para VS Code (gratuitas con tu propia API key)

Si ya tienes una API key de Anthropic, OpenAI o Google, estas extensiones permiten usar Filtrd sin pagar suscripciones mensuales:

| Extensión | Modelos compatibles | Coste | Link |
|---|---|---|---|
| **Cline** | Claude, GPT-4, Gemini | Gratis + tu API key | [marketplace](https://marketplace.visualstudio.com/items?itemName=saoudrizwan.claude-dev) |
| **Continue** | Claude, GPT, Gemini, Ollama | Gratis + tu API key | [continue.dev](https://continue.dev) |
| **Aider** | Claude, GPT, Gemini | Gratis + tu API key (terminal) | [aider.chat](https://aider.chat) |

Con estas extensiones pagas solo por lo que consumes en la API, sin suscripción fija. Para un CV completo con Filtrd, el coste estimado en API es inferior a $0.10 usando Claude Sonnet o Gemini Flash.

---

### Cómo funciona

```
Tus datos profesionales
        │
        ▼
  Abres tu agente favorito y adjuntas:
  ├── contexto.md   ← sistema de diseño y reglas CSS
  └── skill.md      ← instrucciones del agente
        │
        ▼
  El agente genera tu proyecto Astro
  ├── src/pages/index.astro               ← CV bilingüe (ES + EN)
  ├── src/pages/accenture-analista.astro  ← Variante empresa #1
  ├── src/pages/endesa-datos.astro        ← Variante empresa #2
  └── src/styles/global.css              ← CSS personalizado (sin Tailwind)
        │
        ▼
  npm run dev → Vista previa local
  Ctrl+P → PDF perfecto en A4
```

---

### Pasos para usarlo

#### 1. Elige tu agente y adjunta los archivos

Descarga o clona este repositorio. Luego elige tu agente preferido de la lista de arriba y adjunta `contexto.md` y `skill.md`.

#### 2. Comparte tus datos profesionales

Cuéntale al agente tu experiencia, formación, habilidades y enlaza tu GitHub si tienes. El agente hará preguntas y creará un archivo `[nombre]-context.md` con toda tu información organizada.

#### 3. Recibe el proyecto Astro completo

El agente genera todo el código. Para ejecutarlo:

```bash
npm create astro@latest mi-cv
# Sustituye los archivos generados en src/
npm install
npm run dev      # Vista previa en localhost:4321
npm run build    # Build de producción
```

#### 4. Genera variantes para cada oferta de empleo

Pega la descripción del trabajo en el agente. Recibirás:
- Porcentaje de coincidencia con tu perfil
- Nueva página con las palabras clave de la oferta integradas
- Color de acento adaptado al branding de la empresa
- Verificación ATS incluida

#### 5. Exporta a PDF

Navegador → `Ctrl+P` → Guardar como PDF. El CSS garantiza formato A4, fondo blanco limpio y una página por idioma.

---

### Qué hay en cada archivo

```
filtrd/
├── contexto.md     # Sistema de diseño completo
└── skill.md        # Instrucciones del agente
```

**`contexto.md`** — diseño, tipografía Inter, grid de dos columnas, UI glassmorphism, 8 reglas CSS obligatorias, componente de línea de tiempo, optimización de espacio, variantes de color por empresa.

**`skill.md`** — protocolo de recogida de datos, generación bilingüe, adaptación a ofertas, 13 reglas absolutas que el agente no puede saltarse.

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
| Compatible con cualquier agente de IA | ✅ | ❌ | ❌ |

---

### Contribuir

Las contribuciones son bienvenidas:
- Variantes de color para más empresas
- Reglas CSS para casos especiales
- Guías de uso con otros agentes no listados
- Traducciones de `skill.md`

---

---

## English

### What is Filtrd?

Every time you submit a CV, it passes through an ATS (Applicant Tracking System) before reaching any human. **75% of CVs are automatically rejected** by these filters, even when the candidate is a perfect fit.

**Filtrd flips that.**

Two context files that turn any AI agent into a CV specialist. Give it your data once and the agent generates a complete Astro project: a CV that ATS systems read perfectly and that recruiters remember.

---

### Compatible Agents and How to Use Each

Filtrd works with **any AI agent** that supports context files or system prompts. Attach `contexto.md` and `skill.md` and the agent knows exactly what to do.

---

#### Ranking for This Use Case

| Rank | Agent | Why |
|:---:|---|---|
| 🥇 | **Claude (Anthropic)** | Best long-instruction following, 200K token window, most precise with CSS and Astro code |
| 🥈 | **Cursor** | Direct IDE integration, reference files with `@`, generates and runs code in the same environment |
| 🥉 | **Windsurf** | Similar to Cursor, cheaper, good long-context handling |
| 4 | **ChatGPT + Codex** | Very capable but less consistent with 10K+ token instruction files |
| 5 | **Gemini 2.5 Pro** | Huge context (1M tokens), good free alternative |
| 6 | **GitHub Copilot** | Oriented toward autocomplete, less efficient for long agentic tasks |

---

#### Claude — Most Recommended

The agent that gives the best results with `contexto.md` and `skill.md`. Its 200K token context window processes both files completely without losing information.

**Ways to use Claude:**

**A) Claude.ai in the browser (easiest)**

1. Go to [claude.ai](https://claude.ai)
2. Start a new conversation
3. Attach `contexto.md` and `skill.md` using the file button
4. Share your professional data and let the agent work

**B) Claude Code — VS Code extension / terminal**

Claude Code is Anthropic's official CLI. Install as a VS Code extension or use from terminal:

```bash
npm install -g @anthropic-ai/claude-code
claude   # Starts the agent in the current directory
```

Requires **Pro plan or higher** (does not work with free account in terminal).

**C) Cline — free VS Code extension with your own API key**

[Cline](https://github.com/cline/cline) is an open source VS Code extension that uses the Claude API directly. You pay only for tokens consumed, no monthly subscription.

```
VS Code → Extensions → search "Cline" → install → configure your Anthropic API key
```

**Claude Pricing:**

| Plan | Price | Includes | Works for Filtrd? |
|---|---|---|---|
| Free | Free | Claude.ai web, daily message limit | ✅ Yes, with limits |
| Pro | $20/mo | Unlimited Claude.ai, Claude Code CLI/VSCode | ✅ Recommended |
| Max | $100–200/mo | Heavy usage, priority API | ✅ Professional use |
| API (pay-as-you-go) | $3–25 / 1M tokens | Direct access, no subscription | ✅ With Cline or Continue |

---

#### ChatGPT + Codex (OpenAI)

ChatGPT can use `contexto.md` and `skill.md` by attaching the files in the conversation. Codex CLI is OpenAI's terminal agent, included in ChatGPT plans.

**Codex CLI (terminal):**

```bash
npm install -g @openai/codex
codex
```

**ChatGPT / Codex Pricing:**

| Plan | Price | Codex Access | Works for Filtrd? |
|---|---|---|---|
| Free | Free | Limited trial access | ⚠️ Very limited |
| Plus | $20/mo | Full access | ✅ Works well |
| Pro | $200/mo | GPT-5, higher limits | ✅ Heavy use |
| API (pay-as-you-go) | $1.50–30 / 1M tokens | API key only | ✅ With Cline or others |

---

#### Cursor — Best IDE Option

Cursor is a code editor (VS Code fork) with a built-in agent. The advantage for Filtrd: attach `contexto.md` and `skill.md` with `@file` and the agent generates the Astro project directly inside the editor, runs it, and you see results in real time.

**How to use:**

1. Download [Cursor](https://cursor.com) (replaces VS Code, same interface)
2. Open your project folder
3. In the agent chat type: `@contexto.md @skill.md` and share your data
4. The agent generates Astro files directly in the editor

**Cursor Pricing:**

| Plan | Price | Agent Limit | Works for Filtrd? |
|---|---|---|---|
| Hobby (free) | Free | 50 premium requests/mo | ⚠️ To try it out |
| Pro | $20/mo | Unlimited (Auto mode) | ✅ Recommended |
| Business | $40/user/mo | Unlimited + admin | ✅ For teams |

---

#### Windsurf — Cheaper Cursor Alternative

Windsurf is another VS Code-based editor with a built-in agent (Cascade). Same mechanics as Cursor but more affordable.

**Windsurf Pricing:**

| Plan | Price | Credits/mo | Works for Filtrd? |
|---|---|---|---|
| Free | Free | 25 credits | ⚠️ Very limited |
| Pro | $15/mo | 500 credits | ✅ Works well |
| Teams | $30/user/mo | 500 credits per member | ✅ For teams |

---

#### Gemini (Google)

Gemini 2.5 Pro has a 1M token context window (largest on the market) and works well with Filtrd's files. Google AI Studio is completely free for testing.

**How to use:**

1. Go to [aistudio.google.com](https://aistudio.google.com) (free)
2. Create a new prompt and paste `contexto.md` and `skill.md` content into the system prompt
3. Start the conversation with your professional data

**Gemini Pricing:**

| Option | Price | Limit | Works for Filtrd? |
|---|---|---|---|
| Google AI Studio | Free | Rate limits (RPM) | ✅ Good free option |
| Google One AI Pro | $19.99/mo | No limits on web | ✅ Works |
| API Gemini 2.5 Pro | $1.25–2.50 / 1M tokens | Pay-as-you-go | ✅ With Cline or others |
| API Gemini Flash | $0.10 / 1M tokens | Pay-as-you-go | ⚠️ Lower quality |

---

#### GitHub Copilot — VS Code / JetBrains Extension

Copilot is integrated in VS Code and JetBrains. For Filtrd, use Copilot Chat with attached files. Not the most powerful option for long agentic tasks, but functional.

**How to use in VS Code:**

1. Install the GitHub Copilot extension from the VS Code marketplace
2. Open Copilot Chat (`Ctrl+Shift+I`)
3. Use `#contexto.md` and `#skill.md` to attach files to the chat
4. Follow the `skill.md` workflow

**GitHub Copilot Pricing:**

| Plan | Price | Access | Works for Filtrd? |
|---|---|---|---|
| Free | Free | 2,000 completions/mo, limited chat | ⚠️ Very limited |
| Pro | $10/mo | Unlimited chat, cloud agent | ✅ Works |
| Pro+ | $39/mo | All frontier models | ✅ Best performance |

---

#### Free VS Code Extensions (Bring Your Own API Key)

If you already have an API key from Anthropic, OpenAI, or Google, these extensions let you use Filtrd without paying monthly subscriptions:

| Extension | Compatible Models | Cost | Link |
|---|---|---|---|
| **Cline** | Claude, GPT-4, Gemini | Free + your API key | [marketplace](https://marketplace.visualstudio.com/items?itemName=saoudrizwan.claude-dev) |
| **Continue** | Claude, GPT, Gemini, Ollama | Free + your API key | [continue.dev](https://continue.dev) |
| **Aider** | Claude, GPT, Gemini | Free + your API key (terminal) | [aider.chat](https://aider.chat) |

With these extensions you pay only for API consumption. Estimated cost for a full CV with Filtrd: under **$0.10** using Claude Sonnet or Gemini Flash.

---

### How It Works

```
Your professional data
        │
        ▼
  Open your preferred agent and attach:
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

---

### Usage Steps

#### 1. Choose your agent and attach the files

Download or clone this repo. Then choose your preferred agent from the list above and attach `contexto.md` and `skill.md`.

#### 2. Share your professional data

Tell the agent your experience, education, skills, and link your GitHub if you have one. The agent will ask questions and create a `[name]-context.md` file with everything organized.

#### 3. Receive the full Astro project

The agent generates all the code. To run it:

```bash
npm create astro@latest my-cv
# Replace generated files in src/
npm install
npm run dev      # Preview at localhost:4321
npm run build    # Production build
```

#### 4. Generate variants for each job offer

Paste the job description. You'll get:
- Match percentage with your profile
- New page with the offer's keywords naturally integrated
- Accent color adapted to the company's branding
- ATS verification included

#### 5. Export to PDF

Browser → `Ctrl+P` → Save as PDF. The CSS guarantees A4 format, clean white background, and one page per language.

---

### What's in Each File

```
filtrd/
├── contexto.md     # Full design system
└── skill.md        # Agent instructions
```

**`contexto.md`** — design system, Inter typography, two-column grid, glassmorphism UI, 8 mandatory CSS rules, timeline component, space optimization, company color variants.

**`skill.md`** — data collection protocol, bilingual generation, job offer adaptation, 13 absolute rules the agent cannot break.

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
| Works with any AI agent | ✅ | ❌ | ❌ |

---

### Contributing

Contributions welcome:
- Company color variants for `contexto.md`
- CSS rules for special layout cases
- Usage guides for unlisted agents
- Translations of `skill.md`

---

<div align="center">

**Licencia MIT — úsalo, compártelo y adáptalo sin restricciones.**

**MIT License — use it, share it, and adapt it freely.**

---

Hecho con IA · Para candidatos que se niegan a ser filtrados por una máquina

Made with AI · For candidates who refuse to be filtered out by a machine

---

Si te ha sido útil, deja una ⭐ — ayuda a que otros lo encuentren.

If this helped you, leave a ⭐ — it helps others find it.

</div>
