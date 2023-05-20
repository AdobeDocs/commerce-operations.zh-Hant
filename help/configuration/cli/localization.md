---
title: 翻譯詞典和語言包
description: 瞭解如何生成翻譯詞典和生成語言包。
exl-id: dd27ccdd-158d-40a6-a2e2-563857820ae9
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1503'
ht-degree: 0%

---

# 本地化

{{file-system-owner}}

商務翻譯使您能夠通過生成以下內容來為多個區域和市場定制和本地化您的儲存：

- **翻譯詞典**，這是定制或翻譯的方便方法 _有_ 詞和短語，例如用於自定義模組或主題的詞和短語。
- **語言包** 使你能夠翻譯 _任意或全部_ 中的單詞和短語。

請參閱 [翻譯概述]。

## 生成翻譯詞典

可以生成 [翻譯詞典] 自定義現有字串、在自定義模組中翻譯單詞和短語、本地化主題或建立語言包。

要開始翻譯，請使用命令生成包含所有現有短語和詞的收集清單的字典CSV檔案。

要生成字典並開始翻譯，請執行以下操作：

1. 使用翻譯收集命令從啟用的元件中提取可翻譯的單詞和短語。 內容提取到CSV檔案。
1. 翻譯現有的單詞和短語。 您可以根據需要添加其他自定義術語。

   您有使用已翻譯詞典的選項：

1. 您可以將翻譯詞典打包成語言包，並將包提供給Commerce儲存管理員。

1. 在管理員中，儲存管理員 [配置翻譯]。

命令選項：

```bash
bin/magento i18n:collect-phrases [-o|--output="<csv file path and name>"] [-m|--magento] <path to directory to translate>
```

下表說明了參數和值：

| 參數 | 值 | 需要？ |
|--- |--- |--- |
| `<path to directory to translate>` | 具有可翻譯代碼的目錄的路徑；換句話說，PHP、PHTML或XML檔案具有要翻譯的短語。<br><br>該工具在您輸入的路徑上開始搜索，並搜索它包含的所有檔案和子目錄。<br><br>如果使用 `-m --magento`。 | 是（字典），否（包）。 |
| `-m --magento` | 從此翻譯字典建立語言包時需要。 如果使用，則搜索包含bin/magento的目錄。 此選項將主題或模組添加到字典中的每一行。<br><br>示例如下：<br><br>&quot;找不到項&quot;,&quot;找不到項&quot;,module,Magento_Wishlist | 否 |
| `-o --output="<path>"` | 指定要建立的翻譯字典CSV檔案的絕對檔案系統路徑和檔案名。 輸入的值區分大小寫。 CSV檔案的名稱必須與區域設定名稱完全匹配，包括字元大小寫。<br><br>如果忽略此參數，則輸出將定向到stdout。 | 否 |

>[!INFO]
>
>要從翻譯詞典建立語言包，您 _必須_ 使用 `-m|--magento` 的雙曲餘切值。

### 翻譯指南

在翻譯單詞和短語時，請使用以下准則：

- 僅更改第二列的內容。 從英語翻譯短語(`US`)。
- 為區域設定建立詞典時，請使用預設的Commerce字串。
- 翻譯時，請注意佔位符： `%1`。 `%2`

Commerce使用佔位符插入上下文值；他們 _不_ 用於翻譯。 例如：

```text
Product '%1' has been added to shopping cart.
```

使用值填充：

```text
Product 'Multimeter-2000' has been added to shopping cart.
```

生成的短語必須至少包含每個佔位符中的一個。 例如，假設有佔位符 `%1` 至 `%3` 在原語中。 翻譯可以按任意順序包含多個這些佔位符，但必須至少出現一次 `%1`。 `%2`, `%3`。 轉換不能包含原始值中不存在的佔位符值(例如， `%4`。 `%5`等)。

翻譯短語的示例：

```text
"Buy %1 for %2 (%3 incl. tax) each","Compre %1 por %2 (%3 incl. imposto) cada"
```

## 建立語言包

