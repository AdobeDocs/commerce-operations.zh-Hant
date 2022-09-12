---
title: 遷移資料
description: 了解如何使用將資料從Magento1移轉至Magento2 [!DNL Data Migration Tool].
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---


# 遷移資料

開始之前，請執行下列步驟以準備：

1. 登入您的應用程式伺服器為 [檔案系統所有者](../../../installation/prerequisites/file-system/overview.md).
1. 更改到應用程式安裝目錄，或確保將其添加到您的系統中 `PATH`.

請參閱 [第一步](overview.md#first-steps) 一節以取得詳細資訊。

## 運行資料遷移命令

若要開始移轉資料，請執行：

```bash
bin/magento migrate:data [-r|--reset] [-a|--auto] {<path to config.xml>}
```

其中：

* `[-a|--auto]` 是可選引數，當遇到完整性檢查錯誤時，該引數會阻止遷移停止。

* `[-r|--reset]` 是從頭開始移轉的選用引數。 您可以使用此引數來測試移轉。

* `{<path to config.xml>}` 是的絕對檔案系統路徑 `config.xml`;此引數為必要項目

在此步驟中， [!DNL Data Migration Tool] 為Magento1資料庫中的遷移表建立其他表和觸發器。 它們用於 [增量/增量](delta.md) 移轉步驟。 其他表包含有關最終遷移執行後更改記錄的資訊。 資料庫觸發器用於填充這些額外表，因此，如果正在對特定表執行新操作（添加/修改/刪除記錄），則這些資料庫觸發器會將有關此操作的資訊保存到額外表。 執行增量遷移流程時， [!DNL Data Migration Tool] 檢查這些表以獲取未處理的記錄，並將必要的內容遷移到Magento2資料庫。

每個新表格都包含：

* `m2_cl` 前置詞
* `INSERT`, `UPDATE`, `DELETE` 事件觸發。

例如，對於 `sales_flat_order` the [!DNL Data Migration Tool] 建立：

* `m2_cl_sales_flat_order` 表格：

   ```sql
   CREATE TABLE `m2_cl_sales_flat_order` (
     `entity_id` int(11) NOT NULL COMMENT 'Entity_id',
     `operation` text COMMENT 'Operation',
     `processed` tinyint(1) NOT NULL DEFAULT '0' COMMENT 'Processed',
     PRIMARY KEY (`entity_id`)
   ) COMMENT='m2_cl_sales_flat_order';
   ```

* `trg_sales_flat_order_after_insert`, `trg_sales_flat_order_after_update`, `trg_sales_flat_order_after_delete` 觸發器：

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
>此 [!DNL Data Migration Tool] 在運行時保存其當前進度。 如果錯誤或用戶干預使其無法運行，則工具將在上次已知良好狀態恢復進度。 強制 [!DNL Data Migration Tool] 若要從頭開始執行，請使用 `--reset` 引數。 在這種情況下，我們建議您還原Magento2資料庫轉儲，以防止複製以前遷移的資料。


## 可能的一致性錯誤

執行時， [!DNL Data Migration Tool] 可報告Magento1和Magento2資料庫之間的不一致，並顯示如下消息：

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

請參閱 [疑難排解](https://support.magento.com/hc/en-us/articles/360033020451) 一節，以取得詳細資訊和建議。

## 下一個移轉步驟

[移轉變更](delta.md)
