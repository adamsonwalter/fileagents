# FileAgents × Karpathy LLM Wiki — mapping and shared vocabulary

This note is for people who already understand [Andrej Karpathy’s “LLM Wiki” gist](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f) and the surrounding idea: **markdown on disk, maintained by an agent, so knowledge compounds across sessions** instead of ending up only inside a stateless chat or a pure chunk-retrieval loop.

FileAgents is **not** a drop-in replacement for that wiki pattern. It is **governance-first**: each **folder** gets a durable constitution (`FILEAGENTS.md`), optional execution (`AGENTS.md`), and optional human lens (`humans.html`). You can still run a `raw/` → compiled notes → lint loop **inside** a governed folder; FileAgents tells the model **what the folder is for** and **what rules apply** while that happens.

---

## Mapping table

| Karpathy / market term | Closest FileAgents primitive | Fit |
|------------------------|------------------------------|-----|
| **LLM Wiki** (compiled markdown tree) | Governed folder(s) with substantive `.md` + L2/L3 elaboration | **Partial** — FA emphasizes *folder identity and rules*; wiki pattern emphasizes *encyclopedia articles and backlinks*. |
| **`raw/`** (immutable-ish sources) | Unstructured inputs in a folder, or flat `Input_*` in a mini-SOP | **Composable** — not global in the spec; encouraged as a *local* convention in pipeline folders (see `MINI_SOP.md`). |
| **`wiki/`** (LLM-maintained articles) | Body of `FILEAGENTS.md` + other `.md` the folder needs | **Partial** — treat `FILEAGENTS.md` as *constitution*, not every note page; extra pages can act as “wiki” leaves under the same tag. |
| **Index / catalog** (`index.md`, etc.) | Root `fileagents.index.md` | **Strong** — disposable tag → path map for discovery. |
| **Idea file** (copy-paste agent bootstrap) | Six files under `system/` + root `llms.txt` | **Strong** — same distribution model: repo text, not an installable app. |
| **Stateful vs stateless RAG** (framing) | Persistent `FILEAGENTS.md` / `AGENTS.md` / index / receipts | **Strong** — knowledge lives in the tree; sessions stay cheap to restart. |
| **Research librarian / compile** | `fileagents.scan.md` + `fileagents.elaborate.md` + human-gated L2/L3 | **Partial** — FA *compiles* folder meaning, not only article summaries; upgrades require explicit approval (Rule 3). |
| **Lint / health check** | Staleness and batch discipline in `OPERATIONS.md`; optional passes after big moves | **Gap to close** — borrow the word *lint* in prompts (“lint this vault’s index and tags”). |
| **Agent schema** (`CLAUDE.md`, Codex rules, etc.) | `AGENTS.md` (do this here) + `FILEAGENTS.md` (what this is) | **Strong** — FA splits *policy* from *procedure* deliberately. |
| **Backlinks / graph** | Tags in frontmatter + index resolution | **Different mechanism** — stable **tags**, not `[[wikilinks]]`; paths stay out of cross-folder refs. |
| **Obsidian = IDE, LLM = programmer, wiki = codebase** | Filesystem = truth; LLM elaborates **per folder**; `humans.html` = human-readable layer | **Metaphor carries** — swap “wiki” for “governed folder + index” when explaining FileAgents. |

---

## Vocabulary to borrow (makes the repo approachable)

Use these phrases **alongside** existing FileAgents terms — not as replacements for `FILEAGENTS.md` / tag rules.

| Borrow | Where it helps | Suggested usage |
|--------|----------------|-----------------|
| **Stateful knowledge base** | README, social preview one-liners | “FileAgents is a **stateful, markdown-native** layer over your folders.” |
| **Compounding** (already used) | Tie explicitly to “post–LLM Wiki” readers | “Same compounding move as an LLM Wiki, but **per-folder governance**.” |
| **Compile** | Scan / elaborate prompts | “**Compile** folder meaning into `FILEAGENTS.md`; don’t spam manual prose.” |
| **Lint** | `OPERATIONS.md`, receipts | “Periodic **lint**: index vs disk, orphan tags, stale `humans.html`.” |
| **Librarian** (optional) | QUICKSTART, tutorials | Model acts as **librarian** only where the human approved L2+. |
| **File-over-app** | README, CONTRIBUTING | Aligns with Karpathy discourse; matches your MIT / plain-markdown posture. |
| **Idea / prompt kit** | Repo tags, issues | Describe `system/` as an **idea kit** not a framework. |

**Avoid implying equivalence** where it isn’t true: FileAgents is **not** “always create `raw/` + `wiki/`”; it **is** “every important folder gets a constitution, then optional SOP depth.”

---

## Concrete repo touchpoints (already wired or easy)

| Surface | Action |
|---------|--------|
| **README** | Short “If you know LLM Wiki…” blurb + link here. |
| **QUICKSTART** | One paragraph translation for Karpathy-literate readers. |
| **llms.txt** | One bridging bullet for tools that ingest `llms.txt`. |
| **`docs/OPERATIONS.md`** | Add an optional bullet list titled **Vault lint** (index, tags, `humans.html` freshness). |
| **`system/fileagents.system.md`** | Optional future: glossary line linking **compile** → elaborate, **lint** → consistency pass (keep short). |

---

## When to use both patterns

- **FileAgents alone:** Operating context across many project/client folders; stable tags; human-gated upgrades.
- **LLM Wiki inside a folder:** Drop `raw/` + working notes + compiled summaries **inside** one L3 folder; let `FILEAGENTS.md` state scope and naming; put automation in `AGENTS.md`.

That composition preserves FileAgents’ **anti-contamination** posture (governed boundary, optional human lens) while keeping Karpathy-style **ingest → compile → lint** for research-heavy leaves.
