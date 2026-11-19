# Project Sycamore (梧桐计划)

Anfu Road high-density urban sandbox vertical slice built with **Unreal Engine 5 (C++)** and an **AI-Agent (Devin) driven CI/CD workflow**.

## Core Architecture
- **Crowd System (`/Plugins/AnfuCrowdSystem`)**: Mass Entity (ECS) + ZoneGraph + MassAvoidance (RVO) + SmartObjects + VAT rendering.
- **Automation & Profiling**: Headless `UnrealEditor-Cmd -NullRHI` stress test (500 entities / 60s) via GitHub Actions Self-Hosted Runner with `CSVProfiler` frame-time gating (`GameThread < 10ms`, `P99 < 16.6ms`).

## Roadmap
- [x] Architecture RFC & Repo Scaffolding
- [ ] `DEVIN.md` & `MassCrowd_RFC.md` integration
- [ ] Core `MassProcessor` C++ implementation via Devin PRs
