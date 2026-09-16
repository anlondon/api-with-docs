---
name: app-api-docs
description: >-
  Writes technician App API docs in 使用方法 / 传参方法 / 注意事项. Use when updating
  docs/SOP接口说明.md, 工单说明, 工单预览, NFC写卡协议, Apifox endpoint descriptions,
  or when the user asks to 更新接口说明、对接文档、Apifox 说明. Do not use
  chinese-ai-humanizer on these docs.
---

# App 接口说明（给前端）

读者是 Android / iOS / Harmony 技术员 App。只写页面上怎么用。

先读 `CONTEXT.md` **Language**。文档里的加粗词必须已在那里出现。没有就先问用户再写，禁止临场起名。

不要跑 `/chinese-ai-humanizer`。那是改文风，改不了造词，也写不成下面三块。

## 每个接口只写三块

### 使用方法

何时调、调完去哪、成功/失败前端怎么走（看 `code` 和约定字段，不要靠长文案猜路由）。

### 传参方法

字段名、从哪来（上一接口哪段）、填什么、和页面哪一块对应。表格优先。

### 注意事项

别和谁搞混、不要调哪些接口、失败 toast 哪句。一句一件事。

Apifox 的接口说明、参数说明、响应说明同一套三块，不要另起「概述 / 实现原理 / 数据流」。

## 禁止

- 造词或用更「精炼」的替换词（凭证、应用工单、点位标签、SOP节点当两种东西用）
- 把 PHP、表名、SQL、落库、队列、ensureJob 写进这份。表结构去 `docs/SOP业务链路与数据表关系.md`
- 把函数实现翻译成中文长段
- 同一含义两个字段名并列当主说明

## 对照

差：

> `nfcResolve` 会先按 `lbs_sop_nfc_tag.tag_code` 命中标签，再 `JobVisitState::resolveMany` 聚合 visit_status，服务中则内部调用 `nfcScan` 写 verified 并 `array_merge` 填写载荷……

好：

**使用方法**：未进工单贴 NFC 时调。`code≠200` 只 toast。有 `data.point` 进工单节点页；`point` 为 null 进工单页并 toast `tip`。

**传参方法**：只要 `nfc_code`（32 位小写 hex）。要登录和请求签名。

**注意事项**：工单内贴卡走 `nfcScan`，不要用本接口。`is_inherited` 在 `data.point.risk_list[]` 里，不在根上。

写完自检：有没有 CONTEXT 里没有的新词？有没有表名/类名？前端能否只靠三块对接？
