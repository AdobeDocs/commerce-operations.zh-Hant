---
title: 自定義基目錄路徑
description: 使用MAGE_DIRS變數設定絕對路徑陣列。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 0%

---


# 基本目錄路徑

的 `MAGE_DIRS` 環境變數允許您指定Commerce應用程式用於構建到各種檔案或生成URL的絕對路徑的自定義基目錄路徑和基URL片段。

## 設定MAGE_DIRS

指定鍵為常數的關聯陣列 [\\Magento\\App\\Filesystem\\DirectoryList][directory-list] 值分別是目錄的絕對路徑或其URL路徑。

可以設定 `MAGE_DIRS` 以下列任何方式執行：

- [設定引導參數的值](../bootstrap/set-parameters.md)
- 使用自定義入口點指令碼，如：

   ```php
   <?php
   /**
    * Copyright © Magento, Inc. All rights reserved.
    * See COPYING.txt for license details.
    */
   
   use Magento\Framework\App\Bootstrap;
   use Magento\Framework\App\Filesystem\DirectoryList;
   use Magento\Framework\App\Http;
   
   require __DIR__ . '/app/bootstrap.php';
   $params = $_SERVER;
   $params[Bootstrap::INIT_PARAM_FILESYSTEM_DIR_PATHS] = [
        DirectoryList::PUB => [DirectoryList::URL_PATH => ''],
        DirectoryList::MEDIA => [DirectoryList::PATH => '/mnt/nfs/media', DirectoryList::URL_PATH => ''],
        DirectoryList::STATIC_VIEW => [DirectoryList::URL_PATH => 'static'],
        DirectoryList::UPLOAD => [DirectoryList::URL_PATH => '/mnt/nfs/media/upload'],
        DirectoryList::CACHE => [DirectoryList::PATH => '/mnt/nfs/cache'],
   ];
   $bootstrap = Bootstrap::create(BP, $params);
   /** @var Http $app */
   $app = $bootstrap->createApplication(Http::class);
   $bootstrap->run($app);
   ```

上面的示例為 `[cache]` 和 `[media]` 目錄 `/mnt/nfs/cache` 和 `/mnt/nfs/media`的下界。

<!-- link definitions -->

[directory-list]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Filesystem/DirectoryList.php
