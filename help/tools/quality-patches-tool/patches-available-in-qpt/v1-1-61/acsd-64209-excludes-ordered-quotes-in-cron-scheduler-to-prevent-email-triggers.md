---
title: ACSD-64209： Cron排程器會擷取可協商的報價，而不會排除[!UICONTROL Ordered]個報價
description: 套用ACSD-64209修補程式以修正Adobe Commerce問題，該問題導致cron排程器擷取所有可協商的引號，而不排除狀態為[!UICONTROL Ordered]的引號，進而觸發電子郵件或電子郵件。
feature:  B2B, Communications
role: Admin, Developer
exl-id: 51ba0edc-ad0c-4e32-acd7-2337a62bff53
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-64209： Cron排程器會擷取可協商的報價，而不會排除[!UICONTROL Ordered]個報價

ACSD-64209修補程式修正了cron排程器擷取所有可協商的引號，而不排除狀態為&#x200B;**[!UICONTROL Ordered]**&#x200B;的引號的問題，進而觸發電子郵件或電子郵件。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61時，即可使用此修補程式。 修補程式ID為ACSD-64209。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

cron排程器會擷取所有可協商的報價，而不會排除狀態為&#x200B;**[!UICONTROL Ordered]**&#x200B;的報價，從而導致觸發電子郵件或電子郵件。

<u>要再現的步驟</u>：


1. 在&#x200B;*管理員*&#x200B;側邊欄上，前往&#x200B;**[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL B2B Features]**&#x200B;並啟用公司和B2B報價。
1. 在&#x200B;**[!UICONTROL Default Expiration Period]**&#x200B;管理員&#x200B;*>* > *>* > **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]**&#x200B;中將&#x200B;**[!UICONTROL Sales]**&#x200B;設為&#x200B;**[!UICONTROL Quotes]** 1 **[!UICONTROL General]**。
1. 建立公司、啟用公司，並以公司管理員身分登入。
1. 新增產品至購物車。
1. 要求報價。
1. 在&#x200B;*管理員*&#x200B;側邊欄上，移至&#x200B;**[!UICONTROL Sales]** > **[!UICONTROL Quotes]**。
1. 選取已建立的報價單，然後按一下&#x200B;**[!UICONTROL Send]**&#x200B;將報價單傳回給購買者。
1. 以公司管理員身分登入店面。
1. 選取報價單，然後按一下&#x200B;**[!UICONTROL Proceed to checkout]**&#x200B;完成購買。
1. 檢查報價的狀態是否為&#x200B;**[!UICONTROL Ordered]**，且店面無法再執行動作。
1. 觸發`negotiable_quote_send_emails` cron工作。


<u>預期結果</u>：

由於報價已下單，且無法採取進一步的動作，因此不應傳送有關報價到期的電子郵件。

<u>實際結果</u>：

已傳送電子郵件&#x200B;*報價即將到期*。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
