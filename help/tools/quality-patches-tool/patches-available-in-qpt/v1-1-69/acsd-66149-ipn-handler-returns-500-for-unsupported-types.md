---
title: ACSD-66149：不支援的型別會傳回*500* IPN處理常式
description: 套用ACSD-66149修補程式以修正Adobe Commerce問題，其中IPN處理常式不會忽略不支援或未知IPN型別，導致問題無法記錄、中斷處理程式並傳回500錯誤。
feature: Payments
role: Admin, Developer
type: Troubleshooting
exl-id: d4794e24-1b6b-4bb5-b54c-9a248fa5f3bd
source-git-commit: cf0f5992c7b2a51b270a4a1a81fd50305a92759c
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# ACSD-66149： IPN處理常式針對不支援的型別傳回&#x200B;*500*

ACSD-66149修補程式修正IPN （即時付款通知）處理常式針對不支援或未知IPN型別傳回500錯誤的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69時，即可使用此修補程式。 修補程式ID為ACSD-66149。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

問題是IPN處理常式會針對不支援或未知的IPN型別傳回&#x200B;*500*&#x200B;錯誤。 當Paypal傳送IPN時缺少某些欄位，就會發生這種情況。

<u>要再現的步驟</u>：

1. 建立自訂模組，以模擬來自PayPal的各種未知IPN型別。
1. 至少建立一個產品。
1. 使用您自己的憑證設定PayPal Express。
1. 使用Paypal Express下訂單。
1. 執行PayPal模擬器。

<u>預期結果</u>：

應用程式IPN處理常式忽略不正確的IPN型別，且不會產生&#x200B;*500*&#x200B;錯誤：

```Order 000000001: Status processing — HTTP 500```

<u>實際結果</u>：

應用程式在處理不正確的IPN期間會產生許多&#x200B;*500*&#x200B;錯誤，而且如果預期欄位不存在，偶爾也不會處理某些訂單。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]： Tools指南中用於品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具
