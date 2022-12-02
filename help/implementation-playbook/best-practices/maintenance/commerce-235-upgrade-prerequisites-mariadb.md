---
title: Adobe Commerce 2.3.5 MariaDB的升級必要條件
description: 了解如何準備Adobe Commerce資料庫以從Adobe Commerce 2.3.5升級。
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: 071e88c6a07df0f74b6d4b09cce858710c9332cc
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 0%

---


# Adobe Commerce 2.3.5升級必要條件

本文說明從2.3.4版或更舊版本升級至Adobe Commerce 2.3.5時，如何準備資料庫。

此升級需要支援團隊將雲基礎架構上的MariaDB從MariaDB 10.0升級至10.2，以符合Adobe Commerce 2.3.5版及更新版本的需求。

## 受影響的產品和版本

Adobe Commerce，使用Adobe Commerce 2.3.4版或更舊版本以及MariaDB 10.0版或更舊版本，在雲端基礎架構上部署。

## 準備資料庫以進行升級

在Adobe Commerce支援團隊開始升級過程之前，請通過轉換資料庫表來準備資料庫：

- 從 `COMPACT` to `DYNAMIC`
- 將儲存引擎從 `MyISAM` to `InnoDB`

規劃和排程轉換時，請謹記下列考量事項：

- 從 `COMPACT` to `DYNAMIC` 若使用大型資料庫，表可能需要數小時的時間。

- 為防止資料損毀，請勿在即時網站上完成轉換工作。

- 在網站的低流量期間完成轉換工作。

- 將您的網站切換為 [維護模式](../../../installation/tutorials/maintenance-mode.md) 運行命令以轉換資料庫表之前。

### 轉換資料庫表行格式

可以轉換群集中一個節點上的表。 更改會自動複製到其他服務節點。

1. 在雲端基礎架構環境上，透過Adobe Commerce使用SSH連線至節點1。

1. 登錄MariaDB。

1. 標識要從緊湊格式轉換為動態格式的表。

   ```mysql
   SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format 'Compact';
   ```

1. 決定表格大小，以便排程轉換工作。

   ```mysql
   SELECT table_schema as 'Database', table_name AS 'Table', round(((data_length + index_length) / 1024 / 1024), 2) 'Size in MB' FROM information_schema.TABLES ORDER BY (data_length + index_length) DESC;
   ```

   要轉換較大的表格，需要較長的時間。 複查表並按優先順序和表大小批處理轉換工作，以幫助規劃所需的維護窗口。

1. 將所有表格一次轉換為動態格式。

   ```mysql
   ALTER TABLE [ table name here ] ROW_FORMAT=DYNAMIC;
   ```

### 轉換資料庫表儲存格式

可以轉換群集中一個節點上的表。 更改會自動複製到其他服務節點。

針對Adobe Commerce Starter和Adobe Commerce Pro專案，轉換儲存格式的程式不同。

- 對於入門體系結構，請使用MySQL `ALTER` 命令轉換格式。
- 在Pro體系結構上，使用MySQL `CREATE` 和 `SELECT` 命令建立資料庫表 `InnoDB` 將資料從現有表中儲存並複製到新表中。 此方法可確保將更改複製到群集中的所有節點。

**轉換Adobe Commerce Pro專案的表格儲存格式**

1. 標識使用 `MyISAM` 儲存。

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. 將所有表轉換為 `InnoDB` 儲存格式一次為一。

   - 更名現有表以防止名稱衝突。

      ```mysql
      RENAME TABLE <existing_table> <table_old>;
      ```

   - 建立使用 `InnoDB` 使用現有表格中的資料儲存。

      ```mysql
      CREATE TABLE <existing_table> ENGINE=InnoDB SELECT * from <table_old>;
      ```

   - 驗證新表包含所有必需資料。

   - 刪除您重新命名的原始表。


**轉換Adobe Commerce Starter專案的表格儲存格式**

1. 標識使用 `MyISAM` 儲存。

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. 轉換使用 `MyISAM` 儲存 `InnoDB` 儲存。

   ```mysql
   ALTER TABLE [ table name here ] ENGINE=InnoDB;
   ```

### 驗證資料庫轉換

在計畫升級到MariaDB 10.2版的前一天，驗證所有表都具有正確的行格式和儲存引擎。 需要驗證，因為完成轉換後進行的程式碼部署可能會導致某些表格還原為其原始設定。

1. 登入您的資料庫。

1. 檢查是否有任何表仍具有 `COMPACT` 行格式。

   ```mysql
   SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
   ```

1. 檢查是否有任何表仍使用 `MyISAM` 儲存格式

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. 如果已還原任何表，請重複這些步驟以更改表行格式和儲存引擎。

## 其他資訊

[Adobe Commerce雲端基礎架構資料庫最佳實務](../planning/database-on-cloud.md)
