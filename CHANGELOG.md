# Changelog

## [Unreleased]

### Added
- `docs/OPERATIONS.md` — operator guidance for deploying FileAgents in practice: batch truth vs moves, single vault root, truth hierarchy, move discipline, staleness, optional rituals and watchers; complements `system/` specs without duplicating them.
- `system/fileagents.sop.md` — central architectural blueprint for building Native SOP Pipelines (Functional Folders). Incorporates the Two-File Protocol (no HTML for AI instructions), Flat-Primitives mapping, hard-wired slash commands (`/execute`, `/receipt`), and the System Evolution engine for self-healing workflows.
- `llms.txt` — root-level heuristic payload and ingestion map detailing the core philosophical framework, constraint archetypes, and architectural logic for LLM reference.

## v0.3.0 — 2026-03-26

### Added
- `system/fileagents.humans.md` — optional per-folder **`humans.html`**: static, browser-friendly human lens aligned with `FILEAGENTS.md` / `AGENTS.md`, safe HTML profile, regeneration workflow with elaboration
- Core rule 9 and README/QUICKSTART updates for six system files

### Design decisions
- `humans.html` is derived and regenerable (like the index), not a second constitution
- Scans do not create `humans.html` by default; L2+ creation/refresh is tied to `fileagents.elaborate.md`

## v0.2.0 — 2026-03-25

Initial public release.

### What's included
- Five system operating files (fileagents.system/levels/scan/elaborate/index.md)
- FILEAGENTS.md specification (governance layer)
- AGENTS.md specification (execution layer, uses existing open standard)
- fileagents.index.md specification (discovery layer)
- Four-level progressive elaboration model (L0–L3)
- Tag-based cross-referencing (no paths)
- Governance inheritance (downward, FILEAGENTS.md only)
- Activity heatmap for cluster detection
- First-pass scan algorithm with 50-folder ceiling
- Complete examples for L1, L2, and L3

### Design decisions
- Two files per folder, not six (simplified from v0.1.0 draft)
- AGENTS.md uses the existing open standard — no custom format
- FILEAGENTS.md is the new invention — governance layer for knowledge folders
- Index is disposable and regenerable
- Human-gated elaboration (L2+ requires approval)
