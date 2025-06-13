---
title: ACSD-47520：建立銷退折讓單時，客戶會失去獎勵積分
description: 套用ACSD-47520修補程式，修正建立銷退折讓單時客戶遺失獎勵點的Adobe Commerce問題。
feature: Admin Workspace, Cache, Orders, Rewards, Returns
role: Admin
exl-id: 09104451-e9f0-4ddb-b019-8aa34630edb9
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-47520：建立銷退折讓單時，客戶會失去獎勵積分

ACSD-47520修補程式修正建立銷退折讓單時，客戶遺失獎勵點數的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.25時，即可使用此修補程式。 修補程式ID為ACSD-47520。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**
* Adobe Commerce （所有部署方法） 2.4.5

**與Adobe Commerce版本相容：**
* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.5-p4

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

建立銷退折讓單時，客戶會失去獎勵積分。

<u>要再現的步驟</u>：

1. 前往Adobe Commerce Admin > **[!UICONTROL Store]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Reward Points]**。
1. 變更設定：
   * **[!UICONTROL Enable Reward Points Functionality]** = _是_
   * **[!UICONTROL Enable Reward Points Functionality on Storefront]** = _是_
   * **[!UICONTROL Customers May See Reward Points History]** = _是_
   * **[!UICONTROL Refund Reward Points Automatically]** = _否_
   * **[!UICONTROL Deduct Reward Points from Refund Amount Automatically]** = _是_
1. 前往「管理員> **[!UICONTROL Store]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Reward Exchange Rates]**」，然後按一下&#x200B;**[!UICONTROL Add New Rate]**。
1. 新增速率(1:1)並清除快取。
1. 建立客戶並新增10個獎勵點數至此帳戶。
1. 前往「管理員> **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Create New Order]** >選取在上一步中建立的客戶」。
1. 選取任何價格大於獎勵分數的產品。
1. 透過任何付款方式與獎勵點數下訂單。
1. 建立訂單的商業發票。
1. 建立銷退折讓單，但不退款獎勵點。

<u>預期結果</u>：

* 管理員可以退還獎勵積分。

* 訂單狀態將會關閉。

<u>實際結果</u>：

* 無法退款獎勵積分。

* 訂單狀態為&#x200B;**[!UICONTROL Completed]**。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
