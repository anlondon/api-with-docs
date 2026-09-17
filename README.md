# api-docs

Cursor Agent skill for **client-facing API / Apifox copy**.  
给调用方写接口说明、字段说明、Apifox 描述的 Cursor Agent skill。

Not a business-process writer. Not a code-to-Chinese translator.  
不写业务流程文档，不把实现翻译成中文。

---

## 中文

### 做什么

读者是 App / 前端 / 其他调用方。每个接口（字段更短）只写三块：

1. **使用方法** — 第一句写用途；接着写必要的调用约束（一次存几侧、成功看哪、失败怎么办、配合哪个接口）。
2. **传参方法** — 只写参数表看不出来的对应关系，不抄 Apifox 字段清单。
3. **注意事项** — 一条一事。多种流程状态或业务场景结果不同时才按状态/场景分列；有易混接口才写「本接口不做什么」。

对照见 [examples.md](examples.md)。用词见本仓库 [CONTEXT.md](CONTEXT.md)。写作规则见 [SKILL.md](SKILL.md)。

### 不做什么

- 不造词。有业务术语就写成「中文(`代码标识`)」；没有中文名就留字段名并标 **待确认**。
- 不写推断、不补「因为」、不把程序流程摘要成业务。
- 不改业务仓库的 glossary（那是 grill-with-docs 的事）。
- 不跑 `/chinese-ai-humanizer`。

### 和 grill-with-docs

| | grill-with-docs | api-docs |
|---|---|---|
| 何时 | 方案对齐、新词还没定 | 词已有（或只能用代码标识）要出对接文 |
| 产物 | `CONTEXT.md`、偶发 ADR | 三块对接说明 |

缺词时：沿术语来源找；找不到就 `job_type = 9`（待确认），不停写、不临场起名。

### 安装（Cursor）

放到个人 skill 目录后即可 `/api-docs`：

```text
~/.cursor/skills/api-docs/
  SKILL.md
  CONTEXT.md
  examples.md
  README.md
```

本仓库若已 junction 到该目录，改这里即改 Cursor 里的 skill。

---

## English

### What it does

The reader is the client (App / frontend / caller). Each endpoint uses three blocks only (fields use the same shape, shorter):

1. **How to use** — first sentence is *purpose*; then only the call constraints the caller must know.
2. **How to pass params** — mapping the schema does not show. Do not copy the Apifox parameter table.
3. **Notes** — one rule per bullet. Split by workflow state / business scenario only when outcomes differ. Write duty boundaries only when another endpoint is easy to confuse with this one.

See [examples.md](examples.md). Glossary: [CONTEXT.md](CONTEXT.md). Agent rules: [SKILL.md](SKILL.md).

### What it does not do

- No coined names. Pair existing domain terms as `中文(\`code\`)`. If there is no Chinese name, keep the identifier and mark **待确认**.
- No speculation, no invented “because”, no summarizing backend call chains as “business”.
- Does not edit a product repo’s glossary (that is grill-with-docs).
- Do not run `/chinese-ai-humanizer` on this copy.

### With grill-with-docs

| | grill-with-docs | api-docs |
|---|---|---|
| When | Aligning a plan; terms still fuzzy | Terms exist (or only code ids) and you need caller docs |
| Output | `CONTEXT.md`, occasional ADRs | The three-block caller text |

If the glossary is missing: harvest names from existing docs / UI / comments; otherwise write the code identifier and **待确认**. Keep writing. Do not invent a nicer Chinese name.

### Install (Cursor)

```text
~/.cursor/skills/api-docs/
  SKILL.md
  CONTEXT.md
  examples.md
  README.md
```

Then invoke `/api-docs`. If this repo is already a junction to that folder, edits here are the live skill.
