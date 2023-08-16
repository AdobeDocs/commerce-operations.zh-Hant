---
title: 修改資料庫表格的最佳作法
description: 瞭解如何以及何時修改Adobe Commerce和協力廠商資料庫表格。
role: Developer, Architect
feature: Best Practices
last-substantial-update: 2022-11-15T00:00:00Z
exl-id: 9e7adaaa-b165-4293-aa98-5dc4b8c23022
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '1438'
ht-degree: 0%

---

# 修改資料庫表格的最佳作法

本文提供修改由建立的資料庫表格的最佳實務 [!DNL Adobe Commerce] 或協力廠商模組。 瞭解何時以及如何有效修改表格，有助於確保商務平台的長期可行性和穩定性。

正在從移轉 [!DNL Magento 1] 和其他電子商務平台，或使用來自的模組 [!DNL Adobe Commerce] Marketplace可能需要新增和儲存額外資料。 您的第一反應可能是將資料行新增至資料庫表格，或是調整現有的資料行。 不過，您應該只修改核心 [!DNL Adobe Commerce] 表格（或協力廠商表格）。

## 為什麼Adobe建議避免修改

避免修改核心資料表的主要原因在於Adobe Commerce包含包含原始SQL查詢的基礎邏輯。 變更表格結構可能會造成難以疑難排解的意外副作用。 此變更也會影響DDL （資料定義語言）作業，對效能造成非預期和無法預測的影響。

