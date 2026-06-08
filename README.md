# NotebookLM Dev FAQ Builder

Turn any local software project into NotebookLM-ready developer FAQ material.

`NotebookLM Dev FAQ Builder` is a public Codex Skill repository for generating source-backed project reference material and a developer-facing NotebookLM metaprompt. It is designed for developers who want to ask precise questions about specifications, implementation details, maintenance context, contradictions, and open issues after importing the generated files into NotebookLM.

> Current skill invocation name: `$making-reference-for-notebooklm`

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

The goal is simple: make a project immediately question-answerable in NotebookLM without manually rebuilding context from scattered README files, docs, scripts, tests, and local Git state.

### Quick Start

1. Clone or copy this repository into a Codex skill directory.
2. Confirm the skill is recognized as:

   ```text
   $making-reference-for-notebooklm
   ```

3. Run it in a local project:

   ```text
   Use $making-reference-for-notebooklm to inspect this project and create NotebookLM FAQ source material and a developer FAQ metaprompt.
   ```

4. Check the generated files:

   ```text
   docs/notebooklm/notebooklm-project-faq-source.md
   docs/notebooklm/notebooklm-developer-faq-metaprompt.md
   ```

5. Import the generated source document and metaprompt into NotebookLM, then ask developer-facing specification questions.

### Before / After

Before:

- README, docs, scripts, tests, and local Git state are scattered.
- NotebookLM answers may be vague because the source context is incomplete.
- Contradictions and assumptions are easy to miss.

After:

- A source-backed project FAQ source document is generated.
- A developer metaprompt tells NotebookLM how to answer precisely.
- Confirmed facts, assumptions, contradictions, risks, and open questions are separated.
- Generation metadata and source index make the snapshot easier to audit.

### What It Does

- Reads local project docs, Git state, configuration shape, scripts, tests, and source entry points.
- Separates confirmed facts, assumptions, contradictions, risks, and open questions.
- Produces NotebookLM-friendly Markdown with generation metadata and a source index.
- Helps NotebookLM answer with evidence, not vague summaries.
- Avoids raw secrets, `.env` values, private credentials, and personal path details in shareable outputs.

### What It Does Not Do

- It does not upload files to NotebookLM.
- It does not fetch remote repositories or online sources unless explicitly requested.
- It does not inspect GitHub issues, pull requests, or external services by default.
- It does not read or copy raw secret-bearing files.

### Safety Guarantees

By default, this skill:

- does not upload files to NotebookLM
- does not call external services
- does not fetch GitHub issues or pull requests
- does not read raw `.env` or credential files
- handles `.env.example`, `.env.sample`, and `.env.template` as names/comments only
- redacts user-specific paths when output may be shared
- stops before overwriting existing NotebookLM output files when manual notes cannot be preserved

### Installation

Copy this repository folder into a Codex skill root, or install it as a user skill using your Codex environment's supported skill path.

The current skill invocation name is:

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

### Examples

Example outputs are available under:

```text
examples/sample-notebooklm-project-faq-source.md
examples/sample-notebooklm-developer-faq-metaprompt.md
```

They show the intended output shape without exposing private project data.

---

## 日本語

### 概要

`NotebookLM Dev FAQ Builder` は、ローカル開発プロジェクトを NotebookLM で仕様確認しやすい、根拠付きFAQ資料へ変換するための Codex Skill リポジトリです。

このSkillは、プロジェクトの最新ローカル状態をもとに、次の2つのMarkdownファイルを作成することを目的にしています。

- `notebooklm-project-faq-source.md`: 根拠付きの仕様説明・FAQ参照資料
- `notebooklm-developer-faq-metaprompt.md`: NotebookLMに開発者向けの仕様確認Q&Aをさせるためのメタプロンプト

目的は、README、docs、scripts、tests、Git状態に散らばった情報を整理し、NotebookLMでプロジェクト仕様をすぐ質疑応答できる状態にすることです。

### Quick Start

1. このリポジトリをCodexのSkill directoryへcloneまたはcopyします。
2. Skillが次の名前で認識されることを確認します。

   ```text
   $making-reference-for-notebooklm
   ```

3. ローカルプロジェクトで実行します。

   ```text
   Use $making-reference-for-notebooklm to inspect this project and create NotebookLM FAQ source material and a developer FAQ metaprompt.
   ```

4. 生成されたファイルを確認します。

   ```text
   docs/notebooklm/notebooklm-project-faq-source.md
   docs/notebooklm/notebooklm-developer-faq-metaprompt.md
   ```

5. 生成された資料とメタプロンプトをNotebookLMへ入れ、開発者向けの仕様確認質問を行います。

