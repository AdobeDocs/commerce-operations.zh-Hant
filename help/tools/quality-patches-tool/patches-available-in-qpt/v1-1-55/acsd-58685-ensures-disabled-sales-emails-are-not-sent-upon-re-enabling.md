---
title: ACSD-58685：停用的銷售電子郵件會在重新啟用時傳送
description: 套用ACSD-58685修補程式來修正Adobe Commerce問題，此問題導致在停用電子郵件通訊時起始的銷售電子郵件在重新啟用電子郵件通訊後傳送。
feature: Configuration
role: Admin, Developer
exl-id: 773c0e0e-92c3-42b1-8fbf-fcb05e0e8311
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# ACSD-58685：停用的銷售電子郵件會在重新啟用時傳送

ACSD-58685修補程式修正了在電子郵件通訊停用時初始的銷售電子郵件在電子郵件通訊重新啟用後傳送的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55時，即可使用此修補程式。 修補程式ID為ACSD-58685。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

電子郵件通訊停用時初始的銷售電子郵件會在電子郵件通訊重新啟用時傳送。

<u>要再現的步驟</u>：

1. 前往「**[!UICONTROL Sales]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Mail Sending Settings]**」，並將&#x200B;**[!UICONTROL Disable Email Communications]**&#x200B;設為&#x200B;*[!UICONTROL No]*。
1. 導覽至&#x200B;**[!UICONTROL Sales]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales Emails]** > **[!UICONTROL General Settings]**，並將&#x200B;**[!UICONTROL Asynchronous Sending]**&#x200B;設為&#x200B;*[!UICONTROL Yes]*。
1. 清除設定快取。
1. 下訂單。
1. 啟用電子郵件通訊。
1. 下另一張訂單。
1. 執行cron。

<u>預期結果</u>：

只傳送第二張訂單的電子郵件。

<u>實際結果</u>：

會同時傳送第一筆和第二筆訂單的電子郵件。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

[[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
