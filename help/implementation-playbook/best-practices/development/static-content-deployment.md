---
title: 靜態內容部署最佳做法
description: 瞭解如何避免靜態內容未出現在您的Adobe Commerce或Magento Open Source店面上。
role: Developer
feature: Best Practices
feature-set: Commerce
exl-id: 9f521963-6fe4-4844-b2d1-fd457b706900
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---

# 靜態內容部署最佳做法

本文介紹在Adobe Commerce部署靜態內容(SCD)的最佳做法，以幫助避免在您的網站上無法訪問靜態內容的問題。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 共：

* Adobe Commerce在雲基礎架構上
* Adobe Commerce內部
* Magento Open Source

## 最佳做法

要避免靜態內容在您的網站上不可用的問題，請遵循以下最佳做法確保靜態內容已正確配置和部署：

1. 確保遵循部署准則：
   * 有關Adobe Commerce本地和Magento Open Source（所有版本），請參見 [部署概述](../../../configuration/deployment/overview.md) 我們的開發人員文檔中。
   * 有關Adobe Commerce雲基礎架構（所有版本）的資訊，請參見 [雲部署過程](https://devdocs.magento.com/cloud/deploy/cloud-deployment-process.html) 和 [靜態內容部署策略](https://devdocs.magento.com/cloud/deploy/static-content-deployment.html) 我們的開發人員文檔中。

1. 對於Adobe Commerce雲基礎架構（所有版本），確保ece-tools位於最新版本。 請參閱： [更新ece-tools版本](https://devdocs.magento.com/cloud/release-notes/ece-release-notes.html) 我們的開發人員文檔中。
1. 對於雲基礎架構（所有版本）上的Adobe Commerce，請確保在構建階段而不是部署階段部署靜態內容。 請參閱： [儲存設定的配置管理 — 靜態內容部署效能](https://devdocs.magento.com/cloud/live/sens-data-over.html#cloud-confman-scd-over) 我們的開發人員文檔中。
1. 確保沒有長期運行的cron作業並停止任何長期運行的cron進程。 長時間運行的cron作業會佔用CPU資源，並可能大大增加部署時間。
1. 對於Adobe Commerce本地和Magento Open Source（所有版本），請檢查 `php` CLI中的進程可以訪問 `pub/static` 的子菜單。 否則，您可能會面臨靜態內容部署無法將檔案寫入該目錄的問題。 有關詳細資訊： [檔案系統訪問權限](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/file-system-permissions.html) 我們的開發人員文檔中。
1. 確保 `generated` 目錄不是跨生成的共用目錄；否則，生成可能會隨機失敗。 有關詳細資訊：
   * Adobe Commerce本地和Magento Open Source（所有版本）: [技術詳細資訊](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/technical-details.html) 我們的開發人員文檔中。
   * Adobe Commerce雲基礎架構（所有版本）: [部署流程 — 第2階段：構建](https://devdocs.magento.com/cloud/reference/discover-deploy.html#cloud-deploy-over-phases-build) 我們的開發人員文檔中。

1. 檢查SCD策略。 的 *快* 策略是預設值。 有關詳細資訊：
   * Adobe Commerce本地和Magento Open Source（所有版本）: [靜態檔案部署策略](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/static-view/static-view-file-strategy.html) 我們的開發人員文檔中。
   * Adobe Commerce雲基礎架構（所有版本）: [部署變數 — SCD\_STRATEGY](https://devdocs.magento.com/cloud/env/variables-deploy.html#scd_strategy) 我們的開發人員文檔中。

## 其他資訊

在我們的開發人員文檔中：

* [靜態內容容器](https://developer.adobe.com/commerce/admin-developer/pattern-library/containers/static-content/)
* [靜態內容簽名](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/static-content-signing.html)
* [部署變數 — STATIC\_CONTENT\_SYMLINK](https://devdocs.magento.com/cloud/env/variables-deploy.html#static_content_symlink)
* [部署流](../../../performance/deployment-flow.md)
* [零停機部署](https://devdocs.magento.com/cloud/deploy/reduce-downtime.html)
* [優化雲部署](https://devdocs.magento.com/cloud/deploy/optimize-cloud-deployment.html)
