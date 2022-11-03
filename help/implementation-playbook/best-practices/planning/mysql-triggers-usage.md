---
title: MySQL觸發器用法
description: 了解如何搭配Adobe Commerce有效使用MySQL觸發程式。
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: 79a825a094a80892cf1a30aa7f5c61bd351c69f5
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# MySQL觸發器使用的最佳做法

本文說明使用MySQL觸發器時如何避免效能問題。 觸發器用於將更改記錄到審核表中。

## 受影響的產品和版本

- Adobe Commerce內部
- Adobe Commerce雲基礎架構

>[!WARNING]
>
>針對雲端專案的Adobe Commerce，在變更生產環境的設定之前，請一律在測試環境中測試設定變更。

## 了解效能影響

觸發器被解釋為代碼，這表示MySQL不會預編譯它們。

在查詢的事務空間中掛接，觸發器會為使用表執行的每個查詢增加剖析器和解釋器的開銷。 觸發器與原始查詢共用相同的事務空間，而當這些查詢在表上爭奪鎖時，觸發器獨立地在另一表上爭奪鎖。

如果使用許多觸發器，此額外負荷可能會對網站的效能造成負面影響。

>[!WARNING]
>
>Adobe Commerce不支援Adobe Commerce資料庫中的任何自訂觸發程式，因為自訂觸發程式可能會導致與未來Adobe Commerce版本不相容。 如需最佳實務，請參閱 [一般MySQL指南](../../../installation/prerequisites/database/mysql.md) 在Adobe Commerce檔案中。

## 有效使用觸發器

若要防止使用觸發器時發生效能問題，請遵循下列准則：

- 如果您有自訂觸發器，會在觸發器執行時寫入部分資料，請改為將此邏輯直接寫入稽核表。 例如，在應用程式程式碼中新增其他查詢後，要在查詢後建立觸發器。
- 檢閱現有的自訂觸發器，並考慮移除觸發器，並直接從應用程式端寫入表格。 使用 [`SHOW TRIGGERS` SQL陳述式](https://dev.mysql.com/doc/refman/8.0/en/show-triggers.html).
- 如需其他協助、問題或疑慮， [提交Adobe Commerce支援票證](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?#submit-ticket).

## 其他資訊

- [MySQL先決條件](../../../installation/prerequisites/database/mysql.md)
- [Adobe Commerce雲端基礎架構資料庫最佳實務](database-on-cloud.md)
