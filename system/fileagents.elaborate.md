# FileAgents — Elaborate operation

Read this when the user asks to deepen, improve, or set up a specific folder.
For level definitions and file templates, see fileagents.levels.md.
For `humans.html`, see `fileagents.humans.md`.

## What you are doing

Upgrading a folder from one level to the next by adding governance
(FILEAGENTS.md body) or execution capability (AGENTS.md).

## L1 → L2: Adding governance

The folder has frontmatter-only FILEAGENTS.md. User wants rules and structure.

1. Read the existing FILEAGENTS.md frontmatter
2. Examine the folder contents (file names, types, count)
3. Ask the user about OR infer from contents:
   - Purpose: what is this folder for?
   - File governance: any naming conventions?
   - Quality standards: what makes a good output?
   - Constraints: what should never happen here?
   - Tone: formal/informal, audience?
4. Add body sections to FILEAGENTS.md (keep the frontmatter unchanged)
5. Update frontmatter if needed (add domain, depends_on_tags, owner)
6. Create or refresh **humans.html** in this folder (see `fileagents.humans.md`) — derived from the new governance + shallow directory listing
7. If tags or depends_on_tags changed → regenerate index (see fileagents.index.md)

Use only the body sections the folder actually needs. See LEVELS.md for
the full list of available sections and a complete L2 example.

## L2 → L3: Adding execution

The folder has governed FILEAGENTS.md. User wants operational procedures.

1. Read FILEAGENTS.md (understand rules and constraints)
2. Ask the user: what do you repeatedly do in this folder?
3. Create AGENTS.md starting RUDIMENTARY:
   - Overview (2-3 sentences)
   - 1-2 key conventions or procedures
4. Refresh **humans.html** so the “Procedures at a glance” section reflects `AGENTS.md` headings (see `fileagents.humans.md`).
5. As the user works over time, offer to add:
   - More procedures with detailed steps
   - Templates with {{placeholder}} markers
   - Verification checklists
   - Edge cases
   - Domain knowledge

Start simple. Grow through use. Never front-load complexity.
See LEVELS.md for complete L3 example.

## AGENTS.md rules

- Must NEVER contradict FILEAGENTS.md (FILEAGENTS always wins)
- Does NOT inherit from parent folders
- Platform tools (Claude Skills, GPT Actions) are hints only:
  "If available, delegate to [tool]. Otherwise follow these steps..."
- The folder must work with any LLM

## Permission rules

```
HARD RULE: Never create L2 or L3 content without human approval.
You may SUGGEST elaboration. You must WAIT for confirmation.
```

## When to suggest elaboration (heuristics)

Suggest L1→L2 when:
- User has worked in the folder 3+ times across sessions
- User gives the same kind of instruction twice (repetition signal)
- User states quality rules or naming conventions verbally

Suggest L2→L3 when:
- User performs 3+ distinct procedures in the folder
- User says "every time I do X in this folder..."
- Folder produces deliverables needing consistent formatting

## Activity heatmap (L2+ folders)

### Purpose
Track file access patterns to detect clusters for potential extraction.

### How it works
At the end of each work session in an L2+ folder:
1. Append files you accessed to ## Activity heatmap in FILEAGENTS.md
2. Increment session count per file, update last-accessed date
3. If >100 entries, drop the entries with lowest session count
4. Update last_updated date

### Format
```markdown
## Activity heatmap
last_updated: 2026-03-24
- report-draft.docx | 12 sessions | last: 2026-03-24
- contract-v3.pdf | 8 sessions | last: 2026-03-22
- pricing.xlsx | 5 sessions | last: 2026-03-20
```

## humans.html (L2+)

Whenever you materially change `FILEAGENTS.md` or `AGENTS.md`, or the user reports
significant file churn in the folder, offer to refresh `humans.html` using
`fileagents.humans.md`. Keep it in sync with governance the same way you would
update an Activity heatmap: humans see the folder; models read `FILEAGENTS.md` first.

## Cluster detection (when heatmap reaches 50+ entries)
1. Identify files frequently accessed together
2. Generate candidate tags for the cluster
3. Check fileagents.index.md for existing folders with matching tags
4. Suggest to user:
   - Match found: "These files cluster together. Move to [existing folder]?"
   - No match: "These files cluster together. Create new folder?"
5. WAIT for approval
6. If approved: move files, create FILEAGENTS.md for new folder,
   update parent heatmap, regenerate index (see fileagents.index.md)

## Edge cases

- User asks to elaborate a folder that has no FILEAGENTS.md →
  create L1 first, then proceed to L2
- User asks for L3 on a folder with no L2 →
  create L2 first (ask about governance), then create AGENTS.md
- AGENTS.md already exists from another system (code repo) →
  keep it, create FILEAGENTS.md alongside, move any identity/metadata
  from AGENTS.md into FILEAGENTS.md
