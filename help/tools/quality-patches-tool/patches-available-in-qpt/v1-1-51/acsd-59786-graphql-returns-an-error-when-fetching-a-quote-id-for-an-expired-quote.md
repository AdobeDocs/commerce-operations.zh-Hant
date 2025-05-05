---
title: ACSD-59786：為已到期的報價擷取「quote_id」時，GraphQL傳回錯誤
description: 套用ACSD-59786修補程式以修正Adobe Commerce問題，該問題導致GraphQL查詢在擷取過期報價的「quote_id」時傳回錯誤。
feature: GraphQL, Quotes, Companies
role: Admin, Developer
exl-id: 3c7aaa99-a2e0-44fe-9426-b24095615915
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# ACSD-59786：擷取過期報價的`quote_id`時GraphQL傳回錯誤

ACSD-59786修補程式修正擷取過期報價的`quote_id`時GraphQL查詢傳回錯誤的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.51時，即可使用此修補程式。 修補程式ID為ACSD-59786。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

擷取過期報價的`quote_id`時，GraphQL查詢傳回錯誤。

<u>要再現的步驟</u>：

1. 啟用&#x200B;**[!UICONTROL Companies]**&#x200B;和&#x200B;**[!UICONTROL Purchase Orders]**。
   * **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**&#x200B;並將&#x200B;**[!UICONTROL Enable Company]**&#x200B;設為&#x200B;*是*。
   * **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]** > **[!UICONTROL Order Approval Configuration]**&#x200B;並將&#x200B;**[!UICONTROL Enable Purchase Orders]**&#x200B;設為&#x200B;*是*。
1. 建立新公司並將&#x200B;**[!UICONTROL Enable Purchase Orders]**&#x200B;設定為&#x200B;*是*。
1. 建立簡單產品並將其指派至類別。
1. 使用公司管理員帳戶登入Storefront，並使用&#x200B;**[!UICONTROL Purchase Order]**&#x200B;作為付款方式建立新訂單。
1. 變更&#x200B;**[!UICONTROL Quote Lifetime (days)]**。
   * **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Shopping Cart]** > **[!UICONTROL Quote Lifetime (days)]** = *0*。
1. 執行命令`bin/magento c:f`。
1. 移至DB `quote_table`並以過去一天的時間變更`created_at`和`updated_at`值。
1. 執行命令`bin/magento cron:run --group="sales_clean_quotes`。
1. 使用建立&#x200B;**[!UICONTROL Purchase Order]**&#x200B;之管理員的授權Token，執行下方指定的GraphQL要求：

   ```GraphQL
   {
       customer {
           purchase_order(uid: "MQ==") {
               quote {
                   id
               }
           }
       }
   } 
   ```

<u>預期結果</u>：

GraphQL查詢傳回`quote_id`。

<u>實際結果</u>：

GraphQL查詢傳回內部伺服器錯誤。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
