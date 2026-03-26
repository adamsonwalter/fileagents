# Decision log

## 2026-03-26 — humans.html (spec 0.3.0)

**Problem:** Humans browsing folders used as LLM knowledge bases need a fast, browser-native summary without reading full governance markdown; this should stay aligned with `FILEAGENTS.md` / `AGENTS.md`.

**Solution:** Add optional per-folder `humans.html` plus `system/fileagents.humans.md` defining content (orientation, scope, inventory granularity, LLM routing, tags-only cross-refs), a safe static HTML profile, regeneration triggers tied to elaboration, and L1 optional / L2+ recommended. Bump spec to **0.3.0**.

**Why:** Keeps a single source of truth (`FILEAGENTS.md`) while giving people a low-friction “human lens” that can be regenerated like the index, without new tooling or network dependencies.
