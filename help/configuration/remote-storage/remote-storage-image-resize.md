---
title: 為遠程儲存配置影像大小調整
description: 通過配置伺服器端影像大小來優化磁碟資源。
source-git-commit: 96fe0c5eeaa029347c829c39547ee5e473c8d04d
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 1%

---

# 為遠程儲存配置影像大小調整

預設情況下， [!DNL Commerce] 支援在應用程式端調整影像大小。 但是，通過啟用遠程儲存模組，您可以使用Nginx將影像大小調整卸載到伺服器端，在伺服器端可以節省磁碟資源並優化磁碟使用。

下圖顯示了Nginx如何檢索、調整影像大小和在快取中儲存影像。 調整大小由URL中包含的參數（如高度和寬度）決定。

![調整影像大小](../../assets/configuration/remote-storage-nginx-image-resize.png)

## 在中配置URL格式 [!DNL Commerce]

要調整伺服器端影像的大小，必須配置Commerce以提供影像的高度、寬度和位置(URL)參數。

**配置Commerce以調整伺服器端影像大小**:

1. 在 _管理_ 面板，按一下 **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]**。

1. 在右窗格中，展開 **[!UICONTROL Url options]**。

1. 在 _編錄媒體URL格式_ 部分，清除 **[!UICONTROL Use system value]**。

1. 選擇 `Image optimization based on query parameters` 中的URL **_編錄媒體URL格式_** 的子菜單。

1. 按一下 **[!UICONTROL Save Config]**.

1. 繼續 [Nginx配置](#configure-nginx)。

## 配置Nginx

要繼續配置伺服器端影像大小調整，必須準備 `nginx.conf` 檔案和提供 `proxy_pass` 值。

**啟用Nginx調整影像大小**:

1. 安裝 [Nginx影像濾波模組][nginx-module]。

   ```shell
   load_module /etc/nginx/modules/ngx_http_image_filter_module.so;
   ```

1. 建立 `nginx.conf` 基於包含的模板的檔案 `nginx.conf.sample` 的子菜單。 例如：

   ```conf
   location ~* \.(jpg|jpeg|png|gif|webp)$ {
       set $width "-";
       set $height "-";
       if ($arg_width != '') {
           set $width $arg_width;
       }
       if ($arg_height != '') {
           set $height $arg_height;
       }
       image_filter resize $width $height;
       image_filter_jpeg_quality 90;
   }
   ```

1. [_可選_] 配置 `proxy_pass` 特定適配器的值。

   - [Amazon簡單儲存服務(AmazonS3)](remote-storage-aws-s3.md)

<!-- link definitions -->

[nginx-module]: https://nginx.org/en/docs/http/ngx_http_image_filter_module.html
