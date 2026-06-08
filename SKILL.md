---
name: making-reference-for-notebooklm
description: Use this skill when the user wants to inspect a local software project and create NotebookLM-ready reference material plus a developer-facing FAQ metaprompt. It should analyze local docs, git status, configuration shape, tests, scripts, and source structure, while separating confirmed facts from assumptions and excluding secrets.
---

# Making Reference for NoteBookLM

Use this skill to create reference material that lets developers ask NotebookLM high-quality specification questions about a local software project.

The standard output is two Markdown files:

- `notebooklm-project-faq-source.md`: source-backed project specification and FAQ source material.
- `notebooklm-developer-faq-metaprompt.md`: a metaprompt for asking NotebookLM developer-oriented specification questions.

For the required output structure, use [output-templates.md](references/output-templates.md).

## Scope

Default source of truth is the latest local project state:

- current files and local documentation
- current branch and HEAD
- uncommitted changes and untracked files
- local configuration shape, tests, scripts, public interfaces, and source entry points

Remote fetching, GitHub issue or PR inspection, NotebookLM upload, browser automation, and external service login are out of scope unless the user explicitly requests them.

## Workflow

1. Identify the target project root.
   - Prefer `git rev-parse --show-toplevel` when the target is a git repository.
   - If not a git repository, use the current working directory or the user-provided path.

2. Choose the output directory.
   - Use the user-specified output directory if provided.
   - Otherwise create or update `docs/notebooklm` under the project root.

3. Capture local project state before reading source material.
   - Use the command set in the "Git State" section when git is available.
   - If git is unavailable or the directory is not a repository, mark branch, HEAD, and working tree status as `unknown`.

4. Inspect project sources in priority order.
   - Local agent instructions: `AGENTS.md`, `RULES.md`, or equivalent project guidance
   - Overview docs: `README*`, `CONTRIBUTING*`, `CHANGELOG*`
   - `docs/`, design notes, architecture notes
   - manifests and dependency files
   - configs with values redacted
   - tests and fixtures that reveal intended behavior
   - scripts and task runners
   - public interfaces and source entry points

5. Draft the two output files using the reference templates.
   - Separate confirmed facts, assumptions, contradictions, risks, and open questions.
   - Make every major claim source-backed.
   - Include generation metadata and a source index.

6. Validate the output.
   - Check that no raw secrets or environment values were included.
   - Check that paths are redacted if the output may be shared.
   - Check that NotebookLM ingestion checklist items are present.

## Git State

Capture this initial context when git is available:

```shell
git rev-parse --show-toplevel
git branch --show-current
git rev-parse --short HEAD
git log -n 5 --oneline --decorate
git status --short --branch
git diff --stat
git diff --name-only
```

Use stable working tree labels:

- `clean`: no tracked or untracked changes
- `dirty`: tracked files are modified, added, deleted, renamed, or copied
- `untracked-only`: only untracked files are present
- `unknown`: git state cannot be determined

Prefer file names and diff stats. Read `git diff` body only when needed to understand a local behavior change, and never copy large diffs into NotebookLM source material.

## Security And Redaction

Do not read or copy raw values from:

- `.env`, `.env.local`, `.env.production`
- credentials, private keys, tokens, password stores, and secret-bearing files
- raw environment variable dumps
- files that appear to contain private credentials

Allowed with caution:

- `.env.example`
- `.env.sample`
- `.env.template`

For example or template env files, extract only variable names and human-readable comments. Do not copy example values if they resemble real secrets, emails, private endpoints, credentials, tokens, or URLs with embedded credentials.

For private local use, absolute project paths may be useful. If the output may be shared, redact user-specific path segments such as `/Users/<user>/`, `/home/<user>/`, or `C:\Users\<user>\`, and prefer including both project name and redacted project root.

## Source-Backed Claims

Every major claim in the NotebookLM source document must include at least one of:

- a source file path
- a summarized command result
- a clearly marked assumption
- an open question when not verified

When sources conflict:

- Prefer current code and tests over old docs for observed behavior.
- Prefer project instruction files for project policy.
- Prefer README and docs for intended public explanation.
- Do not silently resolve conflicts.
- Record both source paths, current interpretation, and a suggested verification action.

## Existing Output Files

If output files already exist:

- Do not silently overwrite them.
- Read them briefly before replacing or updating.
- Preserve useful manual notes where possible.
- Add or update generation metadata with generated time, branch, HEAD, working tree status, changed file summary, and skill name.
- If manual notes cannot be safely preserved, stop and ask the user.

## Stop Conditions

Stop and ask the user before:

- reading files that appear to contain secrets or private credentials
- overwriting existing NotebookLM output files when manual notes cannot be safely preserved
- fetching remote repositories or online sources
- uploading anything to NotebookLM or another external service

