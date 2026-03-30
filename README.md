# Loom — Generative UI Designer for AI Agents

**Loom** is a desktop tool that uses Claude AI to design beautiful, production-ready UI pages for AI agents. Describe what your agent does, and Loom generates multiple visual designs in parallel — ready to download, export as React, or scaffold into a full deployable Next.js app.

---

## Requirements

- **Windows 10 / 11** (64-bit)
- **[Claude Code](https://claude.ai/code)** installed and available in your PATH
  - Loom uses the `claude` CLI under the hood for all generation
  - After installing, verify it works: open a terminal and run `claude --version`

---

## Installation

1. Download **`Loom_0.1.0_x64-setup.exe`**
2. Double-click to run the installer
3. Follow the Next → Install → Finish wizard
4. Launch **Loom** from the Start Menu or Desktop shortcut

---

## Getting Started

### 1. Describe your agent

Type a description of what your AI agent does in the left panel. Be specific about the data it outputs and the purpose of the UI.

**Examples:**
- *"An analytics agent that monitors website traffic, user sessions, and conversion funnels"*
- *"A research agent that returns summaries, sources, and confidence scores"*
- *"A customer support agent showing ticket status, NPS trends, and at-risk accounts"*

**Shortcuts to get started:**
- Click any **preset chip** (Analytics Dashboard, AI Monitor, SaaS Landing, etc.) to auto-fill a prompt
- Click **✦ Enhance** to have Claude expand a short description into a rich design brief
- Click **↗ URL** to import a design brief from any existing website
- Click **🧩 Builder** to use the structured prompt form instead of free text

### 2. Choose how many variants

Select **1, 2, 3, 4, or 6** variants using the pill buttons at the top of the sidebar. More variants = more design directions generated in parallel.

### 3. Generate

Click **Generate** (or press `Ctrl + Enter`). Loom runs up to 6 design personalities in parallel:

| Personality | Style |
|-------------|-------|
| Dark Studio | Bold, high-contrast dark UI |
| Editorial | Clean, typographic, whitespace-heavy |
| Data Dense | Metric-rich dashboards with tables and charts |
| Glassmorphism | Frosted glass, layered depth |
| Minimal | Ultra-clean, reduced chrome |
| Vibrant | Bright, colorful, energetic |

### 4. Pick a design

The variant picker shows all generated designs as cards. Click any card to open it in the full preview.

---

## Working with a Design

### Refine
Type a refinement instruction at the bottom and press **Apply** — Claude updates the design while preserving its style. Full undo/redo history (`Ctrl+Z` / `Ctrl+Shift+Z`).

### Section-level editing
Click **✦ Sections** to enter section mode — click any part of the preview to select a section, then refine just that area without regenerating the whole page.

### Preview at different sizes
Toggle **Desktop / Tablet / Mobile** in the toolbar to see how the design responds at each viewport. Tablet and mobile show a realistic device frame with correct dimensions and no horizontal scroll.

### Multi-page designs
Click **+ Page** to add linked pages (e.g. a detail view or settings page). All pages share the same style. Download the full set as a ZIP.

---

## Export Options

| Action | Button | What you get |
|--------|--------|--------------|
| Download HTML | **↓ HTML** | Self-contained `.html` file |
| Download PNG | **⬛ PNG** | Screenshot of the current view |
| Export React | **React** tab | Typed `.tsx` component with shiki-highlighted code |
| Open in browser | **↗** | Opens in your default browser |
| Multi-page ZIP | **↓ ZIP** | All linked pages as a bundle |
| Export to CodeSandbox | **↗ Sandbox** | Opens design in CodeSandbox instantly |
| Generative UI App | **🚀 Generative UI** | Full deployable Next.js app with AI SDK tool + typed component |

---

## Generative UI Export

The **🚀 Generative UI** button converts your design into a complete, deployable Next.js application:

1. Claude converts the HTML design into a **typed React component** with a `Props` interface
2. Claude generates a matching **Zod schema** for AI SDK tool calling
3. Loom scaffolds a full **Next.js App Router project** with:
   - `app/page.tsx` — chat UI using `useChat`
   - `app/api/chat/route.ts` — `streamText` route with your component as a tool
   - `components/<YourComponent>.tsx` — the typed React component
   - `lib/schema.ts` — Zod schema for the tool
   - `package.json`, `tsconfig.json`, `next.config.ts`

The resulting ZIP can be unzipped, `npm install`-ed, and deployed to Vercel immediately.

---

## Component Registry

The **⊕ Register** button saves any design as a named component in the local registry:

1. Enter a name (e.g. `analytics-dashboard`) and optional description
2. Claude generates a typed React component + Zod schema
3. The component is stored in Loom's SQLite database

Registered components can be retrieved by name at runtime by AI agents, enabling dynamic UI selection based on context.

---

## History

The **Recent** panel in the left sidebar shows saved designs as thumbnail cards (2 per row). Designs are auto-saved when you pick a variant.

- **Open** — reload the design into the preview
- **↺ Rework** — reuse the prompt to generate fresh variants
- **✕** — delete (click to arm, click again to confirm)
- **Search** — filter by prompt text
- **Load more** — shows 10 at a time

---

## Prompt Tips

| Goal | Tip |
|------|-----|
| Better results | Use **✦ Enhance** to expand a short prompt into a richer brief |
| Reference an existing UI | Use **↗ URL** to import from any website |
| Structured input | Click **🧩 Builder** to fill a form (title, sections, data fields, tone) |
| Consistent brand | Set your brand kit in **Settings** — colors, tone, and font preferences are injected into every generation |
| Reduce token usage | Set **Token Usage → Economy** in Settings to use Haiku-only mode |

---

## Settings

Click the **⚙** gear icon in the top-right to open Settings:

### Claude
- **Connection status** — shows which account is active and whether `claude` is found in PATH

### Generation Defaults
- **Variant count** — default number of designs to generate (1, 2, 3, 4, or 6)
- **Auto-Refine** — runs a second Claude pass after generation to self-critique and improve quality

### Token Usage
Control which Claude model is used for all generation in the current session:

| Mode | Model | Speed | Cost |
|------|-------|-------|------|
| Economy | Haiku only | Fastest | Lowest |
| Balanced | Haiku + Sonnet fallback | Default | Default |
| Quality | Sonnet primary | Slower | Higher |

> Resets to Balanced on restart.

### Brand Kit
- **Company name** — injected into all generated designs
- **Primary color** — hex color used as the brand accent
- **Tone** — e.g. "professional", "playful", "minimal"
- **Font preference** — typeface hint passed to the generation prompt

---

## Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Ctrl + Enter` | Generate designs |
| `Ctrl + Z` | Undo last refine |
| `Ctrl + Shift + Z` | Redo |
| `Esc` | Exit fullscreen preview |

---

## Troubleshooting

**"Claude Code not found" banner**
→ Install Claude Code from [claude.ai/code](https://claude.ai/code) and ensure `claude` is in your system PATH. Restart Loom after installing.

**Generation produces no output / blank preview**
→ Open a terminal and run `claude --version`. If it prompts you to log in, complete the login then try again in Loom.

**Tablet / mobile preview has horizontal scroll**
→ Update to the latest installer — this was fixed by injecting proper viewport constraints into the preview HTML for device views.

**Generative UI export is slow (~30s)**
→ This is expected — it runs two Claude passes (HTML→TSX, then props→Zod schema) before assembling the ZIP. Set Token Usage to Economy in Settings to speed it up.

---

## About

Loom v0.1.0 — Built with Tauri v2, Rust, React, and Claude.

> *"Weave UI for Your AI Agents"*
