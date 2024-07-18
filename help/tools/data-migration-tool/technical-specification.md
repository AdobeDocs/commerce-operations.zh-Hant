---
title: '[!DNL Data Migration Tool]技術規格'
description: 瞭解 [!DNL Data Migration Tool] 的實作詳細資料，以及在Magento1和Magento2之間傳輸資料時如何擴充。
exl-id: fec3ac3a-dd67-4533-a29f-db917f54d606
topic: Commerce, Migration
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '2098'
ht-degree: 0%

---

# [!DNL Data Migration Tool]技術規格

本節說明[!DNL Data Migration Tool]實作詳細資料，以及如何擴充其功能。

## 存放庫

若要存取[!DNL Data Migration Tool]原始程式碼，請參閱GitHub [存放庫](https://github.com/magento/data-migration-tool)。

## 系統需求

[!DNL Data Migration Tool]的[系統需求](../../installation/system-requirements.md)與Magento2相同。

## 內部結構

### 目錄結構

下圖代表[!DNL Data Migration Tool]的目錄結構：

```
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
│       ├── ResourceModel                   --- contains adapter for connection to data storage and classes to work with structured data
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
│       ├── Exception.php
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

執行移轉程式的指令碼位於： `magento-root/bin/magento`。

## 設定

組態`config.xsd`檔案的結構描述位於`etc/`目錄中。 系統會為每個Magento1.x版本建立預設組態檔(`config.xml.dist`)。它位於`etc/`下的另一個目錄中。

預設組態檔可以自訂組態檔取代（請參閱[命令語法](migrate-data/overview.md#command-syntax)）。

組態檔案具有下列結構：

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

* 來源 — 資料來源的設定。 可用的來源型別：資料庫

* destination — 資料目的地的設定。 可用的目的地型別：資料庫

* options — 引數清單。 包含必要(map_file、settings_map_file、bulk_size)和選擇性(custom_option、resource_adapter_class_name、prefix_source、prefix_dest、log_file)引數

變更首碼選項，以備在資料庫表格中安裝了首碼的Magento時使用。 它可以設定為Magento1和Magento2資料庫。 請相應地使用「source_prefix」和「dest_prefix」組態選項。

可使用`\Migration\Config`類別存取設定資料。

## 可用步驟作業

| 檔案 | 欄位 |
|---|---|
| `step` | 「步驟」節點內的第二層節點。 必須在`title`屬性中指定相關步驟的描述。 |
| `integrity` | 指定負責完整性檢查的PHP類別。 比較表格欄位名稱、型別和其他資訊，以驗證Magento1和2資料結構之間的相容性。 |
| `data` | 指定負責資料檢查的PHP類別。 將資料、表格從Magento1傳輸至Magento2。 |
| `volume` | 指定負責磁碟區檢查的PHP類別。 比較表格之間的記錄數，以驗證傳輸是否成功。 |
| `delta` | 指定負責差異檢查的PHP類別。 在完整資料移轉後，將差異從Magento1傳輸到Magento2。 |

## Source資料庫資訊屬性

| 檔案 | 欄位 | 必填？ |
|---|---|---|
| `name` | Magento1伺服器的資料庫名稱。 | 是 |
| `host` | Magento1伺服器的主機IP位址。 | 是 |
| `port` | Magento1伺服器的連線埠號碼。 | 否 |
| `user` | Magento1資料庫伺服器的使用者名稱。 | 是 |
| `password` | Magento1資料庫伺服器的密碼。 | 是 |
| `ssl_ca` | SSL憑證授權單位檔案的路徑。 | 否 |
| `ssl_cert` | ssl憑證檔案的路徑。 | 否 |
| `ssl_key` | SSL金鑰檔案的路徑。 | 否 |

## 目的地資料庫資訊屬性

| 檔案 | 欄位 | 必填？ |
|---|---|---|
| `name` | Magento2伺服器的資料庫名稱。 | 是 |
| `host` | Magento2伺服器的主機IP位址。 | 是 |
| `port` | Magento2伺服器的連線埠號碼。 | 否 |
| `user` | Magento2資料庫伺服器的使用者名稱。 | 是 |
| `password` | Magento2資料庫伺服器的密碼。 | 是 |
| `ssl_ca` | SSL憑證授權單位檔案的路徑。 | 否 |
| `ssl_cert` | ssl憑證檔案的路徑。 | 否 |
| `ssl_key` | SSL金鑰檔案的路徑。 | 否 |

## 使用TLS通訊協定連線

您也可以使用TLS通訊協定（亦即使用公開/私用密碼編譯金鑰）連線到資料庫。 將下列選擇性屬性新增至`database`元素：

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

移轉程式包含多個步驟。

步驟是一個單位，提供移轉一些個別資料所需的功能。 步驟可包含一或多個階段（完整性檢查、資料、磁碟區檢查以及差異）。

依預設，有幾個步驟（[對應](#map-step)、[EAV](#eav)、[URL重寫](#url-rewrite-step)等）。 您也可以選擇新增自己的步驟。

步驟相關類別位於src/Migration/Step目錄中。

若要執行Step類別，必須在config.xml檔案中定義類別。

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

每個階段類別都必須實作StageInterface。

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

如果資料階段支援回覆，它應該實作`RollbackInterface`介面。

Symfony的ProgressBar元件提供執行步驟的視覺效果（請參閱[進度列](https://symfony.com/doc/current/components/console/helpers/progressbar.html)）。 以LogLevelProcessor存取此元件的步驟。

主要使用方法如下：

```xml
$this->progress->start();
$this->progress->advance();
$this->progress->finish();
```

## 步驟階段

### 完整性檢查

每個步驟都必須檢查資料來源的結構(預設為Magento1)和資料目的地的結構(Magento2)是否相容。 如果沒有 — 不相容的實體會顯示錯誤。 如果欄位有不同的資料型別(相同欄位的Magento1有十進位資料型別，Magento2有整數)，則會顯示警告訊息（除非該訊息涵蓋在地圖檔案中）。

### 資料傳輸

如果完整性檢查通過，則傳輸資料正在執行。 如果出現錯誤，則執行復原以恢復Magento2的上一個狀態。 如果步驟類別實作`RollbackInterface`介面，則當發生錯誤時，就會執行復原方法。

### 磁碟區檢查

資料移轉後，「磁碟區檢查」會提供額外檢查，以確認所有資料皆已正確傳輸。

### 差異傳遞

差異功能負責傳遞主要移轉後新增的其餘資料。

## 執行模式

工具應以三種不同的模式依特定順序執行：

1. 設定 — 移轉系統設定
1. 資料 — 主要資料移轉
1. delta — 移轉主要移轉後新增的其餘資料

每個模式都有各自要執行的步驟清單。 請參閱config.xml

### 設定移轉模式

此工具的設定移轉模式用於轉移以下實體：

1. 網站、商店、商店檢視。
1. 存放區組態（主要是M2中的存放區 — >組態或M1中的系統 — >組態）

所有存放區組態都會將其資料保留在資料庫的core_config_data表格中。 settings.xml檔案包含適用於此資料表的規則，這些規則會在移轉程式期間套用。 此檔案說明應忽略、重新命名或變更其值的設定。 settings.xml檔案具有以下結構：

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

在節點`<key>`下，有些規則可與`core_config_data`資料表中的&#39;path&#39;資料行搭配使用。 `<ignore>`規則防止工具傳輸某些設定。 此節點中可以使用萬用字元。 `<ignore>`節點中未列出的所有其他設定都會移轉。 如果設定的路徑在Magento2中變更，則應將其新增到`//key/rename`節點，其中舊路徑指示在`//key/rename/path`節點中，新路徑指示在`//key/rename/to`節點中。

在節點`<value>`下，有些規則可與`core_config_data`資料表中的&#39;value&#39;資料行搭配使用。 這些規則旨在透過處理常式（實作`Migration\Handler\HandlerInterface`的類別）轉換設定值，並針對Magento2進行調整。

### 資料移轉模式

在此模式中，大多數資料都會移轉。 在資料移轉之前，會針對每個步驟執行完整性檢查階段。 如果完整性檢查通過，[!DNL Data Migration Tool]會安裝deltalog表格（前置詞為`m2_cl_*`）以及對應至Magento1資料庫的觸發程式，並執行步驟的資料移轉階段。 當移轉完成且無錯誤時，磁碟區檢查會檢查資料的一致性。 如果您移轉即時存放區，此畫面會顯示警告訊息。 不用擔心，差異移轉會處理這些增量資料。 最有價值的移轉步驟包括地圖、URL重寫和EAV。

#### 地圖步驟

對應步驟負責將大部分資料從Magento1傳輸至Magento2。 此步驟會從map.xml檔案（位於`etc/`目錄）中讀取指示。 此檔案說明來源(Magento1)和目的地(Magento2)的資料結構之間的差異。 如果Magento1包含屬於Magento2中不存在之某些擴充功能的表格或欄位，則這些實體可放置在此處，以透過「對應步驟」忽略它們。 否則，它會顯示錯誤訊息。

對應檔案的格式如下：

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

* *來源* — 包含來源資料庫的規則

* *目的地* — 包含目的地資料庫的規則

選項：

* *忽略* — 忽略標示有此選項的檔案、欄位或資料型別

* *重新命名* — 說明不同名稱的檔案之間的名稱關係。 如果目的地檔名稱與來原始檔不同，您可以使用重新命名選項來設定與目的地表格名稱相似的來源檔名稱

* *move* — 設定將指定欄位從來原始檔移動到目的地檔案的規則。 附註：目的檔名稱應與來源檔名稱相同。 如果來源和目的地檔名稱不同 — 您需要對包含已移動欄位的檔案使用重新命名選項

* *轉換* — 是允許使用者根據處理常式中描述的行為移轉欄位的選項

* *處理常式* — 說明欄位的轉換行為。 若要呼叫處理常式，您必須在`<handler>`標籤中指定處理常式類別名稱。 將`<param>`標籤與引數名稱和值資料一起使用，以將其傳遞給處理常式

**Source**&#x200B;可用作業：

| 檔案 | 欄位 |
|--- |--- |
| 忽略重新命名 | 忽略移動轉換 |

**目的地**&#x200B;可用的作業：

| 檔案 | 欄位 |
|--- |--- |
| 忽略 | 忽略轉換 |

#### 萬用字元

若要忽略具有類似部分(`document_name_1`， `document_name_2`)的檔案，您可以使用萬用字元功能。 放入`*`符號而非重複部分(`document_name_*`)，而且此遮罩會涵蓋符合此遮罩的所有來源或目的地檔案。

#### URL重寫步驟

此步驟很複雜，因為在Magento1中開發的許多不同演演算法與Magento2不相容。 對於Magento1的不同版本，可能有不同的演演算法。 因此，在Step/UrlRewrite資料夾下，有一些針對某些特定Magento版本開發的類別，Migration\Step\UrlRewrite\Version191to2000就是其中之一。 它可以將URL重寫資料從Magento1.9.1傳輸至Magento2。

#### EAV步驟

此步驟會將所有屬性（產品、客戶、RMA）從Magento1移轉至Magento2。 它使用map-eav.xml檔案，其中包含與map.xml檔案中規則相似的規則，用於處理資料的特定情況。

在步驟中處理的一些表格：

* `eav_attribute`
* `eav_attribute_group`
* `eav_attribute_set`
* `eav_entity_attribute`
* `catalog_eav_attribute`
* `customer_eav_attribute`
* `eav_entity_type`

### 差異移轉模式

主要移轉後，其他資料可能已新增到Magento1資料庫（例如店面的客戶）。 若要追蹤此資料，工具會在移轉程式開始時設定資料表的資料庫觸發程式。 如需詳細資訊，請參閱[移轉由協力廠商擴充功能建立的資料](migrate-data/delta.md#migrate-data-created-by-third-party-extensions)。

## 資料來源

若要存取Magento1和Magento2的資料來源並操作其資料（選取、更新、插入、刪除），資源資料夾中有許多類別。 Migration\ResourceModel\Source和Migration\ResourceModel\Destination是主要類別。 所有移轉步驟都會使用它來操作資料。 這些資料包含在Migration\ResourceModel\Document、Migration\ResourceModel\Record、Migration\ResourceModel\Structure等類別中。

以下是這些類別的類別圖：

![移轉工具資料結構](../../assets/data-migration/MmigrationToolDataStructure.png)

## 記錄

為了實作移轉程式的輸出並控制所有可能的層級，套用Magento中使用的PSR記錄器。 已實作`\Migration\Logger\Logger`類別以提供記錄功能。 若要使用記錄器，您應該透過建構函式相依性插入來插入記錄器。

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

之後，您可以使用此類別來記錄某些事件：

```php
$this->logger->info("Some information message");
$this->logger->debug("Some debug message");
$this->logger->error("Message about error operation");
$this->logger->warning("Some warning message");
```

可以自訂記錄資訊的寫入位置。 您可以透過使用記錄器的pushHandler()方法將處理常式新增到記錄器來執行此操作。 每個處理常式都應該實作`\Monolog\Handler\HandlerInterface`介面。 目前有兩個處理常式：

* ConsoleHandler：將訊息寫入主控台

* FileHandler：將訊息寫入已在「log_file」組態選項中設定的記錄檔

您也可以實作任何其他處理常式。 Magento架構中有一組處理常式。 將處理常式新增至記錄器的範例：

```php
// $this->consoleHandler is the object of Migration\Logger\ConsoleHandler class
// $this->logger is the object of Migration\Logger\Logger class
$this->logger->pushHandler($this->consoleHandler);
```

若要為記錄器設定其他資料（目前模式、表格名稱），您可以使用記錄器處理器。 有一個現有的處理器(MessageProcessor)。 其建立是為了新增用於記錄訊息的「額外」資料，並在每次執行記錄方法時呼叫。 MessageProcessor已保護$extra var，其中包含&#39;mode&#39;、&#39;stage&#39;、&#39;step&#39;和&#39;table&#39;的空白值。 額外的資料可以作為log方法的第二個引數（內容）傳遞給處理器。 目前以AbstractStep->runStage （傳遞目前模式、階段和步驟至處理器）方法傳送給處理器的其他資料集，以及使用logger->debug方法的資料類別（傳遞移轉表格名稱）。 將處理器新增至記錄器的範例：

```php
// $this->processoris the object of Migration\Logger\messageProcessor class
// $this->logger is the object of Migration\Logger\Logger class
$this->logger->pushProcessor([$this->processor, 'setExtra']);
// As a second array value you need to pass method that should be executed when processor called
```

您可以設定詳細程度的等級。 目前共分為三個層級：

* `ERROR` （只將錯誤寫入記錄檔）
* `INFO` （僅重要資訊會寫入記錄檔，預設值）
* `DEBUG` （所有內容皆已寫入）

您可以呼叫`setLevel()`方法，個別設定每個處理常式的詳細資訊記錄層級。 如果您想要透過命令列引數設定詳細程度層級，您應在應用程式啟動時變更「詳細」選項。

您可以使用單色格式化程式來格式化記錄訊息。 若要讓格式化程式功能運作，您必須使用`setFormatter()`方法指定記錄處理常式。 目前，我們有一個格式化程式類別(`MessageFormatter`)，在訊息處理期間（透過從處理常式執行的`format()`方法）設定特定格式（取決於詳細程度層級）。

在`Migration\Logger\Manager`類別的`process()`方法中執行以詳細模式操控記錄器（新增處理常式與處理器）與處理。 方法會在應用程式啟動時呼叫。

## 自動測試

[!DNL Data Migration Tool]中有三種型別的測試：

* 靜態
* 單位
* 整合

它們位於工具的`tests/`目錄中，與測試型別相同（單元測試位於`tests/unit`目錄中）。 若要啟動測試，您應該已安裝phpunit。 將目前目錄切換到測試目錄並啟動phpunit。 例如：

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
