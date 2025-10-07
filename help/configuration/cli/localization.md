---
title: 翻譯字典和語言套件
description: 瞭解如何產生Adobe Commerce的翻譯字典和建置語言套件。 探索當地語系化及多語言商店設定。
exl-id: dd27ccdd-158d-40a6-a2e2-563857820ae9
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '1441'
ht-degree: 0%

---

# 本地化

{{file-system-owner}}

Commerce翻譯可讓您針對多個地區和市場自訂您的商店並將其當地化，方法如下：

- **翻譯字典**，這是自訂或翻譯&#x200B;_某些_&#x200B;單字和短語的便利方式，例如自訂模組或佈景主題的單字和短語。
- **語言套件**，可讓您在Commerce應用程式中翻譯&#x200B;_任何或全部_&#x200B;個字詞和片語。

請參閱[翻譯概觀]。

## 產生翻譯字典

您可以產生[翻譯字典]，以自訂現有的字串、翻譯自訂模組中的單字與片語、本地化佈景主題或建立語言套件。

若要開始翻譯，請使用命令產生字典CSV檔案，其中包含所有現有短語和單字的收集清單。

若要產生字典並開始翻譯：

1. 使用翻譯集合指令，從已啟用的元件中擷取可翻譯的字詞和片語。 內容擷取至CSV檔案。
1. 翻譯現有的字詞和片語。 您可以視需要新增其他自訂詞語。

   您可以選擇使用翻譯的字典：

1. 您可以將翻譯字典封裝成語言套件，然後提供套件給Commerce商店管理員。

1. 在管理員中，商店管理員[設定翻譯]。

命令選項：

```bash
bin/magento i18n:collect-phrases [-o|--output="<csv file path and name>"] [-m|--magento] <path to directory to translate>
```

下表說明引數和值：

| 引數 | 值 | 必填？ |
|--- |--- |--- |
| `<path to directory to translate>` | 具有可翻譯程式碼的目錄的路徑；換句話說，就是具有要翻譯之片語的PHP、PHTML或XML檔案。<br><br>工具會從您輸入的路徑開始搜尋，並搜尋它包含的所有檔案和子目錄。<br><br>如果您使用`-m --magento`，請勿使用此引數。 | 是（字典）、否（套件）。 |
| `-m --magento` | 從此翻譯字典建立語言套件時需要。 若已使用，會搜尋包含bin/magento的目錄。 此選項會將主題或模組新增至字典中的每一行。<br><br>範例如下：<br><br>「找不到專案」、「找不到專案」、模組、Magento_Wishlist | 否 |
| `-o --output="<path>"` | 指定要建立的翻譯字典CSV檔案的絕對檔案系統路徑和檔案名稱。 您輸入的值區分大小寫。 CSV檔案的名稱必須與地區設定名稱（包括字元的大小寫）完全相符。<br><br>如果省略此引數，輸出會導向至stdout。 | 否 |

>[!INFO]
>
>若要從翻譯字典建立語言套件，您&#x200B;_必須_&#x200B;使用`-m|--magento`選項。

### 翻譯指南

翻譯字詞和短語時，請遵循下列准則：

- 僅變更第二欄的內容。 將短語從英文(`US`)翻譯成所要的語言。
- 建立地區設定的字典時，請使用預設的Commerce字串。
- 翻譯時，請注意預留位置： `%1`， `%2`

Commerce使用預留位置來插入內容值；它們&#x200B;_不_&#x200B;用於翻譯。 例如：

```text
Product '%1' has been added to shopping cart.
```

填入一個值：

```text
Product 'Multimeter-2000' has been added to shopping cart.
```

產生的片語必須至少包含每個預留位置之一。 例如，假設原始片語中有從`%1`到`%3`的預留位置。 翻譯可以有任意順序的這些預留位置，但必須至少有一個`%1`、`%2`和`%3`出現。 轉譯不能包含原始值中不存在的預留位置值（例如，`%4`、`%5`等）。

翻譯片語的範例：

```text
"Buy %1 for %2 (%3 incl. tax) each","Compre %1 por %2 (%3 incl. imposto) cada"
```

## 建立語言套件

與翻譯字典相反，您可以使用語言套件翻譯Commerce應用程式中的任何或所有字詞和片語。 您可以使用翻譯字典來翻譯特定元件（例如模組或主題）。 [進一步瞭解語言套件]。

本節將討論如何建立語言套件，其會將CSV檔案寫入模組和主題。 若要建立語言套件，您必須執行下列各節中討論的工作：

