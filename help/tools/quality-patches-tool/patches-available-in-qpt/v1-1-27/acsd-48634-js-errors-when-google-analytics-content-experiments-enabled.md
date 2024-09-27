---
title: 'ACSD-48634： [!DNL Google Analytics Content Experiments] 啟用時發生 [!DNL JS] 錯誤'
description: 啟用 [!DNL Google Analytics Content Experiments] 時，套用ACSD-48634修補程式來修正 [!DNL staging] 更新頁面上的 [!DNL JS] 錯誤。
feature: Catalog Management, Categories, Console, Page Content
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-48634：啟用[!DNL Google Analytics Content Experiments]時發生[!DNL JS]個錯誤

啟用[!DNL Google Analytics Content Experiments]時，ACSD-48634修補程式修正[!DNL staging]更新頁面上的[!DNL JS]錯誤。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.27時，即可使用此修補程式。 修補程式ID為ACSD-48634。 請注意，問題已在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

啟用[!DNL Google Analytics Content Experiments]時，[!DNL staging]更新頁面上發生[!DNL JS]個錯誤。

<u>要再現的步驟</u>：

1. 在&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**&#x200B;中，建立其他網站、商店和&#x200B;**[!UICONTROL Store View]**。 確定&#x200B;**[!UICONTROL Store View]**&#x200B;是&#x200B;*[!UICONTROL Enabled]*。
1. 移至&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Google API]**&#x200B;以設定&#x200B;**[!DNL Configure Google Analytics]**：
   * 針對&#x200B;**[!DNL Main]**&#x200B;和其他網站[!DNL scope]：
      * **[!UICONTROL Enabled]**： *[!UICONTROL Yes]*
      * **[!UICONTROL Account type]**： *[!UICONTROL Google Tag Manager]*
      * **[!UICONTROL Anonymize IP]**： *[!UICONTROL Yes]*
      * **[!UICONTROL Enable Content Experiments]**： *[!UICONTROL Yes]*
      * **[!UICONTROL Container Id]**： *[!UICONTROL (GTM container ID)]*
      * 其他欄位的&#x200B;**[!DNL Uncheck]** *[!UICONTROL Use Default]*，但不變更它們。
   * 針對&#x200B;**[!DNL Default Config]** [!DNL scope]：
      * **[!UICONTROL Enabled]**： *[!UICONTROL Yes]*
      * **[!UICONTROL Account type]**： *[!UICONTROL Universal Analytics]*
      * **[!UICONTROL Account Number]**： *[!UICONTROL (Universal Analytics account number)]*
      * **[!UICONTROL Anonymize IP]**： *[!UICONTROL Yes]*
      * **[!UICONTROL Enable Content Experiments]**： *[!UICONTROL Yes]*
1. 將&#x200B;**[!UICONTROL Enable]**&#x200B;從&#x200B;*[!UICONTROL Yes]*&#x200B;變更為&#x200B;*[!UICONTROL No]*，以停用&#x200B;**[!DNL Default Config]** [!DNL scope]上的&#x200B;**[!DNL Configure Google Analytics]**。 請勿變更其他任何專案！
1. 前往&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Categories]**。
1. 建立並編輯任何&#x200B;**[!UICONTROL category]**&#x200B;並為其新增排定的更新：
   * 任何名稱、未來的開始日期、未來的結束日期，以及&#x200B;**[!UICONTROL category]**&#x200B;中的任何變更([!UICONTROL For Example]： *[!UICONTROL disable category]*)。
1. 儲存更新並檢查[!DNL browser developer console]是否有錯誤。

<u>預期結果</u>：

沒有[!DNL JS]錯誤，對[!DNL staging]更新的變更已成功儲存。

<u>實際結果</u>：

主控台中顯示[!DNL JS]個錯誤，表單格式錯誤，而且在儲存後不會停用[!DNL spinner]。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
