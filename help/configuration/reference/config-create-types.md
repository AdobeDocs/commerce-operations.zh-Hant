---
title: 配置類型
description: 建立或擴展配置類型。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '597'
ht-degree: 0%

---


# 配置類型

## 擴展配置類型

要擴展現有配置類型，您只需在 [模組](https://glossary.magento.com/module)。

例如，要添加事件觀察器，請建立 `app/code/{VendorName}/{ModuleName}/etc/events.xml` 並宣佈新的觀察員。

由於事件配置類型存在於Commerce中，因此載入器和 `events.xsd` 驗證架構已存在且正常。

您的新 `events.xml` 自動從您的模組中收集並與其他模組合併 `events.xml` 檔案。

## 建立配置類型

要建立配置類型，必須至少添加：

- 裝載機
- XSD驗證架構
- XML配置檔案

例如， [適配器](https://glossary.magento.com/adapter) 對於新的搜索伺服器，建立：

- 裝載機
- XSD架構檔案
- 一個名稱正確的配置檔案。 比如說， `search.xml`。 此檔案將根據您的架構進行讀取和驗證。
- 您的工作所需的任何其他類。

>[!INFO]
>
>如果新模組具有 `search.xml` 檔案，它們在載入時與檔案合併。

### 示例

要建立配置類型：

1. 建立XSD檔案。
1. 建立XML檔案。
1. 在中定義配置對象 `di.xml`。

   Magento_銷售模組的以下示例 [di.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/etc/di.xml) 說明了配置對象的外觀。

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

   - 第一種類型節點設定Reader的檔案名，與 `Converter` 和 `SchemaLocator` 類。
   - 然後， `pdfConfigDataStorage` 虛擬類型節點將讀取器類附加到的實例 [Magento\Framework\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Data.php)。
   - 最後，最後一個類型節點將配置資料虛擬類型附加到 [Magento\Sales\Model\Order\Pdf\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Order/Pdf/Config.php) 類，用於實際讀取 [pdf.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/etc/pdf.xml) 的子菜單。

1. 通過擴展定義讀取器 [Magento\Framework\Config\Reader\Filesystem](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php) 類並重寫以下參數：

   ```php
   $_idAttributes // Array of node attribute IDs.
   ```

**示例：**

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
>如果您希望建立您自己的閱讀器版本，可以通過實施 `\Magento\Framework\Config\ReaderInterface`。 請參閱 [Magento分析配置讀取器](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/ReportXml/Config/Reader.php)

定義讀取器後，使用它收集、合併、驗證配置檔案並將其轉換為內部陣清單示法。

## 驗證配置類型

每個配置檔案都根據特定於其配置類型的架構進行驗證。 示例：事件，在早期的Commerce版本中，這些事件在 `config.xml`，現在在中配置 `events.xml`。

配置檔案可以在影響相同配置類型的多個檔案合併之前（可選）和之後都進行驗證。 除非單個檔案和合併檔案的驗證規則相同，否則您應提供兩個用於驗證配置檔案的方案：

- 用於驗證個人的方案
- 驗證合併檔案的架構

新配置檔案必須與XSD驗證架構相伴。 XML配置檔案及其XSD驗證檔案必須具有相同的名稱。

如果必須將兩個XSD檔案用於單個XML檔案，則架構的名稱應可識別並與XML檔案關聯。
如果你有 `events.xml` 檔案和第一個 `events.xsd` 檔案，合併後的XSD檔案 `events.xml` 可以命名檔案 `events_merged.xsd`。
要確保通過適當的XSD檔案驗證XML檔案，必須將統一資源名稱(URN)添加到XML檔案中的XSD檔案。 例如：

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager:etc/config.xsd">
```

IDE可以在運行時和開發期間驗證配置檔案。
