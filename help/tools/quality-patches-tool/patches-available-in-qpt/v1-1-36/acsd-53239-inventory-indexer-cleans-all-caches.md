---
title: 'ACSD-53239：清查索引器清除所有快取'
description: 套用ACSD-53239修補程式以修正清查索引器在[!UICONTROL Update on Schedule]模式中清除所有快取的Adobe Commerce問題。
feature: GraphQL, Inventory, Catalog Management
role: Admin, Developer
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# ACSD-53239：詳細目錄索引器會清除[!UICONTROL Update on Schedule]模式中的所有快取

ACSD-53239修補程式修正清查索引器在[!UICONTROL Update on Schedule]模式中清除所有快取的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.36時，即可使用此修補程式。 修補程式ID為ACSD-53239。 請注意，問題已在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.5-p4

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

清查索引器會清除[!UICONTROL Update on Schedule]模式中的所有快取。

<u>要再現的步驟</u>：

1. 移至&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Catalog Products]**&#x200B;並選取約&#x200B;*1200*&#x200B;個產品。
2. 將&#x200B;*[!UICONTROL Qty]*&#x200B;更新為新值並按一下&#x200B;**[!UICONTROL Save]**。
3. 儲存後立即執行`bin/magento cron:run`。
4. 執行下列GraphQL查詢：

   ```GraphQL
   {
     storeConfig {
     absolute_footer
     }
   }
   ```

<u>預期結果</u>

查詢會在平常的時間長度內處理。

<u>實際結果</u>

查詢的處理速度異常緩慢。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
