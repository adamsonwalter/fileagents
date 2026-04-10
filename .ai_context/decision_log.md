# Decision log

## 2026-03-26 — humans.html (spec 0.3.0)

**Problem:** Humans browsing folders used as LLM knowledge bases need a fast, browser-native summary without reading full governance markdown; this should stay aligned with `FILEAGENTS.md` / `AGENTS.md`.

**Solution:** Add optional per-folder `humans.html` plus `system/fileagents.humans.md` defining content (orientation, scope, inventory granularity, LLM routing, tags-only cross-refs), a safe static HTML profile, regeneration triggers tied to elaboration, and L1 optional / L2+ recommended. Bump spec to **0.3.0**.

**Why:** Keeps a single source of truth (`FILEAGENTS.md`) while giving people a low-friction “human lens” that can be regenerated like the index, without new tooling or network dependencies.

## 2026-04-10 — Karpathy LLM Wiki bridge (docs + onboarding vocabulary)

**Problem:** After Andrej Karpathy’s viral “LLM Wiki” gist and coverage, newcomers map “stateful markdown knowledge base” to a single pattern; FileAgents uses the same *compounding file-over-app* idea but with **per-folder constitutions**, tags, and human-gated elaboration—easy to miss without explicit mapping.

**Solution:** Add `docs/KARPATHY_LLM_WIKI_BRIDGE.md` (mapping table + borrow list), link it from `README.md`, `QUICKSTART.md`, and `llms.txt`; add a **vault lint** section to `docs/OPERATIONS.md` using shared vocabulary.

**Why:** Lowers adoption friction for the educated market without changing core spec semantics; keeps distinctions honest (wiki = content graph vs FileAgents = governance unit).

## 2026-04-10 — Orchestrator glossary (Karpathy LLM Wiki terms)

**Problem:** Operators who load only `system/fileagents.system.md` miss the shared vocabulary (*compile*, *lint*) now used in `docs/` for **Andrej Karpathy LLM Wiki**-literate readers.

**Solution:** Add a short “Karpathy LLM Wiki discourse (glossary)” section to `system/fileagents.system.md` pointing at `docs/OPERATIONS.md` §6 and `docs/KARPATHY_LLM_WIKI_BRIDGE.md`.

**Why:** Keeps the six-file bundle self-contained when the model reads the orchestrator first.
