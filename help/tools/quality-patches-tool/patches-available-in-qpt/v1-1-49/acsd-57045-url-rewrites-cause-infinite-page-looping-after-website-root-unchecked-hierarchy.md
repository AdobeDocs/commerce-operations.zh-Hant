---
title: ACSD-57045： URL重寫導致在[!UICONTROL Website Root]取消核取[!UICONTROL Hierarchy]後出現無限的頁面循環
description: 套用ACSD-57045修補程式以修正Adobe Commerce問題，該問題導致URL重寫在[!UICONTROL Website Root]取消核取[!UICONTROL Hierarchy]後造成無限頁面循環。
feature: CMS
role: Admin, Developer
exl-id: 7beaee40-a392-4644-917e-c507e79bddcc
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# ACSD-57045： URL重寫導致在[!UICONTROL Website Root]取消核取[!UICONTROL Hierarchy]後出現無限的頁面循環

ACSD-57045修補程式修正了URL重寫造成在&#x200B;**[!UICONTROL Website Root]**&#x200B;取消核取&#x200B;**[!UICONTROL Hierarchy]**&#x200B;後出現無限頁面循環的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.49時，即可使用此修補程式。 修補程式ID為ACSD-57045。 請注意，此問題已排程在Adobe Commerce 2.5.0中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5 - 2.4.6-p7

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

從&#x200B;**[!UICONTROL Hierarchy]**&#x200B;中取消選取&#x200B;**[!UICONTROL Website Root]**&#x200B;之後，URL重寫會導致無限的頁面循環。

<u>要再現的步驟</u>：

1. 建立名為&#x200B;*Test-Parent*&#x200B;的CMS頁面。
1. 建立名為&#x200B;*Test-Child*&#x200B;的頁面，並在&#x200B;**[!UICONTROL Hierarchy]**&#x200B;區段中，選取&#x200B;**[!UICONTROL Website Root]** > **[!UICONTROL Parent]**&#x200B;並儲存。
1. 前往&#x200B;**[!UICONTROL Marketing]** > **[!UICONTROL URL Rewrites]**。
1. 請注意，有兩個新的重新寫入：
   * 指向&#x200B;*cms/page/view/page_id/ID_NUMBER_FOR_PAGE*&#x200B;的&#x200B;*Test-Parent*&#x200B;要求路徑
   * 指向&#x200B;*cms/page/view/page_id/ID_NUMBER_FOR_PAGE*&#x200B;的&#x200B;*Test-Child*&#x200B;要求路徑
1. 造訪店面並將&#x200B;*test-child*&#x200B;新增至URL。 您應該會看到子頁面。
1. 執行相同的動作，但將&#x200B;*test-parent/test-child/*&#x200B;新增至URL並看到相同的頁面。
1. 前往&#x200B;**[!UICONTROL Marketing]** > **[!UICONTROL URL Rewrites]**&#x200B;並選取&#x200B;**[!UICONTROL Add URL Rewrite]**。 選擇下列設定：
   * 型別： *自訂*
   * 要求路徑： *test-parent/test-child*
   * 目標路徑： *test-child*
   * 重新導向型別： *永久(301)*
1. 造訪&#x200B;*test-parent/test-child*&#x200B;路徑，您應該重新導向至&#x200B;*test-child*。
1. 編輯子頁面（**[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** >挑選子項並選取&#x200B;**[!UICONTROL Edit]**）。
1. 在&#x200B;**[!UICONTROL Hierarchy]**&#x200B;區段下，保留&#x200B;*Test-Parent*&#x200B;已選取，但取消選取&#x200B;**[!UICONTROL Website Root]**&#x200B;並儲存。
1. 移至&#x200B;**[!UICONTROL Marketing]** > **[!UICONTROL URL Rewrites]**，並注意遺漏原始&#x200B;*test-child*&#x200B;到&#x200B;*cms/page/view/page_id*&#x200B;的重新導向，且此時會由指向&#x200B;*test-child*&#x200B;到&#x200B;*test-parent/test-child*&#x200B;的路徑取代。
1. 造訪店面，並嘗試造訪&#x200B;*Test-Child*&#x200B;頁面。

<u>預期結果</u>：

*Test-Child*&#x200B;頁面已開啟。

<u>實際結果</u>：

*Test-Child*&#x200B;頁面未開啟。 瀏覽器嘗試在無限回圈中開啟&#x200B;*test-parent/test-child*&#x200B;頁面。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
