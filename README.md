# Finos

**Multi-platform workspace app with real-time collaboration, Intelligence-driven intelligence, and seamless web/desktop sync.**

> Finos is a production workspace platform built on a monorepo architecture spanning Next.js web, Tauri desktop, and edge API. Real-time state syncing between platforms, AI-augmented task intelligence, and typed SQL schema bridges enable teams to collaborate efficiently across devices.

## Architecture

```
Browser / Desktop ──┬──> Finos Web (Next.js 15, CF Workers)
                   │         │
                   │         ├─> Supabase Auth
                   │         ├─> Shared State Service
                   │         └─> Voice Registry
                   │
                   ├──> Finos Desktop (Tauri 2.x, React 19)
                   │         └─> Local state ↔ Web sync
                   │
                   └──> Finos API (Hono, Cloudflare Workers)
                            ├─> SQL Bridge (typed views)
                            ├─> AI Engine (LLM integration)
                            └─> Intel Module (analytics)
```

## Tech Stack

| Layer | Tech | Purpose |
|-------|------|---------|
| **Frontend (Web)** | Next.js 15, React 19, Vite | SSR + client-side routing, marketing + workspace |
| **Frontend (Desktop)** | Tauri 2.x, React 19, Vite | Native desktop app with OS-level integrations |
| **UI Layer** | TypeScript, Zod schemas, voice registry | Shared component library + design tokens |
| **Backend (API)** | Hono, Cloudflare Workers | Edge API — no cold starts, globally distributed |
| **Database** | Supabase (PostgreSQL) | Auth, state storage, real-time subscriptions |
| **State Sync** | Custom layer | Web/desktop state synchronization, conflict resolution |
| **AI Integration** | LLM API | Task intelligence, suggestions, analysis |
| **Type Safety** | TypeScript strict, Zod | End-to-end schema validation, typed SQL views |

## What's Built

### Apps
- **finos-web** — Next.js 15 SPA + marketing landing page, Supabase auth, live workspace
- **finos-desktop** — Tauri 2.x native app (Windows/macOS/Linux), local sync with web state
- **finos-api** — Hono API on Cloudflare Workers, serves both web and desktop

### Packages
- **ui** — React 19 component library, design tokens, styling (Syne/DM Sans/JetBrains Mono)
- **sql-bridge** — Typed views client, Zod schema generation from Postgres, query builder
- **ai-engine** — LLM API integration, prompt caching, streaming responses
- **intel** — Analytics module, insights generation, trend detection
- **voice** — Voice input/output registry, audio processing utilities

## Key Engineering Details

**Multi-Platform Sync**
- Web and desktop apps share real-time state via Supabase subscriptions
- Conflict-free merging of concurrent edits (CRDT-inspired)
- Optimistic updates on both platforms

**Type-Safe Database**
- SQL Bridge generates TypeScript types from Postgres schema
- Zod schemas for runtime validation
- Strongly-typed query results, zero stringly-typed columns

**AI Integration**
- LLM API with extended thinking (5-min prompt cache TTL)
- Streaming responses for long-running analysis
- Structured output via Zod schemas

**Design System**
- Sidebar navigation + live clock widget
- AI command bar (global search + action trigger)
- Dark-first aesthetic with red accent (#e94560)
- Mobile-responsive with GlobalDock support

**Performance**
- Next.js 15 with RSC (React Server Components)
- Edge runtime on Cloudflare Workers (zero cold starts)
- Client-side caching via SWR + React Query
- Playwright E2E suite for regression testing

## Recent Additions (Last 30 Days)

- Tauri desktop app (Windows/macOS/Linux) with identical UX to web surface
- Multi-platform state sync — real-time web ↔ desktop parity
- Supabase auth integration with SSR cookie-based sessions
- AI command bar with LLM integration and extended thinking
- Tax forecasting screen wired to finos-api
- Playwright E2E regression test suite
- ESLint strict mode (0 errors, full TypeScript + React + Next.js coverage)
- Redesigned sidebar navigation with live clock widget

## Scale

| Metric | Value |
|--------|-------|
| Workspace packages | 5 (ui, sql-bridge, ai-engine, intel, voice) |
| Apps | 3 (web, desktop, api) |
| Component primitives | 10+ (Button, Card, Modal, Input, Toast, etc.) |
| SQL-typed views | 15+ (auto-generated from schema) |
| Platforms | 3 (Web, Windows desktop, macOS desktop) |
| Languages | TypeScript (100%) |

---

Built with Next.js 15, Tauri 2.x, Hono, Cloudflare Workers, and Supabase. Designed for solo builders and small teams.

---

*Built by Frxncois — not open source.*
