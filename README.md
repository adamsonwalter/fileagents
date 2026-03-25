# FileAgents

**Make every folder on your disk self-describing, LLM-navigable, and structurally intelligent — with two markdown files and zero platform lock-in.**

FileAgents is a lightweight open standard for turning ordinary folders into durable AI-readable working contexts. It gives each important folder a small amount of permanent, local intelligence so any LLM can understand what the folder is for, what rules apply there, and how it connects to the rest of your filesystem.

## Why People Care

- Reuses the filesystem you already have instead of creating another app or database
- Works with any model that can read markdown
- Preserves context and operating knowledge across sessions and model upgrades
- Scales progressively: most folders stay untouched, only important ones get smarter
- Survives reorganisation because tags stay stable even when paths change

## In One Minute

1. Add the five `system/` files to your LLM context.
2. Ask it to scan a directory.
3. It creates lightweight `FILEAGENTS.md` files only where useful.
4. You deepen important folders over time.
5. Repeated work gets captured in `AGENTS.md` so the folder remembers.

FileAgents turns your existing filesystem into a distributed knowledge graph. No database. No app. No vendor. Just markdown files that any LLM can read, any human can edit, and any folder can carry forever.

---

## The Problem Nobody Named

Every time you start a new AI session, the model knows nothing about your files. It doesn't know what a folder is *for*, what rules govern it, what quality means there, or how folders relate to each other. So you explain. Every time.

Meanwhile, your filesystem — the largest, oldest, most universal knowledge structure you own — sits there as a dumb hierarchy of names and dates. Decades of organisation logic trapped in your head.

The gap isn't "AI can't read files." The gap is **AI has no idea what your folders mean.**

FileAgents closes that gap permanently.

---

## How It Works

Two files per folder. One index at the root. That's it.

**FILEAGENTS.md** — the *constitution*. Declares what the folder IS: its purpose, governance rules, quality standards, constraints, tone, and cross-references. Written once, rarely changed. This is the folder's identity.

**AGENTS.md** — the *execution layer*. Declares what an LLM can DO here: procedures, templates, verification checklists, edge cases, domain knowledge. Grows organically through use. Optional — most folders never need it.

**fileagents.index.md** — the *discovery cache*. A single auto-generated file at the root that maps every tagged folder. Resolves tags to paths so folders reference each other by stable identifiers, not brittle paths. Disposable — regenerate any time.

### Progressive Elaboration

Not every folder needs intelligence. FileAgents uses a four-level maturity model:

| Level | State | What Exists | How Created |
|-------|-------|-------------|-------------|
| **L0** | Raw | Nothing | Default (~95% of folders) |
| **L1** | Catalogued | FILEAGENTS.md frontmatter only | Automated scan |
| **L2** | Governed | FILEAGENTS.md with body sections | On request |
| **L3** | Operative | FILEAGENTS.md + AGENTS.md | Through use |

Most folders stay L0 forever. Some get catalogued. A few get governed. Only the ones you actually work in become operative. **Intelligence concentrates where activity concentrates.** No wasted effort.

---

## The Eight Core Rules

```
1. The folder is the unit of intelligence. The LLM is disposable.
2. Tags are stable identifiers. Never use file paths for cross-references.
3. Never auto-elaborate without human approval.
4. Never overwrite an existing FILEAGENTS.md or AGENTS.md.
5. FILEAGENTS.md is the constitution. AGENTS.md must not contradict it.
6. The index is disposable — regenerate any time.
7. Governance inherits downward. Execution does not.
8. The system works with any LLM. No platform dependencies.
```

Rule 1 is the philosophical core. Rule 7 is the architectural insight. Rule 8 is the survival guarantee.

---

## Why This Matters: The Multiplier Effects

### 1. Context Window Efficiency (Immediate ROI)

Every LLM session starts cold. Without FileAgents, you burn 20–40% of your context window just getting the model oriented: explaining folder purpose, naming conventions, quality rules, what not to touch.

With FileAgents, the model reads FILEAGENTS.md and *already knows*. One file read replaces hundreds of lines of repeated instruction. The context window is freed for actual work.

**Multiplier: Every governed folder saves context in every future session, across every model, forever.**

