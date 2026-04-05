# Operating FileAgents in the real world

These notes are **operator guidance**: batch scans, people moving folders, and how to stay sane. They complement the instruction files in [`system/`](../system/) (`fileagents.*.md`), which define *what* the system is; this document addresses *how* to deploy **habits** around it.

---

## 1. Batch truth vs moving files

FileAgents is fundamentally **batch-oriented**: you scan, you index, you govern folders. **Paths change** whenever humans move or rename directories. The **index** (`fileagents.index.md`) is **path-based discovery**; it will be **wrong** until the next scan. That is normal—not a bug.

**What stays stable** is the **folder as a unit**: if a governed folder moves **as a whole**, its `FILEAGENTS.md` (and tags in frontmatter) travels with it. **Tags** are the stable identifiers across the system; **paths** are volatile.

**Promise to users (and yourself):** *After a scan, the index and tag map match the disk under the scanned root.* Do not promise omniscience across the entire machine without scanning, or “always current” paths without a fresh index.

---

## 2. Containment: one vault root

The most robust pattern for v1:

1. Declare a **single root** for “life under FileAgents” — e.g. `~/Documents/FileAgentsVault/`, `~/Org/`, or another **boring, explicit** top-level folder name.
2. Keep **active** work and governed trees **inside** that root.
3. Run **full scans** on that root **periodically** and **after any bulk reorganisation**.

This **bounds** cost, makes batch runs predictable, and sets a clear habit: *don’t scatter governed trees across Desktop, Downloads, and random project dirs unless you accept they won’t be seen until scanned.*

Scanning the **whole disk** is optional and expensive; treat it as a deliberate choice, not the default story.

---

## 3. Truth hierarchy (reminder)

| Layer | Role |
|-------|------|
| `FILEAGENTS.md` in each folder | **Truth** for what that folder *is* (governance, metadata, rules). |
| `AGENTS.md` | **Execution** hints for LLMs; must not contradict `FILEAGENTS.md`. |
| `fileagents.index.md` | **Disposable cache** for discovery — regenerate anytime; **not** authoritative over folder content. |

After moves: **rebuild the index**; **re-read** `FILEAGENTS.md` if someone split or merged folders (that’s new governance work, not a silent move).

---

## 4. Move discipline (short operator protocol)

- **Prefer moving whole directories** that already contain `FILEAGENTS.md`, so identity and tags stay attached.
- **After** a big move/rename session: run **one** scan (or “rebuild index + verify”) under the vault root.
- **Splits, merges, or copies** without carrying `FILEAGENTS.md` are **not** inferrable automatically—treat as **elaborate** or manual fix-up, not something the scanner can magically reconcile.

Document this in onboarding: *“Reorg → scan → consistent again.”*

---

## 5. Staleness and expectations

Surface **staleness** honestly:

- **Last scan time** at the top of the index (as sketched in the index spec).
- **Per-folder “verified” or age** where useful (e.g. folders not seen or not re-verified since *N* days).

Users tolerate batch systems when they see **when** truth was last aligned. They lose trust when the UI or assistant **implies** live sync without it.

---

## 6. Optional future: “what changed since last scan?”

A high-leverage enhancement (not required for v1): keep a **snapshot** of path ↔ tag id from the previous run; on the next scan, emit a short **“changes since last scan”** section: added paths, removed paths, moved paths (same tag id, different path). That turns “FileAgents didn’t know” into **“here’s exactly what drifted; accept or fix.”**

---

## 7. Periodic ritual

A **weekly** or **monthly** ritual fits batch reality better than pretending background daemons everywhere:

1. Open the project (Cowork, Cursor, or equivalent) scoped to the vault.
2. Run scan → rebuild index.
3. Review stale or unresolved rows.
4. Optionally run **elaborate** on folders that need L2/L3 promotion.

**Ritual beats magic** for institutional memory.

---

## 8. Optional: filesystem watch (later)

If power users need it: a **watcher** on the vault root that **debounces** (“schedule rescan in 5 minutes”) can reduce manual runs. Keep the **core** product story as **on-demand + periodic scan**; watches are an accelerator, not the contract.

---

## 9. One-line doctrine

> Paths change; tags and `FILEAGENTS.md` travel with the folder; the index is rebuilt on scan—**run a scan after moves.**

---

## 10. Relation to other “OS” or workflow layers

FileAgents governs **the forest** (self-describing folders, discovery by tag). Separate workflow templates or task systems can govern **repeatable AI task patterns** inside whatever part of that forest you point them at. The two are **complementary**, not competing.
