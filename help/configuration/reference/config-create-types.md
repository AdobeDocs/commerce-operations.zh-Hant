---
title: 配置類型
description: 建立或擴充設定類型。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 0%

---


# 配置類型

## 擴充組態類型

若要擴充現有的設定類型，您只需在模組中建立設定檔案即可。

例如，若要新增事件觀察者，請建立 `app/code/{VendorName}/{ModuleName}/etc/events.xml` 並宣佈新的觀察者。

由於事件配置類型存在於商務中，因此載入器和 `events.xsd` 驗證架構已存在且正常運作。

新 `events.xml` 會自動從您的模組收集，並與其他 `events.xml` 其他模組的檔案。

## 建立配置類型

若要建立設定類型，您至少必須新增：

- 載入器
- XSD驗證結構
- XML配置檔案

例如，要為新搜索伺服器引入適配器，使擴展能夠配置其實體在該伺服器中的索引方式，請建立：

- 載入器
- XSD架構檔案
- 名稱適當的配置檔案。 例如， `search.xml`. 系統會根據您的架構讀取和驗證此檔案。
- 您的工作所需的任何其他類。

>[!INFO]
>
>如果新模組有 `search.xml` 檔案時，這些檔案會在載入時與您的檔案合併。

### 使用範例

若要建立設定類型：

1. 建立XSD檔案。
1. 建立XML檔案。
1. 在 `di.xml`.

   以下示例來自Magento_銷售模組的 [di.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/etc/di.xml) 說明設定物件的外觀。

   ```xml
   <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
   
       <type name="Magento\Sales\Model\Order\Pdf\Config\Reader">
           <arguments>
               <argument name="fileName" xsi:type="string">pdf.xml</argument>
               <argument name="converter" xsi:type="object">Magento\Sales\Model\Order\Pdf\Config\Converter</argument>
               <argument name="schemaLocator" xsi:type="object">Magento\Sales\Model\Order\Pdf\Config\SchemaLocator</argument>
           </arguments>
       </type>
   
       <virtualType name="pdfConfigDataStorage" type="Magento\Framework\Config\Data">
           <arguments>
               <argument name="reader" xsi:type="object">Magento\Sales\Model\Order\Pdf\Config\Reader</argument>
               <argument name="cacheId" xsi:type="string">sales_pdf_config</argument>
           </arguments>
       </virtualType>
   
       <type name="Magento\Sales\Model\Order\Pdf\Config">
           <arguments>
               <argument name="dataStorage" xsi:type="object">pdfConfigDataStorage</argument>
           </arguments>
       </type>
   </config>
   ```

   - 第一個類型節點設定Reader的檔案名，與 `Converter` 和 `SchemaLocator` 類別。
   - 然後， `pdfConfigDataStorage` 虛擬類型節點將讀取器類附加到的實例 [Magento\Framework\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Data.php).
   - 最後，最後一個類型節點將該配置資料虛擬類型附加到 [Magento\Sales\Model\Order\Pdf\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Order/Pdf/Config.php) 類別，用於實際讀取 [pdf.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/etc/pdf.xml) 檔案。

1. 通過擴展來定義讀取器 [Magento\Framework\Config\Reader\Filesystem](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php) 類並重寫以下參數：

   ```php
   $_idAttributes // Array of node attribute IDs.
   ```

**範例：**

```php
<?php
/**
 * Copyright © Magento, Inc. All rights reserved.
 * See COPYING.txt for license details.
 */

namespace Vendor\ModuleName\Model\Config;

use Magento\Framework\Config\Reader\Filesystem;

class Reader extends Filesystem
{
    /**
     * List of identifier attributes for merging
     *
     * @var array
     */
    protected $_idAttributes = [
         '</path/to/node_in_your_xml_file>'        => '<identifierAttributeName>',
         '</path/to/other/node_in_your_xml_file>'  => '<identifierAttributeName>',
    ];
}
```

>[!INFO]
>
>如果您偏好建立自己的閱讀器版本，可實作 `\Magento\Framework\Config\ReaderInterface`. 請參閱 [Magento_Analytics設定讀取器](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/ReportXml/Config/Reader.php)

定義讀取器後，使用它來收集、合併、驗證配置檔案，並將其轉換為內部陣清單示。

## 驗證配置類型

每個配置檔案都根據其配置類型特定的架構進行驗證。 範例：事件，在舊版商務中，是在 `config.xml`，現在可在 `events.xml`.

在對影響相同配置類型的多個檔案進行任何合併之前（可選）和之後，都可以驗證配置檔案。 除非個別和合併檔案的驗證規則相同，否則您應提供兩種結構來驗證設定檔：

- 驗證個人的結構
- 驗證合併檔案的結構

新組態檔必須搭配XSD驗證結構。 XML配置檔案及其XSD驗證檔案必須具有相同的名稱。

如果您必須對單個XML檔案使用兩個XSD檔案，則架構的名稱應可識別，並與XML檔案相關聯。
如果您有 `events.xml` 檔案和第一個 `events.xsd` 檔案，合併後的XSD檔案 `events.xml` 檔案可能已命名 `events_merged.xsd`.
要確保通過適當的XSD檔案驗證XML檔案，必須將統一資源名(URN)添加到XML檔案中的XSD檔案。 例如：

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager:etc/config.xsd">
```

IDE可以在運行時和開發期間驗證配置檔案。
