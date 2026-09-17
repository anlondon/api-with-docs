# api-with-docs

**中文** | [English](README.en.md)

给调用方写接口说明、字段说明、Apifox 描述。不写业务流程文档，不把实现翻译成中文。

## 请和 grill-with-docs 一起用

本 skill **依赖** `grill-with-docs`（请先安装同名 skill）来对齐 **业务术语** 并维护项目 `CONTEXT.md`。

没有 grill-with-docs 时：没有稳定词表，模型仍会造词、把代码译成中文、补「因为」。效果会大打折扣。先装并会用 grill，再跑 `/api-with-docs`。

## 做什么

读者是 App / 前端 / 其他调用方。每个接口（字段更短）只写三块：

1. **使用方法** — 第一句写用途；接着写必要的调用约束。
2. **传参方法** — 只写参数表看不出来的对应关系，不抄字段清单。
3. **注意事项** — 一条一事。多种流程状态或业务场景结果不同时才分列；有易混接口才写「本接口不做什么」。

对照 [examples.md](examples.md)。用词 [CONTEXT.md](CONTEXT.md)。规则 [SKILL.md](SKILL.md)。

## 不做什么

- 不造词。有业务术语写成「中文(`代码标识`)」；没有中文名就留字段名并标 **待确认**。
- 不写推断、不补「因为」、不把程序流程摘要成业务。
- 不改业务仓库的 glossary（由 grill-with-docs 维护）。
- 不跑 `/chinese-ai-humanizer`。

## 安装

请阅读 https://github.com/anlondon/api-with-docs 并安装该 skill。
