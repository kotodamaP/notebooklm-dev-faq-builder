# Making Reference for NoteBookLM

`Making Reference for NoteBookLM` is a Codex Skill for turning a local software project into NotebookLM-ready reference material.

It helps create:

- `notebooklm-project-faq-source.md`: a source-backed project specification and FAQ reference document
- `notebooklm-developer-faq-metaprompt.md`: a metaprompt for developer-facing NotebookLM Q&A

The skill is designed for developers who want to ask specification, maintenance, and implementation questions after importing project context into NotebookLM.

## What It Does

- Reads local project docs, git state, configuration shape, scripts, tests, and source entry points.
- Separates confirmed facts, assumptions, contradictions, risks, and open questions.
- Produces NotebookLM-friendly Markdown with generation metadata and a source index.
- Avoids raw secrets, `.env` values, private credentials, and personal path details in shareable outputs.

## What It Does Not Do

- It does not upload files to NotebookLM.
- It does not fetch remote repositories or online sources unless explicitly requested.
- It does not inspect GitHub issues, pull requests, or external services by default.
- It does not read or copy raw secret-bearing files.

## Installation

Copy this repository folder into a Codex skill root, or install it as a user skill using your Codex environment's supported skill path.

The skill invocation name is:

```text
$making-reference-for-notebooklm
```

## Usage

Example prompt:

```text
Use $making-reference-for-notebooklm to inspect this project and create NotebookLM FAQ source material and a developer FAQ metaprompt.
```

By default, generated files should be placed under:

```text
<project-root>/docs/notebooklm/
```

## Safety Model

This skill is intentionally local-state-first and conservative:

- `.env`, `.env.local`, `.env.production`, private keys, tokens, and credential files should not be read or copied.
- `.env.example`, `.env.sample`, and `.env.template` may be inspected only for variable names and human-readable comments.
- Major claims should be backed by source paths, command summaries, explicit assumptions, or open questions.
- Existing output files should not be silently overwritten.

## Repository Contents

```text
SKILL.md
agents/openai.yaml
references/output-templates.md
```

## License

MIT

