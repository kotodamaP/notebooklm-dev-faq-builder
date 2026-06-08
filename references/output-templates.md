# Output Templates

Use these templates when `$notebooklm-dev-faq-builder` creates NotebookLM-ready project FAQ material.

The standard output directory is:

```text
<project-root>/docs/notebooklm/
```

The standard output files are:

```text
notebooklm-project-faq-source.md
notebooklm-developer-faq-metaprompt.md
```

## Template: notebooklm-project-faq-source.md

```markdown
# NotebookLM Project FAQ Source

## Generation Metadata

- Project name:
- Project root:
  - Local/private:
  - Share-safe:
- Output directory:
- Generated at:
- Branch:
- HEAD:
- Working tree status: clean / dirty / untracked-only / unknown
- Changed file summary:
  - modified:
  - added:
  - deleted:
  - untracked:
- Recent commits:
- Skill: notebooklm-dev-faq-builder
- Notes:
  - This document is generated from the latest local project state available at generation time.
  - Confirmed facts, assumptions, contradictions, risks, and open questions are separated.
  - Secrets, private credentials, and raw environment values are intentionally excluded.

## NotebookLM Ingestion Checklist

- [ ] No raw secrets, tokens, private keys, passwords, or raw environment values included
- [ ] Confirmed facts and assumptions are separated
- [ ] Contradictions are listed
- [ ] Open questions are listed
- [ ] Source index is present
- [ ] Generation metadata is present
- [ ] User-specific path segments are redacted if this file may be shared

## For Developers: Start Here

- What this project does:
- What problem it solves:
- Current implementation status:
- What is safe to rely on:
- What is experimental or provisional:
- Where to look for answers:

## Current Local State

Summarize branch, HEAD, working tree status, changed files, recent commits, and any local-only changes that affect specification interpretation.

## Source-Backed Facts

### <Topic>

- Confirmed:
  - ...
- Evidence:
  - `<path>`: ...
  - command result: ...
- Notes:
  - ...

## Architecture And Data Flow

Describe the main components, execution flow, data flow, storage, integration points, and boundaries. Keep claims tied to source paths or command summaries.

## Interfaces And Configuration

Cover public APIs, CLIs, UI entry points, config files, environment variable names from safe templates, schemas, and important defaults.

Do not include raw secrets or raw environment values.

## Developer Commands

List setup, test, build, lint, smoke, and run commands that are directly supported by local docs, manifests, or scripts.

## FAQ Seeds

Write developer-facing questions that NotebookLM should be able to answer from this source.

- Q:
  - Answer basis:
  - Evidence:
- Q:
  - Answer basis:
  - Evidence:

## Contradictions

### <Conflict title>

- Source A:
- Source B:
- Current interpretation: unresolved / likely A / likely B
- Suggested verification:

## Risks

- Risk:
  - Why it matters:
  - Evidence:
  - Mitigation or next check:

## Open Questions

- Question:
  - Why it matters:
  - Suggested file or command to check:

## Assumptions

- Assumption:
  - Reason:
  - How to verify:

## Source Index

| Source | Why it matters | Status |
|---|---|---|
| `<path>` |  | read / summarized / skipped |

## Regeneration Notes

Use this section when replacing or updating a previous output.

- Previous file checked:
- Manual notes preserved:
- Replacement summary:
```

## Template: notebooklm-developer-faq-metaprompt.md

```markdown
# NotebookLM Developer FAQ Metaprompt

You are answering as a developer-facing specification FAQ assistant using only the material in this NotebookLM notebook.

The target reader is not a beginner. They are a developer who wants to confirm unclear behavior, implementation details, maintenance context, or decisions. Keep answers precise, source-backed, and useful for implementation or review.

## Answer Policy

- Prefer evidence from the provided material.
- If there is no evidence in the material, say: "The provided material does not confirm this."
- If you make an inference, clearly label it as an inference and name the files or commands that should be checked next.
- If older documentation conflicts with current implementation, do not silently choose one side. Report the contradiction.
- Do not restate secrets, tokens, personal information, or raw environment values.
- Check the generation metadata before answering when branch, HEAD, or working tree state matters.

## Answer Format

1. Conclusion
2. Evidence
   - Document name, section, and file path
3. Implementation notes
4. Unknowns and inferences
5. Next files or commands to check

## Prohibited Behavior

- Do not assert undocumented specifications as facts.
- Do not treat inferences as confirmed facts.
- Do not repeat secrets, tokens, personal information, or raw environment values.
- Do not hide contradictions between sources.
- Do not oversimplify for beginners when developer-level detail is needed.
```
