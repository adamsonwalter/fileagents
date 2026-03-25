# Quick start

FileAgents turns folders into durable AI operating contexts that compound with use. The fast version: scan once, govern the important folders, and let reusable execution emerge only where repetition proves it is worth capturing.

## 1. Get the system files

Download or clone this repo. The five files in `system/` are all you need:

```
system/
  fileagents.system.md       ← orchestrator (LLM reads this first)
  fileagents.levels.md       ← level definitions and templates
  fileagents.scan.md         ← scan algorithm
  fileagents.elaborate.md    ← elaboration procedures
  fileagents.index.md        ← index generation and tag resolution
```

## 2. Attach to your LLM

**Claude Projects:** Create a new project. Upload all five files as project knowledge.

**Claude Code / Cowork:** Place the five files in your working directory or reference them.

**GPT:** Create a custom GPT or start a conversation with all five files attached.

**Cursor / Windsurf:** Place in your project root. These tools read markdown context files natively.

**Any other LLM:** Paste or attach the files at the start of your session.

## 3. Run your first scan

Say to the LLM:

> Scan my ~/Documents directory

or

> Scan the current working directory

The LLM will:
1. Read `fileagents.scan.md` for the algorithm
2. Walk your directory tree
3. Create L1 `FILEAGENTS.md` files (frontmatter only) at significant folders
4. Generate `fileagents.index.md` at the root
5. Report what it found

This takes minutes. It creates no body content, no AGENTS.md, nothing heavy.

## 4. Pick one folder to deepen

Look at the scan results. Pick one folder you actually work in regularly.

Say:

> Set up the Acme folder in more detail

The LLM will:
1. Read `fileagents.elaborate.md` for the procedure
2. Ask you about purpose, naming rules, quality standards, constraints
3. Add body sections to that folder's FILEAGENTS.md (now L2)
4. Update the index if tags changed

## 5. Let execution emerge

As you work in that folder over time, the LLM may notice patterns:

> "You've run a competitive analysis three times in this folder.
> Should I capture that as a procedure in AGENTS.md?"

Say yes, and the folder gets its AGENTS.md (now L3). The procedure is
captured once and available in every future session, with any LLM.

## That's it

No installation. No configuration. No database. No app.
Five markdown files that teach any LLM how to make your folders intelligent.

## What happens next

The folders you govern today become discoverable tomorrow. Cross-references
via tags mean the LLM can navigate from a client folder to its templates
to its pricing models without you pointing the way.

Each governed folder makes every other governed folder more useful.
The network effect is real and it compounds with every folder you add.

That is the deeper point of the system: the filesystem stops being passive storage
and starts behaving like durable AI context that improves with use.
