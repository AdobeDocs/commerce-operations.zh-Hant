---
title: 設定 [!DNL Data Migration Tool]
description: 了解設定 [!DNL Data Migration Tool] 在Magento1和Magento2之間傳輸資料。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '792'
ht-degree: 0%

---


# 設定 [!DNL Data Migration Tool]

安裝 [!DNL Data Migration Tool]，下列目錄包含映射和配置檔案：

* Magento Open Source:
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/opensource-to-opensource`:從Magento Open Source1移轉至Magento Open Source2的設定和指令碼

* Adobe Commerce:
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/opensource-to-commerce`:從Magento Open Source1移轉至Adobe Commerce 2的設定和指令碼
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/commerce-to-commerce`:從Adobe Commerce 1移轉至Adobe Commerce 2的設定和指令碼

前面的目錄包含每個支援版本的子目錄。

## 設定移轉

有兩種方式可設定 [!DNL Data Migration Tool]:

* 設定 [!DNL Data Migration Tool] （建議）
* 變更 [!DNL Data Migration Tool] 設定 `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/` 目錄。

要使用原始碼控制來管理遷移配置並將其用於部署，必須建立單獨的模組。
如果您打算執行 [!DNL Data Migration Tool] 僅在本機，您可以在 `<your Magento 2 install dir>/vendor/magento/data-migration-tool/` 目錄。

### 在個別模組中設定移轉

移轉任何資料之前，您必須建立Magento2模組。

1. 建立Magento2模組。

   * `<your Magento 2 install dir>/app/code/Vendor/Migration/composer.json`

   ```json
   {
       "name": "vendor/migration",
       "description": "Providing config for migration",
       "config": {
           "sort-packages": true
       },
       "require": {
           "magento/framework": "*",
           "magento/data-migration-tool": "*"
       },
       "type": "magento2-module",
       "autoload": {
           "files": [
               "registration.php"
           ],
           "psr-4": {
               "Vendor\\Migration\\": ""
           }
       },
       "version": "1.0.0"
   }
   ```

   * `<your Magento 2 install dir>/app/code/Vendor/Migration/registration.php`

   ```php
   <?php
   
   \Magento\Framework\Component\ComponentRegistrar::register(
       \Magento\Framework\Component\ComponentRegistrar::MODULE,
       'Vendor_Migration',
       __DIR__
   );
   ```

   * `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/module.xml`

   ```xml
   <?xml version="1.0"?>
   
   <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
           xsi:noNamespaceSchemaLocation="urn:magento:framework:Module/etc/module.xsd">
       <module name="Vendor_Migration" setup_version="1.0.0">
           <sequence>
               <module name="Magento_DataMigrationTool"/>
           </sequence>
       </module>
   </config>
   ```

1. 複製 `config.xml.dist` 配置檔案(位於 [!DNL Data Migration Tool] (`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>`)進入 `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/<ce or version>/config.xml` 檔案。

   例如，若您移轉 `Magento 1.9.3.6 Community Edition` to `Magento 2 Open Source`:

   ```bash
   cd <your Magento 2 install dir>
   ```

   ```bash
   cp vendor/magento/data-migration-tool/etc/opensource-to-opensource/1.9.3.6/config.xml.dist app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.3.6/config.xml
   ```

1. 在 `config.xml` 檔案中，必須將訪問詳細資訊設定為M1和M2資料庫和加密密鑰。

1. 如果您的M1儲存有自訂變更，您應將其餘的設定檔案對應至您的Magento1儲存自訂。 請參閱 [使用配置和映射檔案](#migration-config).

### 在中設定移轉 `vendor` 資料夾

移轉任何資料前，您必須先建立 `config.xml` 組態檔。

若要設定 [!DNL Data Migration Tool] 針對移轉：

1. 以 [檔案系統所有者](../../installation/prerequisites/file-system/overview.md).

1. 更改到以下目錄：

   ```bash
   <your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>
   ```

1. 輸入以下命令以建立 `config.xml` 從提供的範例：

   ```bash
   cp config.xml.dist config.xml
   ```

1. 開啟 `config.xml` 在文字編輯器中。

1. 至少，config.xml檔案必須包含對M1和M2資料庫和加密密鑰的訪問詳細資訊。

   ```xml
   <source>
      <database host="127.0.0.1" name="magento1" user="root"/>
   </source>
   <destination>
      <database host="127.0.0.1" name="magento2" user="root"/>
   </destination>
   <options>
      <crypt_key />
   </options>
   ```

   此 &lt;crypt_key> 標籤必須包含值。 您可以在 `<key>` 標籤，此標籤位於Magento1例項的app/etc/local.xml檔案中。

   可選參數：

   * 資料庫用戶密碼： `password=<password>`
   * 資料庫自定義埠： `port=<port>`
   * 表前置詞： `<source_prefix>`, `<dest_prefix>`

   例如，如果資料庫所有者的用戶名為 `root` 使用密碼 `pass` 你用首碼 `magento1` 在Magento1資料庫中，在 `config.xml`:

   ```xml
   <source>
      <database host="127.0.0.1" name="magento1" user="root" password="pass"/>
   </source>
   <destination>
      <database host="127.0.0.1" name="magento2" user="root" password="pass"/>
   </destination>
   <options>
      <source_prefix>magento1</source_prefix>
      <crypt_key>f3e25abe619dae2387df9fs594f01985</crypt_key>
   </options>
   ```

完成後，將變更儲存至 `config.xml` 並退出文字編輯器。

### 使用TLS通訊協定連線

您也可以使用TLS通訊協定（即使用公開/私用密鑰）連線至資料庫。 將下列選用屬性新增至 `database` 元素：

* `ssl_ca`
* `ssl_cert`
* `ssl_key`

例如：

```xml
<source>
    <database host="localhost" name="magento1" user="root" ssl_ca="/path/to/file" ssl_cert="/path/to/file" ssl_key="/path/to/file"/>
