---
title: 自定義 [!DNL Data Migration Tool]
description: 瞭解如何自定義 [!DNL Data Migration Tool] 在Magento1和Magento2之間傳送擴展建立的資料。
exl-id: a5c1575f-9d77-416e-91fe-a82905ef2e1c
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 0%

---

# 配置 [!DNL Data Migration Tool]

有時，建立的資料格式和結構 [擴展](https://marketplace.magento.com/extensions.html) 或自定義代碼在Magento1和Magento2之間不同。 使用 [!DNL Data Migration Tool] 遷移此資料。 如果資料格式和結構相同，該工具可以自動遷移資料而無需用戶干預。

遷移期間， [映射步驟](technical-specification.md#map-step) 掃描並比較所有Magento1和Magento2表，包括由擴展建立的表。 如果表相同，工具將自動遷移資料。 如果表不同，則工具終止並通知用戶。

>[!NOTE]
>
>閱讀 [技術規格](technical-specification.md) 在嘗試擴展 [!DNL Data Migration Tool]。 另外，請查看 [遷移指南](../overview.md) 的子菜單。


## 少量資料格式和結構更改

在大多數情況下， [映射步驟](technical-specification.md#map-step) 充分解決次要資料格式和結構更改問題，在 `map.xml` 檔案：

- 使用映射規則更改表名或欄位名
- 使用現有處理程式或自定義處理程式轉換資料格式

下面顯示了使用映射規則和處理程式的示例。 此示例使用一個假設的Magento1副檔名「GreatBlog」，該副檔名已對Magento2進行了改進。

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

- 不從遷移 `great_blog_index` 索引表。
- 表格 `great_blog_publication` 已更名為 `great_blog_post` 在Magento2中，因此資料將遷移到新表中。
   - 的 `summary` 欄位已更名為 `title`，因此資料將遷移到新欄位。
   - 的 `priority` 欄位已刪除，Magento2中不再存在。
   - 中的資料 `body` 欄位已更改格式，應由自定義處理程式處理： `\Migration\Handler\GreatBlog\NewFormat`。
- 為第2Magento的「GreatBlog」分機開發了新的評級功能。
   - 新 `great_blog_rating` 已建立表。
   - 新 `great_blog_post.rating` 已建立。

### 在其他步驟中擴展映射

其他步驟支援映射，如 [EAV步驟](technical-specification.md#eav-step) 和客戶屬性步驟。 這些步驟將遷移預定義的Magento表清單。 例如，假設「GreatBlog」擴展在 `eav_attribute` 和第2Magento中更改的名稱。 由於表由 [EAV步驟](technical-specification.md#eav-step)，應為 `map-eav.xml` 的子菜單。 的 `map.xml` 和 `map-eav.xml` 檔案使用相同 `map.xsd` 架構，因此映射規則保持不變。

## 主要資料格式和結構更改

除了「映射步驟」(Map Step)外，還有其他步驟 `config.xml` 遷移資料的檔案，其格式和結構發生了重大變化，包括：

- [URL重寫步驟](technical-specification.md#url-rewrite-step)
- 順序網格步驟
- [EAV步驟](technical-specification.md#eav-step)

與 [映射步驟](technical-specification.md#map-step)，這些步驟將掃描預定義的表清單，而不是所有表。

對於主要資料格式和結構更改，請建立自定義步驟。

### 建立自定義步驟

使用同一「GreatBlog」示例，假設副檔名在Magento1中有一個表，但重新設計為在Magento2中有兩個表。

在Magento1中， `greatblog_post` 表：

```text
| Field     | Type     |
|-----------|----------|
| post_id   | INT      |
| title     | VARCHAR  |
| content   | TEXT     |
| author_id | SMALLINT |
| tags      | TEXT     |
```

在Magento2中，標籤的新表 `greatblog_post_tags` 介紹：

```text
| Field      | Type     |
|------------|----------|
| post_id    | INT      |
| tag        | VARCHAR  |
| sort_order | SMALLINT |
```

Magento2 `greatblog_post` 表現在如下所示：

```text
| Field     | Type     |
|-----------|----------|
| post_id   | INT      |
| title     | VARCHAR  |
| content   | TEXT     |
| author_id | SMALLINT |
```

要將所有資料從舊表結構遷移到新表結構，可以在 `config.xml` 的子菜單。 例如：

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

刀具根據其在 `config.xml` 檔案；從上到下。 在我們的例子中， `GreatBlog Step` 最後一個。

步驟可包括四類類：

- 完整性檢查
- 資料傳遞
- 卷檢查
- 增量交付

>[!NOTE]
>
>請參閱 [配置](technical-specification.md#configuration)。 [步驟內部](technical-specification.md#step-internals)。 [階段](technical-specification.md#step-stages), [運行模式](technical-specification.md#running-modes) 的子菜單。


可以在這些類內組裝複雜的SQL查詢以提取和遷移資料。 此外，應在 [映射步驟](technical-specification.md#map-step) 因為它會掃描所有現有表並嘗試遷移資料，除非它位於 `<ignore>` 標籤 `map.xml` 的子菜單。

對於完整性檢查，在 `config.xml` 檔案，以驗證表結構是否與預期相同。

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

映射檔案 `map-greatblog.xml`:

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

完整性檢查類 `Vendor\Migration\Step\GreatBlog\Integrity` 延伸 `Migration\App\Step\AbstractIntegrity` 包含 `perform` 驗證表結構的方法：

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

接下來，必須建立一個類以處理資料並將資料保存到Magento2資料庫 `Vendor\Migration\Step\GreatBlog\Data`:

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

在卷類中 `Vendor\Migration\Step\GreatBlog\Volume`，我們檢查資料是否已完全遷移：

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

要添加增量遷移功能，請向 `deltalog.xml` 的子菜單。 在 `group`，指定必須檢查的表的名稱以進行更改：

```xml
<groups>
    ...
    <group name="delta_greatblog">
        <document key="post_id">greatblog_post</document>
    </group>
</groups>
```

然後，建立 `Delta` 類 `Vendor\Migration\Step\GreatBlog\Delta` 延伸 `Migration\App\Step\AbstractDelta`:

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

在示例中提供的自定義步驟實現後，系統從單個Magento1表中獲取資料，並使用 `Vendor\Migration\Step\GreatBlog\Data` 將資料儲存在兩個Magento2表中。 在增量遷移時使用 `Vendor\Migration\Step\GreatBlog\Delta` 類。

## 禁止的擴展方法

自 [!DNL Data Migration Tool] Magento2不斷演變，現有步驟和操作人員也會發生變化。 我們強烈建議不要覆蓋像 [映射步驟](technical-specification.md#map-step)。 [URL重寫步驟](technical-specification.md#url-rewrite-step)和處理程式，方法是擴展其類。

某些步驟不支援映射，如果不更改代碼，則無法更改。 您可以在遷移結束時編寫一個額外步驟來更改資料，也可以建立 [GitHub問題](https://github.com/magento/data-migration-tool/issues) 並在現有步驟上要求新的擴展點。
