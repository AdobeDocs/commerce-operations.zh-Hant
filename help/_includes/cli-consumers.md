---
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---
# 訊息佇列取用者的CLI選項

| 名稱 | 說明 | 值 | 必填 |
|------|-------------|-------|----------|
| `--consumers-wait-for-messages` | 決定消費者是否會等待來自佇列的訊息。 | 1 — 是，0 — 否 | 否 |

* `0`：取用者處理佇列中的可用訊息、關閉TCP連線並終止。 即使已處理的訊息數量少於 `--max_messages` 啟動消費者期間指定的值。

* `1`：消費者會繼續處理來自訊息佇列的訊息，直到達到訊息數量上限（為指定的值）為止 `--max_messages` 於 `queue:consumers:start` 命令)，然後關閉TCP連線並終止取用者處理序。 如果佇列在到達之前排空 `--max_messages` 消費者會等待更多訊息到達。 如果您使用背景工作來執行消費者，而不是使用cron工作，請將此變數設為 `1`.

>[!WARNING]
>
>此 `--consumers-wait-for-messages` 選項是全域選項，無法為每個取用者個別設定。
