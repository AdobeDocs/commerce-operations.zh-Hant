---
title: 'ACSD-58383：透過 [!DNL REST API]同時退款請求中的重複銷退折讓單'
description: 套用ACSD-58383修補程式以修正Adobe Commerce的問題，也就是透過 [!DNL REST API] 同時執行兩個相同請求而發出退款，會建立重複的銷退折讓單。
feature: REST, Payments, Returns
role: Admin, Developer
source-git-commit: ce3faa5dfc05500dcd672498761b48307064614e
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---


# ACSD-58383 Adobe Commerce修補程式：透過[!DNL REST API]同時退款請求中的重複銷退折讓單

ACSD-58383修補程式修正透過[!DNL REST API]發行退款，且同時執行兩個相同請求時，導致銷退折讓單重複的問題。

安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55時，即可使用此修補程式。 修補程式ID為ACSD-58383。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.4.6

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p3


>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

重複銷退折讓單會由同時建立的兩個退款產生。

<u>要再現的步驟</u>：

1. 在Commerce [!UICONTROL Admin]中設定[!DNL Paypal Express]。
1. 將付款動作設為&#x200B;*銷售*。
1. 在[!DNL PayPal]沙箱網站上設定[!DNL PayPal] IPN （立即付款通知）。
1. [!DNL PayPal]沙箱網站上的問題退款。
1. 使用開發人員工具模擬[!DNL PayPal]的IPN訊息。 ipn必須建立銷退折讓單。
1. 使用[!DNL API]呼叫建立第二個銷退折讓單。

<u>預期結果</u>：

相同專案只會建立一個銷退折讓單。


<u>實際結果</u>：

系統會為相同料號建立兩個銷退折讓單。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。


## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
