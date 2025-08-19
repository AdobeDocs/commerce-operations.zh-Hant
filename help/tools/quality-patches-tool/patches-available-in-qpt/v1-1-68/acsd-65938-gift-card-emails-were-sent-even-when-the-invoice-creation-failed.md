---
title: ACSD-65938：即使發票建立失敗，也會傳送禮品卡電子郵件
description: 套用ACSD-65938修補程式以修正Adobe Commerce問題，在成功儲存及認可發票之前傳送禮品卡電子郵件，確保在正確儲存發票之後觸發電子郵件。
feature: Orders, Checkout
role: Admin, Developer
type: Troubleshooting
source-git-commit: b688875cd0a7bfc07dba77254605e7055ae7cca4
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---


# ACSD-65938：即使發票建立失敗，也會傳送禮品卡電子郵件

ACSD-65938修補程式可解決在成功儲存及認可發票之前傳送禮品卡電子郵件的問題。 透過此修正，現在僅在成功儲存發票後觸發電子郵件。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68時，即可使用此修補程式。 修補程式ID為ACSD-65938。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在確認發票已成功建立並儲存之前已傳送禮品卡電子郵件，導致即使發票建立失敗也傳送電子郵件。

<u>要再現的步驟</u>：

1. 登入&#x200B;**[!UICONTROL Admin]**&#x200B;面板。
2. 導覽至&#x200B;**[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Gift Cards]** > **[!UICONTROL Gift Card General Settings]**，並將&#x200B;**[!UICONTROL Generate Gift Card Account when Order Item is]**&#x200B;設為&#x200B;*已開立商業發票*。
3. 建立新的禮品卡產品。
4. 新增禮品車產品至購物車，然後繼續前往&#x200B;**[!UICONTROL checkout]**。 您可以使用&#x200B;**[!UICONTROL Check/Money Order]**&#x200B;作為付款方式。
5. 下訂單。
6. 修改`OrderRepository`以模擬訂購期間的例外狀況。
7. 使用下列裝載傳送POST要求給`rest/default/V1/order/<ORDER_ID>/invoice`：

   ```
   {
     "capture": true,
     "notify": true
   }
   ```


<u>預期結果</u>：

如果發票建立失敗，則不應傳送禮品卡電子郵件。

<u>實際結果</u>：

即使發票建立失敗，也會傳送禮品卡電子郵件。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
