# Mini-SOP in one folder (L3)

**WIIFM:** You stop re-explaining “where inputs live, what templates apply, where outputs go, and what order to run” every session. One folder holds the **whole pipeline** the model can follow—without a separate app or orchestrator.

A **mini-SOP** here means: one **L3 operative** folder that behaves like a small manufacturing line (raw in → governed steps → artefact out). The full architecture is in [`system/fileagents.sop.md`](../system/fileagents.sop.md); this page is the **at-a-glance recipe** for GitHub readers who will not open every system file first.

## What you need (checklist)

| Piece | Role | Typical form |
|-------|------|----------------|
| **Governance** | What this folder *is*, naming, quality, constraints | `FILEAGENTS.md` |
| **Execution** | Steps, triggers, handoffs, checklists | `AGENTS.md` |
| **Human lens** (optional) | Browser-friendly summary—**no** AI prompts in HTML | `humans.html` |
| **Inputs** | Raw material for a run | Files with a clear prefix/pattern (e.g. `Input_*.txt`) or a subfolder **only** if volume forces it |
| **Reference / templates** | Ground truth the model must not invent | `Ref_*.md`, templates, rate tables—named in `FILEAGENTS.md` |
| **Outputs** | Where drafts and finals land | e.g. `Output_Draft_*`, `Output_FINAL_*`—same idea: flat and named beats deep trees |
| **Discovery** (vault-wide) | Find this folder by tag, not path | Root `fileagents.index.md` after a scan |

## How it fits the levels

- **L3** = `FILEAGENTS.md` + `AGENTS.md` (operative). That is when “mini-SOP” execution is in play.
- **Native SOP Pipeline** = L3 folder tuned for a **linear** workflow with slash commands (`/execute`, `/receipt`) and optional `.fileagents.receipt.md` closure—see `fileagents.sop.md`.

## Flat beats deep (default)

Prefer **flat files + strict names** in the primary directory. Deep `Input/`, `Process/`, `Templates/`, `Output/` trees **fracture context** unless file volume makes subfolders unavoidable—then document the layout in `FILEAGENTS.md`.

## What you tell the IDE

1. Add the **six `system/` files** to context (or your FileAgents skill).
2. Open the **workflow folder** as part of the workspace.
3. Instruct the model to **read `FILEAGENTS.md` first**, then **`AGENTS.md`** for the procedure—same folder, same session, no mystery paths for cross-folder refs (use **tags** and the index).

You do **not** need four separate “IDE projects” for input, template, and output—unless you **choose** that layout; the spec expects **one governed folder** whose constitution defines where each class of file lives.
