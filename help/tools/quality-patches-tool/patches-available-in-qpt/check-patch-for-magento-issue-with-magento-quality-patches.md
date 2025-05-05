---
title: 使用品質修補工具檢查Adobe Commerce問題的修補程式
description: 本文提供品質修補工具(QPT)的概觀，以及說明其使用方式的資源連結。
feature: Tools and External Services
role: Admin
source-git-commit: 6f311fc4c20caca8b98d4c3c06642e5f61dc614f
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# 使用品質修補工具檢查Adobe Commerce問題的修補程式

本文提供品質修補工具(QPT)的概觀，以及說明其使用方式的資源連結。

## 受影響的產品和版本

* Adobe Commerce內部部署，所有[支援的版本](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
* 雲端基礎結構上的Adobe Commerce，所有[支援的版本](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## 什麼是品質修補工具

[品質修補工具](https://github.com/magento/quality-patches) (QPT)是由Adobe和Magento Open Source社群開發的個別修補程式。

它可讓您：

* 套用封裝內含的品質修補程式
* 回覆先前套用的修補程式
* 檢視已安裝Adobe Commerce版本可用的品質修補程式的一般資訊。

以下是您可以取得狀態表以檢視可用修補程式的範例：

![Magento修補程式_清單](/help/assets/tools/status_table.png)

此工具旨在協助您針對使用Adobe Commerce時可能遇到的問題自助提供修補程式，或輕鬆套用Adobe Commerce支援人員建議的修補程式。

>[!NOTE]
>
>QPT僅適用於品質修補程式。 [Magento安全中心](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/release/notes/overview)提供安全修補程式。

## Quality Patches Tool提供的修補程式

如需可用的修補程式清單，請參閱開發人員檔案中的[品質修補程式工具](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。

## 如何安裝及使用品質修補工具

雲端基礎結構上的Adobe Commerce內部部署和Adobe Commerce的安裝和使用命令不同，因為對於雲端，QPT套件包含在ece-tools套件中。

### 如何在Adobe Commerce內部部署安裝及使用QPT

請參考開發人員檔案中的[軟體更新指南>修補](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/usage)，瞭解如何安裝及使用QPT來套用及還原修補程式的詳細資訊。

### 如何在雲端基礎結構上安裝和使用適用於Adobe Commerce的QPT

如需如何在雲端基礎結構上安裝和使用QPT來套用及還原Adobe Commerce修補程式的詳細資訊，請參閱我們的開發人員檔案中的[Cloud for Adobe Commerce >套用修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

* 在開發人員檔案中[品質修補程式工具發行說明](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/release-notes)。
* [如何套用Adobe](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento)在支援知識庫中提供的撰寫器修補程式。
