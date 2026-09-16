---
name: api-docs
description: >-
  Writes client-facing API docs and Apifox descriptions in 使用方法 / 传参方法 / 注意事项,
  using existing CONTEXT.md terms and no coined names. Use when updating 接口说明,
  对接文档, Apifox endpoint/parameter/response descriptions. Do not use for general
  去 AI 味 or copy polishing; do not run chinese-ai-humanizer on these docs.
disable-model-invocation: false
user-invocable: true
---

# API 对接说明

读者是客户端对接方（App / 前端 / 调用方）。只写页面或调用侧怎么用。

文风像同事写对接说明：清楚、具体、可执行。不像报告，也不像闲聊。

## 和 grill-with-docs

缺词先对齐，再写文档。本 skill **不**改 `CONTEXT.md`。

1. 先读 `CONTEXT.md` 的 **Language**（有 `CONTEXT-MAP.md` 则先定位对应 context）。
2. 文档里的加粗领域词必须已在那里出现。没有就停，问用户，或让用户先跑 grill-with-docs。
3. 禁止临场起名，禁止用更「精炼」的替换词。
4. 写作中发现新概念：标出来，交给 grill；不要一边写接口说明一边往 glossary 塞实现词。

项目另有对接模板时以项目为准；否则每个接口只用下面三块。

## 每个接口只写三块

### 使用方法

何时调、调完去哪、成功/失败调用方怎么走（看 `code` 和约定字段，不要靠长文案猜路由）。

### 传参方法

字段名、从哪来（上一接口哪段）、填什么、和页面哪一块对应。表格优先。必填字段写全，不要用「等等」省略。

### 注意事项

别和谁搞混、不要调哪些接口、失败 toast 哪句。一句一件事。

Apifox 的接口说明、参数说明、响应说明同一套三块，不要另起「概述 / 实现原理 / 数据流」。怎么调用 Apifox CLI 不归本 skill，走 `apifox-cli`。

好/坏对照见 [examples.md](examples.md)。

## 禁止

- 造词，或为避免重复而换同义词
- 表名、SQL、落库、队列、类名、函数实现；那些去业务/表结构文档
- 把代码翻译成中文长段
- 同一含义两个字段名并列当主说明
- 跑 `/chinese-ai-humanizer`：那是改文风，改不了造词，也会拆掉三块、砍掉字段表

## 去 AI 味（只这些）

写的时候直接遵守，不要写完再润色一遍。

- 不用「本质上 / 实际上 / 值得注意的是 / 首先其次最后 / 综上所述 / 一句话讲清楚」
- 不用「不是……而是……」、排比、金句、比喻、`——`
- 中文用中文标点，不用英文逗号
- 不把实现讲成原理散文；没有信息量的句子删掉
- 不要口语到省略约定；也不要写成论文或公众号

## 写完自检

- CONTEXT 里没有的新词？
- 有没有表名 / 类名 / 函数实现？
- 调用方能否只靠三块对接？
- 有没有报告腔、换词、金句、省略必填字段？