### 2. Knowledge Persistence Beyond Sessions (Compound Effect)

LLM sessions are stateless. Your folders are not. FileAgents bridges this gap by encoding operational knowledge into the filesystem itself.

When an L3 folder's AGENTS.md captures "every time I do a gap diagnostic in this folder, here's the procedure" — that knowledge survives model upgrades, platform switches, and session boundaries. The folder remembers what the model forgets.

**Multiplier: Operational knowledge compounds with use. Each session that adds a procedure or edge case to AGENTS.md makes every subsequent session more capable.**

### 3. Network Effects Across Folders (Superlinear Scaling)

A single governed folder is useful. Twenty governed folders with cross-references via tags become a navigable knowledge graph. The index resolves tags to paths, so the model can traverse from a client folder to its legal templates to its pricing models without you pointing the way.

This is Metcalfe's Law applied to your filesystem: the value of the network grows proportionally to the square of connected nodes. Each new governed folder increases the utility of every existing one.

**Multiplier: Value scales as O(n²) with governed folders, not O(n).**

### 4. Structural Survival (Anti-Fragility)

Most knowledge systems break when you reorganise. Move a folder, and every hardcoded path reference dies. FileAgents uses tags as the stable addressing layer. Paths appear only in the disposable index. Move a folder anywhere on disk — its FILEAGENTS.md tags are unchanged. Regenerate the index. Done.

This is the DNS principle applied to filesystems: tags are domain names (stable, human-meaningful), paths are IP addresses (volatile, machine-resolved).

**Multiplier: Reorganisation cost drops to near-zero. You can restructure without fear of breaking cross-references.**

### 5. Governance Inheritance (Efficiency at Scale)

FILEAGENTS.md inherits downward. If a parent folder declares "formal tone, evidence-based, C-suite audience" — every child folder without its own FILEAGENTS.md inherits those rules automatically. You govern the tree, not each leaf.

But AGENTS.md does *not* inherit. Execution procedures are always folder-specific. This prevents a parent's procedures from leaking into contexts where they don't apply.

**Multiplier: One governance decision propagates to N child folders. Execution stays precise.**

### 6. Platform Independence (Option Value)

FileAgents is plain markdown. It works with Claude, GPT, Gemini, Llama, or any model that can read text. No API calls, no proprietary format, no vendor lock-in. Your folder intelligence is an asset you own, not a subscription you rent.

When the next model generation arrives, your folders are already ready for it.

**Multiplier: Investment in folder intelligence carries forward across every platform transition.**

### 7. Human-AI Alignment (Trust Architecture)

The human-gated elaboration model (Rule 3) means the system never writes governance or execution instructions without approval. The activity heatmap surfaces which files cluster together, but waits for you to decide what to do about it.

This creates a trust architecture: the AI suggests, the human approves, the folder remembers. No black-box automation. Full auditability. Every rule in FILEAGENTS.md was human-approved.

**Multiplier: Trust enables delegation. Delegation enables scale. Scale enables leverage.**

### 8. Dead Knowledge Recovery (Hidden Value)

Most organisations have terabytes of files that nobody can navigate without the person who created them. FileAgents' scan operation can catalogue thousands of folders in minutes, creating L1 entries that make previously invisible folders discoverable by tag.

Even L1 — the lightest touch — transforms a folder from "unknown" to "findable." That's the difference between dead storage and living knowledge.

**Multiplier: A single scan surfaces the long tail of your filesystem's latent value.**

---

## The Compounding Architecture

These multiplier effects don't just add — they compound:

```
Scan (L1) → folders become discoverable
         → index creates cross-references
         → cross-references reveal clusters
         → clusters suggest governance (L2)
         → governance enables delegation
         → delegation generates procedures (L3)
         → procedures capture operational knowledge
         → knowledge persists across sessions
         → persistence enables deeper work
         → deeper work generates more knowledge
         → more knowledge → more governed folders
         → more governed folders → richer network
         → richer network → faster discovery
         → faster discovery → ...
```

This is a **reinforcing feedback loop**. The system gets more valuable the more you use it, with near-zero marginal cost per folder. The initial scan is the activation energy. Everything after compounds.

---

## Architecture Decisions Worth Understanding

