---
title: ACSD-62965：修正GraphQL訂單放置回應中缺少LocalizedException訊息的問題
description: 套用ACSD-62965修補程式，修正下單期間Adobe Commerce回應中未包含「LocalizedException」訊息的GraphQL問題。
feature: Orders, GraphQL
role: Admin, Developer
exl-id: cf9d1409-6fe3-4019-9207-df5f12a41505
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACSD-62965：修正GraphQL訂單放置回應中遺失`LocalizedException`訊息的問題

ACSD-62965修補程式修正了下單期間GraphQL回應中未包含`LocalizedException`訊息的問題。 此修補程式可用於[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57。修補程式ID為ACSD-62965。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.4.7

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

訂單放置的GraphQL回應未包含`LocalizedException`訊息，導致偵錯所需的錯誤詳細資料不足。

<u>要再現的步驟</u>：

1. 安裝乾淨的&#x200B;**[!DNL Adobe Commerce]**&#x200B;執行個體。
1. 將產品新增到購物車並繼續訂單放置步驟。
1. 在`app/code/Magento/QuoteGraphQl/Model/Resolver/PlaceOrder.php`中新增`LocalizedException`至`Magento\Framework\Exception\LocalizedException`。
1. 在下列行之後插入例外：

   ```
   $cart = $this->getCartForCheckout->execute($maskedCartId, $userId, $storeId);
   ```

   新增例外：

   ```
   throw new LocalizedException(new Phrase("Test LocalizedException"));
   ```

1. 執行下單GraphQL請求：

   ```
   mutation {
   placeOrder(input: {cart_id: "cart_id"}) {
       order {
       order_number
       }
   }
   }
   ```

1. 觀察回應：
   1. 回應不包含`LocalizedException`訊息。
   1. 不正確回應的範例：

      ```
      {
      "data": {
          "placeOrder": {
          "order": null
          }
      }
      }
      ```

<u>預期結果</u>：

如果發生`LocalizedException`，則應將例外狀況訊息包含在訂單位置GraphQL回應中，以改善錯誤處理。

<u>實際結果</u>：

如果發生`LocalizedException`，訂單位置GraphQL回應中不會包含例外狀況訊息。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
