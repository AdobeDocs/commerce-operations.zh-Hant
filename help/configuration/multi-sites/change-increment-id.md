---
title: 更改增量ID
description: 更改Commerce資料庫實體的增量ID。
source-git-commit: 5c0d285717a79d654af769cb734ec385d2d4046f
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---


# 更改增量ID

本文討論如何使用Commerce Store更改特定Commerce資料庫(DB)實體（訂單、發票、貸項通知單等）的增量ID `ALTER TABLE` SQL陳述式。

## 受影響的版本

- Adobe Commerce（內部）:2.x.x
- Adobe Commerce在雲基礎架構方面：2.x.x
- MySQL: [任何受支援的版本]

## 何時需要更改增量ID

在以下情況下，您可能需要更改新資料庫實體的增量ID:

- 在即時站點上執行硬備份還原後
- 某些訂單記錄已丟失，但付款網關（如PayPal）已在使用它們的ID作為您當前的商戶帳戶。 因此，付款網關停止處理具有相同ID的新訂單，返回「重複發票ID」錯誤

>[!INFO]
>
>您還可以通過在PayPal的「付款接收首選項」中允許每個發票ID進行多次付款來修復PayPal的付款網關問題。 請參閱 [PayPal網關拒絕請求 — 重複發票] 的 _知識庫_。

## 先決條件步驟

1. 查找應更改新增量ID的儲存和實體。
1. 連接到MySQL資料庫。
對於Adobe Commerce雲基礎架構，首先需要使用SSH連接到您的環境。
1. 檢查當前 `auto_increment` 實體序清單的值：

   ```sql
   SHOW TABLE STATUS FROM `{database_name}` WHERE `name` LIKE 'sequence_{entity_type}_{store_id}';
   ```

如果要檢查ID=1的商店上訂單的自動增量，則表名應為&quot;sequenceorder1&quot;。

如果 `auto_increment` 列為&#39;1234&#39;，下一個訂單是 `ID=1` 將具有ID「#100001234」。

## 更新實體以更改增量ID

使用以下查詢更新實體：

```sql
ALTER TABLE sequence_{entity_type}_{store_id} AUTO_INCREMENT = {new_increment_value};
```

>[!INFO]
重要提示：新增量值必須大於當前增量值。

執行以下查詢後：

```sql
ALTER TABLE sequence_order_1 AUTO_INCREMENT = 2000;
```

在商店下一個訂單 `ID=1` 將具有ID「#100002000」。

## 在雲生產環境上建議的其他步驟

執行 `ALTER TABLE` 在Adobe Commerce的雲基礎架構生產環境上進行查詢，強烈建議執行以下步驟：

- Test轉移環境中更改增量ID的整個過程
- [建立資料庫備份] 在出現故障時恢復生產資料庫

<!-- Link Definitions -->

[PayPal網關拒絕請求 — 重複發票]: https://support.magento.com/hc/en-us/articles/115002457473
[建立資料庫備份]: https://support.magento.com/hc/en-us/articles/360003254334
[任何受支援的版本]: https://devdocs.magento.com/guides/v2.4/install-gde/prereq/mysql.html
