---
title: 產生效能測試資料
description: 瞭解如何產生大量資料以進行Adobe Commerce效能測試。 探索資料產生設定檔和測試策略。
feature: Configuration, Orders
exl-id: 2f54701d-88c4-464a-b4dc-56db14d54160
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '768'
ht-degree: 9%

---

# 效能測試資料

## 設定檔

您可以使用&#x200B;_設定檔_ （小、中、大和特大）調整您建立的資料量。 設定檔位於`<magento_root>/setup/performance-toolkit/profiles/<ce|ee>`目錄中。

例如， `/var/www/html/magento2/setup/performance-toolkit/profiles/ce`

下圖顯示如何使用&#x200B;_小型_&#x200B;設定檔在店面中顯示產品：

![產生資料的店面範例](../../assets/configuration/generate-data.png)

下表提供有關資料產生器設定檔的詳細資訊：小、中、大和特大。

| 引數 | 小型設定檔 | Medium設定檔 | Medium多網站設定檔 | 大型設定檔 | 超大型設定檔 |
| --- | --- | --- | --- | --- | --- |
| `websites` | 1 | 3 | 25 | 5 | 5 |
| `store_groups` | 1 | 3 | 25 | 5 | 5 |
| `store_views` | 1 | 3 | 50 | 5 | 5 |
| `simple_products` | 800 | 24,000 | 4,000 | 300,000 | 600,000 |
| `configurable_products` | 16個，24個選項 | 640搭配24個選項 | 800配備24種選項，79配備200種選項 | 8,000個，含24個選項 | 16,000個，含24個選項 |
| `product_images` | 100個影像/每個產品3個影像 | 1000個影像/每個產品3個影像 | 1000個影像/每個產品3個影像 | 2000個影像/每個產品3個影像 | 2000個影像/每個產品3個影像 |
| `categories` | 30 | 300 | 100 | 3,000 | 6,000 |
| `categories_nesting_level` | 3 | 3 | 3 | 5 | 5 |
| `catalog_price_rules` | 20 | 20 | 20 | 20 | 20 |
| `catalog_target_rules` | 5 | 5 | 5 | 5 | 5 |
| `cart_price_rules` | 20 | 20 | 20 | 20 | 20 |
| `cart_price_rules_floor` | 2 | 2 | 2 | 2 | 2 |
| `customers` | 200 | 2,000 | 2,000 | 5,000 | 10,000 |
| `tax rates` | 130 | 40,000 | 40,000 | 40,000 | 40,000 |
| `orders` | 80 | 50,000 | 50,000 | 100,000 | 150,000 |

### 執行資料產生器

{{file-system-owner}}

