# Deadlock Prevention and Recovery Toolkit

## Overview

A fully interactive OS simulation toolkit for visualizing, detecting, preventing, and recovering from deadlocks. Built as a full-stack React + Vite web app with an Express API backend and PostgreSQL database.

## Stack

- **Monorepo tool**: pnpm workspaces
- **Node.js version**: 24
- **Package manager**: pnpm
- **TypeScript version**: 5.9
- **Frontend framework**: React + Vite (artifacts/deadlock-toolkit)
- **Styling**: Tailwind CSS v4, shadcn/ui components
- **State management**: Zustand
- **Animations**: Framer Motion
- **Charts**: Recharts
- **Routing**: Wouter
- **API framework**: Express 5
- **Database**: PostgreSQL + Drizzle ORM
- **Validation**: Zod (`zod/v4`), `drizzle-zod`
- **API codegen**: Orval (from OpenAPI spec)
- **Build**: esbuild (CJS bundle)

## Key Features

- **Interactive Simulator**: Drag-and-drop Resource Allocation Graph with animated SVG edges
- **Banker's Algorithm**: Step-by-step safety check with safe sequence output
- **Wait-For Graph**: Cycle detection for deadlock identification
- **Recovery Strategies**: Process termination and resource preemption
- **Matrix View**: Allocation, Maximum, Need/Request, Available matrices
- **Predefined Scenarios**: 6 built-in scenarios (beginner to advanced)
- **Simulation History**: Save and reload simulation states
- **Learn Page**: Educational content on deadlock theory and algorithms

## Pages

- `/` — Main simulator with RAG visualization and algorithm controls
- `/scenarios` — Predefined deadlock scenarios library
- `/history` — Saved simulations with stats dashboard
- `/learn` — Educational content on deadlock concepts

## Key Commands

- `pnpm run typecheck` — full typecheck across all packages
- `pnpm run build` — typecheck + build all packages
- `pnpm --filter @workspace/api-spec run codegen` — regenerate API hooks and Zod schemas
- `pnpm --filter @workspace/db run push` — push DB schema changes (dev only)
- `pnpm --filter @workspace/api-server run dev` — run API server locally
- `pnpm --filter @workspace/deadlock-toolkit run dev` — run frontend locally

## Architecture

- `artifacts/deadlock-toolkit/` — React frontend
  - `src/lib/deadlock-algorithms.ts` — Banker's Algorithm and Wait-For graph (client-side)
  - `src/lib/simulator-store.ts` — Zustand state management
  - `src/pages/` — Simulator, Scenarios, History, Learn pages
  - `src/components/simulator/` — RAG graph, matrix view, execution log, process panel
- `artifacts/api-server/` — Express API server
  - `src/routes/simulations.ts` — CRUD + stats for simulations
  - `src/routes/scenarios.ts` — List predefined scenarios
- `lib/db/src/schema/` — Drizzle schema (simulations, scenarios tables)
- `lib/api-spec/openapi.yaml` — OpenAPI spec (source of truth)
