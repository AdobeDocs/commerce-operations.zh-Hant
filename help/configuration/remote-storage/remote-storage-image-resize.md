---
title: 為遠程儲存配置影像大小調整
description: 通過配置伺服器端影像大小來優化磁碟資源。
source-git-commit: 7fc5d561baa3c2a4aab160a35a1c8a302a62a3b1
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 為遠程儲存配置影像大小調整

依預設，Adobe Commerce支援在應用程式端調整影像大小。 但是，通過啟用遠程儲存模組，您可以使用Nginx將影像大小調整卸載到伺服器端，在伺服器端，您可以保存磁碟資源並優化磁碟使用。

下圖顯示Nginx如何在快取中擷取、調整大小和儲存影像。 重新調整大小取決於URL中包含的參數，例如高度和寬度。

![影像調整](../../assets/configuration/remote-storage-nginx-image-resize.png)

>[!TIP]
>
>如需雲端基礎架構專案的Adobe Commerce，請參閱 [在雲基礎架構上為Commerce配置遠程儲存](cloud-support.md)

## 在Adobe Commerce中設定URL格式

若要在伺服器端調整影像大小，您必須設定Adobe Commerce，以提供影像高度、寬度和位置(URL)的引數。

**為伺服器端影像調整大小配置商務**:

1. 在 _管理_ 面板，按一下 **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]**.

1. 在右窗格中，展開 **[!UICONTROL Url options]**.

1. 在 _目錄媒體URL格式_ 部分，清除 **[!UICONTROL Use system value]**.

1. 選取 `Image optimization based on query parameters` 中的URL **_目錄媒體URL格式_** 欄位。

1. 按一下 **[!UICONTROL Save Config]**.

1. 繼續 [Nginx設定](#configure-nginx).

## 配置Nginx

若要繼續設定伺服器端影像大小調整，您必須準備 `nginx.conf` 檔案，並提供 `proxy_pass` 值。

**啟用Nginx調整影像大小**:

1. 安裝 [Nginx影像濾鏡模組][nginx-module].

   ```shell
   load_module /etc/nginx/modules/ngx_http_image_filter_module.so;
   ```

1. 建立 `nginx.conf` 檔案（根據隨附的範本） `nginx.conf.sample` 檔案。 例如：

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

1. [_可選_] 設定 `proxy_pass` 值。

   - [Amazon Simple Storage Service(Amazon S3)](remote-storage-aws-s3.md)

<!-- link definitions -->

[nginx-module]: https://nginx.org/en/docs/http/ngx_http_image_filter_module.html
