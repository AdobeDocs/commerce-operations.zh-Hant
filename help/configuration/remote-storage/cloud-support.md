---
title: 雲端基礎結構上Commerce的遠端儲存
description: 請參閱有關如何為雲端基礎結構上的Adobe Commerce設定遠端儲存空間的指南。
feature: Configuration, Cloud, Storage
exl-id: da352466-13f2-42e4-a589-3b0a89728467
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 0%

---

# 在雲端基礎結構上為Commerce設定遠端儲存

從`ece-tools`套件2002.1.5開始，您可以使用環境變數來啟用遠端儲存模組；不過，遠端儲存模組在雲端基礎結構上的Adobe Commerce上有&#x200B;_有限_&#x200B;支援。 Adobe無法完全疑難排解協力廠商儲存配接器服務。

## 環境變數

`REMOTE_STORAGE`變數用於雲端基礎結構專案的[部署階段](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html)。

### `REMOTE_STORAGE`

- **預設**—_未設定_
- **版本**—Commerce 2.4.2和更新版本

設定&#x200B;_儲存配接卡_，使用儲存服務(例如AWS S3)將媒體檔案儲存在永久性的遠端儲存容器中。 啟用遠端儲存模組，針對必須共用資源的複雜、多伺服器設定，提升雲端專案的效能。 以下是使用`.magento.env.yaml`檔案的遠端儲存設定範例：

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

### 使用雲端CLI設定變數

將`REMOTE_STORAGE`變數設為[環境層級變數](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html)，這樣就不會在生產、測試和整合環境之間共用檔案。 在環境層級設定變數，可讓您靈活地在選取的環境上僅使用遠端儲存，例如排除使用遠端儲存的整合環境。

**若要使用Cloud CLI新增遠端儲存體變數**：

```bash
magento-cloud variable:create --level environment --name REMOTE_STORAGE --json true --inheritable false --value '{"driver":"aws-s3","prefix":"uat","config":{"bucket":"aws-bucket-id","region":"eu-west-1","key":"optional-key","secret":"optional-secret"}}'
```

這會使用指定的JSON組態建立`REMOTE_STORAGE`變數。 `REMOTE_STORAGE`變數需要JSON字串才能設定遠端儲存空間。 以下是JSON設定的範例：

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

在您建立組態並部署之後，部署記錄檔應包含遠端儲存體組態的相關資訊，例如`INFO: Remote storage driver set to: "aws-s3"`

### 使用Project Web介面設定變數

或者，您可以使用Project Web介面將變數新增至適當的環境。

**若要使用Project Web介面新增遠端儲存變數**：

1. 在&#x200B;_Project Web介面_&#x200B;中，從左側選取環境。

1. 按一下&#x200B;**設定環境**&#x200B;圖示。

1. 在&#x200B;_設定環境_&#x200B;檢視中，按一下&#x200B;**變數**&#x200B;標籤。

1. 按一下&#x200B;**新增變數**。

1. 在&#x200B;_名稱_&#x200B;欄位中，輸入`REMOTE_STORAGE`

1. 在&#x200B;_Value_&#x200B;欄位中，新增JSON設定。

1. 選取&#x200B;**JSON值**&#x200B;和&#x200B;**敏感**；取消選取&#x200B;**可由子環境繼承**。

1. 按一下&#x200B;**新增變數**。

### 使用選擇性驗證

`key`和`secret`是選用專案。 當您建立變數時，可以選取`key`選項以隱藏`secret`和`sensitive`。 使用此設定時，網頁介面中不會顯示值。 請參閱[雲端基礎結構上的Commerce指南](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html#visibility)中的&#x200B;_變數可見度_。

如果您想使用不同的驗證方法，請從JSON設定中省略`key`和`secret`。 設定替代驗證方法，並確認伺服器已獲得S3儲存貯體的授權。

### 同步處理遠端儲存裝置

啟用遠端儲存模組後，將目前的媒體檔案同步至遠端存放區位置。

**若要啟動同步處理**：

1. 使用SSH登入已設定遠端儲存裝置的遠端環境。

1. 啟動同步。

```bash
bin/magento remote-storage:sync 
```

## Fastly設定

如果您選擇在雲端基礎結構專案上搭配Adobe Commerce使用遠端儲存解決方案，請使用[Fastly](https://docs.fastly.com/en/guides/amazon-s3)檔案中的&#x200B;_Amazon S3_&#x200B;指南，以確保Fastly影像最佳化可搭配AWS S3使用。

準備您的[Fastly認證](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#get-fastly-credentials)。 在Pro專案上，使用SSH連線到您的伺服器並從`/mnt/shared/fastly_tokens.txt`檔案取得Fastly認證。 測試和生產環境都有獨特的認證。 您必須取得每個環境的認證。

請繼續設定雲端專案的遠端儲存空間，完成下列工作：

1. 設定[Fastly後端整合](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/Edge-Modules/EDGE-MODULE-OTHER-CMS-INTEGRATION.md)。

1. 建立[AWS S3驗證](https://docs.fastly.com/en/guides/amazon-s3#using-an-amazon-s3-private-bucket)的VCL邏輯。

1. 為AWS S3儲存貯體[的](https://developer.fastly.com/reference/vcl/variables/backend-connection/req-backend/)後端請求建立VCL邏輯。