>[!WARNING]
>
>在執行資料產生器之前，請停用伺服器上執行的所有cron工作。 停用cron作業可防止資料產生器執行與作用中cron作業衝突的動作，並避免不必要的錯誤。
>
>如果您要在測試效能時使用[!DNL Adobe I/O Events for Adobe Commerce]實作事件，請在訂閱[個事件](https://developer.adobe.com/commerce/extensibility/events/)之前執行此命令。 先訂閱事件可能會導致錯誤。

依照本節所述執行命令。 命令執行後，您必須[重新索引所有索引子](../cli/manage-indexers.md)。

命令選項：

```bash
bin/magento setup:perf:generate-fixtures <path-to-profile>
```

其中`<path-to-profile>`指定設定檔的絕對檔案系統路徑和名稱。

例如，

```bash
bin/magento setup:perf:generate-fixtures /var/www/html/magento2/setup/performance-toolkit/profiles/ce/small.xml
```

小型設定檔的範例輸出：

```
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

## 效能固定裝置

### 管理員使用者

產生管理員使用者。 XML設定檔節點：

```xml
<!-- Number of admin users -->
<admin_users>{int}</admin_users>
```

### 屬性集

使用指定的組態產生屬性集。 XML設定檔節點：

```xml
<!-- Number of product attribute sets -->
<product_attribute_sets>{int}</product_attribute_sets>

<!-- Number of attributes per set -->
<product_attribute_sets_attributes>{int}</product_attribute_sets_attributes>

<!-- Number of values per attribute -->
<product_attribute_sets_attributes_values>{int}</product_attribute_sets_attributes_values>
```

### 套裝產品

產生套件組合產品。 產生的束選取範圍不會單獨顯示在目錄中。 產品會依類別和網站均勻分佈。 如果設定檔中的`assign_entities_to_all_websites`設定為`1`。 產品會指派給所有網站。

XML設定檔節點：

```xml
<!-- Number of products -->
<bundle_products>{int}</bundle_products>

<!-- Number of options per each product -->
<bundle_products_options>{int}</bundle_products_options>

<!-- Number of simple products per each option -->
<bundle_products_variation>{int}</bundle_products_variation>
```

### 購物車價格規則

產生購物車價格規則。 XML設定檔節點：

```xml
<!-- Number of cart price rules -->
<cart_price_rules>{int}</cart_price_rules>

<!-- Number of conditions per rule -->
<cart_price_rules_floor>{int}</cart_price_rules_floor>
```

### 目錄價格規則

產生型錄價格規則。 XML設定檔節點：

```xml
<!-- Number of catalog price rules -->
<catalog_price_rules>{int}</catalog_price_rules>
```

### 類別

產生類別。 如果`assign_entities_to_all_websites`設為`0`，則所有類別會均勻分佈於每個根類別；否則，所有類別都會指派給一個根類別。

XML設定檔節點：

```xml
<!-- Number of categories to generate -->
<categories>{int}</categories>

<!-- Nesting level of categories -->
<categories_nesting_level>{int}</categories_nesting_level>
```

### 設定

設定欄位的值。 XML設定檔節點：

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

### 可設定的產品

產生可設定的產品。 產生的可設定選項不會在目錄中個別顯示。 產品會依類別和網站均勻分佈。 如果`assign_entities_to_all_websites`設定為`1`，則會將產品指派給所有網站。

支援下列XML節點格式：

- 依預設和預先定義屬性集的分佈：

  ```xml
  <!-- Number of configurable products -->
  <configurable_products>{int}</configurable_products>
  ```

- 根據現有屬性集產生產品：

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

- 根據以指定數量的屬性和選項動態建立的屬性集來產生產品：

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

- 根據每個屬性各自指定組態，以動態建立的屬性集來產生產品：

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

產生客戶。 客戶在所有可用網站上皆為正常分佈。 每個客戶都有相同的資料，但客戶電子郵件、客戶群組和客戶地址除外。

XML設定檔節點：

```xml
<!-- Number of customers to generate -->
<customers>{int}</customers>
```

您可以使用下列XML來變更客戶組態：

```xml
<customer-config>
    <!-- Number of addresses per each customer -->
    <addresses-count>{int}</addresses-count>
</customer-config>
```

### 產品影像

產生產品影像。 產生不包括調整大小。

XML設定檔節點：

```xml
<product-images>
    <!-- Number of images to generate -->
    <images-count>{int}</images-count>

    <!-- Number of images to be assigned per each product -->
    <images-per-product>{int}</images-per-product>
</product-images>
```

### 索引子狀態

更新索引器的狀態。 XML設定檔節點：

```xml
<indexer>
    <!-- Name of indexer (e.g. catalogrule_product) -->
    <id>{string}</id>
    <set_scheduled>{bool}</set_scheduled>
</indexer>
```

### 訂購

產生具有不同訂單料號型態的可設定數量之訂單。 選擇性地為產生的訂單產生無效報價單。

XML設定檔節點：

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

產生簡單產品。 產品會根據預設和預先定義的屬性集進行分配。 如果在設定檔中指定額外的屬性集為： `<product_attribute_sets>{int}</product_attribute_sets>`，產品也會依額外的屬性集分配。

產品會依類別和網站均勻分佈。 如果`assign_entities_to_all_websites`設定為`1`，則會將產品指派給所有網站。

XML設定檔節點：

```xml
<!-- Number of simple products to generate -->
<simple_products>{int}</simple_products>
```

### 網站

產生網站。 XML設定檔節點：

```xml
<!-- Number of websites to be generated -->
<websites>{int}</websites>
```

### 存放區群組

產生商店群組（在管理員中稱為&#x200B;_商店_）。 商店群組通常在網站之間分配。

XML設定檔節點：

```xml
<!-- Number of store groups to be generated -->
<store_groups>{int}</store_groups>
```

### 存放區檢視

產生存放區檢視。 存放區檢視通常在存放區群組之間分配。 XML設定檔節點：

```xml
<!-- Number of store views to be generated -->
<store_views>{int}</store_views>

<!-- 1 means that all stores will have the same root category, 0 means that all stores will have unique root category -->
<assign_entities_to_all_websites>{0|1}<assign_entities_to_all_websites/>
```

### 稅率

產生稅率。 XML設定檔節點：

```xml
<!-- Accepts name of CSV file with tax rates (<path to Commerce folder>/setup/src/Magento/Setup/Fixtures/_files) -->
<tax_rates_file>{CSV file name}</tax_rates_file>
```

## 其他設定資訊：

- `<Commerce root dir>/setup/performance-toolkit/config/attributeSets.xml` — 預設屬性集

- `<Commerce root dir>/setup/performance-toolkit/config/customerConfig.xml` — 客戶組態

- `<Commerce root dir>/setup/performance-toolkit/config/description.xml` — 產品完整說明設定

- `<Commerce root dir>/setup/performance-toolkit/config/shortDescription.xml` — 產品簡短說明設定

- `<Commerce root dir>/setup/performance-toolkit/config/searchConfig.xml` — 產品的設定簡短且完整說明。 提供此舊版實作是為了回溯相容性。

- `<Commerce root dir>/setup/performance-toolkit/config/searchTerms.xml` — 搜尋字詞數量較少，提供簡短且完整的說明

- `<Commerce root dir>/setup/performance-toolkit/config/searchTermsLarge.xml` — 較多的搜尋字詞，以用作簡短且完整的說明。
