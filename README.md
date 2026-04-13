<div align="center">

# Loom

### Generative UI Designer for AI Agents

**Design beautiful, production-ready UI pages for your AI agents — powered by Claude.**

[![Platform](https://img.shields.io/badge/platform-Windows%2010%2F11-blue?style=flat-square)](https://github.com)
[![Built with Tauri](https://img.shields.io/badge/built%20with-Tauri%20v2-24C8D8?style=flat-square&logo=tauri)](https://tauri.app)
[![Powered by Claude](https://img.shields.io/badge/powered%20by-Claude%20AI-D97706?style=flat-square)](https://claude.ai/code)
[![License](https://img.shields.io/badge/license-MIT-green?style=flat-square)](LICENSE)

[**Download**](#installation) · [**Getting Started**](#getting-started) · [**Features**](#features) · [**Docs**](#working-with-a-design)

</div>

---

## What is Loom?

Loom is a desktop app that turns a plain-text description of an AI agent into **multiple polished UI designs in parallel**. Pick the one you like, refine it with natural language, build out linked pages, then export as HTML, React, or a full deployable Next.js generative UI app — all without writing code.

```
"An analytics agent showing traffic, sessions, and conversion funnels"
        ↓  Claude generates 6 designs in parallel (~15s)
[ Dark Studio ] [ Editorial ] [ Data Dense ] [ Glassmorphism ] [ Minimal ] [ Vibrant ]
        ↓  Pick one, refine with text, add pages, export
```

---

## Requirements

| Requirement | Details |
|-------------|---------|
| **OS** | Windows 10 / 11 (64-bit) |
| **[Claude Code](https://claude.ai/code)** | Must be installed and in your PATH |

After installing Claude Code, verify it works by running `claude --version` in a terminal.

---

## Installation

1. Go to [**Releases**](../../releases) and download **`Loom_0.2.0_x64-setup.exe`**
2. Double-click to run the installer → Next → Install → Finish
3. Launch **Loom** from the Start Menu or Desktop shortcut

---

## Features

<table>
<tr>
<td width="50%" valign="top">

**Design**
- 6 personalities generated in parallel
- Prompt enhancement with Claude
- Import brief from any URL
- Structured prompt builder form
- Preset chips for quick starts

**Refine**
- Natural language refinement
- Section-level targeted edits
- Undo / redo history
- Desktop / tablet / mobile preview
- Light / dark / auto color scheme

</td>
<td width="50%" valign="top">

**Multi-page**
- Add linked pages (Product, Services, Contact…)
- Each page inherits the Home page style
- Refine each page independently
- Download all pages as ZIP

**Export**
- Self-contained HTML file
- PNG screenshot
- Typed React `.tsx` component
- Open in browser / CodeSandbox
- Full deployable Next.js generative UI app

</td>
</tr>
</table>

---

## Getting Started

### 1. Describe your agent

Type what your AI agent does in the prompt area. Be specific about the data it shows.

```
"A customer support agent showing open tickets, NPS trends, CSAT scores, and at-risk accounts"
```

**Quick start options:**
- **Preset chips** — click any chip (Analytics Dashboard, AI Monitor, SaaS Landing…) to auto-fill
- **✦ Enhance** — Claude expands a short prompt into a detailed design brief
- **↗ URL** — paste any website URL, Claude derives a design brief from it
- **🧩 Builder** — structured form (title, sections, data fields, tone) if you prefer guided input

### 2. Generate

Click **Generate** or press `Ctrl + Enter`. Up to 6 personalities run in parallel:

| Personality | Style |
|-------------|-------|
| Dark Studio | Bold, high-contrast dark UI |
| Editorial | Clean, typographic, whitespace-heavy |
| Data Dense | Metric-rich dashboards with tables and charts |
| Glassmorphism | Frosted glass, layered depth |
| Minimal | Ultra-clean, reduced chrome |
| Vibrant | Bright, colorful, energetic |

### 3. Pick and refine

Click a card to open it. Type a change in the bar at the bottom and press **Apply**:

```
"Make the header darker and use green as the primary color"
"Add a sparkline chart next to each metric card"
"Make it feel more like a Bloomberg terminal"
```

Full undo/redo with `Ctrl+Z` / `Ctrl+Shift+Z`.

---

## Working with a Design

### Section editing
Click **✦ Sections** → click any section in the preview → describe the change. Only that section is regenerated, everything else stays.

### Multi-page designs
Click **+ Page**, type a page name (e.g. "Product Page"), and Loom generates it inheriting your Home page's style and all your refinements. Switch between pages using the tab strip — each page can be refined independently.

### Viewport preview
Toggle **Desktop / Tablet / Mobile** to see the design at each breakpoint with a realistic device frame.

---

## Export Options

| Button | Output |
|--------|--------|
| **↓ HTML** | Self-contained `.html` file, works offline |
| **⬛ PNG** | Screenshot of the current view |
| **React tab** | Typed `.tsx` component with syntax highlighting |
| **↗** | Opens in your default browser |
| **↓ ZIP** | All linked pages bundled together |
| **↗ Sandbox** | Opens instantly in CodeSandbox |
| **🚀 Generative UI** | Full deployable Next.js app (see below) |

---

## Generative UI Export

The **🚀 Generative UI** button scaffolds a complete, deployable Next.js app from your design:

```
your-component-agent-ui/
├── app/
│   ├── page.tsx              ← chat UI using useChat
│   └── api/chat/route.ts     ← streamText route with your component as a tool
├── components/
│   └── YourComponent.tsx     ← typed React component with Props interface
├── lib/
│   └── schema.ts             ← Zod schema for AI SDK tool calling
├── package.json
├── tsconfig.json
└── next.config.ts
```

Unzip → `npm install` → `npm run dev` → deploy to Vercel. The AI agent calls the component by name and streams structured props to it at runtime.

---

## Component Registry

**⊕ Register** saves any design as a named, callable component:

1. Give it a name — e.g. `analytics-dashboard`
2. Claude generates a typed React component + matching Zod schema
3. Stored locally in SQLite — retrievable by any AI agent at runtime via `get_gen_ui_component`

---

## Settings

| Setting | Description |
|---------|-------------|
| **Variant count** | Default number of designs to generate (1, 2, 3, 4, or 6) |
| **Auto-Refine** | Second Claude pass to self-critique and improve each design |
| **Token Usage** | Economy (Haiku only) · Balanced (default) · Quality (Sonnet primary) |
| **Brand Kit** | Company name, primary color, tone, and font — injected into every generation |

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

<details>
<summary><strong>"Claude Code not found" banner</strong></summary>

Install Claude Code from [claude.ai/code](https://claude.ai/code) and ensure `claude` is in your system PATH. Restart Loom after installing. Verify with `claude --version` in a terminal.
</details>

<details>
<summary><strong>Generation produces no output / blank preview</strong></summary>

Run `claude --version` in a terminal. If it prompts you to log in, complete the login then try generating again.
</details>

<details>
<summary><strong>Generative UI export is slow (~30s)</strong></summary>

Expected — it runs two Claude passes (HTML → typed TSX, then props → Zod schema) before zipping. Switch to **Economy** mode in Settings to reduce the time.
</details>

<details>
<summary><strong>Port 5173 already in use (dev mode only)</strong></summary>

Kill any process using port 5173 before running `pnpm dev`.
</details>

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Desktop shell | [Tauri v2](https://tauri.app) (Rust) |
| Frontend | React 18, TypeScript, Tailwind CSS |
| State | Zustand + Immer |
| Database | SQLite via r2d2 + rusqlite |
| AI | [Claude Code CLI](https://claude.ai/code) — streamed NDJSON |
| Bundler | Vite 5 |

---

## Development

```bash
# Prerequisites: Rust, Node.js 18+, pnpm

# Install dependencies
pnpm install

# Start dev server
cd apps/desktop && pnpm dev

# TypeScript typecheck
cd apps/renderer && pnpm typecheck

# Rust check (no binary output)
cargo check --manifest-path apps/desktop/src-tauri/Cargo.toml

# Build installer
cd apps/desktop && pnpm tauri build
# Output: apps/desktop/src-tauri/target/release/bundle/nsis/Loom_0.2.0_x64-setup.exe
```

> **Windows note:** Run `taskkill /F /IM loom.exe` before rebuilding to release the file lock.

---

<div align="center">

**Loom v0.2.0** · Built with Tauri v2, Rust, React, and Claude

*"Weave UI for Your AI Agents"*

</div>
