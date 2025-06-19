---
title: ACSD-55427：管理員無法從產品頁面上的**[!UICONTROL Product in Shared Catalogs]**解除指派產品
description: 套用ACSD-55427修補程式以修正無法從**[!UICONTROL Product in Shared Catalogs]**取消指派產品的Adobe Commerce問題。
feature: Products, B2B
role: Admin, Developer
exl-id: 974347fd-351d-4a4b-a9ca-a534daf3fbd7
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-55427：管理員無法從產品頁面上的&#x200B;**[!UICONTROL Product in Shared Catalogs]**&#x200B;解除指派產品

ACSD-55427修補程式修正了無法在Commerce管理員的目錄內產品頁面上，從&#x200B;**[!UICONTROL Product in Shared Catalogs]**&#x200B;取消指派產品的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.44時，即可使用此修補程式。 修補程式ID為ACSD-55427。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

您無法從Commerce管理員目錄中產品頁面上的&#x200B;**[!UICONTROL Product in Shared Catalogs]**&#x200B;取消指派產品。

<u>要再現的步驟</u>：

先決條件：已安裝Adobe Commerce並啟用B2B和&#x200B;**[!UICONTROL Shared Catalogs]**。
1. 建立產品。
1. 導覽至共用目錄控制面板，然後開啟預設的共用目錄。
1. 將產品指定至預設目錄，並設定低於產品價格的價格。
1. 儲存共用目錄。
1. 執行[!UICONTROL CRON]以更新消費者/索引器。
1. 開啟產品，並從&#x200B;**[!UICONTROL Product in Shared Catalogs]**&#x200B;區段下移除產品。

<u>預期結果</u>：

產品應從&#x200B;**[!UICONTROL Product in Shared Catalogs]**&#x200B;區段下移除。

<u>實際結果</u>：

產品仍會顯示在&#x200B;**[!UICONTROL Product in Shared Catalogs]**&#x200B;區段中。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
