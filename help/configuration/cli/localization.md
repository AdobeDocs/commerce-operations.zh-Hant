---
title: 翻譯字典和語言包
description: 了解如何產生翻譯字典和建立語言套件。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '1509'
ht-degree: 0%

---


# 本地化

{{file-system-owner}}

商務翻譯可讓您針對多個地區和市場自訂和本地化您的商店，方法是：

- **翻譯字典**，這是自訂或翻譯的便利方式 _some_ 字詞和片語，例如自訂模組或主題的字詞和片語。
- **語言套件** 讓你翻譯 _any或all_ 商務應用程式中的字詞和片語。

請參閱 [翻譯概觀].

## 產生翻譯字典

您可以產生 [翻譯字典] 若要自訂現有字串、翻譯自訂模組中的字詞和片語、將主題當地化或建立 [語言包](https://glossary.magento.com/language-package).

若要開始轉譯，請使用命令產生包含所有現有片語和字詞的收集清單的字典CSV檔案。

要生成字典並開始翻譯，請執行以下操作：

1. 使用翻譯收集命令從啟用的元件中提取可翻譯的字詞和短語。 內容擷取為CSV檔案。
1. 翻譯現有的字詞和片語。 您可以視需要新增其他自訂詞語。

   您可以選擇使用翻譯的字典：

1. 您可以將翻譯字典封裝為語言套件，並將套件提供給商務商店管理員。

1. 在管理員中，商店管理員 [配置翻譯].

命令選項：

```bash
bin/magento i18n:collect-phrases [-o|--output="<csv file path and name>"] [-m|--magento] <path to directory to translate>
```

下表說明參數和值：

| 參數 | 值 | 必要？ |
|--- |--- |--- |
| `<path to directory to translate>` | 具有可翻譯代碼的目錄的路徑；換句話說，PHP、PHTML或XML檔案包含要翻譯的片語。<br><br>此工具會從您輸入的路徑開始搜尋，並搜尋其包含的所有檔案和子目錄。<br><br>如果您使用 `-m --magento`. | 是（字典）、否（套件）。 |
| `-m --magento` | 從此翻譯字典建立語言套件時需要。 如果使用，則搜索包含bin/magento的目錄。 此選項會將主題或模組新增至字典中的每行。<br><br>範例如下：<br><br>&quot;No Items Found&quot;,&quot;No Items Found&quot;,module,Magento_Wishlist | 否 |
| `-o --output="<path>"` | 指定要建立的翻譯字典CSV檔案的絕對檔案系統路徑和檔案名。 您輸入的值區分大小寫。 CSV檔案的名稱必須與地區設定名稱完全相符，包括字元的大小寫。<br><br>如果忽略此參數，則輸出會導向至stdout。 | 否 |

>[!INFO]
>
>若要從翻譯字典建立語言包，請 _必須_ 使用 `-m|--magento` 選項。

### 翻譯准則

翻譯字詞和片語時，請使用下列准則：

- 僅變更第二欄的內容。 從英文翻譯片語(`US`)到所需的語言。
- 建立地區設定的字典時，請使用預設的商務字串。
- 翻譯時請注意預留位置： `%1`, `%2`

商務使用預留位置來插入上下文值；它們 _not_ 用於翻譯。 例如：

```text
Product '%1' has been added to shopping cart.
```

填入值：

```text
Product 'Multimeter-2000' has been added to shopping cart.
```

產生的片語必須包含每個預留位置中的至少一個。 例如，假設有預留位置來自 `%1` to `%3` 在原語中。 翻譯可以按任意順序包含任意數量的這些佔位符，但至少必須出現一個 `%1`, `%2`，和 `%3`. 轉換不能包含未出現在原始值中的預留位置值(例如， `%4`, `%5`等)。

翻譯片語的範例：

```text
"Buy %1 for %2 (%3 incl. tax) each","Compre %1 por %2 (%3 incl. imposto) cada"
```

## 建立語言套件

與翻譯字典不同，您可以使用語言套件翻譯商務應用程式中的任何或所有字詞和片語。 您可以使用翻譯字典來翻譯特定元件（例如模組或主題）。 [進一步了解語言套件].

本節探討如何建立語言套件，將CSV檔案寫入模組和主題。 要建立語言包，您必須執行以下部分中討論的任務：

1. [收集和翻譯字詞和片語](#generate-a-translation-dictionary). ( `--magento` 參數為必要項目。)
1. [運行語言包命令](#run-the-language-package-command).
1. [建立目錄和檔案](#create-directories-and-files).
1. （可選。） [為語言配置多個包](#configure-multiple-packages-for-a-language).

### 運行語言包命令

命令用法：

```bash
bin/magento i18n:pack [-m|--mode={merge|replace}] [-d|--allow-duplicates] <source> <locale>
```

下表說明語言包命令的參數和值：

| 參數 | 值 | 必要？ |
|--- |--- |--- |
| `<source>` | CSV檔案的絕對檔案系統路徑和檔案名，該檔案包含合併的翻譯字典和劃分為語言包所需的元資訊。<br><br>使用 [`bin/magento i18n:collect-phrases`](#config-cli-subcommands-xlate-dict-dict) 建立CSV檔案，然後建立語言套件，如 [建立目錄和檔案](#m2devgde-xlate-files). | 是 |
| `<locale>` | [ISO 639-1] （語言）和 [ISO 3166] （國家/地區）語言的識別碼，用於所有產生的CSV檔案的檔案名稱。 範例： `de_DE`, `pt_PT`, `pt_BR`. | 是 |
| `-m --mode` | 如果目標檔案存在，則指定是替換現有語言包還是與新語言包合併。 合併會覆寫任何存在的片語，並新增片語。<br><br>值：合併或替換（預設）。 | 否 |
| `-d --allow-duplicates` | 納入此選項可允許語言包中的重複項。 否則，如果命令在多個具有不同翻譯的條目中遇到相同的短語，則該命令將失敗，並出現錯誤。 | 否 |

### 建立目錄和檔案

語言包位於 `app/i18n/<VendorName>` （在商務檔案系統中），包含下列內容：

- 所需的許可證檔案
- `composer.json`
- `registration.php` the [寄存器] 語言包
- [`language.xml`](#language-package-languagexml) 元資訊檔案

>[!INFO]
>
>您必須將整個路徑小寫。 例如，請參閱 [`de_de`].

要建立這些檔案：

1. 在下建立目錄 `app/i18n`.

   例如，商務語言套件位於 `app/i18n/magento`

1. 添加所需的許可證檔案。
1. 新增 [`composer.json`] 指定語言包的依賴項。
1. 使用註冊語言包 [`registration.php`]
1. 新增 `language.xml` 元資訊檔案，如下一節所述。

#### 語言包language.xml

在 `language.xml` 配置檔案中，必須指定此包的語言繼承順序。

語言繼承可讓您建立名為 _子項_ 根據稱為 _上層_. 子翻譯會覆寫父項。 不過，如果子翻譯無法上傳或顯示，或缺少片語或字詞，商務會使用父項 [地區](https://glossary.magento.com/locale). [語言包繼承的示例](#example-of-language-inheritance).

要聲明包，請指定以下資訊：

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

- `code` — 語言包區域設定（必要）
- `vendor` — 模組的供應商名稱（必要）
- `package` — 語言包名稱（必要）
- `sort_order` — 當存放區有多個語言包時，上載包的優先順序
- `use` — 要繼承字典的父語言包區域設定

如有必要，您可以指定數個父套件。 父程式包會以第一個列出、首次使用的方式應用。

#### 語言繼承範例

假設語言包繼承自另外兩個包，並且這些包還具有父包和「祖父包」包。

如果語言包繼承自兩個包，則其 `language.xml` 看起來可能如下：

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

在上例中：

- `language_package_one` 繼承自 `en_au_package` 和 `en_au_package` 繼承自 `en_ie_package`
- `language_package_two` 繼承自 `en_ca_package` 和 `en_ca_package` 繼承自 `en_us_package`

如果商務應用程式在中找不到字詞或片語 `en_GB` 包，它按照下列順序查看其他包：

1. `parent-package-one/language_package_one`
1. `<vendorname>/en_au_package`
1. `<vendorname>/en_ie_package`
1. `parent-package-two/language_package_two`
1. `<vendorname>/en_ca_package`
1. `<vendorname>/en_us_package`

指定語言包之間的所有繼承可能會導致建立循環繼承鏈。 使用 [Magento\Test\Integrity\App\Language\CircularDependencyTest] 試圖定位和修復這些鏈。

### 為語言配置多個包

為協助您讓商店更具彈性，您可以在商店中上傳使用相同語言的數個語言套件。 因此，您可以針對商店的不同部分使用不同的自訂套件，因為系統會從所有可用語言的套件中編譯單一套件。

要為現有語言啟用附加包，請為新包命名任何名稱，但現有語言代碼名稱除外（以避免混淆）。 在語言包的 `language.xml` 元資訊檔案，如下一節所述。

## 使用翻譯命令的示例

以下各節提供了端到端示例，說明如何使用本主題中討論的命令來建立翻譯字典和翻譯包：

### 範例：為模組或主題建立翻譯字典

若要將德文翻譯新增至要分發給其他商家的模組或主題：

1. 從模組收集片語：

   ```bash
   bin/magento i18n:collect-phrases -o "/var/www/html/magento2/app/code/ExampleCorp/SampleModule/i18n/xx_YY.csv" /var/www/html/magento2/app/code/ExampleCorp/SampleModule
   ```

   >[!INFO]
   >
   >CSV檔案名稱必須 _完全匹配_ 地區，包括字元的大小寫。

1. 使用 [這些准則](#translation-guidelines).
1. 如有必要，請複製 `xx_YY.csv` to `/var/www/html/magento2/app/code/ExampleCorp/SampleModule/i18n` 或模組的主題目錄（取決於翻譯字典是用於模組還是主題）。

### 範例：建立語言套件

與上述範例類似，產生CSV檔案，但請指定整個Commerce應用程式根目錄，而不指定模組或主題目錄。 產生的CSV包含命令在程式碼中可找到的任何片語。

1. 從模組收集片語：

   ```bash
   bin/magento i18n:collect-phrases -o "/var/www/html/magento2/xx_YY.csv" -m
   ```

   >[!INFO]
   >
   >CSV檔案名稱必須 _完全匹配_ 地區，包括字元的大小寫。

1. 使用 [這些准則](#translation-guidelines).
1. 建立語言套件。

   ```bash
   bin/magento i18n:pack /var/www/html/magento2/xx_YY.csv -d xx_YY
   ```

1. 建立語言包的目錄。

   例如， `/var/www/html/magento2/app/i18n/ExampleCorp/xx_yy`

1. 在該目錄中，新增下列所有項目：

   - 許可證（如果需要）
   - `composer.json` （以下範例）
   - `registration.php` （以下範例）
   - `language.xml` （以下範例）

   **範例`composer.json`**:

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

   **範例`registration.php`**:

   ```php
   <?php
   /**
    * Copyright &copy; Magento, Inc. All rights reserved.
    * See COPYING.txt for license details.
    */
   
   use Magento\Framework\Component\ComponentRegistrar;
   
   ComponentRegistrar::register(
       ComponentRegistrar::LANGUAGE,
       'magento_xx_yy',
       __DIR__
   );
   ```

   **範例`language.xml`**:

   ```xml
   <?xml version="1.0"?>
   /**
   * Copyright &copy; Magento, Inc. All rights reserved.
   * See COPYING.txt for license details.
   */
   
   <language xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:App/Language/package.xsd">
       <code>xx_YY</code>
       <vendor>examplecorp</vendor>
       <package>xx_yy</package>
   </language>
   ```

<!-- link definitions -->

[翻譯概觀]: https://developer.adobe.com/commerce/frontend-core/guide/translations/
[翻譯字典]: https://developer.adobe.com/commerce/frontend-core/guide/translations/#translation-dictionaries
[配置翻譯]: https://docs.magento.com/user-guide/stores/store-language-add.html?Highlight=translation
[進一步了解語言套件]: https://developer.adobe.com/commerce/frontend-core/guide/translations/#language-packages
[ISO 639-1]: https://www.iso.org/iso-639-language-codes.html
[ISO 3166]: https://www.iso.org/iso-3166-country-codes.html
[寄存器]: https://developer.adobe.com/commerce/php/development/build/component-registration/
[&#39;de_de&#39;]: https://github.com/magento/magento2/blob/2.4/app/i18n/Magento/de_DE/registration.php
[&#39;composer.json&#39;]: https://developer.adobe.com/commerce/php/development/build/composer-integration/
[&#39;registration.php&#39;]: https://developer.adobe.com/commerce/php/development/build/component-registration/
[Magento\Test\Integrity\App\Language\CircularDependencyTest]: https://github.com/magento/magento2/blob/2.4/dev/tests/static/testsuite/Magento/Test/Integrity/App/Language/CircularDependencyTest.php
