---
title: 設定 [!DNL Data Migration Tool]
description: 瞭解設定 [!DNL Data Migration Tool] 在Magento1和Magento2之間傳輸資料的兩種方法。
exl-id: 273be997-8085-4488-a455-f6005a85b406
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '808'
ht-degree: 0%

---

# 設定[!DNL Data Migration Tool]

安裝[!DNL Data Migration Tool]之後，下列目錄包含對應和組態檔：

* Magento Open Source：
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/opensource-to-opensource`：從Magento Open Source1移轉至Magento Open Source2的設定和指令碼

* Adobe Commerce：
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/opensource-to-commerce`：從Magento Open Source1移轉至Adobe Commerce 2的設定和指令碼
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/commerce-to-commerce`：從Adobe Commerce 1移轉至Adobe Commerce 2的設定和指令碼

上述目錄包含每個支援版本的子目錄。

## 設定移轉

有兩種方法可設定[!DNL Data Migration Tool]：

* 在個別模組中設定[!DNL Data Migration Tool] （建議）
* 變更`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/`目錄中的[!DNL Data Migration Tool]組態。

若要使用原始檔控制來管理您的移轉設定並用於部署，您必須建立個別的模組。
如果您只打算在本機執行[!DNL Data Migration Tool]，可以直接編輯`<your Magento 2 install dir>/vendor/magento/data-migration-tool/`目錄中的檔案。

### 在個別模組中設定移轉

在移轉任何資料之前，您必須建立Magento2模組。

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

1. 將`config.xml.dist`組態檔從[!DNL Data Migration Tool] (`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>`)的適當目錄複製到`<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/<ce or version>/config.xml`檔案中。

   例如，如果您將`Magento 1.9.3.6 Community Edition`移轉至`Magento 2 Open Source`：

   ```bash
   cd <your Magento 2 install dir>
   ```

   ```bash
   cp vendor/magento/data-migration-tool/etc/opensource-to-opensource/1.9.3.6/config.xml.dist app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.3.6/config.xml
   ```

1. 在`config.xml`檔案中，您必須設定M1和M2資料庫的存取詳細資訊以及加密金鑰。

1. 如果您的M1存放區有自訂變更，則應將其餘設定檔案對應至Magento1存放區自訂。 請參閱[使用組態和對應檔案](#migration-config)。

### 在`vendor`資料夾中設定移轉

移轉任何資料之前，您必須從提供的範例建立`config.xml`設定檔。

若要設定[!DNL Data Migration Tool]進行移轉：

1. 以或切換至[檔案系統擁有者](../../installation/prerequisites/file-system/overview.md)的身份登入您的應用程式伺服器。

1. 變更至下列目錄：

   ```bash
   <your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>
   ```

1. 輸入下列命令，從提供的範例建立`config.xml`：

   ```bash
   cp config.xml.dist config.xml
   ```

1. 在文字編輯器中開啟`config.xml`。

1. config.xml檔案至少必須包含M1和M2資料庫的存取詳細資訊以及加密金鑰。

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

   &lt;crypt_key>標籤必須包含值。 您可以在`<key>`標籤中找到它，該標籤位於您Magento1執行個體上的app/etc/local.xml檔案中。

   選用引數：

   * 資料庫使用者密碼： `password=<password>`
   * 資料庫自訂連線埠： `port=<port>`
   * 資料表首碼： `<source_prefix>`， `<dest_prefix>`

   例如，如果您的資料庫擁有者的使用者名稱是密碼為`pass`的`root`，而您在Magento1資料庫中使用前置詞`magento1`，請在`config.xml`中使用下列專案：

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

完成後，將您的變更儲存至`config.xml`並結束文字編輯器。

### 使用TLS通訊協定連線

您也可以使用TLS通訊協定（亦即使用公開/私用密碼編譯金鑰）連線到資料庫。 將下列選擇性屬性新增至`database`元素：

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

## 使用設定和對映檔案

[!DNL Data Migration Tool]使用&#x200B;*對應檔案*&#x200B;來讓您在Magento1和Magento2資料庫之間執行自訂資料庫對應，包括：

* 變更表格名稱

* 變更欄位名稱

* 忽略表格或欄位

* 將欄位的傳輸資料調整為Magento2格式

受支援Magento版本的對應檔案位於`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc`的子目錄中

若要使用對應檔案：

1. 將它們從`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>/`複製到`<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/<ce or version>/`並移除`.dist`副檔名。

1. 更新`config.xml`的`<options>`節點中新複製的檔案的路徑。 更新的路徑應為下列其中一項：

   1. 絕對檔案路徑，例如`/var/www/html/app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.4.1/map.xml`
   1. magento/data-migration-tool模組相對檔案路徑： `etc/opensource-to-opensource/1.9.4.1/map.xml`
   1. 根目錄相對檔案路徑Magento： `app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.4.1/map.xml`

`<Magento 2 dir>/vendor/magento/data-migration-tool/etc`和`<Magento 2 dir>/vendor/magento/data-migration-tool/etc/<ce version>`目錄包含下列組態檔：

即使您大部分時間都在使用`map.xml.dist`檔案，下表仍討論每個對應和其他檔案。

| 對應檔案名稱 | 說明 |
| --- | --- |
| `class-map.xml.dist` | Magento1和Magento2之間類別對應的字典 |
| `config.xml.dist` | 指定Magento1和Magento2資料庫組態、步驟組態和對映檔案連結的主要組態檔 |
| *僅限Adobe Commerce*。`customer-attr-document-groups.xml.dist` | 自訂客戶屬性步驟中使用的表格清單。 |
| *僅限Adobe Commerce*。`customer-attr-map.xml.dist` | 對應自訂客戶屬性步驟中所使用的檔案。 |
| `deltalog.xml.dist` | 包含資料庫常式設定所需的表格清單。 |
| `eav-attribute-groups.xml.dist` | 包含「執行步驟」中所使用的屬性清單。 |
| `eav-document-groups.xml.dist` | 包含執行步驟中所使用的表格清單。 |
| `log-document-groups.xml.dist` | 包含記錄步驟中使用的表格清單。 |
| `map-eav.xml.dist` | EAV步驟中使用的對應檔案。 |
| `map-log.xml.dist` | 記錄對應檔案。 |
| *僅限Adobe Commerce*。`map-sales.xml.dist` | SalesOrder Step中使用的對應檔案。 |
| `map.xml.dist` | 對應步驟所需的對應檔案。 |
| `settings.xml.dist` | 設定移轉組態檔，指定移轉`core_config_data`資料表所需的規則。 |
| `customer-attribute-groups.xml.dist` | 包含用於客戶屬性步驟的屬性清單。 |
| `customer-document-groups.xml.dist` | 包含用於客戶屬性步驟中的表格清單。 |
| `map-customer.xml.dist` | 對應客戶屬性步驟中所使用的檔案。 |
| `order-grids-document-groups.xml.dist` | 包含用於OrderGrids步驟的表格清單。 |
| `map-document-groups.xml.dist` | 定義資料插入時發生重複時更新的欄位 |
| `map-stores.xml.dist` | 對應用於商店步驟的檔案。 |
| `map-tier-price.xml.dist` | 用於層級價格步驟的對映檔案。 |
| *僅限Adobe Commerce*。`visual_merchandiser_map.xml.dist` | VisualMerchandiser步驟中使用的對應檔案。 |
| *僅限Adobe Commerce*。`visual_merchandiser_attribute_groups.xml.dist` | 包含用於VisualMerchandiser步驟的屬性清單。 |
| *僅限Adobe Commerce*。`visual_merchandiser_document_groups.xml.dist` | 包含用於VisualMerchandiser步驟的表格清單。 |

如需詳細資訊，請參閱[[!DNL Data Migration Tool] 技術規格](technical-specification.md)。
