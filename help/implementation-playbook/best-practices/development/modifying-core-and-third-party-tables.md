---
title: 修改資料庫表的最佳做法
description: 了解如何及何時修改Adobe Commerce和協力廠商資料庫表。
role: Developer, Architect
feature: Best Practices
feature-set: Commerce
last-substantial-update: 2022-11-15T00:00:00Z
source-git-commit: 570fa4877f578f636736f0404169ed215fd06b24
workflow-type: tm+mt
source-wordcount: '1469'
ht-degree: 0%

---

# 修改資料庫表的最佳做法

本文提供修改由建立的資料庫表的最佳做法 [!DNL Adobe Commerce] 或協力廠商模組。 了解有效修改表格的時間和方式有助於確保您的商務平台的長期可行性和穩定性。

從移轉 [!DNL Magento 1] 及其他電子商務平台，或使用 [!DNL Adobe Commerce] Marketplace可能需要新增和儲存額外資料。 您的第一反應可能是向資料庫表添加列，或調整現有的列。 不過，您只應修改核心 [!DNL Adobe Commerce] 表（或第三方供應商表）。

## 為何Adobe建議避免修改

避免修改核心表的主要原因是Adobe Commerce包含包含原始SQL查詢的基礎邏輯。 對表格結構的更改可能會導致意外的副作用，這些副作用很難排除。 此更改還可能影響DDL（資料定義語言）操作，從而對效能造成意外和不可預知的影響。

