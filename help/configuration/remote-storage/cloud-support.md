---
title: 雲基礎架構上的Commerce遠程儲存
description: 請參閱如何在雲端基礎架構上為Adobe Commerce設定遠端儲存的指引。
source-git-commit: 2080950852e3c4e6da556733e56f68e0e8005530
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 0%

---


# 在雲基礎架構上為Commerce配置遠程儲存

從 `ece-tools` 包2002.1.5，可以使用環境變數來啟用遠程儲存模組；但是，遠程儲存模組已 _有限_ 支援Adobe Commerce雲端基礎架構。 Adobe無法完全排除第三方儲存適配器服務的故障。

## 環境變數

此 `REMOTE_STORAGE` 變數 [部署階段](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html) 雲基礎設施項目。

### `REMOTE_STORAGE`

- **預設**—_未設定_
- **版本**- Commerce 2.4.2和更新版本

設定 _儲存適配器_ 使用儲存服務(如AWS S3)將媒體檔案儲存在永久、遠端的儲存容器中。 啟用遠程儲存模組，以通過必須共用資源的複雜多伺服器配置來改進雲項目的效能。 以下是使用 `.magento.env.yaml` 檔案：

```yaml
stage:
  deploy:
    REMOTE_STORAGE:
      driver: aws-s3 # Required
      prefix: cloud # Optional
      config:
        bucket: my-bucket # Required
        region: my-region # Required
        key: my-key # Optional
        secret: my-secret-key # Optional
```

### 使用Cloud CLI設定變數

設定 `REMOTE_STORAGE` 變數作為 [環境層級變數](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html) 如此一來，檔案就不會在生產、測試和整合環境之間共用。 在環境級別設定變數可靈活地僅在選定環境中使用遠程儲存，例如排除遠程儲存的整合環境使用。

**使用雲CLI添加遠程儲存變數**:

```bash
magento-cloud variable:create --level environment --name REMOTE_STORAGE --json true --inheritable false --value '{"driver":"aws-s3","prefix":"uat","config":{"bucket":"aws-bucket-id","region":"eu-west-1","key":"optional-key","secret":"optional-secret"}}'
```

這會建立 `REMOTE_STORAGE` 變數和指定的JSON設定。 此 `REMOTE_STORAGE` 變數會使用JSON字串來設定遠端儲存。 以下是JSON設定的範例：

```json
{
  "driver": "aws-s3",
  "prefix": "uat",
  "config": {
    "bucket": "aws-bucket-id",
    "region": "aws-region-id",
    "key": "optional-key",
    "secret": "optional-secret"
  }
}
```

建立配置並部署後，部署日誌應包括有關遠程儲存配置的資訊，例如 `INFO: Remote storage driver set to: "aws-s3"`

### 使用Project Web介面設定變數

或者，您也可以使用專案網頁介面，將變數新增至適當的環境。

**使用Project Web介面添加遠程儲存變數**:

1. 在 _項目Web介面_，請從左側選取環境。

1. 按一下 **配置環境** 表徵圖。

1. 在 _配置環境_ 檢視，按一下 **變數** 標籤。

1. 按一下 **新增變數**.

1. 在 _名稱_ 欄位，輸入 `env:REMOTE_STORAGE`

1. 在 _值_ 欄位中新增JSON設定。

1. 選擇 **JSON值** 和 **敏感**;取消選取 **可由子環境繼承**.

1. 按一下 **新增變數**.

### 使用可選驗證

此 `key` 和 `secret` 為選填。 建立變數時，您可以隱藏 `key` 和 `secret` 選取 `sensitive` 選項。 使用此設定，這些值在Web介面中不可見。 請參閱 [變數可見性](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html#visibility) 在 _雲端基礎架構商務指南_.

如果您想使用不同的驗證方法，請忽略 `key` 和 `secret` 從JSON設定。 設定替代驗證方法，並確認伺服器已授權給S3儲存貯體。

### 同步遠程儲存

啟用遠程儲存模組後，將當前媒體檔案同步到遠程儲存位置。

**啟動同步**:

1. 使用SSH登錄配置了遠程儲存的遠程環境。

1. 啟動同步。

```bash
bin/magento remote-storage:sync 
```

## 快速配置

如果您選擇將遠程儲存解決方案與雲基礎架構項目上的Adobe Commerce一起使用，請使用 [Amazon S3](https://docs.fastly.com/en/guides/amazon-s3) 指南 _快_ 說明檔案，確保Ambey Image Optimization可搭配AWS S3運作。

為您的 [Amply憑據](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#get-fastly-credentials). 在Pro專案上，使用SSH連線至您的伺服器，並從 `/mnt/shared/fastly_tokens.txt` 檔案。 測試和生產環境具有唯一的憑證。 您必須取得每個環境的憑證。

繼續為雲項目設定遠程儲存，執行以下任務：

1. 設定 [Mobbleyd後端整合](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/Edge-Modules/EDGE-MODULE-OTHER-CMS-INTEGRATION.md).

1. 為建立VCL邏輯 [AWS S3驗證](https://docs.fastly.com/en/guides/amazon-s3#using-an-amazon-s3-private-bucket).

1. 為建立VCL邏輯 [傳送至AWS S3儲存貯體的後端請求](https://developer.fastly.com/reference/vcl/variables/backend-connection/req-backend/).
