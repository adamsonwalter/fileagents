# Quick start

FileAgents turns folders into durable AI operating contexts that compound with use. The fast version: scan once, govern the important folders, and let reusable execution emerge only where repetition proves it is worth capturing.

## 1. Get the system files

Download or clone this repo. The six files in `system/` are all you need:

```
system/
  fileagents.system.md       ← orchestrator (LLM reads this first)
  fileagents.levels.md       ← level definitions and templates
  fileagents.scan.md         ← scan algorithm
  fileagents.elaborate.md    ← elaboration procedures
  fileagents.index.md        ← index generation and tag resolution
  fileagents.humans.md       ← humans.html profile and workflow
```

## 2. Attach to your LLM

**Claude Projects:** Create a new project. Upload all six files as project knowledge.

**Claude Code / Cowork:** Place the six files in your working directory or reference them.

**GPT:** Create a custom GPT or start a conversation with all six files attached.

**Cursor / Windsurf:** Place in your project root. These tools read markdown context files natively.

**Any other LLM:** Paste or attach the files at the start of your session.

## 3. The Gold Standard Prompt (Zero Ambiguity)

The most effective way to start is to move from a conversational "request" to a **System Command**. This bypasses AI drift and ensures the model executes the FileAgents protocol with surgical precision.

**Copy and paste this as your first instruction:**
> "Use the **@fileagents** skill to perform a **Scan Turn** on `@target-folder`. 
> 1. Catalog all boundary folders with Level 1 `FILEAGENTS.md` files.
> 2. Regenerate the root `fileagents.index.md` to map all tags.
> 3. Identify the highest-activity folder and suggest it for an L2 Governance upgrade."

### Why this works:
- **"Scan Turn"**: Signals the AI to act as an auditor (L0→L1), not a writer.
- **"Boundary Folders"**: Prevents "Folder Explosion" by cataloging only where context changes.
- **"Regenerate the Index"**: Establishes the discovery cache immediately.

---

## 4. Run your first scan

If you didn't use the prompt above, you can simply say:

> Scan the current working directory

The LLM will:
1. Read `fileagents.scan.md` for the algorithm.
2. Walk your directory tree.
3. Create L1 `FILEAGENTS.md` files (frontmatter only).
4. Generate `fileagents.index.md` at the root.

## 5. Pick one folder to deepen

Look at the scan results. Pick one folder you actually work in regularly.

Say:

> Set up the Acme folder in more detail

The LLM will:
1. Read `fileagents.elaborate.md` for the procedure
2. Ask you about purpose, naming rules, quality standards, constraints
3. Add body sections to that folder's FILEAGENTS.md (now L2)
4. Update the index if tags changed

## 6. Let execution emerge

As you work in that folder over time, the LLM may notice patterns:

> "You've run a competitive analysis three times in this folder.
> Should I capture that as a procedure in AGENTS.md?"

Say yes, and the folder gets its AGENTS.md (now L3). The procedure is
captured once and available in every future session, with any LLM.

## 7. Request folder orientation

At any time, type `/contents` (or `/contents [folder-tag]`) and the LLM will display the `humans.html` lens for that folder—either directly in your chat or by opening your system browser. This gives you an instant, high-fidelity summary without reading markdown.

## That's it

No installation. No configuration. No database. No app.
Six markdown files that teach any LLM how to make your folders intelligent. At L2+, add **`humans.html`** per `fileagents.humans.md` so people get a quick browser summary alongside `FILEAGENTS.md`.

## What happens next

The folders you govern today become discoverable tomorrow. Cross-references
via tags mean the LLM can navigate from a client folder to its templates
to its pricing models without you pointing the way.

Each governed folder makes every other governed folder more useful.
The network effect is real and it compounds with every folder you add.

That is the deeper point of the system: the filesystem stops being passive storage
and starts behaving like durable AI context that improves with use.
