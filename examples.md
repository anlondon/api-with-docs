# 对照

差（代码转中文、造词、原理散文）：

> `nfcResolve` 会先按 `lbs_sop_nfc_tag.tag_code` 命中标签，再 `JobVisitState::resolveMany` 聚合 visit_status，服务中则内部调用 `nfcScan` 写 verified 并 `array_merge` 填写载荷。本质上这不是扫码，而是一次点位解析。

好（三块、已有术语、调用方能照做）：

**使用方法**：未进工单贴 NFC 时调。`code≠200` 只 toast。有 `data.point` 进工单节点页；`point` 为 null 进工单页并 toast `tip`。

**传参方法**：只要 `nfc_code`（32 位小写 hex）。要登录和请求签名。

**注意事项**：工单内贴卡走 `nfcScan`，不要用本接口。`is_inherited` 在 `data.point.risk_list[]` 里，不在根上。

差的典型症状：表名、类名、内部函数、换一种「更准」的叫法、先讲原理再讲用法。
