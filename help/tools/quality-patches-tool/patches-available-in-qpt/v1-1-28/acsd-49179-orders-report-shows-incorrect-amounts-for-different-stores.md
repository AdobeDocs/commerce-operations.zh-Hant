---
title: ACSD-49179：「訂單」報表顯示不同商店的錯誤金額。
description: 套用ACSD-49179修補程式，修正Adobe Commerce發生的問題：若不同商店使用不同貨幣，訂單報表會顯示不正確的金額。
feature: Admin Workspace, Orders
role: Admin
exl-id: b10653ef-c4b1-40df-8bfe-7da755db621b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# ACSD-49179：「訂單」報表顯示不同商店的錯誤金額

ACSD-49179修補程式修正了訂單報錶針對不同商店的不同貨幣顯示錯誤金額的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.28時，即可使用此修補程式。 修補程式ID為ACSD-49179。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

若不同商店的幣別不同，訂單報表會顯示不正確的金額。

<u>要再現的步驟</u>：

1. 前往&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL Catalog]** > **[!UICONTROL Price]**&#x200B;並設定[!UICONTROL Catalog Price Scope] = [!UICONTROL Website]。
1. 建立其他網站、商店和商店檢視。
1. 前往「**[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL General]** > **[!UICONTROL Currency Setup]** > **[!UICONTROL Currency Options]**」並設定：
   * 預設設定：
      * 基礎貨幣： USD
      * 預設顯示幣別：USD
      * 允許的幣別：EUR、USD與THB （泰銖）
   * 主要網站：
      * 基礎貨幣： EUR
      * 預設顯示貨幣：EUR
      * 允許的貨幣：EUR
   * 其他新網站：
      * 基本貨幣：THB （泰銖）
      * 預設顯示幣別：THB （泰銖）
      * 允許的幣別：THB （泰銖）
1. 移至&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Currency]** > **[!UICONTROL Currency Rates]**&#x200B;並設定THB的空轉換率（將率設定為1.0000）。
1. 建立產品、將其指派給兩個網站，並在先前建立的其他網站中隨此產品下訂單。
1. 確定訂單處於&#x200B;*處理*&#x200B;狀態（開票）。
1. 在後端，移至&#x200B;**[!UICONTROL Reports]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]**。
1. 按一下&#x200B;**[!UICONTROL Yellow]**&#x200B;警告以重新整理統計資料。
1. 在先前建立的其他網站上設定報告範圍，並設定篩選器，如下所示：
   * [!UICONTROL Date Used]： [!UICONTROL Created]
   * [!UICONTROL Period]： [!UICONTROL Day]
   * [!UICONTROL From and To]：下測試訂單的同一天
   * [!UICONTROL Order Status]： [!UICONTROL Any]
   * [!UICONTROL Empty rows]： [!UICONTROL No]
   * [!UICONTROL Show Actual Values]： [!UICONTROL No]

<u>預期結果</u>：

銷售總計會顯示轉換為網站貨幣的正確金額。

<u>實際結果</u>：

總計為零。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
