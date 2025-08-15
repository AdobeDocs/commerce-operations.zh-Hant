---
title: ACSD-66179：取消付款型別為[!UICONTROL Not Capture]的商業發票會導致404錯誤頁面
description: 套用ACSD-66179修補程式以修正Adobe Commerce問題，其中取消付款型別為[!UICONTROL Not Capture]的商業發票會導致404錯誤頁面。
feature: Orders, Payments
role: Admin, Developer
type: Troubleshooting
exl-id: a7c1827d-fe28-40e2-9ec6-a04b4a5d33ee
source-git-commit: a35beeb278ac3b72701c54ac7727fd5423e687e7
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# ACSD-66179：取消付款型別為[!UICONTROL Not Capture]的商業發票會導致404錯誤頁面

ACSD-66179修補程式修正取消以&#x200B;*[!UICONTROL Not Capture]*&#x200B;付款型別建立的商業發票導致404錯誤頁面的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68時，即可使用此修補程式。 修補程式ID為ACSD-66179。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p5

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4-p11 - 2.4.4-p14， 2.4.5-p10 - 2.4.5-p13， 2.4.6-p8 - 2.4.6-p11， 2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

取消以&#x200B;*[!UICONTROL Not Capture]*&#x200B;付款型別建立的商業發票會導致404錯誤頁面。

<u>要再現的步驟</u>：

1. 使用PayPal Express Checkout等付款方式建立訂單。
1. 建立發票。 將&#x200B;**[!UICONTROL Amount]**&#x200B;設為&#x200B;*[!UICONTROL Not Capture]*，然後提交發票。
1. 開啟已建立的商業發票，並選取&#x200B;**[!UICONTROL Cancel]**。

<u>預期結果</u>：

1. 已成功取消發票。
1. 顯示成功訊息： *您已取消發票。*

<u>實際結果</u>：

顯示404錯誤頁面： *找不到頁面。*

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
