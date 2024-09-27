---
title: 「ACSD-46581：在購物車中選取國家/地區後，預估稅捐總計未更新」
description: 套用ACSD-46581修補程式以解決在購物車中切換國家/地區後稅率未更新的Adobe Commerce問題。
feature: Orders, Shopping Cart
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# ACSD-46581：在購物車中選取國家/地區後，預估稅捐總計未更新

此ACSD-46581修補程式解決在購物車中切換國家/地區後稅率未更新的問題。 只有在選取送貨方法後才會更新。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.21時，即可使用此修補程式。 修補程式ID為ACSD-46581。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**
* Adobe Commerce （所有部署方法） 2.4.1-p1

**與Adobe Commerce版本相容：**
* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.5

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在購物車中切換國家/地區後，稅率沒有更新。

<u>要再現的步驟</u>：

1. 在Adobe Commerce Admin中，前往&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Tax Zone and Rates]**。
1. 為&#x200B;**[!UICONTROL Country]** = _美國_，**[!UICONTROL State]** = _*_，**[!UICONTROL Rate]** = _8.25_&#x200B;建立新的稅率。
1. 建立&#x200B;**[!UICONTROL Country]** = _印度_，**[!UICONTROL State]** = _*_，**[!UICONTROL Rate]** = _10_&#x200B;的新稅率。
1. 使用美國和印度的稅率建立稅捐規則。
1. 移至&#x200B;**[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Shipping Methods]**&#x200B;並啟用多個送貨方式（例如&#x200B;_統一運費_&#x200B;和&#x200B;_免運費_）。
1. 建立具有&#x200B;**[!UICONTROL Taxable Goods]**&#x200B;稅捐類別的簡單產品。
1. 將產品新增至商店前方的購物車。
1. 開啟購物車並檢查稅捐金額。
1. 系統會套用美國的預設稅捐設定，並根據8.25%的稅率計算稅捐。
1. 切換至印度。

<u>預期結果</u>：

將國家切換至印度時，稅捐金額變更為10%。

<u>實際結果</u>：

在購物車的總計區段中，稅捐金額保持不變。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
