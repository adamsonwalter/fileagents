# FileAgents — Level definitions and examples

This file defines the four levels and gives complete copy-ready examples.
When creating or upgrading files, use these as exact templates.

## L0 — Raw

No FILEAGENTS.md. No AGENTS.md. Just files. ~95% of folders stay here.
Nothing to create.

## L1 — Catalogued

FILEAGENTS.md with frontmatter ONLY. No body. Created by automated scan.
The folder becomes discoverable by tag in the index.

### L1 FILEAGENTS.md (complete file):

```yaml
---
id: client-projects
type: client
tags: [clients, consulting, projects, active]
status: active
created: 2026-03-24
spec_version: "0.3.0"
---
```

That is the ENTIRE file. Nothing after the closing `---`.

### L1 humans.html

**Optional.** Scans do not create it by default. If present, it must be a minimal
orientation page derived only from frontmatter (see `fileagents.humans.md`).

### Frontmatter field reference

```
FIELD             REQUIRED   FORMAT                VALUES/RULES
id                yes        kebab-case string     unique across disk
type              yes        string                client|project|knowledge|archive|system|personal
tags              yes        [string array]        lowercase, no spaces, no paths, max 15
status            recommend  string                active|paused|archived|template
domain            optional   [string array]        semantic domains
created           recommend  ISO 8601 date         YYYY-MM-DD
verified          optional   ISO 8601 date         last human confirmation
depends_on_tags   optional   [string array]        tags of needed folders, NEVER paths
owner             optional   string                person or team
spec_version      recommend  string                "0.3.0"
```

### Type classification heuristics

- "client", "customer", or a company/person name with deliverables → client
- "project" or a named initiative → project
- "knowledge", "reference", "library", "docs", "templates" → knowledge
- "archive", "old", "backup", year folders (2024, 2025) → archive
- "system", "config", "settings" → system
- Otherwise → personal

### Tag generation rules

- Split folder name into lowercase words
- Add the type
- Add meaningful immediate subfolder names (skip: src, docs, assets, tmp, misc)
- Max 10 tags. All lowercase. Multi-word → kebab-case.
- NEVER include filesystem paths as tags

### Id generation rules

- Lowercase folder name. Spaces/underscores → hyphens. Strip specials.
- If collision: prepend parent name ("docs" → "clients-docs")

## L2 — Governed

FILEAGENTS.md with frontmatter AND body sections. No AGENTS.md yet.
Created when user requests governance or approves your suggestion.

### L2 FILEAGENTS.md (complete file):

```yaml
---
id: acme-engagement
type: client
tags: [acme, enterprise, consulting, ai-audit, active]
domain: [consulting, contract-analysis]
status: active
depends_on_tags: [legal-templates, pricing-models]
created: 2025-11-15
verified: 2026-03-01
owner: Walter
spec_version: "0.3.0"
---

## Purpose
Active consulting engagement with Acme Corp focused on AI completeness
gap analysis. All deliverables, communications, and analysis.
NOT for internal business development notes.

## File governance
- Files named: YYYY-MM-DD_{description}.{ext}
- Drafts prefixed: DRAFT_
- Final versions prefixed: FINAL_
- Client-provided originals: never rename, never delete

## Quality standards
- All financial figures cite their source document
- No placeholder text in final outputs
- Executive summaries: max 1 page, no hedging

## Constraints
- Never delete original client-provided documents
- Formal tone for all external communications
- Confidential: do not reference in other folder contexts

## Tone and voice
Formal, precise, evidence-based. C-suite audience.

## Cross-references
- Depends on: legal-templates, pricing-models
- Feeds into: client-deliverables

## Activity heatmap
last_updated: 2026-03-20
- acme-contract-v3.pdf | 8 sessions | last: 2026-03-20
- competitive-brief.md | 6 sessions | last: 2026-03-18
- pricing-proposal.xlsx | 5 sessions | last: 2026-03-15
```

