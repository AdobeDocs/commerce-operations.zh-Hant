---
title: 為遠端儲存設定AWS S3貯體
description: 設定您的Commerce專案，將AWS S3儲存服務用於遠端儲存。
source-git-commit: 31078c836fb088a10712c8c4cf4430a38d1962f2
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# 為遠端儲存設定AWS S3貯體

此 [Amazon Simple Storage Service(Amazon S3)][AWS S3] 是一種物件儲存服務，提供業界領先的可擴充性、資料可用性、安全性和效能。 AWS S3服務使用貯體或容器來儲存資料。 此設定需要您建立 _私人_ 桶。 若需Adobe Commerce雲端基礎架構相關資訊，請參閱 [在雲基礎架構上為Commerce配置遠程儲存](cloud-support.md).

>[!WARNING]
>
>Adobe極不鼓勵使用公共桶，因為它構成嚴重的安全風險。

**使用AWS S3適配器啟用遠程儲存**:

1. 登入您的Amazon S3控制面板，並建立 _私人_ 桶。

1. 設定 [AWS IAM] 角色。 或者，產生存取權和機密金鑰。

1. 禁用預設資料庫儲存。

   ```bash
   bin/magento config:set system/media_storage_configuration/media_database 0
   ```

1. 設定「商務」以使用私人貯體。 請參閱 [遠程儲存選項](remote-storage.md#remote-storage-options) 以取得參數的完整清單。

   ```bash
   bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="<bucket-name>" --remote-storage-region="<region-name>" --remote-storage-prefix="<optional-prefix>" --remote-storage-key=<optional-access-key> --remote-storage-secret=<optional-secret-key> -n
   ```

1. 將媒體檔案與遠程儲存同步。

   ```bash
   bin/magento remote-storage:sync
   ```

## 配置Nginx

Nginx需要其他配置才能使用 `proxy_pass` 指令。 將下列代理資訊新增至 `nginx.conf` 檔案：

>nginx.conf

```conf
location ~* \.(ico|jpg|jpeg|png|gif|svg|js|css|swf|eot|ttf|otf|woff|woff2)$ {
    # Proxying to AWS S3 storage.
    resolver 8.8.8.8;
    set $bucket "<s3-bucket-name>";
    proxy_pass https://s3.amazonaws.com/$bucket$uri;
    proxy_pass_request_body off;
    proxy_pass_request_headers off;
    proxy_intercept_errors on;
    proxy_hide_header "x-amz-id-2";
    proxy_hide_header "x-amz-request-id";
    proxy_hide_header "x-amz-storage-class";
    proxy_hide_header "Set-Cookie";
    proxy_ignore_headers "Set-Cookie";
}
```

### 驗證

如果您使用存取權和密鑰，而非 [AWS IAM] 角色，您必須包含 [`ngx_aws_auth` Nginx模組][ngx repo].

### 權限

S3整合仰賴在本機檔案系統上產生和儲存快取影像的功能。 因此， `pub/media` 而S3的類似目錄與使用本機儲存時相同。

### 檔案操作

強烈建議您使用 [!DNL Commerce] 在您的編碼或擴充功能開發中使用檔案適配器方法，而無論檔案儲存類型為何。 將S3用於儲存時，請勿使用本機PHP檔案I/O操作，例如 `copy`, `rename`，或 `file_put_contents`，因為S3檔案不位於檔案系統內。 請參閱 [DriverInterface.php](https://github.com/magento/magento2/blob/2.4-develop/lib/internal/Magento/Framework/Filesystem/DriverInterface.php#L18) 以取得程式碼範例。

<!-- link definitions -->

[AWS S3]: https://aws.amazon.com/s3
[AWS IAM]: https://aws.amazon.com/iam/
[ngx repo]: https://github.com/anomalizer/ngx_aws_auth
