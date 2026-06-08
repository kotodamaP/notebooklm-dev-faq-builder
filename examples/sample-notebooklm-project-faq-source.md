# NotebookLM Project FAQ Source

## Generation Metadata

- Project name: sample-web-tool
- Project root:
  - Local/private: redacted
  - Share-safe: `<project-root>`
- Output directory: `<project-root>/docs/notebooklm`
- Generated at: 2026-06-08 00:00:00 +00:00
- Branch: `main`
- HEAD: `abc1234`
- Working tree status: clean
- Changed file summary:
  - modified: none
  - added: none
  - deleted: none
  - untracked: none
- Recent commits:
  - `abc1234 docs: update usage guide`
- Skill: notebooklm-dev-faq-builder
- Notes:
  - This sample is synthetic and contains no private project data.
  - Confirmed facts, assumptions, contradictions, risks, and open questions are separated.
  - Secrets, private credentials, and raw environment values are intentionally excluded.

## NotebookLM Ingestion Checklist

- [x] No raw secrets, tokens, private keys, passwords, or raw environment values included
- [x] Confirmed facts and assumptions are separated
- [x] Contradictions are listed
- [x] Open questions are listed
- [x] Source index is present
- [x] Generation metadata is present
- [x] User-specific path segments are redacted if this file may be shared

## For Developers: Start Here

- What this project does: Provides a small command-line utility for exporting project notes.
- What problem it solves: Helps developers collect project notes into a single Markdown export.
- Current implementation status: Stable CLI with tests and documented configuration.
- What is safe to rely on: The CLI command and documented config keys.
- What is experimental or provisional: Planned HTML export support is not implemented.
- Where to look for answers: `README.md`, `src/cli.ts`, `tests/cli.test.ts`, `.env.example`.

## Current Local State

The repository is clean on `main` at `abc1234`. No local changes were detected.

## Source-Backed Facts

### CLI Entry Point

- Confirmed: The project exposes a CLI command named `sample-export`.
- Evidence:
  - `README.md`: documents `sample-export`.
  - `src/cli.ts`: defines the command entry point.

### Configuration

- Confirmed: Safe configuration names are documented in `.env.example`.
- Evidence:
  - `.env.example`: variable names only.
- Notes:
  - Raw `.env` values were not read or copied.

## Contradictions

### HTML Export Mentioned But Not Implemented

- Source A: `README.md` mentions planned HTML export.
- Source B: `src/cli.ts` exposes only Markdown export.
- Current interpretation: HTML export is planned but not implemented.
- Suggested verification: Check roadmap notes or issue tracker if remote inspection is explicitly requested.

## Risks

- Risk: Users may assume HTML export exists.
  - Why it matters: The README uses future-facing language.
  - Evidence: `README.md`, `src/cli.ts`
  - Mitigation or next check: Clarify README wording or add an open question.

## Open Questions

- Question: Is HTML export still planned?
  - Why it matters: README wording may create user expectations.
  - Suggested file or command to check: project roadmap or maintainer notes.

## Source Index

| Source | Why it matters | Status |
|---|---|---|
| `README.md` | public behavior and commands | read |
| `src/cli.ts` | implementation entry point | read |
| `tests/cli.test.ts` | expected behavior | read |
| `.env.example` | safe config names | summarized |
