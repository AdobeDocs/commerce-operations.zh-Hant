---
title: 自訂 [!DNL Data Migration Tool]
description: 瞭解如何自訂 [!DNL Data Migration Tool] 以在Magento 1和Magento 2之間傳輸擴充功能建立的資料。
exl-id: a5c1575f-9d77-416e-91fe-a82905ef2e1c
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 0%

---

# 設定[!DNL Data Migration Tool]

有時候，由[擴充功能](https://marketplace.magento.com/extensions.html)或自訂程式碼建立的資料格式和結構在Magento 1和Magento 2之間會有所不同。 使用[!DNL Data Migration Tool]內的擴充點來移轉此資料。 如果資料格式和結構相同，則工具可自動移轉資料，無需使用者介入。

在移轉期間，[Map Step](technical-specification.md#map-step)會掃描並比較所有Magento 1和Magento 2表格，包括由擴充功能建立的表格。 如果表格相同，工具會自動移轉資料。 如果表格不同，工具會終止並通知使用者。

>[!NOTE]
>
>在嘗試延伸[之前，請先閱讀](technical-specification.md)技術規格[!DNL Data Migration Tool]。 此外，請檢閱[移轉指南](../overview.md)，以瞭解使用移轉工具的一般資訊。


## 微幅資料格式和結構變更

在大多數情況下，[對應步驟](technical-specification.md#map-step)會使用`map.xml`檔案中的下列方法，充分解析次要資料格式和結構變更：

- 使用對應規則變更表格或欄位名稱
- 使用現有處理常式或自訂處理常式轉換資料格式

以下顯示同時使用對應規則和處理常式的範例。 此範例使用名為「GreatBlog」的假設Magento 1擴充功能，Magento 2已改善此功能。

```xml
<source>
    <document_rules>
        <ignore>
            <document>great_blog_index</document>
        </ignore>
        <rename>
            <document>great_blog_publication</document>
            <to>great_blog_post</to>
        </rename>
    </document_rules>
    <field_rules>
        <move>
            <field>great_blog_publication.summary</field>
            <to>great_blog_post.title</to>
        </move>
        <ignore>
            <field>great_blog_publication.priority</field>
        </ignore>
        <transform>
            <field>great_blog_publication.body</field>
            <handler class="\Migration\Handler\GreatBlog\NewFormat">
                <param name="switch" value="yes" />
            </handler>
        </transform>
    </field_rules>
</source>
<destination>
    <document_rules>
        <ignore>
            <document>great_blog_rating</document>
        </ignore>
    </document_rules>
    <field_rules>
        <ignore>
            <field>great_blog_post.rating</field>
        </ignore>
    </field_rules>
</destination>
```

- 請勿從`great_blog_index`索引資料表中移轉不必要的資料。
- 資料表`great_blog_publication`已在Magento 2中重新命名為`great_blog_post`，因此資料會移轉到新資料表。
   - `summary`欄位已重新命名為`title`，因此資料會移轉到新欄位。
   - `priority`欄位已移除，不再存在於Magento 2中。
   - `body`欄位中的資料已變更格式，應該由自訂處理常式處理： `\Migration\Handler\GreatBlog\NewFormat`。
- Magento 2已針對「GreatBlog」擴充功能開發新的評等功能。
   - 已建立新的`great_blog_rating`資料表。
   - 已建立新的`great_blog_post.rating`欄位。

### 在其他步驟中擴充對應

其他步驟支援對應，例如[EAV步驟](technical-specification.md#eav-step)和客戶屬性步驟。 這些步驟會移轉預先定義的Magento表格清單。 例如，假設「GreatBlog」擴充功能在`eav_attribute`表格中有一個額外的欄位，且名稱已在Magento 2中變更。 由於資料表是由[EAV Step](technical-specification.md#eav-step)處理，因此應針對`map-eav.xml`檔案寫入對應規則。 `map.xml`和`map-eav.xml`檔案使用相同的`map.xsd`結構描述，因此對應規則維持相同。

## 重大資料格式和結構變更

除了對應步驟之外，`config.xml`檔案中還有其他步驟會移轉具有主要格式和結構變更的資料，包括：

- [Url重寫步驟](technical-specification.md#url-rewrite-step)
- OrderGrid步驟
- [EAV步驟](technical-specification.md#eav-step)

與[對應步驟](technical-specification.md#map-step)不同，這些步驟會掃描預先定義的表格清單，而非所有表格。

如需進行重大資料格式和結構變更，請建立自訂步驟。

### 建立自訂步驟

以相同的「GreatBlog」範例來說，假設擴充功能在Magento 1中有一個表格，但經過重新設計，在Magento 2中有兩個表格。

在Magento 1中，只有單一`greatblog_post`表格：

```text
| Field     | Type     |
|-----------|----------|
| post_id   | INT      |
| title     | VARCHAR  |
| content   | TEXT     |
| author_id | SMALLINT |
| tags      | TEXT     |
```

在Magento 2中，已引入標籤`greatblog_post_tags`的新表格：

```text
| Field      | Type     |
|------------|----------|
| post_id    | INT      |
| tag        | VARCHAR  |
| sort_order | SMALLINT |
```

Magento 2 `greatblog_post`表格現在看起來像這樣：

```text
| Field     | Type     |
|-----------|----------|
| post_id   | INT      |
| title     | VARCHAR  |
| content   | TEXT     |
| author_id | SMALLINT |
```

若要將所有資料從舊表格結構移轉到新表格結構，您可以在`config.xml`檔案中建立自訂步驟。 例如：

```xml
<steps mode="data">
    ...
    <step title="GreatBlog Step">
        <integrity>Vendor\Migration\Step\GreatBlog\Integrity</integrity>
        <data>Vendor\Migration\Step\GreatBlog\Data</data>
        <volume>Vendor\Migration\Step\GreatBlog\Volume</volume>
    </step>
</steps>
<steps mode="delta">
    ...
    <step title="GreatBlog Step">
        <delta>Vendor\Migration\Step\GreatBlog\Delta</delta>
        <volume>Vendor\Migration\Step\GreatBlog\Volume</volume>
    </step>
</steps>
```

工具會根據步驟在`config.xml`檔案中的位置執行步驟；從上到下。 在我們的範例中，`GreatBlog Step`最後執行。

步驟可包含四種類別：

- 完整性檢查
- 資料傳遞
- 磁碟區檢查
- 差異傳遞

>[!NOTE]
>
>如需詳細資訊，請參考[組態](technical-specification.md#configuration)、[步驟內部](technical-specification.md#step-internals)、[階段](technical-specification.md#step-stages)和[執行模式](technical-specification.md#running-modes)。


可以在這些類別中組合複雜的SQL查詢，以擷取和移轉資料。 此外，這些資料表應在[對應步驟](technical-specification.md#map-step)中「忽略」，因為它會掃描所有現有的資料表，並嘗試移轉資料，除非資料位於`<ignore>`檔案的`map.xml`標籤中。

對於完整性檢查，請在`config.xml`檔案中定義額外的對應檔案，以驗證資料表結構是否如預期般運作。

```xml
<config xmlns:xs="http://www.w3.org/2001/XMLSchema-instance"
        xs:noNamespaceSchemaLocation="urn:magento:module:Magento_DataMigrationTool:etc/config.xsd">
    ...
    <options>
        ...
        <greatblog_map_file>app/code/Vendor/Migration/etc/opensource-to-opensource/map-greatblog.xml</greatblog_map_file>
        ...
    </options>
</config>
```

對應檔案`map-greatblog.xml`：

```xml
<map xmlns:xs="http://www.w3.org/2001/XMLSchema-instance"
     xs:noNamespaceSchemaLocation="urn:magento:module:Magento_DataMigrationTool:etc/map.xsd">
    <source>
        <field_rules>
            <ignore>
                <field>greatblog_post.tags</field>
            </ignore>
        </field_rules>
    </source>
    <destination>
        <document_rules>
            <ignore>
                <document>greatblog_post_tags</document>
            </ignore>
        </document_rules>
    </destination>
</map>
```

完整性檢查類別`Vendor\Migration\Step\GreatBlog\Integrity`延伸`Migration\App\Step\AbstractIntegrity`並包含我們驗證資料表結構的`perform`方法：

```php
class Integrity extends \Migration\App\Step\AbstractIntegrity
{
    ...
    /**
     * Integrity constructor.
     * @param ProgressBar\LogLevelProcessor $progress
     * @param Logger $logger
     * @param Config $config
     * @param ResourceModel\Source $source
     * @param ResourceModel\Destination $destination
     * @param MapFactory $mapFactory
     * @param string $mapConfigOption
     */
    public function __construct(
        ProgressBar\LogLevelProcessor $progress,
        Logger $logger,
        Config $config,
        ResourceModel\Source $source,
        ResourceModel\Destination $destination,
        MapFactory $mapFactory,
        $mapConfigOption = 'greatblog_map_file'
    ) {
        parent::__construct($progress, $logger, $config, $source, $destination, $mapFactory, $mapConfigOption);
    }

    /**
     * @inheritDoc
     */
    public function perform()
    {
        $this->progress->start($this->getIterationsCount());
        $this->check(['greatblog_post'], MapInterface::TYPE_SOURCE);
        $this->check(['greatblog_post', 'greatblog_post_tags'], MapInterface::TYPE_DEST);
        $this->progress->finish();
        return $this->checkForErrors();
    }
    ...
}
```

接下來，您必須建立一個類別，以便處理資料並儲存至Magento 2資料庫`Vendor\Migration\Step\GreatBlog\Data`：

```php
class Data implements \Migration\App\Step\StageInterface
{
    ...
    /**
     * Data constructor.
     *
     * @param ProgressBar\LogLevelProcessor $progress
     * @param ResourceModel\Source $source
     * @param ResourceModel\Destination $destination
     * @param ResourceModel\RecordFactory $recordFactory
     * @param RecordTransformerFactory $recordTransformerFactory
     * @param MapFactory $mapFactory
     */
    public function __construct(
        ProgressBar\LogLevelProcessor $progress,
        ResourceModel\Source $source,
        ResourceModel\Destination $destination,
        ResourceModel\RecordFactory $recordFactory,
        RecordTransformerFactory $recordTransformerFactory,
        MapFactory $mapFactory
    ) {
        $this->progress = $progress;
        $this->destination = $destination;
        $this->recordFactory = $recordFactory;
        $this->source = $source;
        $this->recordTransformerFactory = $recordTransformerFactory;
        $this->map = $mapFactory->create('greatblog_map_file');
    }

    /**
     * @inheritDoc
     */
    public function perform()
    {
        $sourceDocName = 'greatblog_post';
        $sourceDocument = $this->source->getDocument($sourceDocName);
        $destinationDocName = 'greatblog_post';
        $destinationDocument = $this->destination->getDocument($destinationDocName);
        /** @var \Migration\RecordTransformer $recordTransformer */
        $recordTransformer = $this->recordTransformerFactory->create(
            [
                'sourceDocument' => $sourceDocument,
                'destDocument'   => $destinationDocument,
                'mapReader'      => $this->map
            ]
        );
        $recordTransformer->init();

        $this->progress->start($this->source->getRecordsCount($sourceDocName));
        $pageNumber = 0;
        while (!empty($items = $this->source->getRecords($sourceDocName, $pageNumber))) {
            $pageNumber++;
            $recordsToSave = $destinationDocument->getRecords();
            foreach ($items as $item) {
                $sourceRecord = $this->recordFactory->create(
                    ['document' => $sourceDocument, 'data' => $item]
                );
                $destinationRecord = $this->recordFactory->create(['document' => $destinationDocument]);
                $recordTransformer->transform($sourceRecord, $destinationRecord);
                $recordsToSave->addRecord($destinationRecord);
            }
            $this->destination->saveRecords($destinationDocName, $recordsToSave);

            $tags = $this->getTags($items);
            $this->destination->saveRecords('greatblog_post_tags', $tags);
            $this->progress->advance();
        }

        $this->progress->finish();
        return true;
    }
    ...
}
```

在Volume類別`Vendor\Migration\Step\GreatBlog\Volume`中，我們會檢查資料是否已完全移轉：

```php
class Volume extends \Migration\App\Step\AbstractVolume
{
    ...
    /**
     * @inheritdoc
     */
    public function perform()
    {
        $documentName = 'greatblog_post';
        $sourceCount = $this->source->getRecordsCount($documentName);
        $destinationCount = $this->destination->getRecordsCount($documentName);
        if ($sourceCount != $destinationCount) {
            $this->errors[] = sprintf(
                'Mismatch of entities in the document: %s Source: %s Destination: %s',
                $documentName,
                $sourceCount,
                $destinationCount
            );
        }

        return $this->checkForErrors(Logger::ERROR);
    }
    ...
}
```

若要新增差異移轉功能，請在`deltalog.xml`檔案中新增群組。 在`group`中，指定必須檢查變更的資料表名稱：

```xml
<groups>
    ...
    <group name="delta_greatblog">
        <document key="post_id">greatblog_post</document>
    </group>
</groups>
```

然後，建立擴充`Delta`的`Vendor\Migration\Step\GreatBlog\Delta`類別`Migration\App\Step\AbstractDelta`：

```php
class Delta extends \Migration\App\Step\AbstractDelta
{
    /**
     * @var string
     */
    protected $mapConfigOption = 'greatblog_map_file';

    /**
     * @var string
     */
    protected $groupName = 'delta_greatblog';

    /**
     * @inheritDoc
     */
    public function perform()
    {
        $sourceDocumentName = 'greatblog_post';
        $idKeys = ['post_id'];
        $page = 0;
        while (!empty($items = $this->source->getChangedRecords($sourceDocumentName, $idKeys, $page++))) {
            $this->destination->deleteRecords(
                'greatblog_post_tags',
                $idKeys,
                $items
            );

            $tags = $this->getTags($items);
            $this->destination->saveRecords('greatblog_post_tags', $tags);
        }

        //parent class takes care of greatblog_post records automatically
        return parent::perform();
    }
}
```

在這些範例中提供的自訂步驟實作之後，系統會從單一Magento 1表格擷取資料，
使用`Vendor\Migration\Step\GreatBlog\Data`類別加以處理，並將資料儲存在兩個Magento 2表格中。 新記錄和變更記錄會在差異移轉時使用`Vendor\Migration\Step\GreatBlog\Delta`類別傳遞。

## 禁止的延伸方法

由於[!DNL Data Migration Tool]和Magento 2在不斷演化，因此現有步驟和處理常式可能會有所變更。 我們強烈建議不要藉由擴充其類別來覆寫[對應步驟](technical-specification.md#map-step)、[URL重寫步驟](technical-specification.md#url-rewrite-step)等步驟和處理常式的行為。

某些步驟不支援對應，且無法在未變更程式碼的情況下變更。 您可以在移轉結束時撰寫變更資料的額外步驟，或建立[GitHub問題](https://github.com/magento/data-migration-tool/issues)，並要求現有步驟上的新擴充點。