### Available body sections (use only what the folder needs)

```
## Purpose             What the folder is for. What it is NOT for.
## File governance     Naming, file types, retention, versioning.
## Quality standards   Testable output criteria.
## Audit/verification  Checks before files leave the folder.
## Constraints         Hard boundaries. What you must NEVER do.
## Tone and voice      Communication style, audience, formality.
## Output defaults     Default format, naming pattern.
## Cross-references    Related folders BY TAG only. Never paths.
## Activity heatmap    Rolling file access log (max 100 entries).
```

### Size limits

- Frontmatter: < 500 bytes
- Body: < 3000 words (if longer → subfolder extraction needed)
- Heatmap: max 100 entries (rolling: drop lowest when full)

### L2 humans.html

**Recommended.** A single `humans.html` in the same folder as `FILEAGENTS.md`,
regenerated when governance or material inventory changes. It is the **human lens**:
browser-friendly summary and routing to `FILEAGENTS.md` / `AGENTS.md`. Full rules and
HTML profile: `fileagents.humans.md`.

## L3 — Operative

FILEAGENTS.md (same as L2) PLUS AGENTS.md with execution procedures.
Created when user decides this folder needs operational LLM instructions.

At L3, `humans.html` should include a short **Procedures at a glance** section
sourced from `AGENTS.md` headings (not a full copy of procedures).

### L3 AGENTS.md (complete file):

```markdown
# Acme Corp engagement

## Overview
AI completeness gap analysis. Primary deliverables: diagnostic reports,
implementation roadmaps, executive briefings.

## Procedures

### Gap diagnostic
1. Read latest client-provided documents in this folder
2. Identify all AI workflows mentioned or implied
3. For each workflow assess: completeness, confidence calibration,
   human oversight
4. If available, delegate to Claude Skill: egp-diagnostic-designer
   Otherwise follow general framework:
   a. Map inputs → outputs → decisions for each workflow
   b. Identify where output is treated as complete without verification
   c. Rate severity: cosmetic | operational | strategic | existential
5. Produce diagnostic report using template below

### Executive briefing
1. Top 3 findings from most recent diagnostic
2. Each finding: one sentence problem, one sentence impact, one sentence fix
3. Max 1 page. Direct, no hedging, specific numbers.

## Templates

### Diagnostic report
# AI completeness gap diagnostic: {{client_name}}
Date: {{date}}
## Executive summary
{{3 sentences}}
## Findings
### {{Finding title}}
- Workflow: {{name}}
- Gap type: {{completeness|confidence|oversight}}
- Severity: {{cosmetic|operational|strategic|existential}}
- Evidence: {{specific observation}}
- Recommendation: {{action within 90 days}}

## Verification
Before presenting ANY deliverable:
- [ ] Every finding cites a specific document or observation
- [ ] Severity ratings justified with evidence
- [ ] Recommendations actionable within 90 days
- [ ] No placeholder text remains
- [ ] File naming follows FILEAGENTS.md convention

## Edge cases
- Password-protected docs: note as blocked, do not guess
- Ambiguous workflow: flag for clarification, don't assume
- Previous diagnostic exists: compare, note changes

## Domain knowledge
- Acme fiscal year ends June 30
- Primary contact: J. Smith (CTO), prefers bullet points
- Board reporting: quarterly, next April 15
```

### AGENTS.md maturity progression

Start simple. Grow through use. Never front-load complexity.

RUDIMENTARY → overview + 1-2 conventions
INTERMEDIATE → procedures with steps + output conventions + domain knowledge
OPERATIONAL → procedures + templates + verification + edge cases + domain data

### AGENTS.md rules

- Must NEVER contradict FILEAGENTS.md (FILEAGENTS always wins)
- Does NOT inherit from parent folders (always folder-specific)
- Platform tools (Claude Skills, GPT Actions) are hints, not dependencies
- The folder must work with any LLM without platform-specific tools