### Why Tags, Not Paths?

Paths are volatile. You rename a folder, move it to a different drive, restructure your hierarchy — and every hardcoded path breaks. Tags are stable semantic identifiers. They survive any physical reorganisation. The index (disposable, regenerable) handles the tag→path resolution at query time.

This is the same architectural insight behind URNs vs URLs, DNS vs IP addresses, and content-addressable storage vs location-based storage.

### Why Constitution + Execution Separation?

FILEAGENTS.md (what the folder IS) changes slowly. AGENTS.md (what you can DO) changes frequently. Separating them means governance stability doesn't inhibit operational evolution, and operational experimentation can't corrupt governance rules.

This mirrors the separation of policy and mechanism in operating systems, or constitution and legislation in governance.

### Why Human-Gated Elaboration?

Auto-generating governance creates noise. If every folder automatically got L2 governance, you'd have thousands of files making claims nobody verified. The human gate ensures every governed folder reflects actual intent, not inference.

L1 (automated) is cheap and disposable. L2+ (human-approved) is authoritative. The quality gap between these levels is the system's integrity guarantee.

### Why Downward Inheritance for Governance but Not Execution?

A client folder's tone rules ("formal, C-suite") should apply to all its subfolders by default. But a client folder's diagnostic procedure should NOT auto-apply to its archive subfolder. Governance is contextual. Execution is specific. The inheritance model reflects this.

---

## Getting Started

### Prerequisites

Any LLM that can read and write files. No dependencies, no installation, no configuration.

### Quick Start

1. **Point your LLM at the FileAgents system files** — they contain the complete operating instructions
2. **Say "scan this directory"** — the LLM creates L1 FILEAGENTS.md files at boundary folders and generates the index
3. **Pick a folder you work in regularly** — say "set up this folder" to elaborate it to L2
4. **Work normally** — as you repeat procedures, the LLM suggests capturing them in AGENTS.md (L3)

For a practical walkthrough, see [`QUICKSTART.md`](QUICKSTART.md).

### System Files

| File | Purpose |
|------|---------|
| `fileagents.system.md` | Core rules and orchestration logic |
| `fileagents.levels.md` | Level definitions, templates, and field reference |
| `fileagents.scan.md` | Scan algorithm and constraints |
| `fileagents.elaborate.md` | Elaboration procedures (L1→L2→L3) |
| `fileagents.index.md` | Index generation, format, and tag resolution |

### Spec Version

Current: **0.2.0**

## Repository Layout

| Path | Purpose |
|------|---------|
| `system/` | The actual FileAgents operating spec |
| `examples/` | Concrete examples of L1, L2, L3, and index output |
| `QUICKSTART.md` | Fast onboarding guide |
| `CONTRIBUTING.md` | How to contribute examples, edge cases, and spec improvements |
| `CHANGELOG.md` | Release history |

## Best Fit

FileAgents is most useful if you:

- Work across many folders and repeatedly have to explain them to AI tools
- Want durable local context without vendor lock-in
- Care more about portability and clarity than full automation
- Have a growing archive of projects, clients, research, or reference material

It is less useful if all your work already lives inside a single tightly managed application and not in folders.

---

## What You Can Build Today That Compounds Tomorrow

Run the scan. That's it. A single scan across your working directories creates the discovery layer that every future AI session will benefit from. The 15 minutes you spend today saves context-setting time in every session that follows — across every model, every platform, every tool.

The folders you govern today become the foundation of the knowledge graph you'll navigate tomorrow.

---

## Design Philosophy

FileAgents is built on three convictions:

1. **The filesystem is the most durable, universal, platform-independent knowledge structure in computing.** It will outlast every app, every API, every SaaS platform. Build on it.

2. **Intelligence should live where the work lives.** Not in a separate database. Not in a cloud service. Not in a model's memory. In the folder, next to the files, readable by anything.

3. **Systems that grow with use beat systems that require setup.** L0→L1 is automated. L1→L2 is one conversation. L2→L3 emerges from work. No upfront architecture. No migration. No maintenance burden.

---

## License

MIT

---

*FileAgents was designed by Walter Adamson. The folder is the unit of intelligence. The model is disposable.*
