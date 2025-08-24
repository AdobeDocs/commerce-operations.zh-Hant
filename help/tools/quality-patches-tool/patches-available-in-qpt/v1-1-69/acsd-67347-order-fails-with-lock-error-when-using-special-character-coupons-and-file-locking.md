---
title: ACSD-67347：使用優惠券代碼時，訂單失敗並出現「無法取得鎖定」錯誤
description: 將ACSD-67347修補程式套用至Adobe Commerce問題，該問題發生在優惠券代碼包含特殊字元(例如BIT/123456)且啟用檔案鎖定時，訂單失敗並出現「無法取得鎖定」錯誤。
feature: Checkout, Shopping Cart
role: Admin, Developer
type: Troubleshooting
source-git-commit: 1a48428efbb022b53320370f68691eaed44809b3
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---


# ACSD-67347：訂單失敗並出現&#x200B;*使用優惠券代碼時無法取得鎖定*&#x200B;錯誤

ACSD-67347修補程式修正了當優惠券代碼包含特殊字元(例如，BIT/123456)且啟用檔案鎖定時，訂單失敗並出現&#x200B;*無法取得鎖定*&#x200B;錯誤的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69時，即可使用此修補程式。 修補程式ID為ACSD-67347。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p12

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5-p11 - 2.4.5-p13

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用含特殊字元的優惠券且啟用檔案鎖定時，訂單失敗並出現&#x200B;*無法取得鎖定*&#x200B;錯誤。

<u>要再現的步驟</u>：

1. 安裝2.4-develop。
1. 在`env.php`檔案中設定檔案鎖定組態：

   ```
   'lock' => [
           'provider' => 'file',
           'config' => [
               'path' => '/Users/awijesooriya/sites/acsd15194dev/locks'
           ]
       ],
   ```

1. 使用優惠券代碼格式： *BIT/123456*，以優惠券建立購物車規則。
1. 建立簡單的產品。
1. 將產品新增到購物車並套用優惠券代碼。
1. 繼續結帳並下訂單。

<u>預期結果</u>：

已成功下訂單，因為建立優惠券代碼沒有限制。

<u>實際結果</u>：

無法下訂單。 出現下列錯誤： *無法取得鎖定。*

```
File "/Users/test/sites/test/locks/coupon_code_123/abc" cannot be opened Warning!fopen(/Users/test/sites/test/locks/coupon_code_123/abc): Failed to open stream: No such file or directory
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
