# FileAgents — Index operations

Read this when you need to generate, regenerate, read, or use
fileagents.index.md for discovery and cross-reference resolution.

## What fileagents.index.md is

A single auto-generated file at the disk or project root that maps
every tagged folder on the disk. It resolves tags to current paths
so folders can reference each other by tag (stable) instead of
path (volatile).

It is DISPOSABLE. Regenerate it any time. It is a cache, not truth.
The truth lives in each folder's FILEAGENTS.md.

## Format

```markdown
---
generated: {ISO 8601 datetime with timezone}
folders_scanned: {total directories examined}
fileagents_found: {number of FILEAGENTS.md files found or created}
unresolved_dependencies: {count}
---

# Context index

> Auto-generated. Do not manually edit. Regenerate by re-scanning.

## Folders by type

### client
- acme-engagement | /Clients/Acme/ | tags: acme, enterprise, active
- bravo-engagement | /Clients/Bravo/ | tags: bravo, energy, active

### project
- lynchpin-system | /Projects/LYNCHPIN/ | tags: property, monte-carlo

### knowledge
- legal-library | /Knowledge/Legal/ | tags: legal-templates, contracts

## Tag resolution

| tag | id | path |
|-----|----|------|
| acme | acme-engagement | /Clients/Acme/ |
| legal-templates | legal-library | /Knowledge/Legal/ |
| property | lynchpin-system | /Projects/LYNCHPIN/ |

## Unresolved dependencies
- regulatory-compliance | needed by: acme-engagement | NO MATCH

## Stale folders (verified >90 days ago or never)
- old-archive | /Archive/2023/ | verified: null
```

## Generation algorithm

```
1. FIND all FILEAGENTS.md recursively under root
   Max depth: 6
   SKIP: .git, node_modules, __pycache__, .venv, .Trash, Library, Applications
2. For each FILEAGENTS.md found:
   a. PARSE YAML frontmatter
   b. VALIDATE: id and tags must exist and be non-empty
   c. EXTRACT: id, type, tags, status, depends_on_tags, verified
   d. RECORD: path of the containing folder
3. BUILD tag resolution table (one row per unique tag):
   tag → folder id → current path
   WARN if: same tag in multiple folders (ambiguous)
   WARN if: duplicate ids across folders (collision)
4. BUILD unresolved dependencies:
   For each depends_on_tags value across all folders,
   if that tag does not appear in any folder's tags array → unresolved
5. BUILD stale list:
   Any folder where verified is null or >90 days ago
6. WRITE fileagents.index.md at root in the format above
```

## Rules

- Generation is READ-ONLY on all FILEAGENTS.md files
- It writes ONLY fileagents.index.md
- It NEVER modifies any FILEAGENTS.md or AGENTS.md
- If fileagents.index.md already exists, overwrite it (it's disposable)

## When to regenerate

- User asks
- After any folder create, rename, move, or delete
- When a tag lookup fails
- After a scan operation (SCAN.md generates it automatically)
- Periodically if automated (weekly)

## Tag resolution (how to use the index)

When you encounter depends_on_tags or cross-references in a FILEAGENTS.md:

```
1. READ fileagents.index.md
2. LOOK UP the tag in the tag resolution table
3. IF found → use the path to access that folder
4. IF not found → tell the user, continue working
5. NEVER halt or fail on an unresolved dependency
```

### Tag collisions
If two folders have the same tag, the index lists both with WARN.
Present both to the user and ask which they mean.

### Stale index
If fileagents.index.md is missing or stale:
- You can still work locally using the current folder's FILEAGENTS.md
- Cross-references won't resolve until the index is regenerated
- Offer to regenerate

## Inheritance (relevant to discovery)

FILEAGENTS.md inherits downward:
- If a child folder has no FILEAGENTS.md, its nearest parent's governs it
- Walk UP max 6 levels to find the nearest FILEAGENTS.md
- The closest one wins completely (no merging)

AGENTS.md does NOT inherit:
- Execution instructions are folder-specific only
- A parent's AGENTS.md does not apply to children

## Edge cases

```
INDEX MISSING           Work locally, offer to regenerate
INDEX STALE             Use it, note failures, offer to regenerate
TAG NOT FOUND           Report to user, continue gracefully
DUPLICATE TAG           List both folders, ask user to resolve
DUPLICATE ID            WARN, both folders indexed, user should rename one
PATH IN INDEX DEAD      Folder was moved/deleted, regenerate
>100 CONTEXTED FOLDERS  Index may exceed context window — load by
                        type/domain section rather than full index
```

## The critical rule about paths vs tags

Paths appear ONLY in fileagents.index.md (which is regenerable).
Every other file in the system uses TAGS for cross-references.
When a folder moves, its FILEAGENTS.md tags are unchanged.
Only the index needs regenerating to update the path mapping.

This is why folders survive renames, moves, and restructuring.
