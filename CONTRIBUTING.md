# Contributing to FileAgents

FileAgents is an open standard. Contributions that make the system simpler,
more robust, or more widely adopted are welcome.

## What to contribute

**Most valuable:**
- Real-world usage reports (what worked, what broke, what's missing)
- Edge cases we haven't covered
- Examples from different domains (engineering, legal, creative, academic)
- LLM compatibility reports (tested on GPT, Gemini, Llama, Mistral, etc.)

**Also welcome:**
- Improvements to the system files (fileagents.*.md)
- Better examples
- Tooling (scanners, validators, index generators)
- Documentation

**Please don't:**
- Add complexity without clear justification
- Propose features that require specific LLM platforms
- Add dependencies on external tools or services

## Design principles to follow

1. Two files per folder, one index at root. Don't add more files.
2. Plain markdown only. No YAML files, no JSON configs, no databases.
3. Any LLM must be able to operate the system. No vendor-specific features.
4. Progressive elaboration: L0→L1 is automated, L2+ requires human approval.
5. Tags for references, never paths.

## How to submit

1. Fork the repo
2. Make your changes
3. Test with at least one LLM (describe which in your PR)
4. Submit a pull request with a clear description of what and why

## Reporting issues

Open an issue with:
- What you tried to do
- What happened
- Which LLM you were using
- The FILEAGENTS.md and/or AGENTS.md content (if relevant)
