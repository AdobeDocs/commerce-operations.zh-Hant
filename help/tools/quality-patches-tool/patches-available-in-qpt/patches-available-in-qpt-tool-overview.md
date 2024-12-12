---
title: QPT工具概觀中可用的修補程式
description: 本文提供 [!DNL Quality Patches Tool] (QPT)的概觀，以及說明其使用方式的資源連結。
feature: Support, Tools and External Services
role: Admin
exl-id: e67e5823-d878-4efc-90af-c7bb8c59d654
source-git-commit: 32800bcca9174eb09ff7a723bdc775ebaa569807
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# QPT工具概觀中可用的修補程式

本文提供[!DNL Quality Patches Tool] (QPT)的概觀，以及說明其使用方式的資源連結。

## 受影響的產品和版本

* Adobe Commerce內部部署，所有[支援的版本](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
* 雲端基礎結構上的Adobe Commerce，所有[支援的版本](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## 什麼是品質修補工具？

[[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) (QPT)是一種工具，可讓您套用由Adobe和Magento Open Source社群開發的個別品質修補程式。

它可讓您：

* 套用封裝內含的品質修補程式
* 回覆先前套用的修補程式
* 檢視已安裝Adobe Commerce版本可用的品質修補程式的一般資訊。

以下是您可以取得狀態表以檢視可用修補程式的範例：

![Magento修補程式_清單](/help/assets/tools/status_table.png)

此工具旨在協助您針對使用Adobe Commerce時可能遇到的問題自助提供修補程式，或輕鬆套用Adobe Commerce支援人員建議的修補程式。

>[!NOTE]
>
>QPT僅適用於品質修補程式。 安全性修補程式可在Adobe Commerce和Magento Open Source的[發行說明中取得](https://experienceleague.adobe.com/docs/commerce-operations/release/notes/overview.html)。

## [!DNL Quality Patches Tool]中可用的修補程式

在Adobe Commerce支援知識庫的這個區段中，您會找到按QPT發行版本分組的QPT修補程式所解決之問題的詳細說明。
您也可以檢視可用的QPT修補程式清單，並使用支援知識庫中[[!DNL Quality Patches Tool]：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上動態產生的表格來依元件篩選。

## 如何安裝及使用[!DNL Quality Patches Tool]

雲端基礎結構上的Adobe Commerce內部部署和Adobe Commerce的安裝和使用命令不同，因為對於雲端，QPT套件包含在ece-tools套件中。

### 如何在Adobe Commerce內部部署安裝及使用QPT

如需有關如何安裝及使用QPT來套用和還原修補程式的詳細資訊，請參閱開發人員檔案中的[Commerce >工具>使用方式](../usage.md)。

### 如何在雲端基礎結構上安裝和使用適用於Adobe Commerce的QPT

請參閱開發人員檔案中的[雲端基礎結構上的Commerce指南>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)，以取得有關如何在Adobe Commerce上安裝和使用QPT來套用及還原修補程式的詳細資訊。

## 相關閱讀

* 在開發人員檔案中[[!DNL Quality Patches Tool] 發行說明](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/release-notes.html)。
