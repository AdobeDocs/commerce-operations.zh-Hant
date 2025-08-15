---
title: ACSD-61133： 'sales_clean_quotes' cron會從未核准的採購單中刪除報價
description: 套用ACSD-61133修補程式以修正Adobe Commerce的問題，即「sales_clean_quotes」cron會從未核准的採購單中刪除報價。
feature: B2B, Purchase Orders
role: Admin, Developer
exl-id: 06979d4b-08ea-40fe-a211-3d950c9afb47
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-61133： `sales_clean_quotes` cron會從未核准的採購單中刪除報價

ACSD-61133修補程式修正了`sales_clean_quotes` cron從未核准的採購單中刪除報價的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.53時，即可使用此修補程式。 修補程式ID為ACSD-61133。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.4.7-p1

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.4-p5 - 2.4.4-p11、2.4.5-p4 - 2.4.5-p10和2.4.6-p2 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

`sales_clean_quotes` cron會從未核准的採購單中刪除報價。 *[B2B採購單]*&#x200B;無法轉換為與採購單相關的報價單，因為cron會刪除它。

<u>必要條件</u>：

Adobe Commerce [!UICONTROL B2B]模組已安裝且已啟用。

<u>要再現的步驟</u>：

1. 啟用&#x200B;*[!UICONTROL B2B Purchase Order]*&#x200B;功能。
1. 建立公司。
1. 建立&#x200B;*[!UICONTROL Purchase Order]*。
1. 等候報價過期並由cron刪除。 報價到期日可透過&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Quotes]** > **[!UICONTROL General]** > **[!UICONTROL Default Expiration Period configuration]**&#x200B;設定。
1. 透過&#x200B;*[!UICONTROL Purchase Order]*&#x200B;或使用&#x200B;*[!UICONTROL My Purchase Order in Customer Dashboard]* [!DNL GraphQL]突變將`placeOrderForPurchaseOrder`轉換為訂單。

<u>預期結果</u>：

與作用中&#x200B;*[!UICONTROL Purchase Order]*&#x200B;關聯的報價未被cron刪除為已過期。 已成功在店面或透過[!DNL GraphQL]下訂單。

<u>實際結果</u>：

未下訂單，且店面顯示錯誤或在[!DNL GraphQL]回應中傳回。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
