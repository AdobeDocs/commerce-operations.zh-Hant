---
title: Adobe Commerce2.3.5 MariaDB升級先決條件
description: 瞭解如何準備從Adobe Commerce升級的Adobe Commerce2.3.5資料庫。
role: Developer
feature-set: Commerce
feature: Best Practices
exl-id: b86e471f-e81f-416b-a321-7aa1ac73d27c
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '641'
ht-degree: 0%

---

# 升級MariaDB的先決條件

從Adobe Commerce2.3.4或更低版本升級到任何較新版本需要將雲基礎架構上的MariaDB服務從10.0或10.2版升級到10.3或10.4版。MariaDB 10.3及更高版本要求資料庫使用動態表行格式，而Adobe Commerce則要求使用InnoDB儲存引擎進行表格升級。 本文介紹如何更新資料庫以符合這些MariaDB要求。

準備資料庫後，請提交Adobe Commerce支援票證以更新雲基礎架構上的MariaDB服務版本，然後再繼續Adobe Commerce升級過程。

## 受影響的產品和版本

Adobe Commerce在雲基礎架構上使用Adobe Commerce版本2.3.4或更早版本和MariaDB版本10.0或更早版本。

## 準備資料庫以進行升級

在Adobe Commerce支援團隊開始升級過程之前，請通過轉換資料庫表來準備資料庫：

- 轉換行格式 `COMPACT` 至 `DYNAMIC`
- 將儲存引擎從 `MyISAM` 至 `InnoDB`

在計畫和計畫轉換時，請牢記以下注意事項：

- 轉換自 `COMPACT` 至 `DYNAMIC` 使用大型資料庫時，表可能需要幾個小時。

- 要防止資料損壞，請不要在即時站點上完成轉換工作。

- 在站點上的低流量期間完成轉換工作。

- 將您的站點切換到 [維護模式](../../../installation/tutorials/maintenance-mode.md) 運行轉換資料庫表的命令之前。

### 轉換資料庫表行格式

可以轉換集群中一個節點上的表。 這些更改會自動複製到其他服務節點。

1. 在雲基礎架構環境上的Adobe Commerce上，使用SSH連接到節點1。

1. 登錄到MariaDB。

1. 標識要從壓縮格式轉換為動態格式的表。

   ```mysql
   SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
   ```

1. 確定表大小，以便您可以安排轉換工作。

   ```mysql
   SELECT table_schema as 'Database', table_name AS 'Table', round(((data_length + index_length) / 1024 / 1024), 2) 'Size in MB' FROM information_schema.TABLES ORDER BY (data_length + index_length) DESC;
   ```

   較大的表要轉換需要較長時間。 查看表並按優先順序和表大小對轉換工作進行批處理，以幫助規劃所需的維護窗口。

1. 將所有表一次轉換為動態格式。

   ```mysql
   ALTER TABLE [ table name here ] ROW_FORMAT=DYNAMIC;
   ```

### 轉換資料庫表儲存格式

可以轉換集群中一個節點上的表。 這些更改會自動複製到其他服務節點。

對於Adobe CommerceStarter和Adobe CommercePro項目，轉換儲存格式的過程不同。

- 對於Starter體系結構，使用MySQL `ALTER` 的子菜單。
- 在Pro體系結構上，使用MySQL `CREATE` 和 `SELECT` 命令建立資料庫表 `InnoDB` 將資料從現有表中儲存並複製到新表中。 此方法確保將更改複製到群集中的所有節點。

**轉換Adobe CommercePro項目的表儲存格式**

1. 標識使用 `MyISAM` 儲存。

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. 將所有表轉換為 `InnoDB` 儲存格式，一次一個。

   - 更名現有表以防止名稱衝突。

      ```mysql
      RENAME TABLE <existing_table> <table_old>;
      ```

   - 建立使用 `InnoDB` 儲存。

      ```mysql
      CREATE TABLE <existing_table> ENGINE=InnoDB SELECT * from <table_old>;
      ```

   - 驗證新表是否包含所有所需資料。

   - 刪除已更名的原始表。


**轉換Adobe Commerce初學者項目的表儲存格式**

1. 標識使用 `MyISAM` 儲存。

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. 轉換使用 `MyISAM` 儲存 `InnoDB` 儲存。

   ```mysql
   ALTER TABLE [ table name here ] ENGINE=InnoDB;
   ```

### 驗證資料庫轉換

在計畫升級到MariaDB 10.2版的前一天，驗證所有表的行格式和儲存引擎是否正確。 需要驗證，因為完成轉換後進行的代碼部署可能會導致某些表恢復為其原始配置。

1. 登錄到資料庫。

1. 檢查是否有 `COMPACT` 的下界。

   ```mysql
   SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
   ```

1. 檢查是否仍使用 `MyISAM` 儲存格式

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. 如果已還原任何表，請重複這些步驟以更改表行格式和儲存引擎。

## 更改儲存引擎

請參閱 [將MyISAM表轉換為InnoDB](../planning/database-on-cloud.md)。

## 其他資訊

- [針對Adobe Commerce的雲基礎架構資料庫最佳做法](../planning/database-on-cloud.md)
- [在雲上更新Adobe Commerce的MariaDB從10.0更新為12.0](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/upgrade-mariadb-10.0-to-10.2-for-magento-commerce-cloud.html)
