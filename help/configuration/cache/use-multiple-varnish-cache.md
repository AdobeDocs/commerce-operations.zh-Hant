---
title: 使用多個清漆執行個體進行快取清除
description: 瞭解快取清除如何與Adobe Commerce中的多個Varnish執行個體搭配運作。 探索設定和管理最佳實務。
feature: Configuration, Cache
exl-id: 289a4e54-9e73-454c-bfb9-e78e405af56c
badgePaas: label="內部部署" type="Informative" url="https://experienceleague.adobe.com/zh-hant/docs/commerce/user-guides/product-solutions" tooltip="僅適用於Adobe Commerce內部部署專案。"
autotag-review: '2026-06-22T22:16:50.500Z'
TQID: 'https://experienceleague.adobe.com/GeX8wkpM1rLLWM7jMhP2r-SJ8uV-x7fLXC8WEazZQDo'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%
---
# 使用多個Varnish執行個體進行快取清除

Adobe Commerce可支援多個Varnish執行個體。

本主題說明使用Commerce設定多個Varnish執行個體的基本知識。

{{varnish-config-cloud}}

## 清除多個Varnish例項的設定

使用[`magento setup:config:set`](../../installation/tutorials/deployment.md)命令設定清漆主機後，Commerce會清除清漆主機。

您應該使用`--http-cache-hosts`引數來指定Varnish主機和接聽連線埠的逗號分隔清單。 （請勿以空格字元分隔主機。）

引數格式必須是`<hostname or ip>:<listen port>`，若是連線埠80，則可以省略`<listen port>`。

例如，

```shell
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:8080
```

當您在管理員中重新整理Commerce快取（也稱為&#x200B;_清除_&#x200B;快取）或使用命令列時，可以清除所有Varnish主機。

若要使用Admin重新整理快取，請按一下[工具] > [快取管理] > [工具] **&#x200B;**，然後按一下頁面頂端的[排清Magento快取] **。**&#x200B;**&#x200B;**（您也可以重新整理個別快取型別。）

若要從cli重新整理多個Varnish執行個體的快取，請使用[`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types)命令做為[檔案系統擁有者](../../installation/prerequisites/file-system/overview.md)。
