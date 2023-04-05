---
title: 資料遷移設定
description: 了解如何開始將設定從Magento1移轉至Magento2，方法是使用 [!DNL Data Migration Tool].
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 資料遷移設定

此 `Settings` 模式遷移儲存、網站和系統配置，如運費、付款和稅務設定。 根據我們的資料遷移 [訂購](overview.md#migration-order)，您應先移轉設定。

開始之前，請執行下列步驟以準備：

1. 以 [檔案系統所有者](../../../installation/prerequisites/file-system/overview.md).

1. 變更為 `/bin` 目錄，或確認已將其新增至您的系統 `PATH`.

>[!NOTE]
>
>確保Magento2部署在 `default` 模式。 開發人員模式可能會在移轉工具中造成驗證錯誤。


請參閱 [第一步](overview.md#first-steps) 一節以取得詳細資訊。

## 運行設定遷移命令

若要開始移轉設定，請執行：

```bash
bin/magento migrate:settings [-r|--reset] [-a|--auto] {<path to config.xml>}
```

其中：

* `[-r|--reset]` 是從頭開始移轉的選用引數。 您可以使用此引數來測試移轉

* `[-a|--auto]` 是可選引數，當遇到完整性檢查錯誤時，該引數會阻止遷移停止。

* `{<path to config.xml>}` 是遷移工具的絕對檔案系統路徑 [`config.xml`](../configure.md#configure-migration-in-vendor-folder) 檔案；此引數為必要項目。

>[!NOTE]
>
>此命令不會遷移所有配置設定。 在繼續操作之前，先驗證「Magento2管理員」中的所有設定。


此 `Migration completed` 成功傳輸設定後，會顯示訊息。

## 設定自訂移轉規則

遷移設定時，您可以忽略、更名或更改系統配置。 為此，請在 `settings.xml` 檔案。

1. 以（或） [檔案系統所有者](../../../installation/prerequisites/file-system/overview.md).

1. 更改到以下目錄：

   ```bash
   cd <your application 2 install dir>/vendor/magento/data-migration-tool/etc/<edition-to-edition>
   ```

   例如，如果應用程式安裝在 `/var/www/html`, `settings.xml.dist` 檔案位於以下目錄之一：

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/commerce-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-opensource`

1. 建立 `settings.xml` 檔案（從提供的範例），執行：

   ```bash
   cp settings.xml.dist settings.xml
   ```

1. 在 `settings.xml`.

1. 要指定要映射的設定檔案的新名稱，請更改 `<settings_map_file>` 標籤 `path/to/config.xml` 檔案。

如需詳細資訊，請參閱 [設定移轉模式](../technical-specification.md#settings-migration-mode) 工具的 [規格](../technical-specification.md).

## 下一個移轉步驟

* [遷移資料](data.md)