### Before / After

Before:

- README、docs、scripts、tests、Git状態が散らばっている。
- NotebookLMに入れる参照元が弱く、回答が曖昧になりやすい。
- 矛盾、推測、未確認事項が見落とされやすい。

After:

- 根拠付きのプロジェクトFAQ参照資料が生成される。
- 開発者向けメタプロンプトにより、NotebookLMが精密に回答しやすくなる。
- 確認済み事実、推測、矛盾、リスク、未確認事項が分離される。
- 生成メタ情報とSource Indexにより、いつ・何を根拠にした資料か追跡しやすくなる。

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

### Safety Guarantees

標準では、このSkillは次のことを行いません。

- NotebookLMへファイルをアップロードしない
- 外部サービスを呼び出さない
- GitHub IssueやPull Requestを取得しない
- raw `.env` やcredential fileを読まない
- `.env.example`、`.env.sample`、`.env.template` は変数名とコメントだけ扱う
- 共有される可能性のある出力ではユーザー固有パスを伏せる
- 手動メモを安全に保持できない場合、既存NotebookLM出力を無言で上書きしない

### インストール

このリポジトリのフォルダを、利用中のCodex環境が認識するSkill rootへ配置してください。

現在のSkill呼び出し名は次の通りです。

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

### Examples

出力例は次の場所にあります。

```text
examples/sample-notebooklm-project-faq-source.md
examples/sample-notebooklm-developer-faq-metaprompt.md
```

公開用の安全なサンプルとして、出力の形を確認できます。

---

## 繁體中文

### 概覽

`NotebookLM Dev FAQ Builder` 是一個 Codex Skill repository，用來把本機開發專案整理成適合 NotebookLM 使用的、有來源依據的開發者 FAQ 參考資料。

這個 Skill 會根據專案目前的本機狀態，準備兩個 Markdown 檔案：

- `notebooklm-project-faq-source.md`：有來源依據的專案規格與 FAQ 參考資料
- `notebooklm-developer-faq-metaprompt.md`：讓 NotebookLM 以開發者角度回答規格問題的 metaprompt

目標是把分散在 README、docs、scripts、tests 與 Git 狀態中的資訊整理好，讓 NotebookLM 可以立即回答開發者的規格確認問題。

### Quick Start

1. 將此 repository clone 或 copy 到 Codex 的 Skill directory。
2. 確認 Skill 可以用以下名稱呼叫：

   ```text
   $making-reference-for-notebooklm
   ```

3. 在本機專案中執行：

   ```text
   Use $making-reference-for-notebooklm to inspect this project and create NotebookLM FAQ source material and a developer FAQ metaprompt.
   ```

4. 檢查產生的檔案：

   ```text
   docs/notebooklm/notebooklm-project-faq-source.md
   docs/notebooklm/notebooklm-developer-faq-metaprompt.md
   ```

5. 將產生的資料與 metaprompt 匯入 NotebookLM，開始詢問開發者導向的規格問題。

### Before / After

Before:

- README、docs、scripts、tests 與 Git 狀態分散在不同地方。
- NotebookLM 的來源脈絡不足，回答容易變得模糊。
- 矛盾、推論與待確認問題容易被忽略。

After:

- 產生有來源依據的 project FAQ source。
- developer metaprompt 會指示 NotebookLM 精準回答。
- 已確認事實、推論、矛盾、風險與待確認問題會被分開整理。
- generation metadata 與 Source Index 讓資料快照更容易稽核。

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

### Safety Guarantees

預設情況下，這個 Skill：

- 不會上傳檔案到 NotebookLM
- 不會呼叫外部服務
- 不會抓取 GitHub Issues 或 Pull Requests
- 不會讀取 raw `.env` 或 credential files
- 只會從 `.env.example`、`.env.sample`、`.env.template` 取得變數名稱與註解
- 在可能分享的輸出中會遮蔽使用者專屬路徑
- 如果無法安全保留手動註記，不會默默覆寫既有 NotebookLM 輸出檔

### 安裝

請將此 repository 資料夾放到你的 Codex 環境支援的 Skill root 中。

目前的 Skill 呼叫名稱如下：

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

### Examples

輸出範例位於：

```text
examples/sample-notebooklm-project-faq-source.md
examples/sample-notebooklm-developer-faq-metaprompt.md
```

這些範例展示了輸出格式，但不包含私人專案資料。

---

## Repository Contents

```text
README.md
SKILL.md
agents/openai.yaml
references/output-templates.md
examples/sample-notebooklm-project-faq-source.md
examples/sample-notebooklm-developer-faq-metaprompt.md
.gitignore
LICENSE
```

## License

MIT

