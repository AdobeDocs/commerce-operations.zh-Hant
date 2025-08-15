---
title: ACSD-57086：來自啟用條款與條件之非預設網站的訂單會遭到錯誤處理
description: 套用ACSD-57086修補程式，修正來自啟用條款與條件之非預設網站的訂單無法正確處理的Adobe Commerce問題。
feature: Orders
role: Admin, Developer
exl-id: d9f2ef50-12c4-4a2d-b140-dfd0e8948fd3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 0%

---

# ACSD-57086：來自啟用條款與條件之非預設網站的訂單會遭到錯誤處理

ACSD-57086修補程式修正來自啟用條款與條件之非預設網站的訂單無法正確處理的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.49時，即可使用此修補程式。 修補程式ID為ACSD-57086。 請注意，此問題已在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p5

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.6-p7

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用具有AsyncOrder處理的多重商店設定時，由於佇列消費者程式碼中的範圍處理問題，在主要網站以外的任何網站/商店下單的訂單會被拒絕。

<u>要再現的步驟</u>：

1. 安裝[!DNL RabbitMQ]並執行`bin/magento setup:upgrade`以建立[!DNL RabbitMQ]的佇列。
1. 設定AsyncOrder處理方式：

   ```bash
   bin/magento setup:config:set --checkout-async 1
   ```

1. 建立次要網站、商店和商店檢視。
1. 建立兩個網站共用的產品。
1. 啟用條款與條件：
   1. 前往「**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]**」。
   1. 將&#x200B;*[!UICONTROL Enable Terms And Conditions]*&#x200B;設為&#x200B;*是*。
1. 設定這兩個網站的條款與條件：
   1. 前往&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Terms And Conditions]** > **[!UICONTROL Add New Condition]**。
   1. 使用下列設定：
      * *[!UICONTROL Condition Name]*： *任何專案*
      * *[!UICONTROL Status]*： *[!UICONTROL Enabled]*
      * *[!UICONTROL Applied]*： *[!UICONTROL Manually]*
      * *[!UICONTROL Store View]*： *[!UICONTROL Default Store View]*
   1. 為第二個網站/商店檢視建立另一個條件。
1. 前往&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL All Stores]**&#x200B;變更預設網站。 按一下第二個網站，核取&#x200B;*[!UICONTROL Set as Default]*&#x200B;並儲存。
1. 清除快取的方式：

   ```bash
   bin/magento cache:clear
   ```

1. 前往店面並將產品新增到購物車。 繼續結帳並下訂單（您應該會在付款方式步驟中看到核取方塊以接受條款與條件）。
1. 下訂單後返回管理員，並將預設網站變更為原始主要網站並儲存。
1. 清除快取：

   ```bash
   bin/magento cache:clear
   ```

1. 執行以下命令以啟動佇列取用者：

   ```bash
   bin/magento queue:cons:start placeOrderProcessor
   ```

<u>預期結果</u>：

訂單已完成；不會自動拒絕。

<u>實際結果</u>：

訂單狀態為&#x200B;*已拒絕*，附有下列註解：

*未下訂單。 首先，同意條款與條件，然後嘗試再次下訂單。*

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)：搜尋修補程式[!DNL Quality Patches Tool]。
