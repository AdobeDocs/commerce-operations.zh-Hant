---
title: 為遠程儲存配置AWSS3儲存桶
description: 將您的Commerce項目配置為使用AWSS3儲存服務進行遠程儲存。
feature: Configuration, Storage
exl-id: e8aeade8-2ec4-4844-bd6c-ab9489d10436
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# 為遠程儲存配置AWSS3儲存桶

的 [Amazon簡單儲存服務(AmazonS3)][AWS S3] 是一種對象儲存服務，可提供業界領先的可擴充性、資料可用性、安全性和效能。 AWSS3服務使用儲存桶或容器來儲存資料。 此配置要求您建立 _私_ 桶。 有關Adobe Commerce雲基礎架構的資訊，請參閱 [在雲基礎架構上為Commerce配置遠程儲存](cloud-support.md)。

>[!WARNING]
>
>Adobe極力阻止使用公共水桶，因為這會帶來嚴重的安全風險。

**使用AWSS3適配器啟用遠程儲存**:

1. 登錄到您的AmazonS3儀表板並建立 _私_ 桶。

1. 設定 [AWSIAM] 角色。 或者，生成訪問密鑰和密鑰。

1. 禁用預設資料庫儲存。

   ```bash
   bin/magento config:set system/media_storage_configuration/media_database 0
   ```

1. 配置Commerce以使用專用儲存桶。 請參閱 [遠程儲存選項](remote-storage.md#remote-storage-options) 的子菜單。

   ```bash
   bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="<bucket-name>" --remote-storage-region="<region-name>" --remote-storage-prefix="<optional-prefix>" --remote-storage-key=<optional-access-key> --remote-storage-secret=<optional-secret-key> -n
   ```

1. 將媒體檔案與遠程儲存同步。

   ```bash
   bin/magento remote-storage:sync
   ```

## 配置Nginx

Nginx需要其他配置才能使用 `proxy_pass` 指令。 將以下代理資訊添加到 `nginx.conf` 檔案：

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

如果您使用訪問和密鑰而不是 [AWSIAM] 角色，必須包括 [`ngx_aws_auth` Nginx模組][ngx repo]。

### 權限

S3整合依賴於在本地檔案系統上生成和儲存快取映像的能力。 因此，資料夾權限 `pub/media` S3的類似目錄與使用本地儲存時相同。

### 檔案操作

強烈建議您使用 [!DNL Commerce] 在編碼或擴展開發中使用檔案適配器方法，而與檔案儲存類型無關。 在將S3用於儲存時，不要使用本機PHP檔案I/O操作，如 `copy`。 `rename`或 `file_put_contents`，因為S3檔案不在檔案系統中。 請參閱 [DriverInterface.php](https://github.com/magento/magento2/blob/2.4-develop/lib/internal/Magento/Framework/Filesystem/DriverInterface.php#L18) 的上界。

<!-- link definitions -->

[AWS S3]: https://aws.amazon.com/s3
[AWSIAM]: https://aws.amazon.com/iam/
[ngx repo]: https://github.com/anomalizer/ngx_aws_auth
