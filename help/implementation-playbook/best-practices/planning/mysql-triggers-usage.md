---
title: MySQL觸發器用法
description: 瞭解如何在Adobe Commerce中有效使用MySQL觸發器。
role: Developer
feature-set: Commerce
feature: Best Practices
exl-id: acac3e47-67c8-4eea-80e3-e26f2854391a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# MySQL觸發器用法的最佳做法

本文介紹了在使用MySQL觸發器時如何避免效能問題。 觸發器用於將更改記錄到審計表中。

## 受影響的產品和版本

- Adobe Commerce內部
- Adobe Commerce在雲基礎架構上

>[!WARNING]
>
>對於Adobe Commerce的雲項目，在更改生產環境的配置之前，始終test登台環境中的配置更改。

## 瞭解效能影響

觸發器被解釋為代碼，表示MySQL不預編譯它們。

觸發器鈎聯到查詢的事務空間，為使用表執行的每個查詢向解析器和解釋器添加開銷。 觸發器與原始查詢共用相同的事務空間，當這些查詢爭用表上的鎖時，觸發器獨立地爭用另一個表上的鎖。

如果使用了多個觸發器，則此額外開銷可能會對站點的效能產生負面影響。

>[!WARNING]
>
>Adobe Commerce不支援Adobe Commerce資料庫中的任何自定義觸發器，因為自定義觸發器可能會與未來的Adobe Commerce版本不相容。 有關最佳做法，請參見 [常規MySQL准則](../../../installation/prerequisites/database/mysql.md) 在Adobe Commerce檔案里。

## 有效使用觸發器

要防止在使用觸發器時出現效能問題，請遵循以下准則：

- 如果在執行觸發器時有自定義觸發器寫入某些資料，請移動此邏輯直接寫入審計表。 例如，通過在應用程式碼中添加附加查詢，在要為其建立觸發器的查詢之後添加附加查詢。
- 查看現有的自定義觸發器，並考慮刪除它們並直接從應用程式端寫入表。 使用 [`SHOW TRIGGERS` SQL陳述式](https://dev.mysql.com/doc/refman/8.0/en/show-triggers.html)。
- 如需其他幫助、問題或關切， [提交Adobe Commerce支援票證](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?#submit-ticket)。

## 其他資訊

- [MySQL先決條件](../../../installation/prerequisites/database/mysql.md)
- [針對Adobe Commerce的雲基礎架構資料庫最佳做法](database-on-cloud.md)
