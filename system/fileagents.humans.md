# FileAgents — humans.html (human lens)

Read this when you need to create, refresh, or validate `humans.html` in a folder.
For level definitions, see `fileagents.levels.md`. Governance and procedures stay in
`FILEAGENTS.md` and `AGENTS.md`; `humans.html` is a **derived, human-optimized view**
of the same truth.

## What humans need (research basis)

When a folder is an LLM knowledge base, people still open folders in Finder,
code hosts, or shared drives. They need **fast orientation** without reading long
governance markdown. Good folder-level human docs (analogous to README best
practice: purpose, scope, status, how to get help) typically answer:

| Need | Why it helps |
|------|----------------|
| **What this is** (one breath) | Reduces mistaken use of the wrong folder |
| **Who it is for / not for** | Matches audience to content; avoids policy mistakes |
| **In scope / out of scope** | Mirrors `FILEAGENTS.md` purpose; sets boundaries |
| **How to use this folder with an LLM** | Points to `FILEAGENTS.md` + `AGENTS.md` as machine-readable source of truth |
| **What is actually here** | Inventory at the right granularity (see below) |
| **Where to start** | 3–7 “entry” files or subfolders a human should open first |
| **Freshness & trust** | Last updated date; confidentiality / export warnings if present in governance |
| **Related folders** | By **tag name**, not path (consistent with FileAgents rules) |

**Inventory granularity (match folder homogeneity):**

- **Tight / focused folder** — Name notable files or a short grouped list (e.g. “3 briefs, 1 contract PDF”).
- **Broad / diverse folder** — Summarize **clusters** (subfolders + role), not every file. Prefer “what kinds of things” over a raw file listing.
- **Large / volatile** — High-level map + “see `FILEAGENTS.md` Activity heatmap” if present.

`humans.html` must **not** invent policy. If something matters, it must already appear in
`FILEAGENTS.md` (or, for procedures, in `AGENTS.md`). This file **summarizes and routes**;
it does not replace governance.

## What humans.html is

- **Optional at L1**, **recommended at L2+** (see `fileagents.levels.md`).
- **Static HTML only** — no build step, no JavaScript required, no network fetches.
- **Opened in a browser** — double-click or `file://` URL; must render in all major browsers.
- **Regenerable** — treat like `fileagents.index.md`: safe to replace wholesale when
  regenerating from current `FILEAGENTS.md` + `AGENTS.md` + directory listing, unless the
  user explicitly marks the file as hand-maintained (see below).

## Hard rules

1. **Never contradict `FILEAGENTS.md`.** If there is a conflict, `FILEAGENTS.md` wins;
   fix `humans.html`.
2. **Do not use file paths for cross-folder references** — use **tags** (same as rest of FileAgents).
3. **Escape text** — `&`, `<`, `>` in body copy must be escaped as `&amp;`, `&lt;`, `&gt;`.
4. **No external resources required** — no `<link href="…">` to stylesheets, no `@import`,
   no fonts from URLs, no images unless they are **same-folder relative** and the user asked
   for them (default: **no images**).
5. **No JavaScript** — not needed for this use case; avoids CSP and `file://` quirks.
6. **Human approval** — do not create L2+ `humans.html` from scratch or bulk-replace an
   existing one without the same approval model as other elaboration (`fileagents.elaborate.md`).

## Safe HTML profile (low load, high compatibility)

Use **HTML5** with a small, boring subset:

- `DOCTYPE html`, `<html lang="…">`, `<head>`, `<body>`.
- **Charset:** `<meta charset="utf-8">` as the first element inside `<head>`.
- **Viewport (optional, recommended):** `<meta name="viewport" content="width=device-width, initial-scale=1">` for phones.
- **Title:** `<title>` = short folder label (usually matches the folder’s intent, not necessarily the disk name).
- **Metadata (optional):** `<meta name="description" content="…">` — one sentence summary for bookmarks and search.

**Optional readability styling (allowed):** a single `<style>` block in `<head>` using only
widely supported declarations, for example:

```html
<style>
  body { font-family: system-ui, Segoe UI, Roboto, Helvetica, Arial, sans-serif;
         line-height: 1.45; max-width: 52rem; margin: 1rem auto; padding: 0 1rem; }
  h1 { font-size: 1.35rem; }
  h2 { font-size: 1.1rem; margin-top: 1.25rem; }
  .muted { color: #444; font-size: 0.9rem; }
</style>
```

