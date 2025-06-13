---
title: ACSD-58375：在商店檢視層級新增視訊時，YouTube API金鑰設定錯誤會導致錯誤
description: 套用ACSD-58375修補程式，修正在商店檢視層級新增Adobe Commerce視訊時，錯誤YouTube API金鑰設定會導致錯誤的YouTube問題。
feature: Catalog Management, Configuration
role: Admin, Developer
exl-id: 24187308-d9dc-4ce2-9cfa-70ccb7726a5b
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# ACSD-58735：在商店檢視層級新增視訊時，YouTube API金鑰設定錯誤會導致錯誤

ACSD-58735修補程式修正了在商店檢視層級新增YouTube視訊時，錯誤YouTube API金鑰設定導致錯誤的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.49時，即可使用此修補程式。 修補程式ID為ACSD-58735。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.6-p7

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

錯誤的YouTube API金鑰設定會在存放區檢視層級新增YouTube視訊時導致錯誤。

<u>要再現的步驟</u>：

1. 前往「管理員> **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Video]**」。
1. 將&#x200B;*範圍*&#x200B;變更為&#x200B;*[!UICONTROL Main Website]*&#x200B;層級。
1. 新增YouTube API金鑰。
1. 前往&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Products]**。
1. 選取任何產品並捲動至&#x200B;*[!UICONTROL Images and Video]*。 按一下&#x200B;**[!UICONTROL Add Video]**。
1. 複製YouTube視訊連結，並將其貼到視訊連結欄位中。 從欄位移出。

<u>預期結果</u>：

YouTube API金鑰具有全域範圍，並在網站層級隱藏。

<u>實際結果</u>：

擲回下列錯誤： *由於下列原因，未顯示視訊： API金鑰無效。 請傳遞有效的API金鑰*。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
