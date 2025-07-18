---
title: ACSD-53658：存放區檢視中未正確更新**[!UICONTROL Recently Viewed Product]**資料
description: 套用ACSD-53658修補程式以修正Adobe Commerce中**[!UICONTROL Recently Viewed Product]**資料未在存放區檢視中正確更新的問題。
feature: CMS, Personalization
role: Admin, Developer
exl-id: a91fac3d-cb6f-4f65-aec2-d28cee4fd39f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# ACSD-53658：在存放區檢視中未正確更新&#x200B;**[!UICONTROL Recently Viewed Product]**&#x200B;資料

ACSD-53658修補程式修正存放區檢視中&#x200B;**[!UICONTROL Recently Viewed Product]**&#x200B;資料未正確更新的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.42時，即可使用此修補程式。 修補程式ID為ACSD-53658。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在存放區檢視中未正確更新&#x200B;**[!UICONTROL Recently Viewed Product]**&#x200B;資料。

<u>要再現的步驟</u>：

1. 登入「管理」面板。
1. 為預設網站建立第二個商店檢視。
1. 建立簡單的產品。
1. 為新商店檢視設定不同的產品名稱。
1. 建立&#x200B;**[!UICONTROL Recently Viewed Product]** Widget。
1. 設定此Widget以顯示於首頁。
1. 從預設商店檢視開啟店面上的產品頁面。
1. 開啟「首頁」。
1. 使用存放區切換器，切換至第二個存放區檢視。

<u>預期結果</u>：

產品名稱會在Widget中更新。

<u>實際結果</u>：

Widget中的產品名稱未更新。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
