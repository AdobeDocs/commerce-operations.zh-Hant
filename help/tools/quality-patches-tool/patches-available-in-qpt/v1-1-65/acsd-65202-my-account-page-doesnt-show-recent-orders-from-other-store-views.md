---
title: ACSD-65202：「我的帳戶」頁面不會顯示其他商店檢視的最近訂單
description: 套用ACSD-65202修補程式來修正Adobe Commerce問題，該問題導致「我的帳戶」頁面無法顯示同一商店內其他商店檢視的最近訂單。
feature: Orders, User Account
role: Admin, Developer
type: Troubleshooting
exl-id: 031f12f2-1b70-4cbc-92a0-8eb561e34067
source-git-commit: b1912bbc5aabd36067563326ee5c6bb84e14441d
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-65202： [!UICONTROL My Account]頁面未顯示其他商店檢視的最近訂單

ACSD-65202修補程式修正&#x200B;**[!UICONTROL My Account]**&#x200B;頁面未顯示相同商店內其他商店檢視的最近訂單的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65時，即可使用此修補程式。 修補程式ID為ACSD-65202。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4-p12

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當您前往客戶帳戶頁面（**[!UICONTROL My Account]**&#x200B;區段）時，沒有看到最近在其他商店檢視下下的訂單。 但是，當您移至訂單歷史記錄（區段&#x200B;*[!UICONTROL My Orders]*）時，您會在兩個「商店檢視」中看到所有訂單。

<u>要再現的步驟</u>：

1. 安裝Adobe Commerce。
1. 在&#x200B;*管理員*&#x200B;面板中，建立新的「商店檢視」，並以&#x200B;*秒*&#x200B;輸入其程式碼以識別該檢視。
1. 建立簡單產品並重新索引。
1. 建立客戶帳戶，並在預設商店檢視中下訂單，其程式碼為&#x200B;*預設*。
1. 移至&#x200B;**[!UICONTROL My Orders]**&#x200B;頁面，並檢查在兩個存放區檢視中是否顯示順序，例如：
1. 預設值： https://localhost/pub/default/sales/order/history/
1. 第二： https://localhost/pub/second/sales/order/history/

1. 在兩個存放區檢視中移至&#x200B;**[!UICONTROL My Account]**&#x200B;頁面：
1. 預設值： https://localhost/pub/default/customer/account/
1. 第二： https://localhost/pub/second/customer/account/

<u>預期結果</u>：

您可以在「訂單」頁面上，從兩個商店檢視中檢視訂單。 這是同一商店，只是不同的商店檢視。

<u>實際結果</u>：

行為不一致。 訂單不會出現在第二個商店檢視中。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
