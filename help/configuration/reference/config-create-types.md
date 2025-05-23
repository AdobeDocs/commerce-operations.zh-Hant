---
title: 設定型別
description: 建立或擴充組態型別。
exl-id: 4390c310-b35a-431a-859f-3fd46d8ba6bf
source-git-commit: 4116d0983edc797ce42d24e711fb5ecdbf8fdec9
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 0%

---

# 設定型別

## 擴充組態型別

若要擴充現有的組態型別，您只需在模組中建立組態檔。

例如，若要新增事件觀察者，請建立`app/code/{VendorName}/{ModuleName}/etc/events.xml`並宣告新的觀察者。

由於Commerce中存在事件組態型別，因此載入程式和`events.xsd`驗證結構描述已存在且運作正常。

系統會自動從您的模組收集您的新`events.xml`，並將它與其他模組的其他`events.xml`檔案合併。

## 建立設定型別

若要建立組態型別，您至少必須新增：

- 載入器
- XSD驗證結構
- XML組態檔

例如，若要為新的搜尋伺服器引入配接器，讓擴充功能能夠設定如何在該伺服器中索引其實體，請建立：

- 載入器
- XSD結構描述檔案
- 適當命名的組態檔。 例如，`search.xml`。 系統會讀取此檔案，並針對您的結構描述進行驗證。
- 您工作所需的任何其他類別。

>[!INFO]
>
>如果新模組有`search.xml`檔案，載入時它們會與您的檔案合併。

### 使用範例

若要建立組態型別，請執行下列動作：

1. 建立您的XSD檔案。
1. 建立您的XML檔案。
1. 在`di.xml`中定義您的設定物件。

   以下Magento_Sales模組的[di.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/etc/di.xml)範例說明組態物件的外觀。

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

   - 第一個型別節點會設定Reader的檔案名稱、相關聯的`Converter`和`SchemaLocator`類別。
   - 然後，`pdfConfigDataStorage`虛擬型別節點會將讀取器類別附加至[Magento\Framework\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Data.php)的執行個體。
   - 最後，最後一個型別節點會將該設定資料虛擬型別附加至[Magento\Sales\Model\Order\Pdf\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Order/Pdf/Config.php)類別，用來實際讀取這些[pdf.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/etc/pdf.xml)檔案中的值。

1. 藉由延伸[Magento\Framework\Config\Reader\Filesystem](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php)類別來定義讀取器，並重寫下列引數：

   ```php
   $_idAttributes // Array of node attribute IDs.
   ```

**範例：**

```php
<?php
/**
 * Copyright [first year code created] Adobe
 * All Rights Reserved.
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
>若您想要建立自己的讀取器版本，您可以實作`\Magento\Framework\Config\ReaderInterface`來執行此操作。 檢視[Magento_Analytics設定讀取器](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/ReportXml/Config/Reader.php)

定義讀取器後，使用它來收集、合併、驗證組態檔，並將其轉換為內部陣列表示。

## 驗證設定型別

每個設定檔案都會根據設定型別特定的結構描述進行驗證。 範例：在舊版Commerce中設定於`config.xml`的事件，現在已在`events.xml`中設定。

在影響相同設定型別的多個檔案合併之前（選用）和之後，都可以驗證設定檔案。 除非個別和合併檔案的驗證規則相同，否則您應該提供兩個結構描述來驗證組態檔：

- 用於驗證個人的結構描述
- 用於驗證合併檔案的結構描述

新的設定檔必須搭配XSD驗證結構描述。 XML組態檔及其XSD驗證檔必須具有相同的名稱。

如果您必須為單一XML檔案使用兩個XSD檔案，則結構描述的名稱應該可辨識並且與XML檔案關聯。
如果您有`events.xml`檔案和前`events.xsd`個檔案，合併的`events.xml`檔案的XSD檔案可能命名為`events_merged.xsd`。
若要確保透過適當的XSD檔案驗證XML檔案，您必須將統一資源名稱(URN)新增至XML檔案中的XSD檔案。 例如：

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager:etc/config.xsd">
```

您的IDE可以在執行階段和開發期間驗證您的組態檔。
