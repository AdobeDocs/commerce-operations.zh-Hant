---
title: 配置 [!DNL Data Migration Tool]
description: 瞭解配置 [!DNL Data Migration Tool] 在Magento1和Magento2之間傳輸資料。
exl-id: 273be997-8085-4488-a455-f6005a85b406
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '789'
ht-degree: 0%

---

# 配置 [!DNL Data Migration Tool]

安裝後 [!DNL Data Migration Tool]，以下目錄包含映射和配置檔案：

* Magento Open Source:
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/opensource-to-opensource`:用於從Magento Open Source1遷移到Magento Open Source2的配置和指令碼

* Adobe Commerce:
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/opensource-to-commerce`:用於從Magento Open Source1遷移到Adobe Commerce2的配置和指令碼
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/commerce-to-commerce`:用於從Adobe Commerce1遷移到Adobe Commerce2的配置和指令碼

前面的目錄包含每個受支援版本的子目錄。

## 配置遷移

有兩種方法可配置 [!DNL Data Migration Tool]:

* 配置 [!DNL Data Migration Tool] 在單獨的模組中（推薦）
* 更改 [!DNL Data Migration Tool] 配置 `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/` 的子菜單。

要使用原始碼管理來管理遷移配置並將其用於部署，必須建立單獨的模組。
如果你計畫 [!DNL Data Migration Tool] 僅在本地，您可以編輯 `<your Magento 2 install dir>/vendor/magento/data-migration-tool/` 的子菜單。

### 在單獨的模組中配置遷移

遷移任何資料之前，必須建立Magento2模組。

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

1. 複製 `config.xml.dist` 的相應目錄下的配置檔案 [!DNL Data Migration Tool] (`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>`) `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/<ce or version>/config.xml` 的子菜單。

   例如，如果您 `Magento 1.9.3.6 Community Edition` 至 `Magento 2 Open Source`:

   ```bash
   cd <your Magento 2 install dir>
   ```

   ```bash
   cp vendor/magento/data-migration-tool/etc/opensource-to-opensource/1.9.3.6/config.xml.dist app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.3.6/config.xml
   ```

1. 在 `config.xml` 檔案，必須將訪問詳細資訊設定為M1和M2資料庫和加密密鑰。

1. 如果M1儲存有自定義更改，則應將其餘配置檔案映射到Magento1儲存自定義。 請參閱 [使用配置和映射檔案](#migration-config)。

### 配置遷移 `vendor` 資料夾

遷移任何資料之前，必須建立 `config.xml` 提供的示例中的配置檔案。

配置 [!DNL Data Migration Tool] 對於遷移：

1. 以或切換到的應用程式伺服器 [檔案系統所有者](../../installation/prerequisites/file-system/overview.md)。

1. 更改到以下目錄：

   ```bash
   <your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>
   ```

1. 輸入以下命令以建立 `config.xml` 從提供的示例中：

   ```bash
   cp config.xml.dist config.xml
   ```

1. 開啟 `config.xml` 的子菜單。

1. config.xml檔案至少必須包含對M1和M2資料庫和加密密鑰的訪問詳細資訊。

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

   的 &lt;crypt_key> 標籤必須包含值。 你可以在 `<key>` 標籤，位於Magento1實例的app/etc/local.xml檔案中。

   可選參數：

   * 資料庫用戶密碼： `password=<password>`
   * 資料庫自定義埠： `port=<port>`
   * 表前置詞： `<source_prefix>`。 `<dest_prefix>`

   例如，如果資料庫所有者的用戶名是 `root` 帶密碼 `pass` 你用前置詞 `magento1` 在Magento1資料庫中，使用 `config.xml`:

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

完成後，將更改保存到 `config.xml` 並退出文本編輯器。

### 使用TLS協定連接

您還可以使用TLS協定（即使用公共/私有加密密鑰）連接到資料庫。 將以下可選屬性添加到 `database` 元素：

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

的 [!DNL Data Migration Tool] 使用 *映射檔案* 使您能夠在Magento1和Magento2資料庫之間執行自定義資料庫映射，包括：

* 更改表名

* 更改欄位名稱

* 忽略表或欄位

* 將欄位的資料傳輸適應於Magento2格式

支援的Magento版本的映射檔案位於 `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc`

要使用映射檔案：

1. 從 `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>/` 至 `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/<ce or version>/` 並刪除 `.dist` 擴展。

1. 更新中新複製檔案的路徑 `<options>` 節點 `config.xml`。 更新的路徑應為下列路徑之一：

   1. 絕對檔案路徑，e。g `/var/www/html/app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.4.1/map.xml`
   1. magento/data migration-tool模組相對檔案路徑： `etc/opensource-to-opensource/1.9.4.1/map.xml`
   1. Magento根相對檔案路徑： `app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.4.1/map.xml`

的 `<Magento 2 dir>/vendor/magento/data-migration-tool/etc` 和 `<Magento 2 dir>/vendor/magento/data-migration-tool/etc/<ce version>` 目錄包含以下配置檔案：

即使你和 `map.xml.dist` 檔案，下表將討論每個映射和其他檔案。

| 映射檔案名 | 說明 |
| --- | --- |
| `class-map.xml.dist` | Magento1和Magento2之間類映射的字典 |
| `config.xml.dist` | 主配置檔案，指定Magento1和Magento2資料庫配置、步驟配置以及指向映射檔案的連結 |
| *僅Adobe Commerce*。 `customer-attr-document-groups.xml.dist` | 自定義客戶屬性步驟中使用的表的清單。 |
| *僅Adobe Commerce*。 `customer-attr-map.xml.dist` | 映射在自定義客戶屬性步驟中使用的檔案。 |
| `deltalog.xml.dist` | 包含資料庫常式設定所需的表清單。 |
| `eav-attribute-groups.xml.dist` | 包含在Eav步驟中使用的屬性清單。 |
| `eav-document-groups.xml.dist` | 包含在Eav步驟中使用的表的清單。 |
| `log-document-groups.xml.dist` | 包含日誌步驟中使用的表的清單。 |
| `map-eav.xml.dist` | 在EAV步驟中使用的映射檔案。 |
| `map-log.xml.dist` | 日誌映射檔案。 |
| *僅Adobe Commerce*。 `map-sales.xml.dist` | 映射在SalesOrder步驟中使用的檔案。 |
| `map.xml.dist` | 映射步驟需要映射檔案。 |
| `settings.xml.dist` | 設定遷移配置檔案，指定遷移所需的規則 `core_config_data` 的子菜單。 |
| `customer-attribute-groups.xml.dist` | 包含在客戶屬性步驟中使用的屬性清單。 |
| `customer-document-groups.xml.dist` | 包含在「客戶屬性」步驟中使用的表的清單。 |
| `map-customer.xml.dist` | 映射在「客戶屬性」步驟中使用的檔案。 |
| `order-grids-document-groups.xml.dist` | 包含在OrderGrids步驟中使用的表的清單。 |
| `map-document-groups.xml.dist` | 定義在資料插入時發生複製時更新的欄位 |
| `map-stores.xml.dist` | 在儲存步驟中使用的映射檔案。 |
| `map-tier-price.xml.dist` | 映射層價格步驟中使用的檔案。 |
| *僅Adobe Commerce*。 `visual_merchandiser_map.xml.dist` | 在VisualStlocker步驟中使用的映射檔案。 |
| *僅Adobe Commerce*。 `visual_merchandiser_attribute_groups.xml.dist` | 包含在VisualStlocker步驟中使用的屬性清單。 |
| *僅Adobe Commerce*。 `visual_merchandiser_document_groups.xml.dist` | 包含在VisualStlocker步驟中使用的表的清單。 |

您可以參考 [[!DNL Data Migration Tool] 技術規格](technical-specification.md) 的子菜單。
