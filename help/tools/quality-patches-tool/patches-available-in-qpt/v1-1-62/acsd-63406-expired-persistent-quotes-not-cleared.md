---
title: ACSD-63406：persistent_clear_expired cron工作執行時未清除過期的永久性引號
description: 套用ACSD-63406修補程式來修正Adobe Commerce問題，亦即在「persistent_clear_expired」cron工作執行時，到期的永久性引號未由任何cron工作清除。
feature: Quotes, Shopping Cart
role: Admin, Developer
exl-id: 795d1ddf-0d5b-406c-870b-36cb92cf07fa
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# ACSD-63406：執行`persistent_clear_expired` cron工作時未清除過期的永久性引號

ACSD-63406修補程式修正了`persistent_clear_expired` cron工作執行時，任何cron工作都無法清除過期的永久性引號的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62時，即可使用此修補程式。 修補程式ID為ACSD-63406。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4-p9 - 2.4.4-p12， 2.4.5-p8 - 2.4.5-p11， 2.4.6-p6 - 2.4.7-p4

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當`persistent_clear_expired` cron工作執行時，任何cron工作都不會清除過期的永久性引號。

<u>要再現的步驟</u>：

1. 建立類別和產品。
1. 前往「**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Persistent Shopping Cart]**」。
   1. 將所有選項設定為&#x200B;*是*。
   1. 將&#x200B;**[!UICONTROL Persistence Lifetime (seconds)]**&#x200B;設為&#x200B;*60*。
1. 在店面建立客戶帳戶並登入。
1. 新增產品至購物車。
1. 登出，等待60秒，然後重新登入。

<u>預期結果</u>：

`persistent_clear_expired` cron工作應該根據組態中的持續性存留期設定來刪除持續性引號。

<u>實際結果</u>：

客戶報價的`is_persistent`值在報價表中仍為&#x200B;*1*。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。


## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
