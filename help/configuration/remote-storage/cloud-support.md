---
title: 雲基礎架構上的Commerce遠程儲存
description: 請參閱有關如何在雲基礎架構上為Adobe Commerce設定遠程儲存的指導。
feature: Configuration, Cloud, Storage
exl-id: da352466-13f2-42e4-a589-3b0a89728467
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 0%

---

# 在雲基礎架構上為Commerce配置遠程儲存

從 `ece-tools` 軟體包2002.1.5，可以使用環境變數啟用遠程儲存模組；但是，遠程儲存模組 _有限_ 支援Adobe Commerce的雲基礎架構。 Adobe無法完全排除第三方儲存適配器服務的故障。

## 環境變數

的 `REMOTE_STORAGE` 變數在 [部署階段](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html) 雲基礎架構項目。

### `REMOTE_STORAGE`

- **預設**—_未設定_
- **版本**—Commerce 2.4.2及更高版本

配置 _儲存適配器_ 使用儲存服務(如AWSS3)將媒體檔案儲存在持久的遠程儲存容器中。 使遠程儲存模組能夠提高雲項目的效能，這些項目具有必須共用資源的複雜多伺服器配置。 以下是使用 `.magento.env.yaml` 檔案：

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

### 使用雲CLI設定變數

設定 `REMOTE_STORAGE` 變數 [環境級變數](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html) 這樣，檔案就不會在生產、轉移和整合環境之間共用。 在環境級別設定變數使在選定環境中僅使用遠程儲存具有靈活性，如排除遠程儲存的整合環境使用。

**使用雲CLI添加遠程儲存變數**:

```bash
magento-cloud variable:create --level environment --name REMOTE_STORAGE --json true --inheritable false --value '{"driver":"aws-s3","prefix":"uat","config":{"bucket":"aws-bucket-id","region":"eu-west-1","key":"optional-key","secret":"optional-secret"}}'
```

這將建立 `REMOTE_STORAGE` 具有指定JSON配置的變數。 的 `REMOTE_STORAGE` 變數使用JSON字串來配置遠程儲存。 以下是JSON配置示例：

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

建立配置和部署後，部署日誌應包括有關遠程儲存配置的資訊，例如 `INFO: Remote storage driver set to: "aws-s3"`

### 使用Project Web介面設定變數

或者，也可以使用Project Web介面將變數添加到相應的環境中。

**使用Project Web介面添加遠程儲存變數**:

1. 在 _Project Web介面_，從左側選擇環境。

1. 按一下 **配置環境** 表徵圖

1. 在 _配置環境_ 的 **變數** 頁籤。

1. 按一下 **添加變數**。

1. 在 _名稱_ 欄位，輸入 `REMOTE_STORAGE`

1. 在 _值_ 欄位，添加JSON配置。

1. 選擇 **JSON值** 和 **敏感**;取消 **可由子環境繼承**。

1. 按一下 **添加變數**。

### 使用可選身份驗證

的 `key` 和 `secret` 為可選項。 建立變數時，可隱藏 `key` 和 `secret` 選擇 `sensitive` 的雙曲餘切值。 使用此設定，這些值在Web介面中不可見。 請參閱 [變數可見性](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html#visibility) 的 _雲基礎架構上的商務指南_。

如果要使用其他驗證方法，請忽略 `key` 和 `secret` 從JSON配置中。 配置備用身份驗證方法，並驗證伺服器是否已授權到S3儲存桶。

### 同步遠程儲存

啟用遠程儲存模組後，將當前媒體檔案同步到遠程儲存位置。

**啟動同步**:

1. 使用SSH登錄配置了遠程儲存的遠程環境。

1. 啟動同步。

```bash
bin/magento remote-storage:sync 
```

## 快速配置

如果您選擇將遠程儲存解決方案與Adobe Commerce雲基礎架構項目配合使用，請使用 [AmazonS3](https://docs.fastly.com/en/guides/amazon-s3) 指南 _快速_ 文檔，以確保Ampliest Image Optimization與AWSS3配合使用。

準備好 [快速憑據](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#get-fastly-credentials)。 在Pro項目上，使用SSH連接到伺服器並從 `/mnt/shared/fastly_tokens.txt` 的子菜單。 暫存和生產環境具有獨特的憑據。 您必須獲取每個環境的憑據。

繼續執行以下任務，繼續為雲項目設定遠程儲存：

1. 配置 [快速後端整合](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/Edge-Modules/EDGE-MODULE-OTHER-CMS-INTEGRATION.md)。

1. 建立VCL邏輯 [AWSS3驗證](https://docs.fastly.com/en/guides/amazon-s3#using-an-amazon-s3-private-bucket)。

1. 建立VCL邏輯 [後端請求到AWSS3儲存桶](https://developer.fastly.com/reference/vcl/variables/backend-connection/req-backend/)。
