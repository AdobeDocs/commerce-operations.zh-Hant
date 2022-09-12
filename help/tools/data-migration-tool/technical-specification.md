---
title: '"[!DNL Data Migration Tool] 技術規格」'
description: 「了解 [!DNL Data Migration Tool] 以及在Magento1和Magento2之間傳輸資料時如何延伸。」
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '2085'
ht-degree: 0%

---


# [!DNL Data Migration Tool] 技術規範

本節說明 [!DNL Data Migration Tool] 實作詳細資訊及如何擴充其功能。

## 儲存庫

若要存取 [!DNL Data Migration Tool] 原始碼，請參閱GitHub [存放庫](https://github.com/magento/data-migration-tool).

## 系統需求

此 [系統需求](../../installation/system-requirements.md) 針對 [!DNL Data Migration Tool] 與Magento2相同。

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

## 進入點

運行遷移過程的指令碼位於： `magento-root/bin/magento`.

## 設定

配置的架構 `config.xsd` 檔案位於 `etc/` 目錄。 預設配置檔案(`config.xml.dist`)會針對每個Magento1.x版建立。它位於 `etc/`.

預設設定檔案可以取代為自訂設定檔案(請參閱 [命令語法](migrate-data/overview.md#command-syntax))。

設定檔案的結構如下：

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

* 步驟 — 說明移轉期間處理的所有步驟

* 源 — 資料源的配置。 可用源類型：資料庫

* 目的地 — 資料目的地的設定。 可用的目標類型：資料庫

* 選項 — 參數清單。 包含必填(map_file、settings_map_file、bulk_size)和可選(custom_option、resource_adapter_class_name、prefix_source、prefix_dest、log_file)參數

更改前置詞選項，以備在資料庫表中安裝帶有前置詞的Magento時使用。 可為Magento1和Magento2資料庫設定。 請據以使用「source_prefix」和「dest_prefix」設定選項。

可透過 `\Migration\Config` 類別。

## 可用操作的步驟

| 檔案 | 欄位 |
|---|---|
| `step` | 「步驟」節點內的二級節點。 相關步驟的說明必須在 `title` 屬性。 |
| `integrity` | 指定負責完整性檢查的PHP類。 比較表欄位名稱、類型和其他資訊，以驗證Magento1和2資料結構之間的相容性。 |
| `data` | 指定負責資料檢查的PHP類。 將資料（依表格）從Magento1傳輸至Magento2。 |
| `volume` | 指定負責卷檢查的PHP類。 比較表之間的記錄數，以驗證傳輸是否成功。 |
| `delta` | 指定負責增量檢查的PHP類。 完整資料移轉後，將差值從Magento1傳輸至Magento2。 |

## 源資料庫資訊屬性

| 檔案 | 欄位 | 必要？ |
|---|---|---|
| `name` | Magento1伺服器的資料庫名稱。 | 是 |
| `host` | Magento1伺服器的主機IP地址。 | 是 |
| `port` | Magento1伺服器的埠號。 | no |
| `user` | Magento1資料庫伺服器的用戶名。 | 是 |
| `password` | Magento1資料庫伺服器的口令。 | 是 |
| `ssl_ca` | SSL憑證授權檔案的路徑。 | no |
| `ssl_cert` | SSL憑證檔案的路徑。 | no |
| `ssl_key` | SSL密鑰檔案的路徑。 | no |

## 目標資料庫資訊屬性

| 檔案 | 欄位 | 必要？ |
|---|---|---|
| `name` | Magento2伺服器的資料庫名稱。 | 是 |
| `host` | Magento2伺服器的主機IP地址。 | 是 |
| `port` | Magento2伺服器的埠號。 | no |
| `user` | Magento2資料庫伺服器的用戶名。 | 是 |
| `password` | Magento2資料庫伺服器的口令。 | 是 |
| `ssl_ca` | SSL憑證授權檔案的路徑。 | no |
| `ssl_cert` | SSL憑證檔案的路徑。 | no |
| `ssl_key` | SSL密鑰檔案的路徑。 | no |

## 使用TLS通訊協定連線

您也可以使用TLS通訊協定（即使用公開/私用密鑰）連線至資料庫。 將下列選用屬性新增至 `database` 元素：

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

移轉程式包含步驟。

步驟是提供移轉某些個別資料所需功能的單位。 步驟可由一個或多個階段組成（完整性檢查、資料、卷檢查和增量）。

依預設，有數個步驟([地圖](#map-step), [EAV](#eav), [URL重新寫入](#url-rewrite-step)等)。 您也可以選擇新增自己的步驟。

步驟相關類位於src/Migration/Step目錄中。

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

每個階段類都必須實施StageInterface。

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

如果資料階段支援回滾，則應實作 `RollbackInterface` 介面。

運行步驟的可視化由Symfony的ProgressBar元件提供(請參閱 [進度列](http://symfony.com/doc/current/components/console/helpers/progressbar.html))。 以LogLevelProcessor的形式在步驟中訪問此元件。

主要使用方法為：

```xml
$this->progress->start();
$this->progress->advance();
$this->progress->finish();
```

## 步驟階段

### 完整性檢查

每個步驟都必須檢查資料源的結構(預設為Magento1)和資料目標的結構(Magento2)是否相容。 若不相容，系統會針對不相容的實體顯示錯誤。 如果欄位具有不同的資料類型(相同欄位在Magento1中具有小數資料類型，在Magento2中具有整數)，則會顯示警告消息（映射檔案中涵蓋該欄位時除外）。

### 資料傳輸

如果通過完整性檢查，則傳輸資料正在運行。 如果出現錯誤，則回滾運行以恢復到Magento2的以前狀態。 如果步驟類實作 `RollbackInterface` 介面，然後在出現錯誤時執行回滾方法。

### 卷檢查

遷移資料後，卷檢查將提供其他檢查，以檢查所有資料是否都正確傳輸。

### 增量傳送

增量功能負責傳送主要移轉後新增的其餘資料。

## 執行模式

該工具應以三種不同模式運行，具體順序為：

1. 設定 — 系統設定移轉
1. 資料 — 主要資料移轉
1. 增量 — 主要遷移後添加的其餘資料的遷移

每個模式都有各自要執行的步驟清單。 請參閱config.xml

### 設定移轉模式

此工具的設定移轉模式用於轉移下列實體：

1. 網站、商店、商店檢視。
1. 儲存配置（主要是M2中的Stores->Configuration或M1中的System->Configuration）

所有儲存配置都將其資料保留在資料庫的core_config_data表中。 settings.xml檔案包含此表的規則，這些規則在遷移過程中應用。 此檔案說明應忽略、重新命名或應變更其值的設定。 settings.xml檔案的結構如下：

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

在節點底下 `<key>` 有些規則可搭配「路徑」欄使用，位於 `core_config_data` 表格。 `<ignore>` 規則會阻止工具傳輸某些設定。 可在此節點中使用通配符。 未列於 `<ignore>` 節點會移轉。 如果Magento2中設定的路徑已變更，則應將其新增至 `//key/rename` 節點，舊路徑在中指示 `//key/rename/path` 節點和新路徑指示於 `//key/rename/to` 節點。

在節點底下 `<value>`，則有可搭配 `core_config_data` 表格。 這些規則旨在由處理程式（實作的類）轉換設定的值 `Migration\Handler\HandlerInterface`)並調整以適應Magento2。

### 資料遷移模式

在此模式中，大部分資料都會移轉。 在資料遷移之前，完整性檢查階段會針對每個步驟運行。 如果完整性檢查通過，則 [!DNL Data Migration Tool] 安裝deltalog表（帶前置詞） `m2_cl_*`)和Magento1資料庫的對應觸發器，並執行資料移轉階段的步驟。 完成遷移時，卷檢查將檢查資料一致性。 如果您移轉即時商店，則會顯示警告訊息。 不要擔心，增量遷移會處理此增量資料。 最有價值的移轉步驟是地圖、URL重寫和EAV。

#### 對應步驟

映射步驟負責將大部分資料從Magento1傳輸到Magento2。 此步驟會從map.xml檔案(位於 `etc/` 目錄)。 該檔案描述源(Magento1)和目標(Magento2)的資料結構之間的差異。 若Magento1包含屬於某些 [擴充功能](https://glossary.magento.com/extension) Magento2中不存在的實體，則可以將這些實體放置在此處，以便透過「對應步驟」忽略它們。 否則，會顯示錯誤訊息。

映射檔案的格式為：

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

* *來源*  — 包含源資料庫規則

* *目的地*  — 包含目標資料庫規則

選項：

* *忽略*  — 忽略用此選項標籤的文檔、欄位或資料類型

* *重新命名*  — 描述具有不同名稱的文檔之間的名稱關係。 在目標文檔名稱與源文檔不同的情況下，可以使用更名選項來設定與目標表名稱類似的源文檔名稱

* *移動*  — 設定規則，將指定欄位從源文檔移動到目標文檔。 注意：目標文檔名稱應與源文檔名稱相同。 如果源文檔和目標文檔名稱不同，則需要對包含移動欄位的文檔使用更名選項

* *轉換*  — 是選項，允許用戶根據處理程式中描述的行為遷移欄位

* *處理常式*  — 說明欄位的轉換行為。 要調用處理程式，需要在 `<handler>` 標籤。 使用 `<param>` 標籤，其參數名稱和值資料可傳遞至處理常式

**來源** 可用操作：

| 檔案 | 欄位 |
|--- |--- |
| 忽略更名 | 忽略移動轉換 |

**目的地** 可用操作：

| 檔案 | 欄位 |
|--- |--- |
| 忽略 | 忽略轉換 |

#### 萬用字元

要忽略具有類似部件的文檔(`document_name_1`, `document_name_2`)，則可使用萬用字元功能。 Put `*` 符號而非重複部分(`document_name_*`)，此掩碼將覆蓋符合此掩碼的所有源文檔或目標文檔。

#### URL重寫步驟

此步驟很複雜，因為Magento1中開發的許多不同演算法與Magento2不相容。 對於不同版本的Magento1，可能有不同的演算法。 因此，在Step/UrlRewrite資料夾下，有些類別是針對某些特定版本的Magento和Migration\Step\UrlRewrite\Version191to2000 is one of them所開發。 它可將URL重寫資料從Magento1.9.1傳輸至Magento2。

#### EAV步驟

此步驟將所有屬性（產品、客戶、RMA）從Magento1轉移到Magento2。 它使用map-eav.xml檔案，其中包含與map.xml檔案中的規則類似的規則，以處理資料的特定案例。

在步驟中處理的部分表格：

* `eav_attribute`
* `eav_attribute_group`
* `eav_attribute_set`
* `eav_entity_attribute`
* `catalog_eav_attribute`
* `customer_eav_attribute`
* `eav_entity_type`

### 增量遷移模式

主要移轉後，可將其他資料新增至Magento1資料庫（例如，由店面上的客戶）。 為了追蹤此資料，工具會在遷移過程開始時為表設定資料庫觸發器。 如需詳細資訊，請參閱 [移轉由協力廠商擴充功能建立的資料](migrate-data/delta.md#migrate-data-created-by-third-party-extensions).

## 資料來源

要訪問Magento1和Magento2的資料源並使用其資料（選擇、更新、插入、刪除），「資源」資料夾中有許多類。 Migration\ResourceModel\Source和Migration\ResourceModel\Destination是主類。 所有移轉步驟都會使用它來運作資料。 此資料包含在Migration\ResourceModel\Document、Migration\ResourceModel\Record、Migration\ResourceModel\Structure等類中。

以下是這些類的類圖：

![移轉工具資料結構](../../assets/data-migration/MmigrationToolDataStructure.png)

## 記錄

為了實現遷移過程的輸出，並控制Magento中使用的所有可能級PSR記錄器。 `\Migration\Logger\Logger` 已實作類別，以提供記錄功能。 若要使用記錄器，您應透過建構函式插入它 [依賴注入](https://glossary.magento.com/dependency-injection).

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

之後，您就可以使用此類別記錄某些事件：

```php
$this->logger->info("Some information message");
$this->logger->debug("Some debug message");
$this->logger->error("Message about error operation");
$this->logger->warning("Some warning message");
```

您可以自訂記錄資訊的寫入位置。 您可以使用記錄器的pushHandler()方法，將處理常式新增至記錄器，以執行此操作。 每個處理常式應實作 `\Monolog\Handler\HandlerInterface` 介面。 目前有兩個處理常式：

* 控制台處理程式：將訊息寫入主控台

* 檔案處理程式：將消息寫入「log_file」配置選項中設定的日誌檔案

您也可以實施任何其他處理常式。 Magento框架中有一組處理程式。 向記錄器添加處理程式的示例：

```php
// $this->consoleHandler is the object of Migration\Logger\ConsoleHandler class
// $this->logger is the object of Migration\Logger\Logger class
$this->logger->pushHandler($this->consoleHandler);
```

要為記錄器設定其他資料（當前模式、表名），可以使用記錄器處理器。 有一個現有處理器(MessageProcessor)。 它的建立是為了為記錄訊息新增「額外」資料，且每次執行記錄方法時都會呼叫。 MessageProcessor已保護$extra var，其中包含「mode」、「stage」、「step」和「table」的空值。 額外資料可作為記錄方法的第二個參數（內容）傳遞至處理器。 當前在AbstractStep->runStage（將當前模式、階段和步驟傳遞給處理器）方法和資料類中使用記錄器 — >調試方法（傳遞遷移表名）的附加資料集。 將處理器添加到記錄器的示例：

```php
// $this->processoris the object of Migration\Logger\messageProcessor class
// $this->logger is the object of Migration\Logger\Logger class
$this->logger->pushProcessor([$this->processor, 'setExtra']);
// As a second array value you need to pass method that should be executed when processor called
```

有可能設定詳細程度。 目前有三個層級：

* `ERROR` （僅將錯誤寫入日誌）
* `INFO` （只有重要資訊寫入日誌，預設值）
* `DEBUG` （所有內容都寫完）

可借由呼叫來個別設定每個處理常式的詳細程度記錄層級 `setLevel()` 方法。 如果您想透過命令列參數設定詳細程度層級，應在應用程式啟動時變更「verbose」選項。

您可以使用monolog格式化程式來格式化日誌消息。 要使格式化程式功能發揮作用，必須使用 `setFormatter()` 方法。 目前，我們有一個格式化程式類(`MessageFormatter`)，在訊息處理期間(透過 `format()` 方法)。

在 `process()` 方法 `Migration\Logger\Manager` 類別。 應用程式啟動時會呼叫方法。

## 自動測試

中有三種類型的測試 [!DNL Data Migration Tool]:

* 靜態
* 單位
* 整合

它們位於工具的 `tests/` 目錄，與測試類型(單元測試位於 `tests/unit` 目錄)。 若要啟動測試，您應已安裝Phpunit。 將當前目錄更改為測試目錄並啟動phpunit。 例如：

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
