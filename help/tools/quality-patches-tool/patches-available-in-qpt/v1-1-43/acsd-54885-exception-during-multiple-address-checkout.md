---
title: ACSD-54885：當管理員以客戶身分登入時，在多個地址簽出期間發生例外狀況
description: 套用ACSD-54885修補程式來修正Adobe Commerce問題，該問題發生在管理員使用*[!UICONTROL Login as Customer]*功能時多個位址簽出期間發生錯誤。
feature: Checkout
role: Admin, Developer
exl-id: c146bc2a-2df1-4825-9cfc-69e04095b3c2
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-54885：當管理員以客戶身分登入時，在多個地址簽出期間發生例外狀況

ACSD-54885修補程式修正了管理員使用&#x200B;*[!UICONTROL Login as Customer]*&#x200B;功能時，多個位址簽出期間發生錯誤的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.43時，即可使用此修補程式。 修補程式ID為ACSD-54885。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

管理員使用&#x200B;*[!UICONTROL Login as Customer]*&#x200B;功能時，在多個位址簽出期間發生錯誤。

<u>要再現的步驟</u>：

1. 確定已啟用&#x200B;*[!UICONTROL Login as Customer]*。 前往「**[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configurations]** > **[!UICONTROL Advanced]** > **[!UICONTROL Admin]** > **[!UICONTROL Admin Actions]** > **[!UICONTROL Logging]** > **[!UICONTROL Login as Customer]**」。
1. 建立簡單的產品。
1. 使用地址建立新的客戶帳戶。
1. 前往後端中的客戶帳戶：

   * 移至&#x200B;**[!UICONTROL Account Information]**&#x200B;標籤，並設定&#x200B;*[!UICONTROL Allow remote shopping assistance]* = *是*。
   * 按一下&#x200B;**[!UICONTROL Login as Customer]**。

1. 將產品加入購物車並繼續前往&#x200B;*[!UICONTROL Checkout with multiple addresses]*。
1. 更新產品數量。
1. 嘗試返回購物車。

<u>預期結果</u>：

您可以更新購物車並使用多個地址結帳。

<u>實際結果</u>：

返回購物車時出現以下錯誤。

```PHP
report.CRITICAL: Error: Call to a member function getCustomer() on null in magento2ee/app/code/Magento/LoginAsCustomerLogging/Observer/LogUpdateQtyObserver.php:88
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