避免更改資料庫表結構的另一個原因是，如果核心開發團隊或第三方開發人員更改其資料庫表的結構，則您的更改可能會引起問題。 例如，有一些核心資料庫表具有名為的列 `additional_data`. 這一直是 `text` 欄類型。 不過，基於效能原因，核心團隊可能會將欄變更為 `longtext`. 此類型的欄是JSON的別名。 轉換為此欄類型後，該欄便新增了效能增益和可搜尋性，而這些增益和可搜尋性不存在於 `text` 類型。 如需深入了解此主題，請參閱 [JSON資料類型](https://mariadb.com/kb/en/json-data-type/){target=&quot;_blank&quot;}。

## 知道何時儲存或移除資料

Adobe建議您先判斷是否需要儲存此資料。 如果您要從舊版系統移動資料，您可移除的任何資料都能在移轉期間節省時間和精力。 （如果以後需要存取資料，則有封存資料的方法。） 為了能夠很好地管理應用程式和效能，您可以挑戰保存額外資料的請求。 您的目標是確保儲存資料是滿足無法以其他方式填補的業務需求的一項需求。

### 舊版資料

如果您的專案包含舊有資料（例如舊訂單或客戶記錄），請考慮使用替代的查閱方法。 例如，如果業務僅需要訪問資料以供偶爾參考，請考慮對在商務平台之外托管的舊資料庫實施外部搜索，而不是將舊資料遷移到 [!DNL Adobe Commerce].

這種情況需要將資料庫遷移到伺服器，提供用於讀取資料的Web介面，或者使用MySQL Workbench或類似工具進行培訓。 將這些資料排除在新資料庫之外，可讓開發團隊專注於新網站，而非疑難排解資料移轉問題，以加快移轉速度。

將資料保留為商務外部，但允許您即時使用的另一個相關選項，是運用其他工具，例如GraphQL網格。 此選項會結合不同的資料來源，並以單一回應傳回。

例如，您可以 `stitch` 將外部資料庫的舊訂單加在一起，可能是已退役的舊Magento1站點。 然後使用GraphQL網格，將它們顯示為客戶訂單歷史記錄的一部分。 這些舊訂單可與您目前的訂單結合 [!DNL Adobe Commerce] 環境。

如需如何將API網格與GraphQL搭配使用的詳細資訊，請參閱 [什麼是API Mesh](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/){target=&quot;_blank&quot;})和 [GraphQL網格網關](https://developer.adobe.com/graphql-mesh-gateway/){target=&quot;_blank&quot;}。

## 使用擴充功能屬性移轉舊版資料

如果您判斷舊版資料需要移轉，或需要將新資料儲存於 [!DNL Adobe Commerce],Adobe建議使用 [擴充功能屬性](https://developer.adobe.com/commerce/php/development/components/add-attributes/){target=&quot;_blank&quot;}。 使用擴充功能屬性來儲存其他資料具有以下優點：

- 您可以控制要保存的資料和資料庫結構，這可確保以正確的列類型和正確的索引保存資料。
- 中的大部分實體 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 支援使用擴充功能屬性。
- 擴充功能屬性是一種不受儲存限制的機制，可靈活地將資料儲存在項目的最佳位置。

儲存位置的兩個示例是資料庫表和 [!DNL Redis]. 選擇位置時要考慮的關鍵是位置會帶來額外的複雜性還是影響效能。

### 考慮其他替代方案

身為開發人員，請務必一律考慮在外部使用工具 [!DNL Adobe Commerce] 環境，例如GraphQL網格和Adobe應用程式產生器。 這些工具可協助您保留對資料的存取權，但對核心商務應用程式或其基礎資料庫表格沒有影響。 透過此方法，您可透過API公開資料。 接著，您新增資料來源至App Builder設定。 使用GraphQL網格，您可以組合這些資料源並生成單個響應，如 [舊資料](#legacy-data).

有關GraphQL網格的其他詳細資訊，請參見 [GraphQL網格網關](https://developer.adobe.com/graphql-mesh-gateway/){target=&quot;_blank&quot;}。 如需Adobe應用程式產生器的相關資訊，請參閱 [App Builder簡介](https://experienceleague.adobe.com/docs/adobe-developers-live-events/events/2021/oct2021/introduction-app-builder.html?lang=en){target=&quot;_blank&quot;}。

## 修改核心表或第三方表

如果您決定透過修改核心來儲存資料 [!DNL Adobe Commerce] 或第三方模組資料庫表，請使用以下指南將對穩定性和效能的影響降至最低。

- 僅新增欄。
- 永不修改 _type_ 現有欄的值。 例如，請勿變更 `integer` 到 `varchar` 以滿足您獨特的使用案例。
- 避免向EAV屬性表添加列。 這些表格已經因邏輯和責任而超載。
- 調整表格之前，請確定其大小。 變更大型表格會影響部署，而套用變更時，可能會造成數分鐘或數小時的延遲。

## 修改外部資料庫表的最佳做法

Adobe建議在將列添加到核心資料庫表或第三方表時執行以下步驟：

1. 在您的命名空間中建立一個模組，其名稱代表您要更新的內容。

   例如： `app/code/YourCompany/Customer`

1. 建立適當的檔案以啟用模組(請參閱 [建立模組](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/create-module.html){target=&quot;_blank&quot;}。

1. 建立檔案，稱為 `db_schema.xml` 在 `etc` ，並進行適當的更改。

   如果適用，請產生 `db_schema_whitelist.json` 檔案。 請參閱 [聲明性結構](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/){target=&quot;_blank&quot;}以取得詳細資訊。

### 潛在影響

將欄新增至外部資料庫可能會以下列方式影響您的Adobe Commerce專案：

- 升級可能更複雜。
- 如果修改的表格很大，則部署會受到影響。
- 遷移到新平台可能更複雜。

## 避免修改核心表的方法

您可以避免使用 [擴充功能屬性](#migrate-legacy-data-with-extension-attributes). 另一個替代方法是使用特殊欄(`additional_data`)，以儲存資料並以JSON編碼格式儲存。

### 將資料儲存在JSON編碼的資料欄中

某些核心表格具有 `additional_data` 包含JSON編碼資料的欄。 此欄提供在一個欄位中對應其他資料的原生方式。 使用該方法避免了為儲存用於資料檢索的資訊的簡單的小型資料元素添加表，而無需搜索。 此 `additional_data` 欄通常只適用於項目層，不適用於整個報價或訂單。

- 使用的優點 `additional_data` 欄位

   - 不需要其他欄位，因此欄數最少。 這在銷售流中很有用，因為在銷售流中已涉及許多表。 最好不要給這個本已複雜的過程增加更多複雜性。 此方法可滿足許多使用案例，但並非全部。

- 缺點

   - 此方法僅適用於儲存只讀資料。 出現此問題是因為需要取消序列化代碼來修改和構建對象以添加依賴項或資料庫關係。

   - 很難使用資料庫操作來搜索這些欄位。 使用此方法的搜索速度慢。

   - 將資料儲存在 `additional_data` 欄，以避免觸發序列化或取消序列化操作，這些操作可能會借由建立無效的JSON來中斷程式碼，或在執行階段期間造成讀取錯誤。

   - 程式碼中必須清楚宣告這些欄位，開發人員才能輕鬆找到這些欄位。

   - 可能發生的其他問題可能很難診斷。 例如，若您未使用 [!DNL Adobe Commerce] 由核心應用程式提供的包裝方法所轉換資料的最終結果可以不同於期望的格式。 請一律使用包裝函式，以確保儲存或擷取的資料的一致性和可預測性。

以下是表格的範例，其中包含 `additional_data` 欄。

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

在2.4.3、2.4.4和2.4.5版中，有10個錶帶有列 `additional_data`.

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
