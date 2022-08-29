---
title: '"[!DNL Data Migration Tool] 技術規格」'
description: 「瞭解ControlControlControlControlControlControlControlControlControlControControlControControCo [!DNL Data Migration Tool] 以及在Magento1和Magento2之間傳輸資料時如何擴展。」
source-git-commit: d609c497fdf00c5e5f975a5679b1d072cec4f8a2
workflow-type: tm+mt
source-wordcount: '2091'
ht-degree: 0%

---


# [!DNL Data Migration Tool] 技術規範

本節介紹 [!DNL Data Migration Tool] 實現詳細資訊以及如何擴展其功能。

## 儲存庫

訪問 [!DNL Data Migration Tool] 原始碼，請參閱GitHub [儲存庫](https://github.com/magento/data-migration-tool)。

## 系統要求

的 [系統要求](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html) 為 [!DNL Data Migration Tool] 與第2Magento相同。

## 內部結構

### 目錄結構

下圖表示的目錄結構 [!DNL Data Migration Tool]:

```terminal
├── etc                                    --- all configuration files
│   ├── opensource-to-opensource            --- configuration files for migration from Magento Open Source 1 to Magento Open Source 2
│   │   ├── 1.9.1.1
│   │   │   ├── config.xml.dist
│   │   │   └── map.xml.dist
│   │   ├── 1.9.2.0
│   │   │   ├── config.xml.dist
│   │   │   └── map.xml.dist
│   │   ├── ........
│   │   ├── class-map.xml.dist
│   │   ├── deltalog.xml.dist
│   │   └── settings.xml.dist
│   │   ├── ........
│   ├── opensource-to-commerce              --- configuration files for migration from Magento Open Source 1 to Adobe Commerce 2
│   ├── commerce-to-commerce                --- configuration files for migration from Adobe Commerce 1 to Adobe Commerce 2
│   ├── class-map.xsd
│   ├── config.xsd
│   ├── map.xsd
│   └── settings.xsd
├── src
│   └── Migration
│       ├── App                             --- application framework
│       ├── Console
│       ├── Handler                         --- handlers are used by map files
│       │   ├── AbstractHandler.php
│       │   ├── AddPrefix.php
│       │   ├── ConvertIp.php
│       │   ├── ........
│       ├── Logger
│       ├── Reader
│       ├── Mode
│       │   ├── AbstractMode.php
│       │   ├── Data.php
│       │   ├── Delta.php
│       │   └── Settings.php
│       ├── ResourceModel                   --- contains [adapter](https://glossary.magento.com/adapter) for connection to data storage and classes to work with structured data
│       │   ├── Adapter
│       │   │   └── Mysql.php
│       │   ├── AbstractCollection.php
│       │   ├── AbstractResource.php
│       │   ├── AdapterInterface.php
│       │   ├── Destination.php
│       │   ├── Document.php
│       │   ├── Record.php
│       │   ├── Source.php
│       │   └── Structure.php
│       ├── Config.php
│       ├── [Exception](https://glossary.magento.com/exception).php
│       └── Step                            --- functionality for migrating specific data
│           ├── Eav
│           │   ├── Data.php
│           │   ├── Helper.php
│           │   ├── InitialData.php
│           │   ├── Integrity.php
│           │   └── Volume.php
│           ├── Map
│           │   ├── Data.php
│           │   ├── Delta.php
│           │   ├── Helper.php
│           │   ├── Integrity.php
│           │   └── Volume.php
│           ├── UrlRewrite
│           │   ├── Version11300to2000.php
│           │   ├── Version11410to2000.php
│           │   └── Version191to2000.php
│           ├── ..........
└── tests
    ├── integration
    ├── static
    └── unit
```

## 入口點

運行遷移進程的指令碼位於： `magento-root/bin/magento`。

## 配置

配置的架構 `config.xsd` 檔案位於 `etc/` 的子菜單。 預設配置檔案(`config.xml.dist`)。它位於下面的一個單獨目錄中 `etc/`。

預設配置檔案可替換為自定義配置檔案(請參見 [命令語法](migrate-data/overview.md#command-syntax))。

配置檔案具有以下結構：

```xml
<config xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="config.xsd">
    <steps mode="settings">
        <step title="Settings step">
            <integrity>Migration\Step\Settings</integrity>
            <data>Migration\Step\Settings</data>
        </step>
    </steps>
    <steps mode="data">
        <step title="Map step">
            <integrity>Migration\Step\Map\Integrity</integrity>
            <data>Migration\Step\Map\Data</data>
            <volume>Migration\Step\Map\Volume</volume>
        </step>
        ...
    </steps>
    <steps mode="delta">
        <step title="Map step">
            <delta>Migration\Step\Map\Delta</delta>
            <volume>Migration\Step\Map\Volume</volume>
        </step>
        ...
    </steps>
    <source>
        <database host="localhost" name="magento1" user="root" password=""/>
    </source>
    <destination>
        <database host="localhost" name="magento2" user="root" password=""/>
    </destination>
    <options>
        <map_file>map-file.xml</map_file>
        <settings_map_file>settings-map-file.xml</settings_map_file>
        <bulk_size>100</bulk_size>
        <custom_option>custom_option_value</custom_option>
        <source_prefix />
        <dest_prefix />
        ...
    </options>
</config>
```

* 步驟 — 描述遷移過程中處理的所有步驟

* source — 資料源的配置。 可用源類型：資料庫

* 目標 — 資料目標的配置。 可用目標類型：資料庫

* 選項 — 參數清單。 包含必需(mapfile、settingsmapfile、bulksize)和可選(customoption、resourceadapterclassname、prefixsource、prefixdest、logfile)參數

更改前置詞選項，以防在資料庫表中安裝帶有前置詞的Magento。 它可以設定為Magento1和Magento2資料庫。 相應地使用&quot;source_prefix&quot;和&quot;dest_prefix&quot;配置選項。

配置資料可通過 `\Migration\Config` 類。

## 可用操作的步驟

| 文檔 | 欄位 |
|---|---|
| `step` | 「步驟」節點內的二級節點。 相關步驟的說明必須在 `title` 屬性。 |
| `integrity` | 指定負責完整性檢查的PHP類。 比較表欄位名稱、類型和其他資訊，以驗證Magento1和2資料結構之間的相容性。 |
| `data` | 指定負責資料檢查的PHP類。 將資料從Magento1按表傳輸到Magento2。 |
| `volume` | 指定負責卷檢查的PHP類。 比較表之間的記錄數以驗證傳輸是否成功。 |
| `delta` | 指定負責增量檢查的PHP類。 在完全資料遷移後，將增量從Magento1傳輸到Magento2。 |

## 源資料庫資訊屬性

| 文檔 | 欄位 | 需要？ |
|---|---|---|
| `name` | Magento1伺服器的資料庫名稱。 | 是 |
| `host` | Magento1伺服器的主機IP地址。 | 是 |
| `port` | Magento1伺服器的埠號。 | 不 |
| `user` | Magento1資料庫伺服器的用戶名。 | 是 |
| `password` | Magento1資料庫伺服器的密碼。 | 是 |
| `ssl_ca` | SSL證書頒發機構檔案的路徑。 | 不 |
| `ssl_cert` | SSL證書檔案的路徑。 | 不 |
| `ssl_key` | SSL密鑰檔案的路徑。 | 不 |

## 目標資料庫資訊屬性

| 文檔 | 欄位 | 需要？ |
|---|---|---|
| `name` | Magento2伺服器的資料庫名稱。 | 是 |
| `host` | Magento2伺服器的主機IP地址。 | 是 |
| `port` | Magento2伺服器的埠號。 | 不 |
| `user` | Magento2資料庫伺服器的用戶名。 | 是 |
| `password` | Magento2資料庫伺服器的密碼。 | 是 |
| `ssl_ca` | SSL證書頒發機構檔案的路徑。 | 不 |
| `ssl_cert` | SSL證書檔案的路徑。 | 不 |
| `ssl_key` | SSL密鑰檔案的路徑。 | 不 |

## 使用TLS協定連接

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

## 步驟內部

遷移過程包括步驟。

步驟是提供遷移某些分離資料所需的功能的單元。 步驟可以包括一個或多個階段（完整性檢查、資料、卷檢查和增量）。

預設情況下，有幾個步驟([地圖](#map-step)。 [電視](#eav)。 [URL重寫](#url-rewrite-step)等)。 您也可以選擇添加您自己的步驟。

與步驟相關的類位於src/Migration/Step目錄中。

要執行Step類，必須在config.xml檔案中定義該類。

```xml
<config xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="config.xsd">
    <steps mode="mode_name">
        <step title="Step Name">
            <integrity>Migration\Step\StepName\Integrity</integrity>  <!-- integrity check stage of the step -->
            <data>Migration\Step\StepName\Data</data>
            <volume>Migration\Step\StepName\Volume</volume>
        </step>
        ...
    </steps>
    ...
</config>
```

每個階段類必須實現StageInterface。

```php
class StageClass implements StageInterface
{
  /**
   * Perform the stage
   *
   * @return bool
   */
  public function perform()
  {
  }
}
```

如果資料階段支援回滾，則應實現 `RollbackInterface` 。

運行步驟的可視化由Symfony的ProgressBar元件提供(請參見 [進度欄](http://symfony.com/doc/current/components/console/helpers/progressbar.html))。 以LogLevelProcessor的形式在步驟中訪問此元件。

主要使用方法有：

```xml
$this->progress->start();
$this->progress->advance();
$this->progress->finish();
```

## 步驟階段

### 完整性檢查

每個步驟都必須檢查資料源(預設情況下Magento1)的結構與資料目的地(Magento2)的結構是否相容。 如果不相容，將顯示一個錯誤，其中包含不相容的實體。 如果欄位具有不同的資料類型(同一欄位在Magento1中具有小數資料類型，在Magento2中具有整數)，則會顯示警告消息（在映射檔案中覆蓋時除外）。

### 資料傳輸

如果通過完整性檢查，則傳輸資料正在運行。 如果出現錯誤，則運行回滾以恢復Magento2的上一狀態。 如果步驟類實現 `RollbackInterface` 介面，然後在出現錯誤時執行回滾方法。

### 卷檢查

遷移資料後，卷檢查將提供其他檢查，以確保所有資料都正確傳輸。

### 增量交付

增量功能負責提供主遷移後添加的其餘資料。

## 運行模式

該工具應以三種不同的模式運行，具體順序為：

1. 設定 — 遷移系統設定
1. 資料 — 主要資料遷移
1. delta — 主遷移後添加的其他資料的遷移

每個模式都有其自己的要執行的步驟清單。 請參見config.xml

### 設定遷移模式

此工具的設定遷移模式用於傳輸以下實體：

1. 網站、商店、商店視圖。
1. 儲存配置（主要是M2中的儲存 — >配置或M1中的系統 — >配置）

所有儲存配置都將其資料保留在資料庫中的core_config_data表中。 settings.xml檔案包含遷移過程中應用的此表規則。 此檔案描述了應忽略、更名或應更改其值的設定。 settings.xml檔案具有以下結構：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<settings xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="settings.xsd">
    <key>
        <ignore>
            <path>path/to/ignore*</path>
        </ignore>
        <rename>
            <path>path/to/rename</path>
            <to>new/path/renamed</to>
        </rename>
    <key>
    <value>
        <transform>
            <path>some/key/to/change</path>
            <handler class="Some\Handler\Class"/>
        </transform>
    </value>
</settings>
```

節點下 `<key>` 有些規則與 `core_config_data` 的子菜單。 `<ignore>` 規則阻止工具傳輸某些設定。 此節點中可以使用通配符。 未在 `<ignore>` 將遷移節點。 如果Magento2中的設定路徑已更改，則應將其添加到 `//key/rename` 節點，其中舊路徑指示 `//key/rename/path` 節點和新路徑指示 `//key/rename/to` 的下界。

節點下 `<value>`，有些規則與 `core_config_data` 的子菜單。 這些規則旨在通過處理程式（實現的類）轉換設定的值 `Migration\Handler\HandlerInterface`)並適應第2Magento。

### 資料遷移模式

在此模式下，大多數資料都會遷移。 在資料遷移之前，將為每個步驟運行完整性檢查階段。 如果完整性檢查通過， [!DNL Data Migration Tool] 安裝deltalog表（帶前置詞） `m2_cl_*`)和相應的觸發器到Magento1資料庫，並運行資料遷移階段。 在完成遷移時，卷檢查會檢查資料一致性。 如果遷移即時儲存，它可以顯示警告消息。 別擔心，增量遷移會處理這些增量資料。 最有價值的遷移步驟是映射、URL重寫和EAV。

#### 映射步驟

映射步驟負責將大部分資料從Magento1傳輸到Magento2。 此步驟從map.xml檔案中讀取說明(位於 `etc/` )。 該檔案描述了源(Magento1)和目標(Magento2)的資料結構之間的差異。 如果Magento1包含屬於某些 [擴展](https://glossary.magento.com/extension) Magento2中不存在的圖元，則這些圖元可以放在此處，以通過「映射步驟」忽略它們。 否則，它將顯示錯誤消息。

映射檔案具有下一種格式：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<map xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="map.xsd">
    <source>
        <document_rules>
            <ignore>
                <document>some_document2</document>
            </ignore>
            <rename>
                <document>some_document</document>
                <to>some_dest_document</to>
            </rename>
            <log_changes>
                <document key="primary_key">some_dest_document</document>
            </log_changes>
        </document_rules>

        <field_rules>
            <move>
                <field>some_document1.field1</field>
                <to>some_document1.field2</to>
            </move>
            <ignore>
                <field>some_document3.field8</field>
            </ignore>
            <transform>
                <field>some_document1.field1</field>
                <handler class="\Migration\Handler\Convert">
                    <param name="map" value="[value1:value2;value3:value4;value5:value6;]" />
                </handler>
            </transform>
        </field_rules>
    </source>
    <destination>
        <document_rules>
            <ignore>
                <document>some_document8</document>
            </ignore>
        </document_rules>

        <field_rules>
            <transform>
                <field>some_document5.field3</field>
                <handler class="\Migration\Handler\SetValue">
                    <param name="value" value="10" />
                </handler>
            </transform>
        </field_rules>
    </destination>
</map>
```

區域：

* *源*  — 包含源資料庫規則

* *目標*  — 包含目標資料庫規則

選項：

* *忽略*  — 忽略使用此選項標籤的文檔、欄位或資料類型

* *更名*  — 描述不同名稱的文檔之間的名稱關係。 如果目標文檔名稱與源文檔名稱不同，則可以使用更名選項設定與目標表名稱類似的源文檔名稱

* *移動*  — 設定將指定欄位從源文檔移動到目標文檔的規則。 注：目標文檔名稱應與源文檔名稱相同。 如果源和目標文檔名稱不同 — 您需要對包含已移動欄位的文檔使用更名選項

* *變換*  — 是允許用戶根據處理程式中描述的行為遷移欄位的選項

* *處理程式*  — 描述欄位的轉換行為。 要調用處理程式，需要在 `<handler>` 標籤。 使用 `<param>` 帶有參數名稱和值資料的標籤，以將其傳遞給處理程式

**源** 可用操作：

| 文檔 | 欄位 |
|--- |--- |
| 忽略更名 | 忽略移動轉換 |

**目標** 可用操作：

| 文檔 | 欄位 |
|--- |--- |
| 忽略 | 忽略轉換 |

#### 通配符

要忽略具有類似部件的文檔(`document_name_1`。 `document_name_2`)，可以使用通配符功能。 放置 `*` 符號而不是重複部分(`document_name_*`)並且此掩碼覆蓋符合此掩碼的所有源文檔或目標文檔。

#### URL重寫步驟

此步驟很複雜，因為Magento1中開發了許多與Magento2不相容的算法。 對於Magento1的不同版本，可以有不同的算法。 因此，在Step/UrlRewrite資料夾下，有為某些特定版本的Magento和Migration\Step\UrlRewrite\Version191to2000 is one of them開發的類。 它可以將URL從Magento1.9.1重寫資料到Magento2。

#### EAV步驟

此步驟將所有屬性（產品、客戶、RMA）從Magento1轉移到Magento2。 它使用map-eav.xml檔案，該檔案包含與map.xml檔案中的規則類似的規則，用於特定的資料處理案例。

在步驟中處理的某些表：

* `eav_attribute`
* `eav_attribute_group`
* `eav_attribute_set`
* `eav_entity_attribute`
* `catalog_eav_attribute`
* `customer_eav_attribute`
* `eav_entity_type`

### 增量遷移模式

主遷移後，可以將其他資料添加到Magento1資料庫（例如，由店面上的客戶添加）。 要跟蹤此資料，該工具將在遷移進程開始時為表設定資料庫觸發器。 有關詳細資訊，請參見 [遷移由第三方擴展建立的資料](migrate-data/delta.md#migrate-data-created-by-third-party-extensions)。

## 資料源

要訪問Magento1和Magento2的資料源並使用其資料（選擇、更新、插入、刪除）操作，Resource資料夾中有許多類。 Migration\ResourceModel\Source和Migration\ResourceModel\Destination是主類。 所有遷移步驟都使用它來操作資料。 此資料包含在類中，如Migration\ResourceModel\Document、Migration\ResourceModel\Record、Migration\ResourceModel\Structure等。

下面是這些類的類圖：

![遷移工具資料結構](../../assets/data-migration/MmigrationToolDataStructure.png)

## 記錄

為了實現遷移過程的輸出，並控制所有可能級別的PSR記錄器，該記錄器用於Magento。 `\Migration\Logger\Logger` 類已實現以提供日誌記錄功能。 要使用記錄器，應通過建構子將其插入 [依賴注入](https://glossary.magento.com/dependency-injection)。

```php
class SomeClass
{
    ...
    protected $logger;

    public function __construct(\Migration\Logger\Logger $logger)
    {
        $this->logger = $logger;
    }
    ...
}
```

之後，您可以使用此類記錄某些事件：

```php
$this->logger->info("Some information message");
$this->logger->debug("Some debug message");
$this->logger->error("Message about error operation");
$this->logger->warning("Some warning message");
```

可以自定義日誌資訊的寫入位置。 可以通過使用記錄器的pushHandler()方法向記錄器添加處理程式來執行此操作。 每個處理程式應實現 `\Monolog\Handler\HandlerInterface` 。 目前還有兩個處理程式：

* 控制台處理程式：將消息寫入控制台

* 檔案處理程式：將消息寫入「log_file」配置選項中設定的日誌檔案

此外，還可以實現任何附加處理程式。 Magento框架中有一組處理程式。 向記錄器添加處理程式的示例：

```php
// $this->consoleHandler is the object of Migration\Logger\ConsoleHandler class
// $this->logger is the object of Migration\Logger\Logger class
$this->logger->pushHandler($this->consoleHandler);
```

要為記錄器設定其他資料（當前模式、表名），可以使用記錄器處理器。 現有處理器（消息處理器）。 建立它是為了為日誌消息添加「額外」資料，每次執行日誌方法時都會調用它。 MessageProcessor已保護$extra var，它包含「mode」、「stage」、「step」和「table」的空值。 額外資料可以作為日誌方法的第二參數（上下文）傳遞給處理器。 當前，AbstractStep->runStage（傳遞當前模式、階段和步驟到處理器）中處理器的附加資料集，以及使用記錄器 — >調試方法（傳遞遷移表名）的資料類。 將處理器添加到記錄器的示例：

```php
// $this->processoris the object of Migration\Logger\messageProcessor class
// $this->logger is the object of Migration\Logger\Logger class
$this->logger->pushProcessor([$this->processor, 'setExtra']);
// As a second array value you need to pass method that should be executed when processor called
```

有可能設定詳細程度。 至於目前，有三個層次：

* `ERROR` （僅將錯誤寫入日誌）
* `INFO` （只有重要資訊寫入日誌，預設值）
* `DEBUG` （所有內容都寫好）

可通過調用為每個處理程式單獨設定詳細程度日誌級別 `setLevel()` 的雙曲餘切值。 如果要通過命令行參數設定詳細程度級別，應在應用程式啟動時更改「verbose」選項。

可以使用單一格式化程式格式化日誌消息。 要使格式化程式功能正常工作，必須使用 `setFormatter()` 的雙曲餘切值。 當前，我們有一個格式化程式類(`MessageFormatter`)，在消息處理期間(通過 `format()` 方法)。

操作記錄器（添加處理程式和處理器）和以詳細模式處理 `process()` 方法 `Migration\Logger\Manager` 類。 應用程式啟動時調用此方法。

## 自動test

有三種test [!DNL Data Migration Tool]:

* 靜態
* 單位
* 整合

它們位於工具的 `tests/` 目錄，與test類型相同(單位test位於 `tests/unit` )。 要啟動test，應安裝phpunit。 將當前目錄更改為test目錄並啟動phpunit。 例如：

```bash
[10:32 AM]-[vagrant@debian-70rc1-x64-vbox4210]-[/var/www/magento2/vendor/magento/data-migration-tool]-[git master]
$ cd tests/unit
```

```bash
[10:33 AM]-[vagrant@debian-70rc1-x64-vbox4210]-[/var/www/magento2/vendor/magento/data-migration-tool/tests/unit]-[git master]
$ phpunit
PHPUnit 8.1.0 by Sebastian Bergmann.
....
```
