---
title: 修改資料庫表的最佳做法
description: 瞭解如何和何時修改Adobe Commerce和第三方資料庫表。
role: Developer, Architect
feature: Best Practices
feature-set: Commerce
last-substantial-update: 2022-11-15T00:00:00Z
exl-id: 9e7adaaa-b165-4293-aa98-5dc4b8c23022
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1438'
ht-degree: 0%

---

# 修改資料庫表的最佳做法

本文提供了修改由 [!DNL Adobe Commerce] 或第三方模組。 瞭解何時以及如何有效地修改表有助於確保您的商業平台的長期生存性和穩定性。

從遷移 [!DNL Magento 1] 及其他電子商務平台，或使用 [!DNL Adobe Commerce] Marketplace需要添加和保存額外資料。 您的第一反應可能是向資料庫表添加列，或調整現有列。 但是，您只應修改核 [!DNL Adobe Commerce] 表（或第三方供應商表）。

## 為什麼Adobe建議避免修改

避免修改核心表的主要原因是Adobe Commerce包含包含原始SQL查詢的基礎邏輯。 對表結構的更改可能會導致意外的副作用，這些副作用很難排除故障。 更改還可能影響DDL（資料定義語言）操作，從而對效能造成意外和不可預知的影響。

避免更改資料庫表結構的另一個原因是，如果核心開發團隊或第三方開發人員更改其資料庫表的結構，則更改可能會導致問題。 例如，有幾個核心資料庫表具有名為 `additional_data`。 這一直是 `text` 列類型。 但是，由於效能原因，核心團隊可能會將列更改為 `longtext`。 此類型的列是JSON的別名。 通過轉換到此列類型，向該列添加了效能增益和可搜索性，但該列不作為 `text` 的雙曲餘切值。 您可以在 [JSON資料類型](https://mariadb.com/kb/en/json-data-type/){target="_blank"}。

## 知道何時保存或刪除資料

Adobe建議您首先確定是否需要保存此資料。 如果從舊式系統移動資料，則您可以刪除的任何資料都會在遷移過程中節省時間和精力。 （如果以後需要訪問資料，則有存檔方法。） 為了更好地掌控應用程式和效能，可以對保存額外資料的請求提出異議。 您的目標是確保保存資料是滿足無法以其他方式滿足的業務需要的一項要求。

### 舊資料

如果項目包含舊資料，例如舊訂單或客戶記錄，請考慮另一種查找方法。 例如，如果業務需要訪問資料僅供偶爾參考，請考慮對托管在商務平台外的舊資料庫執行外部搜索，而不是將舊資料遷移到 [!DNL Adobe Commerce]。

這種情況要求將資料庫遷移到伺服器，提供Web介面來讀取資料，或者培訓MySQL Workbench或類似工具的使用。 將此資料從新資料庫中排除，可使開發團隊專注於新站點，而不是排除資料遷移問題的故障，從而加快遷移。

另一個相關選項是將資料保持在商業之外，但允許您即時使用這些資料，這將利用其他工具，如GraphQL網格。 此選項將不同的資料源組合在一起，並作為單個響應返回它們。

例如， `stitch` 將外部資料庫的舊訂單(可能是已退出的舊Magento1站點)合併在一起。 然後使用GraphQL網格，將其作為客戶訂單歷史的一部分進行顯示。 這些舊訂單可以與您當前的訂單組合 [!DNL Adobe Commerce] 環境。

有關將API網格與GraphQL配合使用的詳細資訊，請參見 [什麼是API Mesh](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/){target="_blank"}) and [GraphQL Mesh Gateway](https://developer.adobe.com/graphql-mesh-gateway/){target="_blank"}。

## 使用擴展屬性遷移舊式資料

如果您確定舊資料需要遷移，或者新資料需要保存在 [!DNL Adobe Commerce],Adobe建議使用 [擴展屬性](https://developer.adobe.com/commerce/php/development/components/add-attributes/){target="_blank"}。 使用擴展屬性保存附加資料具有以下優點：

- 您可以控制要保留的資料和資料庫結構，這可確保資料以正確的列類型和正確的索引進行保存。
- 中的大多數實體 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 支援使用擴展屬性。
- 擴展屬性是一種獨立於儲存的機制，它提供了將資料保存到項目最佳位置的靈活性。

兩個儲存位置示例是資料庫表和 [!DNL Redis]。 選擇位置時需要考慮的關鍵是位置是否會帶來額外的複雜性或影響效能。

### 考慮其他備選方案

作為開發人員，始終考慮使用您之外的工具 [!DNL Adobe Commerce] 環境，如GraphQL網格和AdobeApp Builder。 這些工具可以幫助您保留對資料的訪問權限，但對核心商務應用程式或其基礎資料庫表沒有影響。 使用此方法，您可以通過API公開資料。 然後，將資料源添加到App Builder配置中。 使用GraphQL網格，您可以組合這些資料源並生成單個響應，如中所述 [舊資料](#legacy-data)。

有關GraphQL網格的其他詳細資訊，請參見 [GraphQL網狀網關](https://developer.adobe.com/graphql-mesh-gateway/){target="_blank"}. For information about the Adobe App Builder,  see [Introducing App Builder](https://experienceleague.adobe.com/docs/adobe-developers-live-events/events/2021/oct2021/introduction-app-builder.html?lang=en){target="_blank"}。

## 修改核心表或第三方表

如果您決定通過修改核心來儲存資料 [!DNL Adobe Commerce] 或第三方模組資料庫表，請使用以下准則將對穩定性和效能的影響降至最低。

- 僅添加新列。
- 從不修改 _類型_ 現有列的值。 例如，不更改 `integer` 到 `varchar` 以滿足您獨特的使用案例。
- 避免向EAV屬性表添加列。 這些表已因邏輯和責任而超負荷。
- 在調整表之前，請確定其大小。 更改大表會影響部署，這可能會在應用更改時造成幾分鐘或數小時的延遲。

## 修改外部資料庫表的最佳做法

Adobe建議在將列添加到核心資料庫表或第三方表時執行以下步驟：

1. 在命名空間中建立一個名稱表示要更新的模組。

   例如： `app/code/YourCompany/Customer`

1. 建立相應檔案以啟用模組(請參見 [建立模組](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/create-module.html){target="_blank"}。

1. 建立名為 `db_schema.xml` 的 `etc` 資料夾，並進行相應的更改。

   如果適用，生成 `db_schema_whitelist.json` 的子菜單。 請參閱 [聲明性架構](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/){target="_blank"} 的子菜單。

### 潛在影響

將列添加到外部資料庫可能會通過以下方式影響您的Adobe Commerce項目：

- 升級可能會更複雜。
- 如果要修改的表較大，則會影響部署。
- 遷移到新平台可能更複雜。

## 避免修改核心表的方法

您可以避免使用 [擴展屬性](#migrate-legacy-data-with-extension-attributes)。 另一種方法是使用特殊列(`additional_data`)在幾個核心表上找到以儲存資料並以JSON編碼格式保存資料。

### 在JSON編碼資料列中保存資料

某些核心表 `additional_data` 包含JSON編碼資料的列。 此列提供了在一個欄位中映射附加資料的本機方法。 使用該方法避免了為小的、簡單的資料元素添加表，這些資料元素儲存用於資料檢索的資訊而不需要搜索。 的 `additional_data` 列通常僅在物料層可用，而不適用於整個報價或訂單。

- 使用 `additional_data` 場

   - 不需要附加欄位，這樣列數就最少。 這對已涉及許多表的銷售流很有幫助。 最好不要給這個本已複雜的過程增加更多的複雜性。 該方法滿足多種使用情況，但並非全部。

- 缺點

   - 該方法僅適用於只讀資料的儲存。 出現此問題是因為需要對代碼進行未序列化以修改和構建對象以添加依賴關係或資料庫關係。

   - 很難使用資料庫操作來搜索這些欄位。 使用此方法搜索速度慢。

   - 在中儲存資料時必須格外小心 `additional_data` 列，以避免觸發串列化或非序列化操作，這些操作可通過建立無效的JSON或在運行時導致讀取錯誤來中斷代碼。

   - 這些欄位必須在代碼中明確聲明，以便開發人員可以輕鬆找到它們。

   - 其他可能發生的問題可能很難診斷。 例如，如果不使用某些本機PHP函式 [!DNL Adobe Commerce] 由核心應用程式提供的包裝方法，轉換資料的最終結果可以不同於預期格式。 始終使用包裝函式來確保保存或檢索的資料的一致性和可預測性。

下面是表的示例，這些表具有 `additional_data` 的雙曲餘切值。

```mysql
MariaDB [main]> DESCRIBE quote_item additional_data;
+-----------------+------+------+-----+---------+-------+
| Field           | Type | Null | Key | Default | Extra |
+-----------------+------+------+-----+---------+-------+
| additional_data | text | YES  |     | NULL    |       |
+-----------------+------+------+-----+---------+-------+
1 row in set (0.001 sec)


MariaDB [main]> DESCRIBE sales_order_item additional_data;
+-----------------+------+------+-----+---------+-------+
| Field           | Type | Null | Key | Default | Extra |
+-----------------+------+------+-----+---------+-------+
| additional_data | text | YES  |     | NULL    |       |
+-----------------+------+------+-----+---------+-------+
1 row in set (0.001 sec)
```

在2.4.3、2.4.4和2.4.5版中，有十個表具有該列 `additional_data`。

```mysql
MariaDB [magento]> SELECT DISTINCT TABLE_NAME FROM INFORMATION_SCHEMA.COLUMNS WHERE COLUMN_NAME IN ('additional_data') AND TABLE_SCHEMA='main';
+------------------------+
| TABLE_NAME             |
+------------------------+
| sales_shipment_item    |
| sales_creditmemo_item  |
| sales_invoice_item     |
| catalog_eav_attribute  |
| sales_order_payment    |
| quote_address_item     |
| quote_payment          |
| quote_item             |
| magento_reward_history |
| sales_order_item       |
+------------------------+
10 rows in set (0.020 sec)
```
