---
title: 配置遠程儲存
description: 瞭解如何為本地Commerce應用程式配置遠程儲存模組。
exl-id: 0428f889-46b0-44c9-8bd9-98c1be797011
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 0%

---

# 配置遠程儲存

遠程儲存模組提供了使用儲存服務(如AWSS3)將媒體檔案儲存並安排在持久的遠程儲存容器中導入和導出的選項。 預設情況下，Adobe Commerce應用程式將媒體檔案儲存在包含該應用程式的同一檔案系統中。 對於複雜的多伺服器配置而言，這是低效的，並且在共用資源時會導致效能降低。 使用遠程儲存模組，可以將媒體檔案儲存在 `pub/media` 目錄和導入/導出檔案 `var` 遠程對象儲存的目錄以利用伺服器端影像調整大小。

>[!INFO]
>
>遠程儲存僅適用於Commerce 2.4.2及更高版本。 查看 [2.4.2發行說明](https://devdocs.magento.com/guides/v2.4/release-notes/open-source-2-4-2.html)。

>[!INFO]
>
>遠程儲存模組具有 _有限_ 支援Adobe Commerce的雲基礎架構。 Adobe無法完全排除第三方儲存適配器服務的故障。 請參閱 [在雲基礎架構上為Commerce配置遠程儲存](cloud-support.md) 用於指導為雲項目實施遠程儲存。

![模式影像](../../assets/configuration/remote-storage-schema.png)

## 遠程儲存選項

您可以使用 `remote-storage` 選項 [`setup` CLI命令](../../installation/tutorials/deployment.md)。 的 `remote-storage` 選項使用以下語法：

```text
--remote-storage-<parameter-name>="<parameter-value>"
```

的 `parameter-name` 引用特定的遠程儲存參數名稱。 下表列出了可用於配置遠程儲存的參數：

| 命令行參數 | 參數名稱 | 說明 | 預設值 |
|--- |--- |--- |--- |
| `remote-storage-driver` | 驅動程式 | 適配器名稱<br>可能的值：<br>**檔案**:禁用遠程儲存並使用本地檔案系統&#x200B;<br>**aws-s3**:使用 [Amazon簡單儲存服務(AmazonS3)](remote-storage-aws-s3.md) | 無 |
| `remote-storage-bucket` | 桶 | 對象儲存或容器名稱 | 無 |
| `remote-storage-prefix` | 前置詞 | 可選前置詞（對象儲存內部的位置） | 空 |
| `remote-storage-region` | 區域 | 區域名稱 | 無 |
| `remote-storage-key` | 訪問密鑰 | 可選訪問密鑰 | 空 |
| `remote-storage-secret` | 密鑰 | 可選密鑰 | 空 |

### 儲存適配器

預設儲存位置位於本地檔案系統中。 A _儲存適配器_ 使您能夠連接到儲存服務並將檔案儲存到任何位置。 [!DNL Commerce] 支援配置以下儲存服務：

- [Amazon簡單儲存服務(AmazonS3)](remote-storage-aws-s3.md)

## 啟用遠程儲存

您可以在Adobe Commerce安裝期間安裝遠程儲存，或將遠程儲存添加到現有Commerce實例。 以下示例說明使用一組 `remote-storage` 與Commerce一起使用的參數 `setup` CLI命令。 至少，你必須提供 `driver`。 `bucket`, `region`。

- 示例：使用遠程儲存安裝Commerce

   ```bash
   bin/magento setup:install --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
   ```

- 示例：在現有Commerce上啟用遠程儲存

   ```bash
   bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
   ```

>[!TIP]
>
>有關Adobe Commerce雲基礎架構的資訊，請參閱 [在雲基礎架構上為Commerce配置遠程儲存](cloud-support.md)。

## 限制

不能同時啟用遠程儲存和資料庫儲存。 如果使用遠程儲存，請禁用資料庫儲存。

```bash
bin/magento config:set system/media_storage_configuration/media_database 0
```

啟用遠程儲存可能會影響您已建立的開發體驗。 例如，某些PHP檔案函式可能無法按預期工作。 必須強制使用Commerce Framework執行檔案操作。

禁止的PHP本機函式清單可在 [Magento編碼標準庫][code-standard]。

## 遷移內容

為特定適配器啟用遠程儲存後，可以使用CLI遷移現有 _媒體_ 檔案到遠程儲存。

```bash
./magento2ce/bin/magento remote-storage:sync
```

>[!INFO]
>
>sync命令僅遷移 `pub/media` 目錄， _不_ 導入/導出檔案 `var` 的子菜單。 請參閱 [計畫導入/導出][import-export] 的 _《 Commerce 2.4使用手冊》_。

<!-- link definitions -->

[import-export]: https://docs.magento.com/user-guide/system/data-scheduled-import-export.html
[code-standard]: https://github.com/magento/magento-coding-standard/blob/develop/Magento2/Sniffs/Functions/DiscouragedFunctionSniff.php
