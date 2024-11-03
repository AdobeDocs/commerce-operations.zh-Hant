---
title: 配置遠端存儲
description: 了解如何為本地商務應用程式配置遠端存儲模組。
feature: Configuration, Storage
exl-id: 0428f889-46b0-44c9-8bd9-98c1be797011
source-git-commit: 419a21604d1fda0a76dd0375ae2340fd6e59ec89
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 0%

---

# 配置遠端存儲

遠端存儲 模組 提供了商店媒體文件以及使用 AWS S3 等儲存服務在持久性遠端儲存容器中計劃導入和導出的選項。

默認情況下，Adobe Systems Commerce 應用程式 將媒體文件存儲在包含應用程式的同一文件系統中。 這對於複雜的多伺服器配置效率低下，並且可能導致共用資源時性能下降。 使用遠端儲存模組，您可以在目錄中商店媒體 `pub/media` 文件，並在遠端物件儲存的目錄中導入/匯出文件 `var` ，以利用伺服器端圖像大小調整。

>[!BEGINSHADEBOX]

不能同時啟用遠端儲存 _和_ 資料庫儲存。 必須先禁用資料庫儲存，然後才能啟用遠端儲存。

```bash
bin/magento config:set system/media_storage_configuration/media_database 0
```

啟用遠端儲存可能會影響您既定的開發體驗。 例如，某些PHP檔案函式可能無法如預期運作。 必須強制使用Commerce Framework進行檔案作業。 禁止的PHP原生函式清單可在[magento-coding-standard](https://github.com/magento/magento-coding-standard/blob/develop/Magento2/Sniffs/Functions/DiscouragedFunctionSniff.php)存放庫中取得。

>[!ENDSHADEBOX]

>[!INFO]
>
>- 遠端儲存僅適用於Commerce 2.4.2版和更新版本。 請參閱[2.4.2發行說明](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/magento-open-source/2-4-2)。
>
>- 遠端儲存模組在雲端基礎結構上的Adobe Commerce上有&#x200B;_限制_&#x200B;支援。 Adobe無法完全疑難排解協力廠商儲存配接器服務。 請參閱[在雲端基礎結構上設定Commerce的遠端儲存](cloud-support.md)，以取得為雲端專案實作遠端儲存的指引。

![結構描述影像](../../assets/configuration/remote-storage-schema.png)

## 遠端儲存選項

您可以使用`remote-storage`選項搭配[`setup` CLI命令](../../installation/tutorials/deployment.md)來設定遠端儲存裝置。 `remote-storage`選項使用下列語法：

```text
--remote-storage-<parameter-name>="<parameter-value>"
```

`parameter-name`參考特定的遠端儲存體引數名稱。 下表列出可用於設定遠端儲存的引數：

| 命令行參數 | 參數名稱 | 說明 | 預設值 |
|--- |--- |--- |--- |
| `remote-storage-driver` | 司機 | 適配器名稱<br>可能的值：<br>**file**：禁用遠端儲存並使用本地文件系統&#x200B;<br>**aws-s3**：使用 [Amazon 簡單存儲服務 （Amazon S3）](remote-storage-aws-s3.md) | 沒有 |
| `remote-storage-bucket` | 桶 | 物件儲存或容器名稱 | 沒有 |
| `remote-storage-prefix` | 前綴 | 選擇性首碼（物件儲存內的位置） | 空白 |
| `remote-storage-region` | 區域 | 區域名稱 | 無 |
| `remote-storage-key` | 存取金鑰 | 選用的存取金鑰 | 空白 |
| `remote-storage-secret` | 秘密金鑰 | 選擇性秘密金鑰 | 空白 |

### 存儲配接器

預設儲存位置位於本地文件系統中。 _儲存適配器_&#x200B;使您能夠連接到 儲存 服務並在任何地方商店檔。[!DNL Commerce] 支持配置以下儲存服務：

- [Amazon 簡單存儲服務 （Amazon S3）](remote-storage-aws-s3.md)

## 啟用遠端儲存

您可以在 Adobe Systems Commerce 安裝過程中安裝遠端儲存，也可以將遠端儲存添加到現有的商務執行個體。 下列範例示範使用一組`remote-storage`引數搭配Commerce `setup` CLI命令的每個方法。 至少您必須提供存放裝置`driver`、`bucket`和`region`。

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
>同步命令只會移轉`pub/media`目錄中的檔案，_不會_ `var`目錄中的匯入/匯出檔案。 請參閱&#x200B;_Commerce 2.4使用手冊_&#x200B;中的[排程匯入/匯出](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-scheduled-import-export.html)。

<!-- link definitions -->

[import-export]: https://docs.magento.com/user-guide/system/data-scheduled-import-export.html
