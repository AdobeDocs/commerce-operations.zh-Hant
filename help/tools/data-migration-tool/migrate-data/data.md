---
title: 遷移資料
description: 瞭解如何開始將資料從Magento1遷移到Magento2, [!DNL Data Migration Tool]。
exl-id: f4ea8f6a-21f8-4db6-b598-c5efecec254f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---

# 遷移資料

在開始之前，請執行以下步驟準備：

1. 以以下方式登錄到應用程式伺服器： [檔案系統所有者](../../../installation/prerequisites/file-system/overview.md)。
1. 更改到應用程式安裝目錄，或確保已將其添加到系統 `PATH`。

查看 [第一步](overview.md#first-steps) 的子菜單。

## 運行資料遷移命令

要開始遷移資料，請運行：

```bash
bin/magento migrate:data [-r|--reset] [-a|--auto] {<path to config.xml>}
```

位置：

* `[-a|--auto]` 是一個可選參數，可防止在遇到完整性檢查錯誤時停止遷移。

* `[-r|--reset]` 是從頭開始遷移的可選參數。 您可以使用此參數來測試遷移。

* `{<path to config.xml>}` 是到 `config.xml`;此參數是必需的

在此步驟中， [!DNL Data Migration Tool] 為Magento1資料庫中的遷移表建立其他表和觸發器。 它們用於 [增量/增量](delta.md) 遷移步驟。 其他表包含有關最終遷移執行後更改的記錄的資訊。 資料庫觸發器用於填充這些額外表，因此，如果正在對特定表執行新操作（添加/修改/刪除記錄），則這些資料庫觸發器會將有關此操作的資訊保存到額外表。 運行增量遷移進程時， [!DNL Data Migration Tool] 檢查這些表以查找未處理的記錄，並將必要的內容遷移到Magento2資料庫中。

每個新表都包含：

* `m2_cl` 前置詞
* `INSERT`。 `UPDATE`。 `DELETE` 事件觸發器。

例如， `sales_flat_order` 這樣 [!DNL Data Migration Tool] 建立：

* `m2_cl_sales_flat_order` 表：

   ```sql
   CREATE TABLE `m2_cl_sales_flat_order` (
     `entity_id` int(11) NOT NULL COMMENT 'Entity_id',
     `operation` text COMMENT 'Operation',
     `processed` tinyint(1) NOT NULL DEFAULT '0' COMMENT 'Processed',
     PRIMARY KEY (`entity_id`)
   ) COMMENT='m2_cl_sales_flat_order';
   ```

* `trg_sales_flat_order_after_insert`。 `trg_sales_flat_order_after_update`。 `trg_sales_flat_order_after_delete` 觸發器：

   ```sql
   DELIMITER ;;
   CREATE TRIGGER `trg_sales_flat_order_after_insert` AFTER INSERT ON `sales_flat_order`
     FOR EACH ROW
     BEGIN
      INSERT INTO m2_cl_sales_flat_order (`entity_id`, `operation`) VALUES (NEW.entity_id, 'INSERT')ON DUPLICATE KEY UPDATE operation = 'INSERT';
     END
   ;;
   
   DELIMITER ;;
   CREATE TRIGGER `trg_sales_flat_order_after_update` AFTER UPDATE ON `sales_flat_order`
     FOR EACH ROW
     BEGIN
      INSERT INTO m2_cl_sales_flat_order (`entity_id`, `operation`) VALUES (NEW.entity_id, 'UPDATE') ON DUPLICATE KEY UPDATE operation = 'UPDATE';
     END
   ;;
   
   DELIMITER ;;
   CREATE TRIGGER `trg_sales_flat_order_after_delete` AFTER DELETE ON `sales_flat_order`
     FOR EACH ROW
     BEGIN
      INSERT INTO m2_cl_sales_flat_order (`entity_id`, `operation`) VALUES (OLD.entity_id, 'DELETE')ON DUPLICATE KEY UPDATE operation = 'DELETE';
     END
   ;;
   ```

>[!NOTE]
>
>的 [!DNL Data Migration Tool] 保存其當前進度。 如果錯誤或用戶干預阻止其運行，則工具將恢復上次已知正常狀態的進度。 強制 [!DNL Data Migration Tool] 要從開始運行，請使用 `--reset` 參數。 在這種情況下，我們建議您恢復Magento2資料庫轉儲，以防止複製以前遷移的資料。


## 可能的一致性錯誤

運行時， [!DNL Data Migration Tool] 可能報告Magento1和Magento2資料庫之間的不一致，並顯示如下消息：

* `Source documents are missing: <EXTENSION_TABLE_1>,<EXTENSION_TABLE_2>,...<EXTENSION_TABLE_N>`
* `Destination documents are missing: <EXTENSION_TABLE_1>,<EXTENSION_TABLE_2>,...<EXTENSION_TABLE_N>`
* `Source documents are not mapped: <EXTENSION_TABLE_1>,<EXTENSION_TABLE_2>,...<EXTENSION_TABLE_N>`
* `Destination documents are not mapped: <EXTENSION_TABLE_1>,<EXTENSION_TABLE_2>,...<EXTENSION_TABLE_N>`
* `Source fields are missing. Document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Destination fields are missing. Document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Source fields are not mapped. Document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Destination fields are not mapped. Document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Mismatch of data types. Source document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Mismatch of data types. Destination document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Incompatibility in data. Source document: <EXTENSION_TABLE>. Field: <FIELD>. Error: <ERROR_MESSAGE>`
* `Incompatibility in data. Destination document: <EXTENSION_TABLE>. Field: <FIELD>. Error: <ERROR_MESSAGE>`

查看 [故障排除](https://support.magento.com/hc/en-us/articles/360033020451) 的子菜單。

## 下一遷移步驟

[遷移更改](delta.md)
