---
title: 雲基礎架構上的Commerce遠程儲存
description: 請參閱如何在雲端基礎架構上為Adobe Commerce設定遠端儲存的指引。
source-git-commit: 9a5993c9a65ad210f1a9682734730f235bbc3d44
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 0%

---


# 在雲基礎架構上為Commerce配置遠程儲存

如果您選擇將遠程儲存解決方案與雲基礎架構項目上的Adobe Commerce一起使用，請使用 [Amazon S3](https://docs.fastly.com/en/guides/amazon-s3) 指南 _快_ 說明檔案，確保Ambey Image Optimization可搭配AWS S3運作。

為您的 [Amply憑據](https://devdocs.magento.com/cloud/cdn/configure-fastly.html#cloud-fastly-creds). 在Pro專案上，使用SSH連線至您的伺服器，並從 `/mnt/shared/fastly_tokens.txt` 檔案。 測試和生產環境具有唯一的憑證。 您必須取得每個環境的憑證。

繼續為雲項目設定遠程儲存，執行以下任務：

1. 設定 [Mobbleyd後端整合](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/Edge-Modules/EDGE-MODULE-OTHER-CMS-INTEGRATION.md).

1. 為建立VCL邏輯 [AWS S3驗證](https://docs.fastly.com/en/guides/amazon-s3#using-an-amazon-s3-private-bucket).

1. 為建立VCL邏輯 [傳送至AWS S3儲存貯體的後端請求](https://developer.fastly.com/reference/vcl/variables/backend-connection/req-backend/).
