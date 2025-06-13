---
title: ACSD-48771： WYSIWYG編輯器轉譯內容的方式不同
description: 套用ACSD-48771修補程式來修正WYSIWYG編輯器以不同方式呈現內容的Adobe Commerce問題。
feature: Cache, Page Content
role: Admin
exl-id: 9480af54-800b-4802-b1a3-65d1a6e169ec
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# ACSD-48771： WYSIWYG編輯器轉譯內容的方式不同

ACSD-48771修補程式修正WYSIWYG編輯器轉譯內容不同的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29時，即可使用此修補程式。 修補程式ID為ACSD-48771。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

WYSIWYG編輯器以不同方式呈現內容。

<u>要再現的步驟</u>：

1. 前往Adobe Commerce管理員，建立具有三欄之列的新頁面，並儲存頁面。
1. 將Adobe Commerce更新至其中一個最新版本。
1. 設定[!DNL Chrome]瀏覽器以停用快取和速度為&#x200B;*快速3G*。
1. 再次移至編輯頁面並重新整理，直到欄變成列。
1. 當欄位於列中時儲存頁面。

<u>預期結果</u>：

管理員頁面產生器不應在列中顯示欄。

<u>實際結果</u>：

欄會顯示在不同的列中。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
