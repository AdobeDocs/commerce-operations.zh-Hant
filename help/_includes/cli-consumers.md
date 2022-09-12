---
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---
# 消息隊列使用者的CLI選項

| 名稱 | 說明 | 值 | 必填 |
|------|-------------|-------|----------|
| `--consumers-wait-for-messages` | 確定消費者是否將等待來自隊列的消息。 | 1 — 是，0 — 否 | 否 |

* `0`:消費者處理隊列中的可用消息、關閉TCP連接並終止。 即使已處理的訊息數量小於 `--max_messages` 啟動使用者期間指定的值。

* `1`:消費者會繼續處理來自訊息佇列的訊息，直到達到訊息數上限(為 `--max_messages` 在 `queue:consumers:start` 命令)，然後關閉TCP連接並終止使用者進程。 如果隊列在到達之前空空 `--max_messages` 消費者會等待更多訊息送達。 如果您使用員工來執行消費者，而不是使用cron工作，請將此變數設為 `1`.

>[!WARNING]
>
>此 `--consumers-wait-for-messages` 選項是全域選項，無法為每個消費者個別設定。
