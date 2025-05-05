---
title: MySQL設定最佳實務
description: 瞭解MySQL觸發器和從屬連線如何影響Commerce網站效能，以及如何有效使用它們。
role: Developer
feature: Best Practices
exl-id: 7c2f51fd-9333-4954-bd35-79c2de3cb2ff
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 0%

---

# MySQL設定最佳實務

>[!NOTE]
>
>此主題包含業界標準的軟體術語，有些人可能會發現這些術語具有種族主義、性別歧視或壓迫性，可能會讓讀者感到傷害、創傷或不受歡迎。 Adobe正在從程式碼、檔案和使用者體驗中移除這些詞語。

## 觸發器

本文說明在使用MySQL觸發程式時，如何避免效能問題。 觸發器用於將變更記錄到稽核表中。

### 受影響的產品和版本

- Adobe Commerce內部部署
- 雲端基礎結構上的Adobe Commerce

>[!WARNING]
>
>對於雲端專案上的Adobe Commerce，在變更生產環境的設定之前，請一律在中繼環境中測試設定變更。

### 效能影響

觸發程式會解譯為程式碼，表示MySQL不會預先編譯它們。

掛接到查詢的交易空間時，會觸發為使用表格執行的每個查詢向剖析器和解譯器增加額外負荷。 觸發程式與原始查詢共用相同的交易空間，當這些查詢競爭表格上的鎖定時，觸發程式會獨立競爭另一個表格上的鎖定。

如果使用許多觸發程式，這些額外的額外開銷可能會對網站上的網站效能產生負面影響。

>[!WARNING]
>
>Adobe Commerce不支援Adobe Commerce資料庫中的任何自訂觸發器，因為自訂觸發器可能會與未來Adobe Commerce版本不相容。 如需最佳實務，請參閱Adobe Commerce檔案中的[一般MySQL准則](../../../installation/prerequisites/database/mysql.md)。

### 有效使用

若要在使用觸發程式時防止效能問題，請遵循下列准則：

- 如果您有在執行觸發程式時寫入某些資料的自訂觸發程式，請移動此邏輯以直接寫入稽核表格。 例如，在應用程式程式碼中新增其他查詢，然後在您打算為其建立觸發器的查詢後進行。
- 檢閱現有的自訂觸發器，並考慮移除這些觸發器，然後直接從應用程式端寫入表格。 使用[`SHOW TRIGGERS` SQL陳述式](https://dev.mysql.com/doc/refman/8.0/en/show-triggers.html)檢查資料庫中現有的觸發程式。
- 如需其他協助、問題或顧慮，[請提交Adobe Commerce支援票證](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=zh-Hant&#submit-ticket)。

## 從屬連線

Adobe Commerce可以非同步讀取多個資料庫。 如果您預期部署在雲端基礎結構Pro架構上的Commerce站台的MySQL資料庫會有高負載，Adobe建議啟用MYSQL從屬連線。

當您啟用MYSQL從屬連線時，Adobe Commerce會使用資料庫的唯讀連線，來接收非主節點上的唯讀流量。 當只有一個節點處理讀寫流量時，可透過負載平衡來改善效能。

### 受影響的版本

雲端基礎結構上的Adobe Commerce，僅限Pro架構

### 設定

在雲端基礎結構上的Adobe Commerce中，您可以設定[MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=zh-Hant#mysql_use_slave_connection)變數，覆寫MYSQL從屬連線的預設設定。 將此變數設為`true`以自動使用資料庫的唯讀連線。

**若要啟用MySQL從屬連線**：

1. 在本機工作站上，變更至專案目錄。

1. 在`.magento.env.yaml`檔案中，將`MYSQL_USE_SLAVE_CONNECTION`設定為true。

   ```
   stage:
     deploy:
       MYSQL_USE_SLAVE_CONNECTION: true
   ```

1. 認可`.magento.env.yaml`檔案變更並推播至遠端環境。

   部署成功完成後，雲端環境就會啟用MySQL從屬連線。
