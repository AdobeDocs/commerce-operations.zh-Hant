---
title: 變更增量ID
description: 變更商務資料庫實體的增量ID。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---


# 變更增量ID

本文探討如何使用 `ALTER TABLE` SQL陳述式。

## 受影響的版本

- Adobe Commerce（內部）:2.x.x
- Adobe Commerce雲基礎架構：2.x.x
- MySQL: [任何支援的版本](../../installation/prerequisites/database/mysql.md)

## 何時需要變更增量ID

在以下情況下，您可能需要更改新資料庫實體的增量ID:

- 在即時站點上執行硬備份還原後
- 某些訂單記錄已丟失，但支付網關（如PayPal）已在使用它們的ID作為當前商家帳戶。 在這種情況下，支付網關停止處理具有相同ID的新訂單，返回「重複發票ID」錯誤

>[!INFO]
>
>您還可以通過在PayPal的「付款接收首選項」中允許每個發票ID進行多筆付款來修復PayPal的付款網關問題。 請參閱 [PayPal網關已拒絕請求 — 重複發票問題] 在 _知識庫_.

## 先決條件步驟

1. 尋找應變更新增ID的儲存區和實體。
1. 連接到MySQL資料庫。
若為雲端基礎架構上的Adobe Commerce，您首先需要使用SSH連線至您的環境。
1. 檢查當前 `auto_increment` 實體序清單的值，使用以下查詢：

   ```sql
   SHOW TABLE STATUS FROM `{database_name}` WHERE `name` LIKE 'sequence_{entity_type}_{store_id}';
   ```

如果檢查ID=1的商店訂單的自動增量，則表名稱為「sequenceorder1」。

若 `auto_increment` 欄是&#39;1234&#39;，是商店下一個 `ID=1` 會有ID &#39;#100001234&#39;。

## 更新實體以更改增量ID

使用以下查詢更新實體：

```sql
ALTER TABLE sequence_{entity_type}_{store_id} AUTO_INCREMENT = {new_increment_value};
```

>[!INFO]
重要：新增量值必須大於當前增量值。

執行下列查詢後：

```sql
ALTER TABLE sequence_order_1 AUTO_INCREMENT = 2000;
```

在商店下一筆訂單 `ID=1` 會有ID &#39;#100002000&#39;。

## 雲端生產環境的其他建議步驟

執行 `ALTER TABLE` 在雲端基礎架構上查詢Adobe Commerce的生產環境，強烈建議您執行下列步驟：

- 在您的測試環境中測試變更遞增ID的整個程式
- [建立資料庫備份] 在出現故障時還原生產資料庫

<!-- Link Definitions -->

[PayPal網關已拒絕請求 — 重複發票問題]: https://support.magento.com/hc/en-us/articles/115002457473
[建立資料庫備份]: https://support.magento.com/hc/en-us/articles/360003254334
[任何支援的版本]
