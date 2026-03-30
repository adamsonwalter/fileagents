# FileAgents — Future Enhancements & Roadmap

This document outlines conceptual upgrades to the FileAgents methodology, engineered to take the system to the next level. The focus is specifically on decentralised, markdown-native logic.

The enhancements are ordered by the **80/20 Principle** (highest system integrity value for the lowest implementation effort).

---

## 1. The Closure Protocol (The "Receipt" Artifact) [COMPLETED]
**Status:** Implemented actively in `fileagents.system.md` and `fileagents.sop.md`.
**Priority:** Highest | **Effort:** Low | **Impact:** High (Immediate Verification)

**Concept:** 
When an AI finishes a complex task in an L2 or L3 governed folder, it currently stops silently. Instead, the AI must output a structured artifact detailing exactly what it modified and where it struggled.

**Implementation Method:**
Update `fileagents.system.md` to mandate a standard **Closure Protocol**. At the end of a session, the AI generates a temporary `.fileagents.receipt.md` inside the folder containing:
- **State Modified:** Exact files changed or generated.
- **Constraints Checked:** Confirmation that no `FILEAGENTS.md` rules were breached.
- **Data Gap Report:** Missing context or ambiguity encountered during execution (Operational Friction).

---

## 2. Hard-Wired Operational Triggers (Slash Commands) [COMPLETED]
**Status:** Implemented actively in `AGENTS.md` references and `fileagents.sop.md`.
**Priority:** High | **Effort:** Low | **Impact:** High (Eliminates Prompt Engineering)

**Concept:** 
Relying on LLMs to implicitly understand conversational paths into folder orchestration (e.g., "Set up this folder") induces high token usage and variance.

**Implementation Method:**
Introduce explicit trigger definitions into `AGENTS.md` templates and `fileagents.elaborate.md`. 
Instead of writing paragraphs of procedure, use explicit commands:
- `Trigger: /govern` → Read `FILEAGENTS.md`, prompt for missing context, build `humans.html`.
- `Trigger: /receipt` → Compile `.fileagents.receipt.md` and report technical debt.
This reduces cognitive load and forces the LLM onto a deterministic execution track.

---

## 3. The Forensic Miner (Asynchronous Self-Correction)
**Priority:** Medium | **Effort:** Moderate | **Impact:** Extremely High (Self-Evolving Folders)

**Concept:**
Instead of expecting the AI to rewrite core governance (`FILEAGENTS.md`) at the very moment it is focused on executing a task, we decouple the "Doing" from the "Learning".

**Implementation Method:**
Build a dedicated system prompt or lightweight script (e.g., `/mine-receipts`) whose sole purpose is to execute periodically.
1. The script sweeps the repository for all `.fileagents.receipt.md` artifacts.
2. It distills the "Data Gap Reports" and operational friction from those receipts.
3. It seamlessly injects the extracted constraints back into the parent `FILEAGENTS.md` and `AGENTS.md` files as permanent rules.
4. It deletes the processed receipts.

*Result:* The local folder's intelligence permanently upgrades through semantic exhaust, remaining entirely self-contained and decentralised.

---

## 4. Cross-Pollination of Local Knowledge
**Priority:** Low | **Effort:** Moderate | **Impact:** Medium (Institutional Memory)

**Concept:**
Currently, each L3 folder discovers rules and procedures organically. If one `AGENTS.md` discovers a specific formatting constraint, other similar project folders remain ignorant.

**Implementation Method:**
Introduce an extraction pattern via `fileagents.index.md`. When the Forensic Miner evaluates friction in an active folder (e.g., "Strategy Deck A"), it cross-references the `fileagents.index.md` for peer folders with matching tags and broadcasts the new constraint to those `FILEAGENTS.md` files simultaneously.

---

## 5. Native SOP Pipelines (Functional Folders) [COMPLETED]
**Status:** Formalized as an architectural standard in `system/fileagents.sop.md`.
**Priority:** High | **Effort:** Structural Standardisation | **Impact:** High (Eliminates OS Bloat)

**Concept:** 
Organisations often require clear, functional pipelines (e.g., `01_SBR PROCESSING`). A common pitfall in other AI systems is entangling the AI's complex instruction prompt (the SOP) with a visually rich, client-facing HTML document. This violates the Single Responsibility Principle: modifying the AI prompt breaks the client layout, and styling the layout forces the AI to process thousands of useless CSS tokens (Token Bleed).

**Implementation Method (The Two-File Protocol):**
Instead of monolithic "HTML-SOPs," FileAgents natively processes simple pipelines (like "Jotform Input → SKILL → SBR Report Output") by enforcing an audience split within an L3 folder:

1. **`AGENTS.md` (The Machine Layer):** Contains the raw, token-efficient SOP. It maps the Triggers, Inputs, Process (Claude SKILLS routing), Constraints, and Outputs. Because it is pure markdown, AI invocation is lightning-fast and highly obedient.
2. **`humans.html` (The Human Layer):** Sources context from `FILEAGENTS.md` and reads `AGENTS.md` to format a visually stunning, client-ready summary. It operates as the routing page, entirely free of raw AI prompting instructions.

**Functional Folder Architecture (Flat-Primitive Mapping):**
When structuring a highly functional folder like `01_SBR PROCESSING`, map the components to native FileAgents primitives rather than deep subfolder nesting:
- **Constitution:** Governed exclusively by `FILEAGENTS.md`.
- **Process:** Governed exclusively by `AGENTS.md`.
- **Inputs, Outputs, Templates, Reference:** Kept as flat files in the root directory and managed via strict naming conventions documented in the Constitution (e.g., `Template_SBR_Standard.docx`). Subfolders (`Input/`, `Output/`) are only instantiated when raw file volume dictates it, preventing folder traversal fatigue.
