---
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 0%

---
# 訊息佇列取用者的CLI選項

| 名稱 | 說明 | 值 | 必填 |
|------|-------------|-------|----------|
| `--consumers-wait-for-messages` | 決定消費者是否會等待來自佇列的訊息。 | 1 — 是，0 — 否 | 否 |

* `0`：消費者處理佇列中的可用訊息、關閉TCP連線，然後終止。 即使已處理的訊息數小於啟動消費者期間指定的`--max_messages`值，消費者也不會等待其他訊息進入佇列。

* `1`：消費者繼續處理來自訊息佇列的訊息，直到達到訊息數目上限（在`--max_messages`命令上為`queue:consumers:start`指定的值）為止，然後關閉TCP連線並終止消費者處理序。 如果佇列在到達`--max_messages`之前排空，消費者會等待更多訊息到達。 如果您使用背景工作來執行消費者，而不是使用cron工作，請將此變數設為`1`。

>[!WARNING]
>
>`--consumers-wait-for-messages`選項是全域選項，無法針對每個消費者個別設定。
