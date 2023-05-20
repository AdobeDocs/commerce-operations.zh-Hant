---
title: 用於雲部署的資料庫配置最佳做法
description: 瞭解如何配置資料庫和應用程式設定以在雲基礎架構上部署Adobe Commerce時提高效能。
role: Developer, Admin
feature-set: Commerce
feature: Best Practices
exl-id: ca377dc8-c8bd-4f77-a24b-22a298e2bba4
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '687'
ht-degree: 0%

---

# 資料庫配置的最佳做法

瞭解在雲基礎架構上部署Adobe Commerce時提高資料庫效能並與資料庫高效協作的最佳做法。

## 受影響的產品

Adobe Commerce在雲基礎架構上

## 將所有MyISAM表轉換為InnoDB

Adobe建議使用InnoDB資料庫引擎。 在預設的Adobe Commerce安裝中，資料庫中的所有表都使用InnoDB引擎儲存。 但是，某些第三方模組（擴展）可以採用MyISAM格式的表。 安裝第三方模組後，請檢查資料庫以標識中的任何表 `myisam` 格式化並將其轉換為 `innodb` 的子菜單。

### 確定模組是否包含MyISAM表

可以在安裝第三方模組代碼之前分析它，以確定它是否使用MyISAM表。

如果已安裝擴展，請運行以下查詢以確定資料庫是否具有任何MyISAM表：

```sql
SELECT table_schema, CONCAT(ROUND((index_length+data_length)/1024/1024),'MB')
    AS total_size FROM information_schema. TABLES WHERE engine='myisam' AND table_schema
    NOT IN ('mysql', 'information_schema', 'performance_schema', 'sys');
```

### 將儲存引擎更改為InnoDB

在 `db_schema.xml` 檔案聲明表，設定 `engine` 相應的屬性值 `table` 節點到 `innodb`。 有關參考，請參見 [配置聲明性架構>表節點](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) 我們的開發人員文檔中。

該聲明性方案在Adobe Commerce對雲基礎設施2.3版進行了介紹。

## 為本機MySQL搜索配置建議的搜索引擎

Adobe建議您始終在雲基礎架構項目上為Adobe Commerce設定Elasticsearch或OpenSearch，即使您計畫為Adobe Commerce應用程式配置第三方搜索工具也是如此。 在第三方搜索工具失敗時，此配置提供了回退選項。

您使用的搜索引擎取決於安裝的雲版本上的Adobe Commerce:

- 對於Adobe Commerce2.4.4及更高版本，使用OpenSearch服務進行本機MySQL搜索。

- 對於早期的Adobe Commerce版本，請使用Elasticsearch。

要確定當前使用的搜索引擎，請運行以下命令：

```bash
./bin/magento config:show catalog/search/engine
```

有關配置說明，請參閱雲上Adobe Commerce的開發人員指南：

- [設定OpenSearch服務](https://devdocs.magento.com/cloud/project/services-opensearch.html)

- [設定Elasticsearch服務](https://devdocs.magento.com/cloud/project/services-elastic.html)

## 避免自定義觸發器

如果可能，請避免使用自定義觸發器。

觸發器用於將更改記錄到審計表中。 Adobe建議將應用程式配置為直接寫入審計表，而不是使用觸發器功能，原因如下：

- 觸發器被解釋為代碼，MySQL不預編譯它們。 掛接到查詢的事務空間後，它們會為使用表執行的每個查詢添加分析器和解釋器開銷。
- 觸發器與原始查詢共用相同的事務空間，當這些查詢爭用表上的鎖時，觸發器獨立地競爭另一表上的鎖。

要瞭解使用自定義觸發器的替代方法，請參見 [有效使用MySQL觸發器](mysql-triggers-usage.md) 我們的支援知識庫。

## 升級 [!DNL ECE-Tools] 至2002.0.21版或更高版本 {#ece-tools-version}

為避免出現Cron死鎖的潛在問題，請將ECE-Tools升級到2002.0.21版或更高版本。 有關說明，請參見 [更新 `ece-tools` 版本](https://devdocs.magento.com/cloud/project/ece-tools-update.html) 我們的開發人員文檔中。

## 安全切換索引器模式

<!--This best practice might belong in the Maintenance phase. Database lock prevention might be consolidated under a single heading-->

交換索引器生成 [!DNL data definition language] (DDL)語句，用於建立可導致資料庫鎖的觸發器。 您可以通過在更改配置之前將網站置於維護模式並禁用cron作業來防止此問題。
有關說明，請參見 [配置索引器](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html#configure-indexers-1) 的 *Adobe Commerce配置指南*。

## 不在生產中運行DDL語句

避免在生產環境中運行DDL語句以防止衝突（如表修改和建立）。 的 `setup:upgrade` 進程是例外。

如果需要運行DDL語句，請將網站置於維護模式並禁用cron（請參閱上一節中有關安全切換索引的說明）。

## 啟用訂單存檔

允許管理員對訂單進行歸檔，以減少隨訂單資料增長而需要的銷售表空間。 存檔可節省MySQL磁碟空間並提高簽出效能。

請參閱 [啟用存檔](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-archive.html) 在Adobe Commerce商人檔案里。

## 其他資訊

- [MySQL儲存引擎](https://dev.mysql.com/doc/refman/8.0/en/storage-engines.html)
- [Adobe Commerce2.3.5 MariaDB升級先決條件](../maintenance/commerce-235-upgrade-prerequisites-mariadb.md)
- [解決資料庫效能問題的最佳做法](../maintenance/resolve-database-performance-issues.md)
