# FileAgents — Native SOP Pipelines

Read this when the user asks to build an SOP, an automated workflow, or a processing pipeline inside a folder.

## What is a Native SOP Pipeline?

A Native SOP Pipeline is a specialized **L3 Operative folder** designed as a linear manufacturing engine (e.g., converting raw survey data into a formatted report).

Instead of relying on fragile, conversational LLM prompts or burying instructions inside visually heavy HTML files, FileAgents strictly separates the execution logic from the human presentation using the **Two-File Protocol**:
1. **`AGENTS.md` (The Machine Layer):** A dense, step-by-step markdown file containing explicit slash commands, role constraints, and verification checklists. It optimizes token density and ensures deterministic execution.
2. **`humans.html` (The Human Layer):** A static dashboard that surfaces the outputs and outlines the pipeline's purpose for a human operator, entirely free of raw AI prompting noise.

## The Flat-Primitive Rule

Never build deep subfolder hierarchies (e.g., `Input/`, `Process/`, `Templates/`, `Output/`) inside an SOP pipeline unless file volume absolutely demands it. Deep nesting fractures LLM context. 

Keep components flat in the primary directory and govern them via strict naming conventions defined in `FILEAGENTS.md`:
- `Input_*.txt`
- `Ref_*.md` (Knowledge/Templates)
- `Output_Draft_*.docx`

## How to build an SOP Pipeline

When asked to create an SOP, generate or update the folder's `AGENTS.md` using this exact architecture:

### 1. Operational Triggers
Define explicit slash commands to bypass semantic inference.
- `/execute {filename}` → Run the pipeline on the target file.
- `/receipt` → Generate the closure artifact to self-evolve the system.

### 2. Target Architecture
Explicitly map the required inputs, the benchmarking knowledge files, and the expected output formatting.

### 3. The Process Pipeline (Roles & Sequence)
Break the workflow into sequential steps. Assign a specific **Role** (e.g., "Data Analyst", "Synthesizer") to each step to narrow the LLM's behavioral scope.
- **Handoff Checks:** At the end of a step, list exactly what data must be verified before the next role takes over.
- **Constraints/Edge Cases:** Define strict boundaries (e.g., "If client revenue < $1M, use the startup template").

### 4. Verification Checklists
Require the LLM to run a boolean checklist (e.g., `[ ] Tone is formal`, `[ ] No placeholder text remains`) before dropping the final output.

### 5. System Evolution (The Closure Protocol)
Every SOP must end with an autonomous or user-prompted `/receipt` command. When triggered, the LLM must generate a `.fileagents.receipt.md` artifact containing:
- **ROI/Execution Stats:** Time/tokens used vs. manual baseline.
- **Operational Friction:** An explicit log of where the LLM struggled, hallucinated, or found the `AGENTS.md` rules ambiguous.
- **System Improvement Fix:** Concrete, modular markdown edits proposed to update `AGENTS.md` to prevent the friction from happening again. This is the pipeline's self-healing mechanic.
