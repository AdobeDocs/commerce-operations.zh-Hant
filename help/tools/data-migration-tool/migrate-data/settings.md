---
title: 資料遷移設定
description: 瞭解如何開始將設定從Magento1遷移到Magento2 [!DNL Data Migration Tool]。
source-git-commit: b5a2c362b09de993e1dc196bdda90e74cf4a8ba2
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---


# 資料遷移設定

的 `Settings` 模式遷移商店、網站和系統配置，如發運、付款和稅務設定。 根據我們的資料遷移 [訂單](overview.md#migration-order)，應首先遷移設定。

在開始之前，請執行以下步驟準備：

1. 使用Magento2實例登錄到伺服器 [檔案系統所有者](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html)。

1. 更改為Magento2 `/bin` 目錄或確保它已添加到系統PATH中。

>[!NOTE]
>
>確保Magento2部署在 `default` 的子菜單。 開發人員模式可能導致遷移工具中的驗證錯誤。


查看 [第一步](overview.md#first-steps) 的子菜單。

## 運行設定遷移命令

要開始遷移設定，請運行：

```bash
bin/magento migrate:settings [-r|--reset] [-a|--auto] {<path to config.xml>}
```

位置：

* `[-r|--reset]` 是從頭開始遷移的可選參數。 您可以使用此參數測試遷移

* `[-a|--auto]` 是一個可選參數，可防止在遇到完整性檢查錯誤時停止遷移。

* `{<path to config.xml>}` 是遷移工具的絕對檔案系統路徑 [`config.xml`](../configure.md#configure-migration-in-vendor-folder) 檔案；此參數是必需的。

>[!NOTE]
>
>此命令不會遷移所有配置設定。 驗證Magento2中的所有設定 [管理](https://glossary.magento.com/admin) 才能繼續。


的 `Migration completed` 設定成功傳輸後，將顯示消息。

## 配置自定義遷移規則

遷移設定時，您可以忽略、更名或更改系統配置。 為此，請在 `settings.xml` 的子菜單。

1. 使用Magento2實例登錄到伺服器，或切換到 [檔案系統所有者](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html)。

1. 更改到以下目錄：

   ```bash
   cd <your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<edition-to-edition>
   ```

   例如，如果Magento2安裝在 `/var/www/html`，也請參見Wiki頁。 `settings.xml.dist` 檔案位於以下目錄之一：

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/commerce-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-opensource`

1. 建立 `settings.xml` 檔案，運行：

   ```bash
   cp settings.xml.dist settings.xml
   ```

1. 在 `settings.xml`。

1. 要指定映射的設定檔案的新名稱，請更改 `<settings_map_file>` 標籤 `path/to/config.xml` 的子菜單。

有關詳細資訊，請參閱 [設定遷移模式](../technical-specification.md#settings-migration-mode) 的 [規格](../technical-specification.md)。

## 下一遷移步驟

* [遷移資料](data.md)
