---
title: ACSD-61348：可透過GraphQL檢視但不在店面顯示的願望清單專案
description: 套用ACSD-61348修補程式來修正Adobe Commerce問題，在多網站環境中，希望清單專案可透過GraphQL顯示，但不會顯示在店面上。
feature: Customers
role: Admin, Developer
exl-id: fcba2c28-077d-4663-b129-7da436e2791d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-61348：可透過GraphQL檢視但不在店面顯示的願望清單專案

ACSD-61348修補程式修正了透過GraphQL顯示願望清單專案，但無法在多網站環境的店面中顯示的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55時，即可使用此修補程式。 修補程式ID為ACSD-61348。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.4.6-p5

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

願望清單專案可透過GraphQL顯示，但無法在多網站環境的店面中顯示。

<u>要再現的步驟</u>：

1. 設定兩個網站。
1. 前往&#x200B;**[!UICONTROL Config Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Account Sharing Options]**&#x200B;並將&#x200B;**[!UICONTROL Share Customer Accounts]**&#x200B;設為&#x200B;*[!UICONTROL Global]*。
1. 移至&#x200B;**[!UICONTROL Config Customers]** > **[!UICONTROL Wishlist]** > **[!UICONTROL General Options]**&#x200B;並將&#x200B;**[!UICONTROL Enable Multiple Wish Lists]**&#x200B;設為&#x200B;*是*。
1. 移至&#x200B;**[!UICONTROL Config General]** > **[!UICONTROL Web]**&#x200B;並將&#x200B;**[!UICONTROL Add Store Code to URLs]**&#x200B;設定為&#x200B;*是*。
1. 建立簡單產品並將其指派給第二個網站。
1. 建立客戶並登入。
1. 將產品新增至願望清單。
1. 將產品指派至預設網站。
1. 前往預設網站上的&#x200B;*[!UICONTROL Wishlist]*&#x200B;頁面。

<u>預期結果</u>：

產品在願望清單上。

<u>實際結果</u>：

願望清單中沒有產品。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
