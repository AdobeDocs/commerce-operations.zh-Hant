---
title: 設定遠端儲存
description: 瞭解如何為內部部署Commerce應用程式設定遠端儲存模組。
feature: Configuration, Storage
exl-id: 0428f889-46b0-44c9-8bd9-98c1be797011
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 0%

---

# 設定遠端儲存

「遠端儲存」模組提供儲存媒體檔案的選項，並可使用儲存服務(例如AWS S3)在永久性的遠端儲存容器中排程匯入和匯出。

依預設，Adobe Commerce應用程式會將媒體檔案儲存在包含該應用程式的相同檔案系統中。 對於複雜的多伺服器設定，這會造成低效率，並可能導致共用資源時效能降低。 使用遠端儲存模組，您可以將媒體檔案儲存在`pub/media`目錄中，並將匯入/匯出檔案儲存在遠端物件儲存的`var`目錄中，以利用伺服器端影像大小調整功能。

>[!BEGINSHADEBOX]

您無法同時啟用遠端存放區&#x200B;_和_&#x200B;資料庫存放區。 您必須先停用資料庫儲存，才能啟用遠端儲存。

```bash
bin/magento config:set system/media_storage_configuration/media_database 0
```

啟用遠端儲存可能會影響您既定的開發體驗。 例如，某些PHP檔案函式可能無法如預期運作。 必須強制使用Commerce Framework進行檔案作業。 禁止的PHP原生函式清單可在[magento-coding-standard](https://github.com/magento/magento-coding-standard/blob/develop/Magento2/Sniffs/Functions/DiscouragedFunctionSniff.php)存放庫中取得。

>[!ENDSHADEBOX]

>[!INFO]
>
>- 遠端儲存僅適用於Commerce 2.4.2版和更新版本。 請參閱[2.4.2發行說明](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/release/notes/magento-open-source/2-4-2)。
>
>- 遠端儲存模組在雲端基礎結構上的Adobe Commerce上有&#x200B;_限制_&#x200B;支援。 Adobe無法完全疑難排解協力廠商儲存配接器服務。 請參閱[在雲端基礎結構上設定Commerce的遠端儲存](cloud-support.md)，以取得為雲端專案實作遠端儲存的指引。

![說明本機與雲端儲存體之間關係的遠端儲存體設定結構描述圖](../../assets/configuration/remote-storage-schema.png)

## 遠端儲存選項

您可以使用`remote-storage`選項搭配[`setup` CLI命令](../../installation/tutorials/deployment.md)來設定遠端儲存裝置。 `remote-storage`選項使用下列語法：

```text
--remote-storage-<parameter-name>="<parameter-value>"
```

`parameter-name`參考特定的遠端儲存體引數名稱。 下表列出可用於設定遠端儲存的引數：

| 命令列引數 | 引數名稱 | 說明 | 預設值 |
|--- |--- |--- |--- |
| `remote-storage-driver` | 驅動程式 | 介面卡名稱<br>可能的值： <br>**檔案**：停用遠端儲存體並使用本機檔案系統&#x200B;<br>**aws-s3**：使用[Amazon Simple Storage Service (Amazon S3)](remote-storage-aws-s3.md) | 無 |
| `remote-storage-bucket` | 貯體 | 物件儲存或容器名稱 | 無 |
| `remote-storage-prefix` | 前置詞 | 選擇性首碼（物件儲存內的位置） | 空白 |
| `remote-storage-region` | 區域 | 區域名稱 | 無 |
| `remote-storage-key` | 存取金鑰 | 選用的存取金鑰 | 空白 |
| `remote-storage-secret` | 秘密金鑰 | 選擇性秘密金鑰 | 空白 |

### 儲存配接卡

預設儲存位置位於本機檔案系統中。 _儲存配接卡_&#x200B;可讓您連線至儲存服務，並將您的檔案存放於任何地方。 [!DNL Commerce]支援設定下列儲存服務：

- [Amazon Simple Storage Service (Amazon S3)](remote-storage-aws-s3.md)

## 啟用遠端儲存

您可以在Adobe Commerce安裝期間安裝遠端儲存裝置，或將遠端儲存裝置新增至現有的Commerce執行個體。 下列範例示範使用一組`remote-storage`引數搭配Commerce `setup` CLI命令的每個方法。 至少您必須提供存放裝置`driver`、`bucket`和`region`。

- 範例：使用遠端儲存裝置安裝Commerce

  ```bash
  bin/magento setup:install --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
  ```

- 範例：在現有Commerce上啟用遠端儲存

  ```bash
  bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
  ```

>[!TIP]
>
>如需雲端基礎結構上的Adobe Commerce，請參閱[在雲端基礎結構上設定Commerce的遠端儲存空間](cloud-support.md)。

## 移轉內容

為特定介面卡啟用遠端存放裝置後，您可以使用CLI將現有的&#x200B;_媒體_&#x200B;檔案移轉至遠端存放裝置。

```bash
./magento2ce/bin/magento remote-storage:sync
```

>[!INFO]
>
>同步命令只會移轉`pub/media`目錄中的檔案，_不會_ `var`目錄中的匯入/匯出檔案。 請參閱[Commerce 2.4使用手冊](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-scheduled-import-export.html?lang=zh-Hant)中的&#x200B;_排程匯入/匯出_。