與翻譯詞典相比，您可以使用語言包翻譯Commerce應用程式中的任何或所有單詞和短語。 可以使用翻譯字典來翻譯特定元件（如模組或主題）。 [瞭解有關語言包的詳細資訊]。

本節討論如何建立語言包，該語言包將CSV檔案寫入模組和主題。 要建立語言包，必須執行以下各節中討論的任務：

1. [收集和翻譯單詞和短語](#generate-a-translation-dictionary)。 ( `--magento` 參數是必填項。)
1. [運行語言包命令](#run-the-language-package-command)。
1. [建立目錄和檔案](#create-directories-and-files)。
1. （可選。） [為語言配置多個包](#configure-multiple-packages-for-a-language)。

### 運行語言包命令

命令用法：

```bash
bin/magento i18n:pack [-m|--mode={merge|replace}] [-d|--allow-duplicates] <source> <locale>
```

下表說明了語言包命令的參數和值：

| 參數 | 值 | 需要？ |
|--- |--- |--- |
| `<source>` | 包含將翻譯字典和元資訊組合在一起以便分解為語言包的CSV檔案的絕對檔案系統路徑和檔案名。<br><br>使用 [`bin/magento i18n:collect-phrases`](#config-cli-subcommands-xlate-dict-dict) 建立CSV檔案，然後建立語言包，如中所述 [建立目錄和檔案](#m2devgde-xlate-files)。 | 是 |
| `<locale>` | [ISO 639-1] （語言）和 [ISO 3166] （國家/地區）所有生成的CSV檔案用作檔案名的語言標識符。 示例： `de_DE`。 `pt_PT`。 `pt_BR`。 | 是 |
| `-m --mode` | 如果目標檔案存在，則指定是替換現有語言包還是與新語言包合併。 合併將覆蓋現有的任何短語並添加新短語。<br><br>值：合併或替換（預設）。 | 否 |
| `-d --allow-duplicates` | 包括此選項以允許語言包中的重複項。 否則，如果命令在具有不同翻譯的多個條目中遇到相同的短語，則該命令將失敗並出現錯誤。 | 否 |

### 建立目錄和檔案

語言包位於 `app/i18n/<VendorName>` 在Commerce檔案系統中，包括以下內容：

- 所需的許可證檔案
- `composer.json`
- `registration.php` 那 [寄存器] 語言包
- [`language.xml`](#language-package-languagexml) 元資訊檔案

>[!INFO]
>
>必須小寫整個路徑。 例如，請參見 [`de_de`]。

要建立這些檔案：

1. 建立目錄 `app/i18n`。

   例如，Commerce語言包位於 `app/i18n/magento`

1. 添加所需的許可證檔案。
1. 添加 [`composer.json`] 指定語言包的依賴項。
1. 註冊語言包 [`registration.php`]
1. 添加 `language.xml` 元資訊檔案，如下一節中所述。

#### 語言包language.xml

在 `language.xml` 配置檔案中，必須指定此包的語言繼承順序。

語言繼承使您能夠建立名為 _孩子_ 基於名為 _父_。 子翻譯將覆蓋父翻譯。 但是，如果子翻譯無法上載或顯示，或缺少短語或字詞，Commerce將使用父語言環境。 [語言包繼承示例](#example-of-language-inheritance)。

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

位置：

- `code` — 語言包區域設定（必需）
- `vendor` — 模組的供應商名稱（必需）
- `package` — 語言包名稱（必需）
- `sort_order` — 當存在多個可用於儲存的語言包時，上載包的優先順序
- `use` — 父語言包區域設定，從中繼承字典

如有必要，可以指定多個父包。 父包以第一個列出的、第一個使用的基準應用。

#### 語言繼承示例

假設語言包繼承自另外兩個包，並且這些包還具有父和「祖父」包。

如果語言包繼承自兩個包，則 `language.xml` 可能如下所示：

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

如果Commerce應用程式在中找不到字詞或短語 `en_GB` 包，它按照以下順序查找其他包：

1. `parent-package-one/language_package_one`
1. `<vendorname>/en_au_package`
1. `<vendorname>/en_ie_package`
1. `parent-package-two/language_package_two`
1. `<vendorname>/en_ca_package`
1. `<vendorname>/en_us_package`

指定語言包之間的所有繼承可能會導致建立循環繼承鏈。 使用 [Magento\Test\Integrity\App\Language\CircularDependencyTest] test定位和固定這些鏈。

### 為語言配置多個包

為了幫助您使商店更靈活，您可以在商店中為同一語言上傳多個語言包。 因此，您可以為儲存的不同部分使用不同的自定義軟體包，因為系統會從所有可用於語言的軟體包中編譯單個軟體包。

要為現有語言啟用附加包，請將新包命名為除現有語言代碼名稱之外的任何名稱（以避免混淆）。 在語言包中指定包的配置 `language.xml` 元資訊檔案，如下一節中所述。

## 使用翻譯命令的示例

以下各節提供了使用本主題中討論的命令建立翻譯詞典和翻譯軟體包的端到端示例：

### 示例：為模組或主題建立翻譯詞典

要將德語翻譯添加到要分發給其他商家的模組或主題中，請執行以下操作：

1. 從模組中收集短語：

   ```bash
   bin/magento i18n:collect-phrases -o "/var/www/html/magento2/app/code/ExampleCorp/SampleModule/i18n/xx_YY.csv" /var/www/html/magento2/app/code/ExampleCorp/SampleModule
   ```

   >[!INFO]
   >
   >CSV檔案名必須 _完全匹配_ 區域設定，包括字元大小寫。

1. 使用 [這些准則](#translation-guidelines)。
1. 如有必要，請複製 `xx_YY.csv` 至 `/var/www/html/magento2/app/code/ExampleCorp/SampleModule/i18n` 或到模組的主題目錄（取決於翻譯字典是用於模組還是主題）。

### 示例：建立語言包

與上例類似，生成CSV檔案，但不指定模組或主題目錄，而是指定整個Commerce應用程式根目錄。 生成的CSV包含命令在代碼中可以找到的任何短語。

1. 從模組中收集短語：

   ```bash
   bin/magento i18n:collect-phrases -o "/var/www/html/magento2/xx_YY.csv" -m
   ```

   >[!INFO]
   >
   >CSV檔案名必須 _完全匹配_ 區域設定，包括字元大小寫。

1. 使用 [這些准則](#translation-guidelines)。
1. 建立語言包。

   ```bash
   bin/magento i18n:pack /var/www/html/magento2/xx_YY.csv -d xx_YY
   ```

1. 為語言包建立目錄。

   比如說， `/var/www/html/magento2/app/i18n/ExampleCorp/xx_yy`

1. 在該目錄中，添加以下所有內容：

   - 許可證（如果需要）
   - `composer.json` （示例如下）
   - `registration.php` （示例如下）
   - `language.xml` （示例如下）

   **示例`composer.json`**:

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

   **示例`registration.php`**:

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

   **示例`language.xml`**:

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

[翻譯概述]: https://developer.adobe.com/commerce/frontend-core/guide/translations/
[翻譯詞典]: https://developer.adobe.com/commerce/frontend-core/guide/translations/#translation-dictionaries
[配置翻譯]: https://docs.magento.com/user-guide/stores/store-language-add.html?Highlight=translation
[瞭解有關語言包的詳細資訊]: https://developer.adobe.com/commerce/frontend-core/guide/translations/#language-packages
[ISO 639-1]: https://www.iso.org/iso-639-language-codes.html
[ISO 3166]: https://www.iso.org/iso-3166-country-codes.html
[寄存器]: https://developer.adobe.com/commerce/php/development/build/component-registration/
[「de_de」]: https://github.com/magento/magento2/blob/2.4/app/i18n/Magento/de_DE/registration.php
[&#39;composer.json&#39;]: https://developer.adobe.com/commerce/php/development/build/composer-integration/
[&#39;registration.php&#39;]: https://developer.adobe.com/commerce/php/development/build/component-registration/
[Magento\Test\Integrity\App\Language\CircularDependencyTest]: https://github.com/magento/magento2/blob/2.4/dev/tests/static/testsuite/Magento/Test/Integrity/App/Language/CircularDependencyTest.php
