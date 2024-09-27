---
title: 「ACSD-54264：客戶嘗試以可轉讓報價結帳時發生錯誤」
description: 套用ACSD-54264修補程式以修正Adobe Commerce問題，其中錯誤訊息「您無法更新要求的屬性。 當客戶嘗試從其他商店檢視中取出可轉讓的報價時，就會出現資料列ID：store_id。
feature: B2B, Checkout
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---

# ACSD-54264：客戶嘗試以可轉讓報價結帳時出現錯誤

ACSD-54264修補程式修正錯誤訊息&#x200B;*您無法更新要求的屬性的問題。 資料列識別碼：當客戶嘗試從另一個商店檢視使用可轉讓的報價結帳時，就會出現store_id*。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.42時，即可使用此修補程式。 修補程式ID為ACSD-54264。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

錯誤訊息&#x200B;*您無法更新要求的屬性。 資料列識別碼：當客戶嘗試從另一個商店檢視使用可轉讓的報價結帳時，就會出現store_id*。

<u>必要條件</u>：

Adobe Commerce B2B模組已安裝並啟用。

<u>要再現的步驟</u>：

1. 為預設網站建立其他商店檢視。
1. 啟用組態中的&#x200B;*[!UICONTROL B2B Quote]*。
1. 在其中一個商店檢視中，以公司客戶身分登入。
1. 將產品新增至&#x200B;*[!UICONTROL Shopping Cart]*。
1. 提交報價以供檢閱。
1. 以管理員使用者身分，前往&#x200B;**[!UICONTROL Sales]** > **[!UICONTROL Quotes]**&#x200B;並提交已核准的報價。
1. 作為公司客戶，將商店檢視變更為不同的商店檢視。
1. 嘗試簽出。

<u>預期結果</u>：

客戶使用此報價單下訂單。

<u>實際結果</u>：

* 儲存送貨資訊時發生錯誤：

  `You cannot update the request attribute. Row ID: store_id =#`

* 會記錄下列錯誤：

  `report.CRITICAL: Magento\Framework\Exception\InputException: You cannot update the requested attribute. Row ID: store_id = 2. in /app/code/Magento/NegotiableQuote/Plugin/Quote/Model/QuoteUpdateValidator.php:100`

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
