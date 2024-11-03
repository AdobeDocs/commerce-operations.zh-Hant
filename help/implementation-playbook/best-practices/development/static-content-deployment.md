---
title: 靜態內容部署最佳實務
description: 瞭解如何避免靜態內容未出現在Adobe Commerce店面的問題。
role: Developer
feature: Best Practices
exl-id: 9f521963-6fe4-4844-b2d1-fd457b706900
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# 靜態內容部署最佳實務

本文介紹Adobe Commerce中的靜態內容部署(SCD)最佳實務，協助避免您的網站上無法使用靜態內容的問題。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md)：

* 雲端基礎結構上的Adobe Commerce
* Adobe Commerce內部部署

## 最佳實務

若要避免靜態內容在網站上無法使用的問題，請遵循下列最佳實務，以確保您的靜態內容已正確設定和部署：

1. 請務必遵循部署准則：
   * 若為Adobe Commerce內部部署（所有版本），請參閱我們的開發人員檔案中的[部署概觀](../../../configuration/deployment/overview.md)。
   * 如需雲端基礎結構上的Adobe Commerce （所有版本），請參閱我們的開發人員檔案中的[雲端部署程式](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process)和[靜態內容部署策略](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/static-content)。

1. 針對雲端基礎結構上的Adobe Commerce （所有版本），請確定ece-tools使用的是最新版本。 請參閱我們的開發人員檔案中的[更新ece-tools版本](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/ece-tools-package)。
1. 對於雲端基礎結構上的Adobe Commerce （所有版本），請確定在建置階段而非部署階段中部署靜態內容。 請參閱：開發人員檔案中的[存放區設定的組態管理 — 靜態內容部署效能](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/store-settings#cloud-confman-scd-over)。
1. 請確定您沒有長期執行的cron工作，並終止任何長期執行的cron程式。 長時間執行的cron工作可能會佔用CPU資源，並可能大幅增加部署時間。
1. 若為Adobe Commerce內部部署（所有版本），請檢查CLI中的`php`處理序是否可存取`pub/static`目錄。 否則，您可能會遇到靜態內容部署無法將檔案寫入該目錄的問題。 如需詳細資訊：開發人員檔案中的[檔案系統存取許可權](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/file-system-permissions.html)。
1. 請確定`generated`目錄不是跨組建的共用目錄；否則，組建可能會隨機失敗。 如需詳細資訊：
   * Adobe Commerce內部部署（所有版本）：開發人員檔案中的[技術詳細資訊](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/technical-details.html)。
   * 雲端基礎結構上的Adobe Commerce （所有版本）： [部署程式 — 階段2：我們的開發人員檔案中的組建](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices#cloud-deploy-over-phases-build)。

1. 檢查您的SCD策略。 *quick*&#x200B;策略為預設值。 如需詳細資訊：
   * Adobe Commerce內部部署（所有版本）：開發人員檔案中的[靜態檔案部署策略](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/static-view/static-view-file-strategy.html)。
   * 雲端基礎結構上的Adobe Commerce （所有版本）： [在開發人員檔案中部署變數 — SCD\_STRATEGY](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#scd_strategy)。

## 其他資訊

在我們的開發人員檔案中：

* [靜態內容容器](https://developer.adobe.com/commerce/admin-developer/pattern-library/containers/static-content/)
* [靜態內容簽署](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/static-content-signing.html)
* [部署變數 — STATIC\_CONTENT\_SYMLINK](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#static_content_symlink)
* [部署流程](../../../performance/deployment-flow.md)
* [零停機部署](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/reduce-downtime)
* [最佳化雲端部署](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/optimization)
