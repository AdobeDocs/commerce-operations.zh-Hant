---
title: 資料移轉設定
description: 瞭解如何透過開始將設定從Magento1移轉至Magento2 [!DNL Data Migration Tool].
exl-id: 6fc8285a-9f26-48a5-9034-49a6a1b66b40
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 0%

---

# 資料移轉設定

此 `Settings` 模式會移轉商店、網站和系統組態，例如運費、付款和稅捐設定。 根據我們的資料移轉 [訂購](overview.md#migration-order)，您應該先移轉設定。

開始之前，請採取下列步驟進行準備：

1. 以以下身分登入應用程式伺服器： [檔案系統擁有者](../../../installation/prerequisites/file-system/overview.md).

1. 變更為 `/bin` 目錄，或確認已將其新增至您的系統 `PATH`.

>[!NOTE]
>
>確保Magento2已部署在 `default` 模式。 開發人員模式可能會在移轉工具中造成驗證錯誤。


請參閱 [第一步](overview.md#first-steps) 區段以取得更多詳細資料。

## 執行設定移轉命令

若要開始移轉設定，請執行：

```bash
bin/magento migrate:settings [-r|--reset] [-a|--auto] {<path to config.xml>}
```

其中：

* `[-r|--reset]` 是選用引數，會從頭開始移轉。 您可以使用此引數來測試移轉

* `[-a|--auto]` 是選用引數，可防止移轉在遇到完整性檢查錯誤時停止。

* `{<path to config.xml>}` 是移轉工具檔案系統的絕對路徑 [`config.xml`](../configure.md#configure-migration-in-vendor-folder) 檔案；此引數為必要專案。

>[!NOTE]
>
>這個命令不會移轉所有組態設定。 在繼續之前，請先驗證Magento2管理員中的所有設定。


此 `Migration completed` 設定傳輸成功後會顯示訊息。

## 設定自訂移轉規則

移轉設定時，您可以忽略、重新命名或變更系統組態。 為此，請在「 」中指定自訂規則 `settings.xml` 檔案。

1. 以或切換方式登入應用程式伺服器 [檔案系統擁有者](../../../installation/prerequisites/file-system/overview.md).

1. 變更至下列目錄：

   ```bash
   cd <your application 2 install dir>/vendor/magento/data-migration-tool/etc/<edition-to-edition>
   ```

   例如，如果應用程式安裝在 `/var/www/html`，則 `settings.xml.dist` 檔案位於下列目錄之一：

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/commerce-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-opensource`

1. 若要建立 `settings.xml` 檔案，執行：

   ```bash
   cp settings.xml.dist settings.xml
   ```

1. 變更於 `settings.xml`.

1. 若要指定對應設定檔案的新名稱，請變更 `<settings_map_file>` 標籤中的變數 `path/to/config.xml` 檔案。

如需詳細資訊，請參閱 [設定移轉模式](../technical-specification.md#settings-migration-mode) 工具的 [規格](../technical-specification.md).

## 下一個移轉步驟

* [移轉資料](data.md)
