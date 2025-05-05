---
title: 變更增量ID
description: 變更Commerce資料庫實體的增量ID。
exl-id: 039fc34c-d9cf-42f4-af5d-16a26a3e8171
source-git-commit: 2a45fe77d5a6fac089ae2c55d0ad047064dd07b0
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# 變更增量ID

本文討論如何使用`ALTER TABLE` SQL陳述式變更特定Commerce存放區中Commerce資料庫(DB)實體（訂單、發票、銷退折讓單等）的增量ID。

## 受影響的版本

- Adobe Commerce （內部部署）： 2.x.x
- 雲端基礎結構上的Adobe Commerce： 2.x.x
- MySQL： [任何支援的版本](../../installation/prerequisites/database/mysql.md)

## 您何時需要變更增量ID

在下列情況下，您可能需要變更新DB實體的增量ID：

- 在即時網站上進行硬備份還原之後
- 有些訂單記錄已遺失，但付款閘道（例如PayPal）已使用其ID代管您目前的商家帳戶。 在這種情況下，付款閘道會停止處理具有相同ID的新訂單，傳回「重複發票識別碼」錯誤

>[!INFO]
>
>您也可以在PayPal的「付款接收偏好設定」中，允許每個商業發票識別碼進行多項付款，以修正PayPal的付款閘道問題。 請參閱[PayPal閘道拒絕的要求 — _知識庫_&#x200B;中的重複發票問題](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/paypal-gateway-rejected-request-duplicate-invoice-issue.html?lang=zh-Hant)。

## 必備條件步驟

1. 尋找應變更新增量ID的存放區和實體。
1. 連線至您的MySQL資料庫。
針對雲端基礎結構上的Adobe Commerce，您首先需要使用SSH連線至您的環境。
1. 使用下列查詢檢查實體序號表的目前`auto_increment`值：

   ```sql
   SHOW TABLE STATUS FROM `{database_name}` WHERE `name` LIKE 'sequence_{entity_type}_{store_id}';
   ```

如果您檢查的是ID=1之商店訂單的自動遞增，則表格名稱為&#39;sequence_order_1&#39;。

如果`auto_increment`欄的值為&#39;1234&#39;，則與`ID=1`一起下個訂單的識別碼將為&#39;#100001234&#39;。

## 更新實體以變更增量ID

使用下列查詢更新實體：

```sql
ALTER TABLE sequence_{entity_type}_{store_id} AUTO_INCREMENT = {new_increment_value};
```

>[!INFO]
>
>重要：新的增量值必須大於目前值。

執行以下查詢之後：

```sql
ALTER TABLE sequence_order_1 AUTO_INCREMENT = 2000;
```

下一個與`ID=1`一起在商店下單的訂單的ID為&#39;#100002000&#39;。

## 雲端生產環境的其他建議步驟

在雲端基礎結構上的Adobe Commerce生產環境中執行`ALTER TABLE`查詢之前，強烈建議您執行下列步驟：

- 在中繼環境中測試變更增量ID的整個程式
- [建立DB備份]以在失敗時還原您的生產DB

<!-- Link Definitions -->

[PayPal gateway rejected request - duplicate invoice issue]: https://support.magento.com/hc/en-us/articles/115002457473
[建立資料庫備份]: https://support.magento.com/hc/en-us/articles/360003254334
[任何支援的版本]
