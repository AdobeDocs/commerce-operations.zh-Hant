---
title: 靜態內容部署最佳實務
description: 了解如何避免靜態內容未出現在Adobe Commerce或Magento Open Source店面的問題。
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: 48c5666ee9b83bbf8a5c6375ec53762d918bcece
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 靜態內容部署最佳實務

本文說明Adobe Commerce中靜態內容部署(SCD)最佳實務，以協助避免靜態內容無法在您的網站上使用的問題。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 共：

* Adobe Commerce雲基礎架構
* Adobe Commerce內部
* Magento Open Source

## 最佳實務

為避免靜態內容無法在您的網站上使用的問題，請遵循下列最佳實務，以確保靜態內容已正確設定和部署：

1. 請務必遵循部署准則：
   * 若為Adobe Commerce內部部署和Magento Open Source（所有版本），請參閱 [部署概述](../../../configuration/deployment/overview.md) 在開發人員檔案中。
   * 如需雲端基礎架構上的Adobe Commerce（所有版本），請參閱 [雲端部署程式](https://devdocs.magento.com/cloud/deploy/cloud-deployment-process.html) 和 [靜態內容部署策略](https://devdocs.magento.com/cloud/deploy/static-content-deployment.html) 在開發人員檔案中。

1. 針對雲端基礎架構上的Adobe Commerce（所有版本），請確定ece工具是最新版本。 請參閱： [更新ece-tools版本](https://devdocs.magento.com/cloud/release-notes/ece-release-notes.html) 在開發人員檔案中。
1. 針對雲端基礎架構上的Adobe Commerce（所有版本），請確定靜態內容部署在建置階段，而非部署階段。 請參閱： [儲存設定的配置管理 — 靜態內容部署效能](https://devdocs.magento.com/cloud/live/sens-data-over.html#cloud-confman-scd-over) 在開發人員檔案中。
1. 請確定您沒有長期執行的cron工作，並終止任何長期執行的cron程式。 長時間運行的cron作業可能佔用CPU資源，並可能大大增加部署時間。
1. 若為Adobe Commerce內部部署和Magento Open Source（所有版本），請檢查 `php` CLI中的進程可以訪問 `pub/static` 目錄。 否則，您可能會面臨靜態內容部署無法將檔案寫入該目錄的問題。 如需詳細資訊： [檔案系統訪問權限](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/file-system-permissions.html) 在開發人員檔案中。
1. 確保 `generated` 目錄不是組建之間的共用目錄；否則，組建可能會隨機失敗。 如需詳細資訊：
   * Adobe Commerce內部部署和Magento Open Source（所有版本）: [技術詳細資訊](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/technical-details.html) 在開發人員檔案中。
   * Adobe Commerce雲端基礎架構（所有版本）: [部署過程 — 第2階段：建置](https://devdocs.magento.com/cloud/reference/discover-deploy.html#cloud-deploy-over-phases-build) 在開發人員檔案中。

1. 檢查您的SCD策略。 此 *快速* 策略是預設值。 如需詳細資訊：
   * Adobe Commerce內部部署和Magento Open Source（所有版本）: [靜態檔案部署策略](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/static-view/static-view-file-strategy.html) 在開發人員檔案中。
   * Adobe Commerce雲端基礎架構（所有版本）: [部署變數 — SCD\_STRATEGY](https://devdocs.magento.com/cloud/env/variables-deploy.html#scd_strategy) 在開發人員檔案中。

## 其他資訊

在開發人員檔案中：

* [靜態內容容器](https://developer.adobe.com/commerce/admin-developer/pattern-library/containers/static-content/)
* [靜態內容簽署](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/static-content-signing.html)
* [部署變數 — STATIC\_CONTENT\_SYMLINK](https://devdocs.magento.com/cloud/env/variables-deploy.html#static_content_symlink)
* [部署流程](../../../performance/deployment-flow.md)
* [零停機部署](https://devdocs.magento.com/cloud/deploy/reduce-downtime.html)
* [優化雲部署](https://devdocs.magento.com/cloud/deploy/optimize-cloud-deployment.html)

