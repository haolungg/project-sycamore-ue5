# MingSha (明朝杀)

A Ming Dynasty-themed multiplayer tactical card & gacha WeChat Mini Game built with a **TypeScript Monorepo (Cocos Creator + Colyseus)** and an **AI-Agent (Devin) driven CI/CD workflow**.

## Core Architecture
- **Pure TS Rules Engine (`packages/engine`)**: FSM + `PriorityEventResolver` (priority event queue & resolution stack) for nested skill chains (朱棣【靖难】、朱允炆【削藩】、朱元璋【诛功/废相】、崇祯【勤政/煤山】), featuring built-in infinite-loop circuit breaking (`depth > 16`, max 256 steps) and immutable `ActionLog[]` replay for reconnection.
- **Authoritative Server (`packages/server`)**: Node.js + Colyseus (`0.15.20`) WebSocket room synchronization, Redis room hot-state & matchmaking, PostgreSQL gacha pity counter & card pool storage.
- **Automation & Benchmarking**: Headless 1,000-match AI vs. AI stress testing via Vitest (`1.6.0`), gating PR merges on **0 infinite loops / crashes** and **average turn resolution < 5ms**.

## Tech Stack
- **Runtime**: Node.js `>= 20.11.0` / `pnpm@9.1.0`
- **Dependencies**: `typescript@5.4.5` (`strict: true`), `colyseus@0.15.20`, `zod@3.23.8`, `vitest@1.6.0`, `tsx@4.11.0`

## Workspace Structure
```text
mingsha-monorepo/
├── pnpm-workspace.yaml
├── package.json
└── packages/
    ├── engine/
    │   ├── src/
    │   │   ├── types/engine.ts
    │   │   ├── core/PriorityEventResolver.ts
    │   │   └── skills/
    │   └── tests/
    └── server/
        └── src/rooms/MingShaRoom.ts
```

## Roadmap
- [x] Architecture RFC, Core TS Interfaces (`engine.ts`) & Monorepo Scaffolding
- [ ] `DEVIN.md` & `PriorityEventResolver.ts` + Vitest suite via Devin PR #1
- [ ] Ming Generals (`朱元璋`, `朱棣`, `朱允炆`, `崇祯`) skill handlers
- [ ] 1,000-game headless AI simulation CI gate & Colyseus room integration
