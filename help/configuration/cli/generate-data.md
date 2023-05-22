---
title: 生成資料以進行效能測試
description: 瞭解如何生成大量資料以用於效能測試。
feature: Configuration, Orders
exl-id: 2f54701d-88c4-464a-b4dc-56db14d54160
source-git-commit: 403a5937561d82b02fd126c95af3f70b0ded0747
workflow-type: tm+mt
source-wordcount: '749'
ht-degree: 8%

---

# 效能測試資料

使用 [效能工具包](https://github.com/magento/magento2/blob/2.4/setup/performance-toolkit) 或者使用其他工具進行效能測試時，必須生成大量資料，如儲存、類別和產品。

{{file-system-owner}}

## 配置檔案

您可以使用 _配置檔案_ （小型、中型、大型和超大型）。 配置檔案位於 `<magento_root>/setup/performance-toolkit/profiles/<ce|ee>` 的子菜單。

比如說， `/var/www/html/magento2/setup/performance-toolkit/profiles/ce`

下圖顯示了如何使用 _小_ 配置檔案：

![帶生成資料的樣例儲存](../../assets/configuration/generate-data.png)

下表提供了有關資料生成器配置檔案的詳細資訊：小型、中型、大型和超大型。

| 參數 | 小輪廓 | 中檔 | 中型多站點配置檔案 | 大輪廓 | 超大配置檔案 |
| --- | --- | --- | --- | --- | --- |
| `websites` | 1 | 3 | 25 | 5 | 5 |
| `store_groups` | 1 | 3 | 25 | 5 | 5 |
| `store_views` | 1 | 3 | 50 | 5 | 5 |
| `simple_products` | 800 | 24,000 | 4,000 | 300,000 | 600,000 |
| `configurable_products` | 16個，含24個選項 | 640，含24個選項 | 800，帶24個選項，79，帶200個選項 | 8,000，帶24個選項 | 16,000（含24個選項） |
| `product_images` | 每產品100個映像/3個映像 | 每產品1000個映像/3個映像 | 每產品1000個映像/3個映像 | 2000個影像/每個產品3個影像 | 2000個影像/每個產品3個影像 |
| `categories` | 30 | 300 | 100 | 3,000 | 6,000 |
| `categories_nesting_level` | 3 | 3 | 3 | 5 | 5 |
| `catalog_price_rules` | 20 | 20 | 20 | 20 | 20 |
| `catalog_target_rules` | 5 | 5 | 5 | 5 | 5 |
| `cart_price_rules` | 20 | 20 | 20 | 20 | 20 |
| `cart_price_rules_floor` | 2 | 2 | 2 | 2 | 2 |
| `customers` | 200 | 2,000 | 2,000 | 5,000 | 10,000 |
| `tax rates` | 130 | 40,000 | 40,000 | 40,000 | 40,000 |
| `orders` | 80 | 50,000 | 50,000 | 100,000 | 150,000 |

### 運行資料生成器

>[!WARNING]
>
>在運行資料生成器之前，請禁用伺服器上運行的所有cron作業。 禁用cron作業可防止資料生成器執行與活動cron作業衝突的操作，並避免不必要的錯誤。

按本節所述運行命令。 命令運行後，必須 [重新索引所有索引](../cli/manage-indexers.md)。

命令選項：

```bash
bin/magento setup:perf:generate-fixtures <path-to-profile>
```

位置 `<path-to-profile>` 指定配置檔案的絕對檔案系統路徑和名稱。

比如說，

```bash
bin/magento setup:perf:generate-fixtures /var/www/html/magento2/setup/performance-toolkit/profiles/ce/small.xml
```

小型配置檔案的輸出示例：

```terminal
Generating profile with following params:
    |- Websites: 1
    |- Store Groups Count: 1
    |- Store Views Count: 1
    |- Categories: 30
    |- Attribute Sets (Default): 3
    |- Attribute Sets (Extra): 10
    |- Simple products: 800
    |- Configurable products: 0
    |--- 5 products for attribute set "Attribute Set 1"
    |--- 5 products for attribute set "Attribute Set 2"
    |--- 5 products for attribute set "Attribute Set 3"
    |--- 40 products for attribute set "Dynamic Attribute Set 1-24"
    |- Product images: 100, 3 per product
    |- Customers: 200
    |- Cart Price Rules: 20
    |- Catalog Price Rules: 20
    |- Catalog Target Rules: 5
    |- Orders: 80
Generating websites, stores and store views...  done in <time>
Generating categories...  done in <time>
Generating attribute sets...  done in <time>
Generating simple products...  done in <time>
... more ...
```

## 效能夾具

### 管理員用戶

生成管理員用戶。 XML配置檔案節點：

```xml
<!-- Number of admin users -->
<admin_users>{int}</admin_users>
```

### 屬性集

生成具有指定配置的屬性集。 XML配置檔案節點：

```xml
<!-- Number of product attribute sets -->
<product_attribute_sets>{int}</product_attribute_sets>

<!-- Number of attributes per set -->
<product_attribute_sets_attributes>{int}</product_attribute_sets_attributes>

<!-- Number of values per attribute -->
<product_attribute_sets_attributes_values>{int}</product_attribute_sets_attributes_values>
```

### 捆綁產品

生成捆綁產品。 生成的束選擇不會單獨顯示在目錄中。 產品按類別和網站統一分發。 如果  `assign_entities_to_all_websites` 從配置檔案設定為 `1`。 產品分配給所有網站。

XML配置檔案節點：

```xml
<!-- Number of products -->
<bundle_products>{int}</bundle_products>

<!-- Number of options per each product -->
<bundle_products_options>{int}</bundle_products_options>

<!-- Number of simple products per each option -->
<bundle_products_variation>{int}</bundle_products_variation>
```

### 購物車價格規則

生成購物車價格規則。 XML配置檔案節點：

```xml
<!-- Number of cart price rules -->
<cart_price_rules>{int}</cart_price_rules>

<!-- Number of conditions per rule -->
<cart_price_rules_floor>{int}</cart_price_rules_floor>
```

### 目錄價格規則

生成目錄價格規則。 XML配置檔案節點：

```xml
<!-- Number of catalog price rules -->
<catalog_price_rules>{int}</catalog_price_rules>
```

### 類別

生成類別。 如果 `assign_entities_to_all_websites` 設定為 `0`所有類別按根類別均勻分佈；否則，所有類別都分配給一個根類別。

XML配置檔案節點：

```xml
<!-- Number of categories to generate -->
<categories>{int}</categories>

<!-- Nesting level of categories -->
<categories_nesting_level>{int}</categories_nesting_level>
```

### 配置

設定配置欄位的值。 XML配置檔案節點：

```xml
<!-- Config variables and values for change -->
<configs>
    <config>
        <path>{string}</path> <!-- e.g. admin/security/use_form_key -->
        <scope>{string}</scope> <!-- e.g. default -->
        <scopeId>{int}</scopeId>
        <value>{int|string}</value>
    </config>

    <!-- ... more entries ... -->
</configs>
```

### 可配置產品

生成可配置產品。 生成的可配置選項不會單獨顯示在目錄中。 產品按類別和網站統一分發。 如果 `assign_entities_to_all_websites` 設定為 `1`，產品將分配給所有網站。

支援以下XML節點格式：

- 按預設和預定義屬性集分配：

   ```xml
   <!-- Number of configurable products -->
   <configurable_products>{int}</configurable_products>
   ```

- 基於現有屬性集生成產品：

   ```xml
   <configurable_products>
   
       <config>
               <!-- Existing attribute set name -->
               <attributeSet>{string}</attributeSet>
   
               <!-- Configurable sku pattern with %s -->
               <sku>{string}</sku>
   
               <!-- Number of configurable products -->
               <products>{int}</products>
   
               <!-- Category Name. Optional. By default category name from Categories fixture will be used -->
               <category>[{string}]</category>
   
               <!-- Type of Swatch attribute e.g. color|image -->
               <swatches>{string}</swatches>
       </config>
   
   <!-- ... more entries ... -->
   </configurable_products>
   ```

- 基於動態建立的具有指定數量的屬性和選項的屬性集生成產品：

   ```xml
   <configurable_products>
   
       <config>
           <!-- Number of attributes in configurable product -->
           <attributes>{int}</attributes>
   
           <!-- Number of options per attribute -->
           <options>{int}</options>
   
           <!-- Configurable sku pattern with %s -->
           <sku>{string}</sku>
   
           <!-- Number of configurable products -->
           <products>{int}</products>
   
           <!-- Category Name. Optional. By default category name from Categories fixture will be used -->
           <category>[{string}]</category>
   
           <!-- Type of Swatch attribute e.g. color|image -->
           <swatches>{string}</swatches>
       </config>
   
       <!-- ... more entries ... -->
   </configurable_products>
   ```

- 基於動態建立的屬性集生成產品，每個屬性具有指定的配置：

   ```xml
   <configurable_products>
   
       <config>
           <attributes>
               <!-- Configuration for a first attribute -->
               <attribute>
                   <!-- Amount of options per attribute -->
                   <options>{int}</options>
   
                   <!-- Type of Swatch attribute -->
                   <swatches>{string}</swatches>
               </attribute>
   
               <!-- Configuration for a second attribute -->
               <attribute>
                   <!-- Amount of options per attribute -->
                   <options>{int}</options>
               </attribute>
           </attributes>
   
           <!-- Configurable sku pattern with %s -->
           <sku>{string}</sku>
   
           <!-- Number of configurable products -->
           <products>{int}</products>
   
           <!-- Category Name. Optional. By default, the category name from Categories fixture will be used -->
           <category>[{string}]</category>
       </config>
   
       <!-- ... more entries ... -->
   </configurable_products>
   ```

### 客戶

生成客戶。 客戶在所有可用網站上均有正常分發。 除客戶電子郵件、客戶組和客戶地址外，每個客戶都有相同的資料。

XML配置檔案節點：

```xml
<!-- Number of customers to generate -->
<customers>{int}</customers>
```

您可以使用以下XML更改客戶配置：

```xml
<customer-config>
    <!-- Number of addresses per each customer -->
    <addresses-count>{int}</addresses-count>
</customer-config>
```

### 產品映像

生成產品映像。 層代不包括調整大小。

XML配置檔案節點：

```xml
<product-images>
    <!-- Number of images to generate -->
    <images-count>{int}</images-count>

    <!-- Number of images to be assigned per each product -->
    <images-per-product>{int}</images-per-product>
</product-images>
```

### 索引器狀態

更新索引器的狀態。 XML配置檔案節點：

```xml
<indexer>
    <!-- Name of indexer (e.g. catalogrule_product) -->
    <id>{string}</id>
    <set_scheduled>{bool}</set_scheduled>
</indexer>
```

### 訂單

生成具有不同類型訂單物料的可配置數量的訂單。 （可選）為生成的訂單生成無效報價。

XML配置檔案節點：

```xml
<!-- It is necessary to enable quotes for orders -->
<order_quotes_enable>{bool}</order_quotes_enable>

<!-- Min number of simple products per each order -->
<order_simple_product_count_from>{int}</order_simple_product_count_from>

<!-- Max number of simple products per each order -->
<order_simple_product_count_to>{int}</order_simple_product_count_to>

<!-- Min number of configurable products per each order -->
<order_configurable_product_count_from>{int}</order_configurable_product_count_from>

<!-- Max number of configurable products per each order -->
<order_configurable_product_count_to>{int}</order_configurable_product_count_to>

<!-- Min number of big configurable products (with big amount of options) per each order -->
<order_big_configurable_product_count_from>{int}</order_big_configurable_product_count_from>

<!-- Max number of big configurable products (with big amount of options) per each order -->
<order_big_configurable_product_count_to>{int}</order_big_configurable_product_count_to>

<!-- Number of orders to generate -->
<orders>{int}</orders>
```

### 簡單產品

生成簡單產品。 產品按預設和預定義的屬性集分發。 如果在配置檔案中將額外屬性集指定為： `<product_attribute_sets>{int}</product_attribute_sets>`，產品也按附加屬性集分發。

產品按類別和網站統一分發。 如果 `assign_entities_to_all_websites` 設定為 `1`，產品將分配給所有網站。

XML配置檔案節點：

```xml
<!-- Number of simple products to generate -->
<simple_products>{int}</simple_products>
```

### 網站

生成網站。 XML配置檔案節點：

```xml
<!-- Number of websites to be generated -->
<websites>{int}</websites>
```

### 儲存組

生成儲存組(在管理員中稱為 _商店_)。 商店組通常在網站之間分發。

XML配置檔案節點：

```xml
<!-- Number of store groups to be generated -->
<store_groups>{int}</store_groups>
```

### 儲存視圖

生成儲存視圖。 儲存視圖通常分佈在儲存組之間。 XML配置檔案節點：

```xml
<!-- Number of store views to be generated -->
<store_views>{int}</store_views>

<!-- 1 means that all stores will have the same root category, 0 means that all stores will have unique root category -->
<assign_entities_to_all_websites>{0|1}<assign_entities_to_all_websites/>
```

### 稅率

生成稅率。 XML配置檔案節點：

```xml
<!-- Accepts name of CSV file with tax rates (<path to Commerce folder>/setup/src/Magento/Setup/Fixtures/_files) -->
<tax_rates_file>{CSV file name}</tax_rates_file>
```

## 其他配置資訊：

- `<Commerce root dir>/setup/performance-toolkit/config/attributeSets.xml` — 預設屬性集

- `<Commerce root dir>/setup/performance-toolkit/config/customerConfig.xml` — 客戶配置

- `<Commerce root dir>/setup/performance-toolkit/config/description.xml` — 產品完整說明配置

- `<Commerce root dir>/setup/performance-toolkit/config/shortDescription.xml` — 產品簡要說明配置

- `<Commerce root dir>/setup/performance-toolkit/config/searchConfig.xml` — 產品簡要說明和完整說明的配置。 提供此較舊的實現是為了實現向後相容性。

- `<Commerce root dir>/setup/performance-toolkit/config/searchTerms.xml` — 簡短和完整說明的搜索詞數很少

- `<Commerce root dir>/setup/performance-toolkit/config/searchTermsLarge.xml` — 在簡短和完整說明中使用的搜索詞數較多。
