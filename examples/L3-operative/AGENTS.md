# Acme Corp engagement

## Overview
AI completeness gap analysis. Primary deliverables: diagnostic reports,
implementation roadmaps, executive briefings.

Key domain context: Acme runs 12 AI-augmented workflows across operations
and finance. Three have known completeness gaps flagged in initial assessment.

## Procedures

### Gap diagnostic
1. Read latest client-provided documents in this folder
2. Identify all AI workflows mentioned or implied
3. For each workflow, assess:
   - Completeness: does the AI output cover all required dimensions?
   - Confidence calibration: does the system indicate uncertainty appropriately?
   - Human oversight: is there a verification step before action?
4. If available, delegate to Claude Skill: egp-diagnostic-designer
   Otherwise, use general framework:
   a. Map inputs → outputs → decisions for each workflow
   b. Identify where output is treated as complete without verification
   c. Rate severity: cosmetic | operational | strategic | existential
5. Produce diagnostic report using template below

### Executive briefing
1. Summarise top 3 findings from most recent diagnostic
2. Each finding: one sentence problem, one sentence impact, one sentence fix
3. Max 1 page total
4. Tone: direct, no hedging, specific numbers where available

### Progress update (weekly)
1. List completed actions since last update
2. List blocked items with specific blocker
3. List next-week priorities (max 3)
4. Format: bullet list, no prose padding

## Templates

### Diagnostic report
```
# AI completeness gap diagnostic: {{client_name}}
Date: {{date}}
Prepared by: {{author}}

## Executive summary
{{3 sentences: what we found, why it matters, what to do}}

## Findings

### {{Finding title}}
- Workflow: {{name}}
- Gap type: {{completeness | confidence | oversight}}
- Severity: {{cosmetic | operational | strategic | existential}}
- Evidence: {{specific observation from client documents}}
- Recommendation: {{specific action, achievable within 90 days}}
- Estimated effort: {{hours or days}}

[Repeat for each finding]

## Methodology
{{Brief description of assessment approach}}
```

## Verification
Run before presenting ANY deliverable from this folder:
- [ ] Every finding cites a specific document or observation
- [ ] Severity ratings are justified with evidence, not assumed
- [ ] Recommendations are actionable within 90 days
- [ ] No placeholder text ({{...}}) remains in output
- [ ] Executive summary is consistent with detailed findings
- [ ] File naming follows FILEAGENTS.md convention
- [ ] Formal tone throughout — no casual language

## Edge cases
- Password-protected documents: note as blocked, do not guess content
- Ambiguous workflow (AI or manual?): flag for clarification, do not assume
- Previous diagnostic exists in folder: compare findings, note changes
  and persistent issues
- Conflicting data between documents: flag the conflict explicitly

## Domain knowledge
- Acme's fiscal year ends June 30
- Primary contact: J. Smith (CTO), prefers bullet-point summaries
- Board reporting cycle: quarterly, next due April 15
- Competitor context: Bravo Corp is a separate engagement —
  do not cross-reference without explicit approval
