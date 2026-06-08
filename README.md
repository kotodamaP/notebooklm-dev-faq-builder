# Making Reference for NoteBookLM

`Making Reference for NoteBookLM` is a Codex Skill for turning a local software project into NotebookLM-ready reference material.

It helps developers create source-backed project documentation and a NotebookLM metaprompt so they can ask specification, maintenance, and implementation questions immediately after importing the generated files into NotebookLM.

## Languages

- [English](#english)
- [日本語](#日本語)
- [繁體中文](#繁體中文)

---

## English

### Overview

This repository provides a Codex Skill that inspects the latest local state of a software project and prepares two Markdown files for NotebookLM:

- `notebooklm-project-faq-source.md`: source-backed project specification and FAQ reference material
- `notebooklm-developer-faq-metaprompt.md`: a developer-facing metaprompt for asking NotebookLM precise project questions

The skill is designed for developers who want to review unclear behavior, implementation details, maintenance context, and project decisions without manually rebuilding the project context every time.

### What It Does

- Reads local project docs, git state, configuration shape, scripts, tests, and source entry points.
- Separates confirmed facts, assumptions, contradictions, risks, and open questions.
- Produces NotebookLM-friendly Markdown with generation metadata and a source index.
- Helps NotebookLM answer with evidence, not vague summaries.
- Avoids raw secrets, `.env` values, private credentials, and personal path details in shareable outputs.

### What It Does Not Do

- It does not upload files to NotebookLM.
- It does not fetch remote repositories or online sources unless explicitly requested.
- It does not inspect GitHub issues, pull requests, or external services by default.
- It does not read or copy raw secret-bearing files.

### Installation

Copy this repository folder into a Codex skill root, or install it as a user skill using your Codex environment's supported skill path.

The skill invocation name is:

```text
$making-reference-for-notebooklm
```

### Usage

Example prompt:

```text
Use $making-reference-for-notebooklm to inspect this project and create NotebookLM FAQ source material and a developer FAQ metaprompt.
```

By default, generated files should be placed under:

```text
<project-root>/docs/notebooklm/
```

### Safety Model

This skill is intentionally local-state-first and conservative:

- `.env`, `.env.local`, `.env.production`, private keys, tokens, and credential files should not be read or copied.
- `.env.example`, `.env.sample`, and `.env.template` may be inspected only for variable names and human-readable comments.
- Major claims should be backed by source paths, command summaries, explicit assumptions, or open questions.
- Existing output files should not be silently overwritten.

---

## 日本語

### 概要

`Making Reference for NoteBookLM` は、ローカルのソフトウェアプロジェクトを調査し、NotebookLM に投入しやすい参照元資料を作成するための Codex Skill です。

このSkillは、プロジェクトの最新ローカル状態をもとに、次の2つのMarkdownファイルを作成することを目的にしています。

- `notebooklm-project-faq-source.md`: 根拠付きの仕様説明・FAQ参照資料
- `notebooklm-developer-faq-metaprompt.md`: NotebookLMに開発者向けの仕様確認Q&Aをさせるためのメタプロンプト

対象読者は初心者ではなく、実装・保守・レビュー・振り返りのために、プロジェクト仕様や未確認点をすぐ確認したい開発者です。

### できること

- ローカルのREADME、設計メモ、Git状態、設定ファイルの形、scripts、tests、source entry pointsを確認します。
- 確認済み事実、推測、矛盾、リスク、未確認事項を分けます。
- NotebookLMが読みやすいMarkdownとして、生成メタ情報とSource Index付きの資料を作ります。
- NotebookLMが曖昧な要約ではなく、根拠に基づいて答えやすい状態を作ります。
- 共有される可能性のある出力では、secret、`.env` の実値、認証情報、個人パス情報を避けます。

### やらないこと

- NotebookLMへのアップロードは行いません。
- 明示的に依頼されない限り、リモートリポジトリやオンライン情報は取得しません。
- GitHub Issue、Pull Request、外部サービスは標準では調査しません。
- secretを含む可能性のあるファイルの実値を読んだり転記したりしません。

### インストール

このリポジトリのフォルダを、利用中のCodex環境が認識するSkill rootへ配置してください。

Skillの呼び出し名は次の通りです。

```text
$making-reference-for-notebooklm
```

### 使い方

プロンプト例:

```text
Use $making-reference-for-notebooklm to inspect this project and create NotebookLM FAQ source material and a developer FAQ metaprompt.
```

標準では、生成物は次の場所に置く想定です。

```text
<project-root>/docs/notebooklm/
```

### 安全設計

このSkillは、ローカル状態を優先しつつ、慎重に資料化する設計です。

- `.env`、`.env.local`、`.env.production`、秘密鍵、token、credential fileは読んだり転記したりしません。
- `.env.example`、`.env.sample`、`.env.template` は、変数名と人間向けコメントだけを扱います。
- 主要な主張には、ファイルパス、コマンド結果の要約、明示した推測、または未確認事項を添えます。
- 既存のNotebookLM出力ファイルは、無言で上書きしません。

---

## 繁體中文

### 概覽

`Making Reference for NoteBookLM` 是一個 Codex Skill，用來檢查本機軟體專案，並產生適合匯入 NotebookLM 的參考資料。

這個 Skill 會根據專案目前的本機狀態，準備兩個 Markdown 檔案：

- `notebooklm-project-faq-source.md`：有來源依據的專案規格與 FAQ 參考資料
- `notebooklm-developer-faq-metaprompt.md`：讓 NotebookLM 以開發者角度回答規格問題的 metaprompt

它適合需要回顧規格、確認實作細節、維護脈絡與專案決策的開發者，而不是只需要入門說明的讀者。

### 可以做什麼

- 讀取本機文件、Git 狀態、設定檔結構、scripts、tests 與 source entry points。
- 區分已確認事實、推論、矛盾、風險與待確認問題。
- 產生適合 NotebookLM 閱讀的 Markdown，包含生成資訊與 Source Index。
- 讓 NotebookLM 更容易根據來源回答，而不是只給模糊摘要。
- 在可能分享的輸出中，避免包含 secret、`.env` 實際值、私人憑證與個人路徑資訊。

### 不會做什麼

- 不會自動上傳檔案到 NotebookLM。
- 除非使用者明確要求，否則不會抓取遠端 repository 或線上資料。
- 預設不會檢查 GitHub Issues、Pull Requests 或外部服務。
- 不會讀取或複製可能含有 secret 的原始檔案內容。

### 安裝

請將此 repository 資料夾放到你的 Codex 環境支援的 Skill root 中。

Skill 呼叫名稱如下：

```text
$making-reference-for-notebooklm
```

### 使用方式

範例 prompt：

```text
Use $making-reference-for-notebooklm to inspect this project and create NotebookLM FAQ source material and a developer FAQ metaprompt.
```

預設輸出位置：

```text
<project-root>/docs/notebooklm/
```

### 安全設計

這個 Skill 採取本機狀態優先且保守的資料處理方式：

- 不應讀取或複製 `.env`、`.env.local`、`.env.production`、private keys、tokens 或 credential files。
- `.env.example`、`.env.sample`、`.env.template` 只可用來擷取變數名稱與給人閱讀的註解。
- 主要結論應附上來源路徑、命令結果摘要、明確標示的推論，或待確認問題。
- 不應在未確認的情況下覆寫既有 NotebookLM 輸出檔案。

---

## Repository Contents

```text
SKILL.md
agents/openai.yaml
references/output-templates.md
```

## License

MIT