</source>
<destination>
    <database host="localhost" name="magento2" user="root" ssl_ca="/path/to/file" ssl_cert="/path/to/file" ssl_key="/path/to/file"/>
</destination>
```

## 使用配置和映射檔案

此 [!DNL Data Migration Tool] uses *映射檔案* 若要讓您在Magento1和Magento2資料庫之間執行自訂資料庫對應，包括：

* 更改表名

* 更改欄位名稱

* 忽略表或欄位

* 調整欄位的資料傳輸以Magento2格式

支援Magento版本的對應檔案位於 `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc`

要使用映射檔案：

1. 複製 `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>/` to `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/<ce or version>/` 並移除 `.dist` [擴充功能](https://glossary.magento.com/extension).

1. 更新新複製檔案的路徑，位於 `<options>` 節點 `config.xml`. 更新的路徑應為下列其中一項：

   1. 絕對檔案路徑，e.g. `/var/www/html/app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.4.1/map.xml`
   1. magento/data-migration-tool模組相對檔案路徑： `etc/opensource-to-opensource/1.9.4.1/map.xml`
   1. Magento根相對檔案路徑： `app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.4.1/map.xml`

此 `<Magento 2 dir>/vendor/magento/data-migration-tool/etc` 和 `<Magento 2 dir>/vendor/magento/data-migration-tool/etc/<ce version>` 目錄包含下列組態檔：

即使您使用 `map.xml.dist` 檔案中，下表主要討論每個映射和其他檔案。

| 映射檔案名 | 說明 |
| --- | --- |
| `class-map.xml.dist` | Magento1和Magento2的類映射字典 |
| `config.xml.dist` | 指定Magento1和Magento2資料庫配置、步驟配置以及映射檔案的連結的主配置檔案 |
| *僅限Adobe Commerce*. `customer-attr-document-groups.xml.dist` | 自訂客戶屬性步驟中使用的表格清單。 |
| *僅限Adobe Commerce*. `customer-attr-map.xml.dist` | 「自訂客戶屬性」步驟中使用的對應檔案。 |
| `deltalog.xml.dist` | 包含資料庫常式設定所需的表清單。 |
| `eav-attribute-groups.xml.dist` | 包含Eav步驟中使用的屬性清單。 |
| `eav-document-groups.xml.dist` | 包含在Eav步驟中使用的表清單。 |
| `log-document-groups.xml.dist` | 包含在日誌步驟中使用的表清單。 |
| `map-eav.xml.dist` | EAV步驟中使用的映射檔案。 |
| `map-log.xml.dist` | 日誌映射檔案。 |
| *僅限Adobe Commerce*. `map-sales.xml.dist` | 映射用於SalesOrder步驟的檔案。 |
| `map.xml.dist` | 映射步驟所需的映射檔案。 |
| `settings.xml.dist` | 設定遷移配置檔案，指定遷移所需的規則 `core_config_data` 表格。 |
| `customer-attribute-groups.xml.dist` | 包含客戶屬性步驟中使用的屬性清單。 |
| `customer-document-groups.xml.dist` | 包含客戶屬性步驟中使用的表格清單。 |
| `map-customer.xml.dist` | 對應用於客戶屬性步驟的檔案。 |
| `order-grids-document-groups.xml.dist` | 包含OrderGrids步驟中使用的表清單。 |
| `map-document-groups.xml.dist` | 定義在資料插入發生重複時會更新哪些欄位 |
| `map-stores.xml.dist` | 映射儲存步驟中使用的檔案。 |
| `map-tier-price.xml.dist` | 映射用於層價步驟的檔案。 |
| *僅限Adobe Commerce*. `visual_merchandiser_map.xml.dist` | 用於VisualStlicer步驟的映射檔案。 |
| *僅限Adobe Commerce*. `visual_merchandiser_attribute_groups.xml.dist` | 包含VisualStlicer步驟中使用的屬性清單。 |
| *僅限Adobe Commerce*. `visual_merchandiser_document_groups.xml.dist` | 包含VisualStlicer步驟中使用的表清單。 |

您可以指 [[!DNL Data Migration Tool] 技術規範](technical-specification.md) 以取得更多詳細資訊。
