---
title: 配置遠程儲存
description: 了解如何為本地Commerce應用程式配置遠程儲存模組。
source-git-commit: 9a5993c9a65ad210f1a9682734730f235bbc3d44
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 0%

---

# 配置遠程儲存

遠端儲存模組提供儲存媒體檔案的選項，並可使用儲存服務(例如AWS S3)，將匯入和匯出排程在永久、遠端的儲存容器中。 預設情況下，Adobe Commerce應用程式將媒體檔案儲存在包含該應用程式的同一檔案系統中。 對於複雜的多伺服器配置而言，這是低效的，並且在共用資源時可能會導致效能降低。 使用遠程儲存模組，您可以將媒體檔案儲存在 `pub/media` 目錄和匯入/匯出檔案 `var` 遠程對象儲存的目錄，以利用伺服器端影像大小調整。

>[!INFO]
>
>遠程儲存僅適用於Commerce 2.4.2版和更新版本。 請參閱 [2.4.2發行說明](https://devdocs.magento.com/guides/v2.4/release-notes/open-source-2-4-2.html).

>[!INFO]
>
>遠程儲存模組具有 _有限_ 支援Adobe Commerce雲端基礎架構。 Adobe無法完全排除第三方儲存適配器服務的故障。 請參閱 [在雲基礎架構上為Commerce配置遠程儲存](cloud-support.md) 用於指導為雲項目實施遠程儲存。

![綱要影像](../../assets/configuration/remote-storage-schema.png)

## 遠程儲存選項

您可以使用 `remote-storage` 選項 [`setup` CLI命令](../../installation/tutorials/deployment.md). 此 `remote-storage` 選項使用下列語法：

```text
--remote-storage-<parameter-name>="<parameter-value>"
```

此 `parameter-name` 指特定的遠程儲存參數名稱。 下表列出了可用於配置遠程儲存的參數：

| 命令列參數 | 參數名稱 | 說明 | 預設值 |
|--- |--- |--- |--- |
| `remote-storage-driver` | 驅動程式 | 適配器名稱<br>可能的值：<br>**檔案**:禁用遠程儲存並使用本地檔案系統&#x200B;<br>**aws-s3**:使用 [Amazon Simple Storage Service(Amazon S3)](remote-storage-aws-s3.md) | 無 |
| `remote-storage-bucket` | 貯體 | 對象儲存或容器名稱 | 無 |
| `remote-storage-prefix` | 前置詞 | 可選前置詞（物件儲存內的位置） | 空白 |
| `remote-storage-region` | 地區 | 地區名稱 | 無 |
| `remote-storage-key` | 存取金鑰 | 可選訪問密鑰 | 空白 |
| `remote-storage-secret` | 密鑰 | 可選密鑰 | 空白 |

### 儲存適配器

預設儲存位置位於本地檔案系統中。 A _儲存適配器_ 使您能夠連接到儲存服務並將檔案儲存到任何位置。 [!DNL Commerce] 支援配置以下儲存服務：

- [Amazon Simple Storage Service(Amazon S3)](remote-storage-aws-s3.md)

## 啟用遠程儲存

您可以在Adobe Commerce安裝期間安裝遠端儲存，或將遠端儲存新增至現有的Commerce執行個體。 下列範例示範每個方法使用 `remote-storage` 搭配商務使用的參數 `setup` CLI命令。 至少，你必須提供儲存 `driver`, `bucket`，和 `region`.

- 範例：使用遠程儲存安裝商務

   ```bash
   bin/magento setup:install --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
   ```

- 範例：在現有商務上啟用遠程儲存

   ```bash
   bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
   ```

>[!TIP]
>
>若需Adobe Commerce雲端基礎架構相關資訊，請參閱 [在雲基礎架構上為Commerce配置遠程儲存](cloud-support.md).

## 限制

不能同時啟用遠程儲存和資料庫儲存。 如果使用遠程儲存，則禁用資料庫儲存。

```bash
bin/magento config:set system/media_storage_configuration/media_database 0
```

啟用遠程儲存可能會影響您已建立的開發體驗。 例如，某些PHP檔案函式可能無法如預期般運作。 必須強制使用Commerce Framework執行檔案操作。

禁止的PHP本機函式清單可在 [magento-coding-standard存放庫][code-standard].

## 移轉內容

為特定適配器啟用遠程儲存後，可以使用CLI遷移現有 _媒體_ 檔案傳送至遠端儲存。

```bash
./magento2ce/bin/magento remote-storage:sync
```

>[!INFO]
>
>sync命令只遷移 `pub/media` 目錄， _not_ 匯入/匯出 `var` 目錄。 請參閱 [排程匯入/匯出][import-export] 在 _Commerce 2.4使用手冊_.

<!-- link definitions -->

[import-export]: https://docs.magento.com/user-guide/system/data-scheduled-import-export.html
[code-standard]: https://github.com/magento/magento-coding-standard/blob/develop/Magento2/Sniffs/Functions/DiscouragedFunctionSniff.php
