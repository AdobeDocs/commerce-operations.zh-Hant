---
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---
# 消息隊列使用者的CLI選項

| 名稱 | 說明 | 值 | 必需 |
|------|-------------|-------|----------|
| `--consumers-wait-for-messages` | 確定使用者是否將等待來自隊列的消息。 | 1 — 是，0 — 否 | 否 |

* `0`:使用者處理隊列中的可用消息，關閉TCP連接並終止。 即使已處理的消息數小於 `--max_messages` 在啟動使用者期間指定的值。

* `1`:使用者繼續處理來自消息隊列的消息，直到達到最大消息數(為 `--max_messages` 的 `queue:consumers:start` 命令)，然後關閉TCP連接並終止使用者進程。 如果隊列在到達前空空 `--max_messages` 消費者等待更多消息到達。 如果您使用工作人員來運行消費者而不是使用cron作業，請將此變數設定為 `1`。

>[!WARNING]
>
>的 `--consumers-wait-for-messages` 選項是全局選項，不能為每個使用者單獨配置。
