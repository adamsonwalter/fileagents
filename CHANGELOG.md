# Changelog

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
