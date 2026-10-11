---
title: 自訂基底目錄路徑
description: 使用MAGE_DIRS變數來設定絕對路徑的陣列。
exl-id: ee8e1a3a-f1d4-412c-8767-16447113f0cd
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%
---
# 基底目錄路徑

`MAGE_DIRS`環境變數可讓您指定自訂基底目錄路徑和基底URL的片段，Commerce應用程式會使用這些路徑建立各種檔案的絕對路徑或產生URL。

## 設定MAGE_DIRS

指定關聯陣列，其中索引鍵是來自[\\Magento\\App\\Filesystem\\DirectoryList](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Filesystem/DirectoryList.php)的常數，而值分別是目錄的絕對路徑或其URL路徑。

您可以透過下列任何方式設定`MAGE_DIRS`：

- [設定啟動程式引數的值](../bootstrap/set-parameters.md)
- 使用自訂進入點指令碼，如下所示：

  ```php
  <?php
  /**
   * Copyright [first year code created] Adobe
   * All Rights Reserved.
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

上述範例分別將`[cache]`和`[media]`目錄的路徑設定為`/mnt/nfs/cache`和`/mnt/nfs/media`。

