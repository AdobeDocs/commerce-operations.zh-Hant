---
title: ACSD-51149：已啟用[!UICONTROL Catalog Permissions]且已排程[!UICONTROL ImportExport]讓索引子失效
description: 套用ACSD-51149修補程式以修正已排程[!UICONTROL ImportExport]且已啟用[!UICONTROL Catalog Permissions]的索引器失效的Adobe Commerce效能問題。
feature: Cache, Data Import/Export
role: Admin
exl-id: eafc69ab-ec81-4192-85f8-a235f0a131a9
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACSD-51149：已啟用[!UICONTROL Catalog Permissions]且已排程[!UICONTROL ImportExport]讓索引子失效

ACSD-51149修補程式修正了排程的[!UICONTROL ImportExport]已啟用[!UICONTROL Catalog Permissions]而使索引子失效的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.35時，即可使用此修補程式。 修補程式ID為ACSD-51149。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

已排程[!UICONTROL ImportExport]且已啟用[!UICONTROL Catalog Permissions]，讓索引子失效。

<u>要再現的步驟</u>：

1. 啟用&#x200B;*[!UICONTROL Catalog Permissions]*。
1. 將所有索引子設定為&#x200B;*[!UICONTROL Update by Schedule]*。
1. 建立簡單的產品。
1. 透過&#x200B;**[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Export]**&#x200B;匯出此產品。
1. 下載匯出的CSV，並將其放到`<AC root folder>/var/import`中。
1. 使用下載的CSV建立排程產品匯入。
1. 執行完整重新索引。
1. 檢查索引器的狀態。 所有索引子都應該處於&#x200B;*[!UICONTROL Ready]*&#x200B;狀態。
1. 從網格執行已建立的排程匯入。
1. 重新檢查索引器的狀態。

<u>預期結果</u>：

所有索引子都處於&#x200B;*[!UICONTROL Ready]*&#x200B;狀態。

<u>實際結果</u>：

部分索引子處於&#x200B;*[!UICONTROL Reindex Required]*&#x200B;狀態。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