避免變更資料庫表格結構的另一個原因是，如果核心開發團隊或第三方開發人員變更其資料庫表格的結構，則您的變更可能會導致問題。 例如，有些核心資料庫表格有一個名為的欄 `additional_data`. 此專案一直 `text` 欄型別。 然而，基於效能考量，核心團隊可能會將欄變更為 `longtext`. 此型別的欄是JSON的別名。 透過轉換為此欄型別，可提升該欄的效能，並且可搜尋，但該欄並不以形式存在 `text` 型別。 有關本主題的詳細資訊，請參閱 [JSON資料型別](https://mariadb.com/kb/en/json-data-type/){target="_blank"}.

## 知道何時儲存或移除資料

Adobe建議您先決定是否需要儲存此資料。 如果您要從舊版系統行動資料，任何可移除的資料都會在移轉期間為您節省時間和精力。 （如果需要稍後存取資料，有一些方式可以封存資料。） 為了妥善管理應用程式和效能，您可以質疑儲存額外資料的要求。 您的目標是確保儲存資料是滿足企業需求（無法透過其他方式滿足）的需求。

### 舊版資料

如果您的專案包含舊有資料（如舊訂單或客戶記錄），請考慮其他查詢方法。 例如，如果企業僅需要存取資料以供偶爾參考，請考慮對託管於商務平台外部的舊資料庫實作外部搜尋，而非將舊資料移轉至 [!DNL Adobe Commerce].

此情況需要將資料庫移轉至伺服器，提供網頁介面來讀取資料，或訓練使用MySQL Workbench或類似工具。 將這個資料從新資料庫排除後，可讓開發團隊專注於新網站，而非疑難排解資料移轉問題，藉此加速移轉。

另一個將資料保留在商業外部，但可讓您即時使用的相關選項是運用其他工具，例如GraphQL mesh。 此選項會結合不同的資料來源，並將其傳回為單一回應。

例如，您可以 `stitch` 將來自外部資料庫的舊訂單(可能是已停止支援的舊Magento1網站)整合在一起。 然後使用GraphQL網格，將其顯示為客戶訂單歷史記錄的一部分。 這些舊訂單可與您目前的訂單合併 [!DNL Adobe Commerce] 環境。

如需搭配GraphQL使用API網狀架構的詳細資訊，請參閱 [什麼是API Mesh](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/){target="_blank"}) and [GraphQL Mesh Gateway](https://developer.adobe.com/graphql-mesh-gateway/){target="_blank"}.

## 使用擴充功能屬性移轉舊資料

如果您判斷舊資料需要移轉，或新資料需要儲存在 [!DNL Adobe Commerce]，Adobe建議使用 [擴充功能屬性](https://developer.adobe.com/commerce/php/development/components/add-attributes/){target="_blank"}. 使用擴充功能屬性來儲存其他資料具備下列優點：

- 您可以控制要儲存的資料和資料庫結構，以確保以正確的欄型別和正確的索引來儲存資料。
- 中的大部分實體 [!DNL Adobe Commerce] 和 [!DNL Magento Open Source] 支援使用擴充功能屬性。
- 擴充功能屬性是一種不受儲存影響的機制，可讓您靈活地將資料儲存在專案的最佳位置。

儲存位置的兩個範例是資料庫表格和 [!DNL Redis]. 選擇位置時需要考慮的關鍵事項是，位置是否會帶來額外的複雜性，或影響效能。

### 考慮其他替代方案

作為開發人員，必須一律考慮使用您以外的工具， [!DNL Adobe Commerce] 環境，例如GraphQL網格和Adobe App Builder。 這些工具可協助您保留資料的存取權，但對核心商務應用程式或其基礎資料庫表格沒有影響。 使用此方法，您可以透過API公開您的資料。 接著，將資料來源新增至App Builder設定。 使用GraphQL Mesh，您可以結合這些資料來源，並產生單一回應，如中所述 [舊資料](#legacy-data).

如需GraphQL網狀架構的其他詳細資訊，請參閱 [GraphQL Mesh Gateway](https://developer.adobe.com/graphql-mesh-gateway/){target="_blank"}. For information about the Adobe App Builder,  see [Introducing App Builder](https://experienceleague.adobe.com/docs/adobe-developers-live-events/events/2021/oct2021/introduction-app-builder.html?lang=en){target="_blank"}.

## 修改核心表格或協力廠商表格

如果您決定透過修改核心來儲存資料 [!DNL Adobe Commerce] 或協力廠商模組資料庫表格時，請遵循下列准則以將對穩定性和效能的影響降至最低。

- 僅新增欄。
- 切勿修改 _type_ 現有欄的值。 例如，請勿變更 `integer` 至 `varchar` 以滿足您獨特的使用案例。
- 避免將欄新增至EAV屬性表格。 這些資料表已因邏輯和職責而超載。
- 調整表格之前，請先決定表格的大小。 變更大型表格會影響部署，這可能會導致套用變更時延遲幾分鐘或幾小時。

## 修改外部資料庫表格的最佳作法

當您將資料行新增至核心資料庫表格或協力廠商表格時，Adobe建議遵循下列步驟：

1. 在名稱空間中建立一個模組，使用代表您正在更新的專案之名稱。

   例如： `app/code/YourCompany/Customer`

1. 建立適當的檔案以啟用模組(請參閱 [建立模組](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/create-module.html){target="_blank"}.

1. 建立名為的檔案 `db_schema.xml` 在 `etc` 資料夾，並進行適當的變更。

   如果適用，請產生 `db_schema_whitelist.json` 檔案。 另請參閱 [宣告式結構描述](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/){target="_blank"} 以取得詳細資訊。

### 潛在影響

將欄新增至外部資料庫可能會以下列方式影響您的Adobe Commerce專案：

- 升級可能會更複雜。
- 如果修改的表格很大，則會影響部署。
- 要移轉至新平台可能比較複雜。

## 避免修改核心表格的方法

您可以避免修改Adobe Commerce資料庫表格，方法是使用 [擴充功能屬性](#migrate-legacy-data-with-extension-attributes). 另一種選擇是使用特殊欄(`additional_data`)來儲存資料，並以JSON編碼格式儲存。

### 將資料儲存在JSON編碼的資料欄中

部分核心表格具有 `additional_data` 儲存JSON編碼資料的欄。 此欄提供在一個欄位中對應其他資料的原生方式。 使用此方法可避免為小型簡單資料元素新增表格，這些元素儲存資料擷取的資訊，而不需要搜尋。 此 `additional_data` 欄通常只適用於料號層次，不適用於整個報價或訂單。

- 使用「 」的優勢 `additional_data` 欄位

   - 不需要其他欄位，將欄數維持在最小。 這在銷售流程中很有幫助，因為其中已經涉及許多表格。 最好不要對這個已經複雜的程式增加更多複雜性。 此方法可滿足許多使用案例，但並非全部。

- 缺點

   - 此方法僅適用於儲存唯讀資料。 發生此問題是因為我們的程式碼需要取消序列化才能修改和建置物件以新增相依性或資料庫關係。

   - 很難使用資料庫作業來搜尋這些欄位。 使用此方法搜尋時速度很慢。

   - 將資料儲存在 `additional_data` 欄，以避免觸發可能透過建立無效JSON來中斷程式碼或在執行期間造成讀取錯誤的序列化或取消序列化作業。

   - 這些欄位必須在程式碼中清楚宣告，讓開發人員可輕鬆找到。

   - 其他可能發生且很難診斷的問題。 例如，如果您不使用某些原生PHP函式 [!DNL Adobe Commerce] 核心應用程式所提供的包裝函式方法，轉換資料的結束結果可能與預期格式不同。 請一律使用包裝函式，確保儲存或擷取資料的一致性和可預測性。

以下是表格的範例，這些表格具有的欄和結構 `additional_data` 欄。

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

在2.4.3、2.4.4和2.4.5版中，有10個表格有欄 `additional_data`.

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