1. [收集並翻譯字詞和短語](#generate-a-translation-dictionary)。 （`--magento`引數為必要項。）
1. [執行語言套件命令](#run-the-language-package-command)。
1. [建立目錄和檔案](#create-directories-and-files)。
1. （選擇性。） [為語言](#configure-multiple-packages-for-a-language)設定多個套件。

### 執行語言套件命令

命令使用方式：

```bash
bin/magento i18n:pack [-m|--mode={merge|replace}] [-d|--allow-duplicates] <source> <locale>
```

下表說明語言套裝程式命令的引數和值：

| 引數 | 值 | 必填？ |
|--- |--- |--- |
| `<source>` | CSV檔案的絕對檔案系統路徑和檔案名稱，該檔案包含劃分成語言套件所需的合併翻譯字典和中繼資訊。<br><br>使用[`bin/magento i18n:collect-phrases`](#config-cli-subcommands-xlate-dict-dict)建立CSV檔案，然後建立語言套件，如[建立目錄和檔案](#m2devgde-xlate-files)中所述。 | 是 |
| `<locale>` | [ISO 639-1] （語言）和[ISO 3166] （國家/地區）識別碼，用來作為所有產生的CSV檔案的檔案名稱。 範例： `de_DE`、`pt_PT`、`pt_BR`。 | 是 |
| `-m --mode` | 如果目標檔案存在，請指定取代現有的語言套件還是與新的語言套件合併。 合併會覆寫任何現有的短語，並加入新的短語。<br><br>值：合併或取代（預設）。 | 否 |
| `-d --allow-duplicates` | 包含此選項以允許語言套件中出現重複專案。 否則，如果命令在多個包含不同翻譯的專案中遇到相同的片語，則會失敗並出現錯誤。 | 否 |

### 建立目錄和檔案

語言套件位於Commerce檔案系統`app/i18n/<VendorName>`下的目錄，包含下列內容：

- 必要的授權檔案
- `composer.json`
- `registration.php`註冊[語言套件的]
- [`language.xml`](#language-package-languagexml)中繼資訊檔案

>[!INFO]
>
>您必須將整個路徑變為小寫。 例如，請參閱[`de_de`]。

若要建立這些檔案：

1. 在`app/i18n`下建立目錄。

   例如，Commerce語言套件位於`app/i18n/magento`

1. 新增必要的許可證檔案。
1. 新增指定語言套件相依性的[`composer.json`]。
1. 向[`registration.php`]註冊語言套件
1. 新增`language.xml`中繼資訊檔案，如下節所述。

#### 語言套件語言.xml

在`language.xml`組態檔中宣告語言套件時，您必須指定此套件的語言繼承順序。

語言繼承可讓您根據名為&#x200B;_parent_&#x200B;的現有翻譯，建立名為&#x200B;_子項_&#x200B;的翻譯。 子翻譯會覆寫父翻譯。 但是，如果子翻譯無法上傳或顯示，或缺少短語或單字，Commerce會使用父級地區設定。 [語言套件繼承的範例](#example-of-language-inheritance)。

若要宣告套件，請指定下列資訊：

```xml
<?xml version="1.0"?>
<language xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:App/Language/package.xsd">
    <code>en_GB</code>
    <vendor>magento</vendor>
    <package>en_gb</package>
    <sort_order>100</sort_order>
    <use vendor="oxford-university" package="en_us"/>
</language>
```

其中：

- `code` — 語言套件地區設定（必要）
- `vendor` — 模組的廠商名稱（必填）
- `package` — 語言套件名稱（必填）
- `sort_order` — 當有多個語言套件可供存放區使用時，上傳套件的優先順序
- `use` — 要繼承字典的父語言套件地區設定

如有必要，您可以指定多個父封裝。 父套裝軟體會套用至先列出的、先使用的基礎。

#### 語言繼承範例

假設語言套件繼承自其他兩個套件，且這些套件也有父和「祖父」套件。

如果語言套件繼承自兩個套件，其`language.xml`可能如下所示：

```xml
<language xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:App/Language/package.xsd">
    <code>en_GB</code>
    <vendor>magento</vendor>
    <package>language_pack</package>
    <sort_order>100</sort_order>
    <use vendor="parent-package-one" package="language_package_one"/>
    <use vendor= "parent-package-two" package="language_package_two"/>
</language>
```

在上述範例中：

- `language_package_one`繼承自`en_au_package`，而`en_au_package`繼承自`en_ie_package`
- `language_package_two`繼承自`en_ca_package`，而`en_ca_package`繼承自`en_us_package`

如果Commerce應用程式在`en_GB`封裝中找不到字詞或片語，則會依下列順序尋找其他封裝：

1. `parent-package-one/language_package_one`
1. `<vendorname>/en_au_package`
1. `<vendorname>/en_ie_package`
1. `parent-package-two/language_package_two`
1. `<vendorname>/en_ca_package`
1. `<vendorname>/en_us_package`

指定語言套件之間的所有繼承可能會導致建立循環繼承鏈。 使用[Magento\Test\Integrity\App\Language\CircularDependencyTest]測試來尋找並修正這類鏈結。

### 針對一種語言設定多個套件

為協助您讓商店更具彈性，您可以在商店中上傳相同語言的多個語言套件。 因此，您可以針對商店的不同部分使用不同的自訂套件，因為系統會從可用于某語言的所有套件中編譯單一套件。

若要為現有語言啟用其他套件，請將現有語言代碼名稱以外的任何名稱命名為新的套件（以避免混淆）。 依照下一節所述，在語言套件的`language.xml`中繼資訊檔案中指定套件的設定。

## 使用翻譯命令的範例

以下各節提供使用本主題中討論的命令來建立翻譯字典和翻譯套件的端對端範例：

### 範例：建立模組或主題的翻譯字典

若要將德文翻譯新增至要分發給其他商家的模組或主題：

1. 從模組收集片語：

   ```bash
   bin/magento i18n:collect-phrases -o "/var/www/html/magento2/app/code/ExampleCorp/SampleModule/i18n/xx_YY.csv" /var/www/html/magento2/app/code/ExampleCorp/SampleModule
   ```

   >[!INFO]
   >
   >CSV檔案名稱必須&#x200B;_完全符合_&#x200B;地區設定，包括字元的大小寫。

1. 使用[這些准則](#translation-guidelines)翻譯文字與片語。
1. 如有必要，請將`xx_YY.csv`複製到`/var/www/html/magento2/app/code/ExampleCorp/SampleModule/i18n`或模組的主題目錄（視翻譯字典是用於模組還是主題而定）。

### 範例：建立語言套件

與上述範例類似，產生CSV檔案，但您不必指定模組或主題目錄，而是指定整個Commerce應用程式根目錄。 產生的CSV包含命令在程式碼中找到的任何片語。

1. 從模組收集片語：

   ```bash
   bin/magento i18n:collect-phrases -o "/var/www/html/magento2/xx_YY.csv" -m
   ```

   >[!INFO]
   >
   >CSV檔案名稱必須&#x200B;_完全符合_&#x200B;地區設定，包括字元的大小寫。

1. 使用[這些准則](#translation-guidelines)翻譯文字與片語。
1. 建立語言套件。

   ```bash
   bin/magento i18n:pack /var/www/html/magento2/xx_YY.csv -d xx_YY
   ```

1. 建立語言套件的目錄。

   例如， `/var/www/html/magento2/app/i18n/ExampleCorp/xx_yy`

1. 在該目錄中，新增下列所有專案：

   - 授權（如果需要）
   - `composer.json` （下列範例）
   - `registration.php` （下列範例）
   - `language.xml` （下列範例）

   **範例`composer.json`**：

   ```json
   {
       "name": "examplecorp/language-xx_yy",
       "description": "Sample language",
       "version": "100.0.2",
       "license": [
           "OSL-3.0",
           "AFL-3.0"
       ],
       "require": {
           "magento/framework": "100.0.*"
       },
       "type": "magento2-language",
       "autoload": {
           "files": [
               "registration.php"
           ]
       }
   }
   ```

   **範例`registration.php`**：

   ```php
   <?php
   /**
    * Copyright [first year code created] Adobe
    * All Rights Reserved.
    */
   
   use Magento\Framework\Component\ComponentRegistrar;
   
   ComponentRegistrar::register(
       ComponentRegistrar::LANGUAGE,
       'magento_xx_yy',
       __DIR__
   );
   ```

   **範例`language.xml`**：

   ```xml
   <?xml version="1.0"?>
   <!--
   Copyright [first year code created] Adobe
   All Rights Reserved.
   -->
   <language xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:App/Language/package.xsd">
       <code>xx_YY</code>
       <vendor>examplecorp</vendor>
       <package>xx_yy</package>
   </language>
   ```

<!-- link definitions -->

[翻譯概觀]: https://developer.adobe.com/commerce/frontend-core/guide/translations/
[翻譯字典]: https://developer.adobe.com/commerce/frontend-core/guide/translations/#translation-dictionaries
[設定轉換]: https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/site-store/store-localize
[進一步瞭解語言套件]: https://developer.adobe.com/commerce/frontend-core/guide/translations/#language-packages
[ISO 639-1]: https://www.iso.org/iso-639-language-codes.html
[ISO 3166]: https://www.iso.org/iso-3166-country-codes.html
[註冊]: https://developer.adobe.com/commerce/php/development/build/component-registration/
[&#39;de_de&#39;]: https://github.com/magento/magento2/blob/2.4/app/i18n/Magento/de_DE/registration.php
[&#39;composer.json&#39;]: https://developer.adobe.com/commerce/php/development/build/composer-integration/
[&#39;registration.php&#39;]: https://developer.adobe.com/commerce/php/development/build/component-registration/
[Magento\Test\Integrity\App\Language\CircularDependencyTest]: https://github.com/magento/magento2/blob/2.4/dev/tests/static/testsuite/Magento/Test/Integrity/App/Language/CircularDependencyTest.php
