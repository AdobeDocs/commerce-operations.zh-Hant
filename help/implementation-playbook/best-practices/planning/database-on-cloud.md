---
title: 雲端部署的資料庫設定最佳實務
description: 了解如何配置資料庫和應用程式設定，以在雲端基礎架構上部署Adobe Commerce時提升效能。
role: Developer, Admin
feature-set: Commerce
feature: Best Practices
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 資料庫配置的最佳做法

了解在雲端基礎架構上部署Adobe Commerce時，改善資料庫效能並有效運用資料庫的最佳實務。

## 受影響的產品

Adobe Commerce雲基礎架構

## 將所有MyISAM表轉換為InnoDB

Adobe建議使用InnoDB資料庫引擎。 在預設的Adobe Commerce安裝中，資料庫中的所有表都使用InnoDB引擎儲存。 不過，某些協力廠商模組（擴充功能）可以導入MyISAM格式的表格。 安裝第三方模組後，請檢查資料庫以標識中的任何表 `myisam` 格式化並轉換為 `innodb` 格式。

### 確定模組是否包含MyISAM表

您可以在安裝第三方模組代碼之前對其進行分析，以確定它是否使用MyISAM表。

如果已安裝擴展，請運行以下查詢以確定資料庫是否具有任何MyISAM表：

```sql
SELECT table_schema, CONCAT(ROUND((index_length+data_length)/1024/1024),'MB')
    AS total_size FROM information_schema. TABLES WHERE engine='myisam' AND table_schema
    NOT IN ('mysql', 'information_schema', 'performance_schema', 'sys');
```

### 將儲存引擎更改為InnoDB

在 `db_schema.xml` 檔案聲明表，設定 `engine` 屬性值 `table` 節點到 `innodb`. 如需參考，請參閱 [配置聲明性架構>表節點](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) 在開發人員檔案中。

Adobe Commerce在雲端基礎架構2.3版中導入了宣告性方案。

## 為本機MySQL搜索配置建議的搜索引擎

Adobe建議您一律在雲端基礎架構專案上為Adobe Commerce設定Elasticsearch或OpenSearch，即使您打算為Adobe Commerce應用程式設定協力廠商搜尋工具亦然。 此設定提供備援選項，以備第三方搜尋工具失敗時使用。

您使用的搜尋引擎取決於安裝的雲端版本上的Adobe Commerce:

- 對於Adobe Commerce 2.4.4和更新版本，請使用OpenSearch服務進行本機MySQL搜尋。

- 若為舊版Adobe Commerce，請使用Elasticsearch。

若要判斷目前使用中的搜尋引擎，請執行下列命令：

```bash
./bin/magento config:show catalog/search/engine
```

如需設定指示，請參閱雲端上Adobe Commerce的開發人員指南：

- [設定OpenSearch服務](https://devdocs.magento.com/cloud/project/services-opensearch.html)

- [設定Elasticsearch服務](https://devdocs.magento.com/cloud/project/services-elastic.html)

## 避免自訂觸發器

盡可能避免使用自訂觸發程式。

觸發器用於將更改記錄到審核表中。 Adobe建議將應用程式配置為直接寫入審計表，而不要使用觸發功能，原因如下：

- 觸發器被解釋為代碼，而MySQL不會預編譯它們。 它們會連結至查詢的交易空間，為使用表執行的每個查詢增加剖析器和解釋器的開銷。
- 觸發器與原始查詢共用相同的事務空間，而當這些查詢在表上競爭鎖時，觸發器獨立地在另一表上競爭鎖。

若要了解使用自訂觸發程式的替代方法，請參閱 [有效使用MySQL觸發器](mysql-triggers-usage.md) 在我們的支援知識庫中。

## 升級 [!DNL ECE-Tools] 到2002.0.21版或更高版本 {#ece-tools-version}

為避免死鎖的潛在問題，請將ECE-Tools升級至2002.0.21版或更高版本。 如需指示，請參閱 [更新 `ece-tools` 版本](https://devdocs.magento.com/cloud/project/ece-tools-update.html) 在開發人員檔案中。

## 安全切換索引器模式

<!--This best practice might belong in the Maintenance phase. Database lock prevention might be consolidated under a single heading-->

切換索引器生成 [!DNL data definition language] (DDL)語句，以建立可能導致資料庫鎖的觸發器。 您可以在變更設定前，將網站置於維護模式並停用cron作業，借此防止此問題。
如需指示，請參閱 [配置索引器](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html#configure-indexers-1) 在 *Adobe Commerce設定指南*.

## 不在生產中運行DDL陳述式

避免在生產環境中運行DDL陳述式以防止衝突（如表修改和建立）。 此 `setup:upgrade` 進程是例外。

如果需要運行DDL語句，請將網站置於維護模式並禁用cron（請參見上一節中有關安全切換索引的說明）。

## 啟用訂單存檔

從管理員啟用訂單歸檔，以在訂單資料增長時減少銷售表所需的空間。 歸檔可節省MySQL磁碟空間並提高簽出效能。

請參閱 [啟用歸檔](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-archive.html) 在Adobe Commerce商家檔案中。

## 其他資訊

- [InnoDB和MYISAM之間的主要區別是什麼](http://www.expertphp.in/article/what-are-the-main-differences-between-innodb-and-myisam)
- [Adobe Commerce 2.3.5 MariaDB的升級必要條件](../maintenance/commerce-235-upgrade-prerequisites-mariadb.md)
- [解決資料庫效能問題的最佳實務](../maintenance/resolve-database-performance-issues.md)
