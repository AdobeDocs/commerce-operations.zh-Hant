---
title: ACSD-62146：選取的帳單地址會在結帳付款頁面上消失
description: 套用ACSD-62146修補程式，修正啟用地址搜尋且「客戶地址數限制」設為1時，選取的帳單地址會在結帳付款頁面上消失的Adobe Commerce問題。
feature: Customers, Checkout
role: Admin, Developer
type: Troubleshooting
source-git-commit: 3de3de80383372d0e3bec5485fd65b9d70fe8860
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---


# ACSD-62146：選取的帳單地址會在結帳付款頁面上消失

ACSD-62146修補程式修正了啟用地址搜尋且[!UICONTROL Number of Customer Addresses Limit]設為1時，選取的帳單地址在結帳付款頁面上消失的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68時，即可使用此修補程式。 修補程式ID為ACSD-62146。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

啟用地址搜尋且&#x200B;**[!UICONTROL Number of Customer Addresses Limit]**&#x200B;設為1時，選取的帳單地址會在結帳付款頁面上消失。

<u>要再現的步驟</u>：

1. 若要啟用地址搜尋，請前往&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]**。
1. 將&#x200B;**[!UICONTROL Number of Customer Addresses Limit]**&#x200B;設為1。
1. 建立客戶並新增兩個不同的地址。
1. 將產品新增到購物車並繼續結帳。
1. 按一下&#x200B;**[!UICONTROL Change Address]**&#x200B;並使用快顯視窗變更地址。
1. 選取地址2作為送貨地址。
1. 按一下&#x200B;**[!UICONTROL Next]**&#x200B;以繼續付款步驟。
1. 確認帳單和運送地址相同。
1. 重新整理頁面而不進行付款。

<u>預期結果</u>：

帳單和運送地址相同時，會顯示運送地址。

<u>實際結果</u>：

預設帳單地址和選取的運送地址不可見。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
