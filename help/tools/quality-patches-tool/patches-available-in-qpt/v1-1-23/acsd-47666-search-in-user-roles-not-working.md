---
title: ACSD-47666：在[!UICONTROL User Roles]中搜尋無法運作
description: 套用ACSD-47666修補程式以修正[!UICONTROL User Roles]上的篩選函式無法如預期運作的Adobe Commerce問題。
feature: Roles/Permissions, Search
role: Admin
exl-id: fb66f114-b95c-402e-a35a-e552f264966c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# ACSD-47666：在&#x200B;**[!UICONTROL User Roles]**&#x200B;中搜尋無法運作

ACSD-47666修補程式解決&#x200B;**[!UICONTROL User Roles]**&#x200B;中的搜尋無法運作的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.23時，即可使用此修補程式。 修補程式ID為ACSD-47666。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

**[!UICONTROL User Roles]**&#x200B;上的篩選函式無法如預期運作。

<u>要再現的步驟</u>：

1. 登入Adobe Commerce Admin > **[!UICONTROL System]** > **[!UICONTROL Permissions]** > **[!UICONTROL User Roles]**。
1. 從清單中開啟任何現有的角色。
1. 開啟&#x200B;**[!UICONTROL Role Users]**&#x200B;標籤。
1. 在欄中輸入任何查詢。
1. 按Enter鍵。

<u>預期結果</u>：

**[!UICONTROL User Roles]**&#x200B;篩選函式應該根據查詢篩選結果。

<u>實際結果</u>：

主控台發生無限載入錯誤&#x200B;_（索引）:9 Uncaught TypeError：無法讀取null的屬性（正在讀取&#39;down&#39;）_。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。 

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)：搜尋修補程式[!DNL Quality Patches Tool]。
