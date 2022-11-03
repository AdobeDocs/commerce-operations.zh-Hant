---
title: Adobe Commerce 2.3.5 MariaDB的升級必要條件
description: 了解如何準備Adobe Commerce資料庫以從Adobe Commerce 2.3.5升級。
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: 1abe86197de68336e10c50cab7ad38eebb098aeb
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Adobe Commerce 2.3.5升級必要條件

本文說明從2.3.4版或更舊版本升級至Adobe Commerce 2.3.5時，如何準備資料庫。

此升級需要支援團隊將雲端基礎架構上的MariaDB從MariaDB 10.0升級至10.2，以符合Adobe Commerce的需求。 Adobe Commerce 2.3.5版及更新版本。

## 受影響的產品和版本

Adobe Commerce，使用Adobe Commerce 2.3.4版或更舊版本以及MariaDB 10.0版或更舊版本，在雲端基礎架構上部署。

## 準備資料庫以進行升級

在Adobe Commerce支援團隊開始升級過程之前，您必須轉換所有表格的格式，以準備資料庫 `COMPACT` to `DYNAMIC`. 您還必須從 `MyISAM` to `InnoDB`.

建立轉換資料庫的計畫和計畫時，請牢記以下准則。

- 從 `COMPACT` to `DYNAMIC` 若使用大型資料庫，表可能需要數小時的時間。

- 為防止資料損毀，請勿在網站上線時執行轉換。

- 在網站的低流量期間完成轉換工作。

- 將您的網站切換為 [維護模式](../../../installation/tutorials/maintenance-mode.md) 執行之前 `ALTER` 命令。

### 轉換資料庫表

可以轉換群集中一個節點上的表。 變更會複製到叢集中的其他核心節點。

1. 在雲端基礎架構環境上，透過Adobe Commerce使用SSH連線至節點1。

1. 登錄MariaDB。

1. 轉換表格格式。

   - 標識要從緊湊格式轉換為動態格式的表。

      ```mysql
      SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format 'Compact';
      ```

   - 決定表格大小，以便排程轉換工作。

      ```mysql
      SELECT table_schema as 'Database', table_name AS 'Table', round(((data_length + index_length) / 1024 / 1024), 2) 'Size in MB' FROM information_schema.TABLES ORDER BY (data_length + index_length) DESC;
      ```

      要轉換較大的表格，需要較長的時間。 在進入和退出維護模式時，您應根據順序規劃要轉換的表批次，以便規劃所需維護窗口的計時

   - 將所有表格一次轉換為動態格式。

      ```mysql
      ALTER TABLE [ table name here ] ROW_FORMAT=DYNAMIC;
      ```

1. 更新表儲存引擎。

   - 標識使用 `MyISAM` 儲存。

      ```mysql
      SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
      ```

   - 轉換使用 `MyISAM` 儲存 `InnoDB` 儲存。

      ```mysql
      ALTER TABLE [ table name here ] ENGINE=InnoDB;
      ```

1. 驗證轉換。

   此步驟為必要，因為完成轉換後進行的程式碼部署可能會導致某些表格還原為其原始設定。

   - 在計畫升級到MariaDB 10.2版的前一天，登錄到您的資料庫並運行查詢以檢查格式和儲存引擎。

      ```mysql
      SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
      ```

      ```mysql
      SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
      ```

   - 如果已還原任何表，請重複這些步驟以更改表格格式和儲存引擎。

## 其他資訊

[Adobe Commerce雲端基礎架構資料庫最佳實務](../planning/database-on-cloud.md)