Do **not** rely on flexbox/grid for **critical** readability (content must still make sense
in Lynx-style reading order). Tables (`<table>`) are allowed for small summaries.

**Forbidden (portability hazards):** external CSS/JS, base href tricks, iframes, inline event
handlers, SVG with script, custom elements.

## Content outline (adapt to level)

### L1 — Catalogued (minimal)

If `humans.html` exists at L1:

- Title + one paragraph: what the tag/id represents, and that governance is frontmatter-only in `FILEAGENTS.md`.
- Link text (not href to paths): name the files `FILEAGENTS.md`, `humans.html` as plain text so users know what to open.

### L2 — Governed (default full outline)

Suggested sections (use `<h2>` headings; skip sections with nothing to say):

1. **Summary** — 2–4 sentences from Purpose + type + status.
2. **Who should use this** — audience from Tone / Purpose.
3. **What’s in this folder** — inventory at appropriate granularity (see above).
4. **Start here** — bullet list of entry points (file names only; no full paths).
5. **Rules that matter** — 3–6 bullets max, taken only from `FILEAGENTS.md` (constraints, quality, naming).
6. **Working with an LLM** — one short paragraph: read `FILEAGENTS.md` first; if present, follow `AGENTS.md` for procedures.
7. **Related (by tag)** — list tag names and plain-language roles; never raw paths.
8. **Freshness** — `Last updated: YYYY-MM-DD` from `FILEAGENTS.md` (`verified`, `last_updated` in heatmap, or today if you just regenerated).

### L3 — Operative

Same as L2, plus:

- **Procedures at a glance** — 3–8 bullets summarizing section titles from `AGENTS.md`, not the full text.

## Generation algorithm

```
1. READ FILEAGENTS.md (frontmatter + body). If missing → do not create humans.html.
2. IF AGENTS.md exists → read headings and overview only (do not dump full markdown).
3. LIST directory (non-recursive or shallow: depth 1). Skip dot-directories.
   Classify: tight vs diverse vs large using file/subfolder counts and FILEAGENTS Purpose.
4. BUILD HTML following “Safe HTML profile” and “Content outline” for this folder’s level.
5. WRITE humans.html in the SAME folder as FILEAGENTS.md.
6. IF user maintains a hand-edited humans.html:
   IF first line is <!-- fileagents-humans: hand-maintained -->
     → do not overwrite; offer a diff in chat instead.
```

## When to create or refresh

Do **together** with governance updates when possible:

| Trigger | Action |
|---------|--------|
| New L2 governance | Create or replace `humans.html` (with approval) |
| `FILEAGENTS.md` body or frontmatter materially changes | Refresh `humans.html` |
| `AGENTS.md` added or section structure changes | Refresh “Procedures at a glance” |
| Material file add/remove/rename in folder | Refresh inventory / “Start here” if affected |
| User says “refresh humans.html” | Regenerate from current sources |

Light-touch L1 scans may **omit** `humans.html` to keep scans fast; add on request or at L2.

## Complete minimal example (structure only)

```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Acme engagement — folder overview</title>
<meta name="description" content="Client workpapers and deliverables for Acme Corp AI audit.">
<style>
  body { font-family: system-ui, Segoe UI, Roboto, Helvetica, Arial, sans-serif;
         line-height: 1.45; max-width: 52rem; margin: 1rem auto; padding: 0 1rem; }
  h1 { font-size: 1.35rem; }
  h2 { font-size: 1.1rem; margin-top: 1.25rem; }
</style>
</head>
<body>
<h1>Acme Corp — consulting engagement</h1>
<p><strong>Summary:</strong> …</p>
<h2>What’s here</h2>
<p>…</p>
<h2>Start here</h2>
<ul>
  <li>…</li>
</ul>
<h2>Rules that matter</h2>
<ul>
  <li>…</li>
</ul>
<h2>Working with an LLM</h2>
<p>Read <strong>FILEAGENTS.md</strong> for governance. If <strong>AGENTS.md</strong> exists, use it for step-by-step procedures.</p>
<h2>Related folders (tags)</h2>
<p>legal-templates, pricing-models</p>
<p class="muted">Last updated: 2026-03-26 · FileAgents spec 0.3.0</p>
</body>
</html>
```

## spec_version

Recommend in `FILEAGENTS.md` frontmatter: `spec_version: "0.3.0"` when using `humans.html`.
