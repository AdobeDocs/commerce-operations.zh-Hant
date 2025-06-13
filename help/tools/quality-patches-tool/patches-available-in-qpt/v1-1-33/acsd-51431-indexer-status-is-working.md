---
title: ACSD-51431：索引子狀態為*[!UICONTROL Working]*，即使變更記錄檔中沒有專案
description: 套用ACSD-51431修補程式以修正索引器狀態為*[!UICONTROL Working]*的Adobe Commerce問題，即使變更記錄檔中沒有專案。
feature: Logs, Price Indexer
role: Admin
exl-id: c87c059b-f435-468d-a7fe-e6786fdba1f8
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# ACSD-51431：即使變更記錄檔中沒有專案，索引子狀態為&#x200B;*[!UICONTROL Working]*

ACSD-51431修補程式修正了索引器狀態為&#x200B;*[!UICONTROL Working]*&#x200B;的效能問題，即使變更記錄檔中沒有專案。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.33時，即可使用此修補程式。 修補程式ID為ACSD-51431。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

即使變更記錄檔中沒有專案，索引子狀態為&#x200B;*[!UICONTROL Working]*。

<u>要再現的步驟</u>：

1. 將&#x200B;**[!UICONTROL indexers]**&#x200B;設為[!UICONTROL Update on Schedule]。
1. 設定cron工作每分鐘執行一次。
1. 同時儲存對不同產品的變更。
1. 在幾分鐘後執行`bin/magento indexer:status`。

<u>預期結果</u>：

已處理變更，且索引子處於&#x200B;*[!UICONTROL Ready]*&#x200B;狀態。 *[!UICONTROL Schedule]*&#x200B;狀態為&#x200B;*[!UICONTROL idle (0 in the backlog)]*。

<u>實際結果</u>：

已處理變更，且索引子處於&#x200B;*[!UICONTROL Ready]*&#x200B;狀態。 但是，*[!UICONTROL Schedule]*&#x200B;狀態會顯示&#x200B;*[!UICONTROL working (0 in the backlog)]*。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
