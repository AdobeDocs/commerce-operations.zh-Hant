---
title: MDVA-44562：預設商店ID已覆寫報價專案的商店ID
description: MDVA-44562修補程式修正了預設商店ID會覆寫GraphQL要求之報價專案的商店ID的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.16後，即可使用此修補程式。 修補程式ID為MDVA-44562。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。
feature: Quotes
role: Admin
exl-id: 007a82f7-4bc9-4a51-8b18-05f6c0867ea7
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# MDVA-44562：預設商店ID已覆寫報價專案的商店ID

MDVA-44562修補程式修正了預設商店ID會覆寫GraphQL要求之報價專案的商店ID的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.16時，即可使用此修補程式。 修補程式ID為MDVA-44562。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.4

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

GraphQL要求的預設商店ID會覆寫報價專案的商店ID。

<u>要再現的步驟</u>：

1. 建立新的存放區檢視。
1. 為每個商店檢視建立具有不同名稱的新簡單產品。
1. 建立新客戶。
1. 取得客戶授權權杖。

   ```GraphQL
    POST /rest/all/V1/integration/customer/token
    {
      "username": "test@example.com",
      "password": "password"
     }
   ```

1. 使用授權權杖為客戶建立新報價。

   ```GraphQL
   POST rest/default/V1/carts/mine
   ```

1. 新增產品至購物車。

   ```GraphQL
   POST /rest/default/V1/carts/mine/items
   {
     "cartItem": {
       "sku": "simple1",
       "qty": 1,
       "quote_id": "1"
     }
   }
   ```

1. 取得預設商店檢視的購物車內容。

   ```GraphQL
   GET rest/default/V1/carts/mine/
   ```

1. 取得新商店檢視的購物車內容。

   ```GraphQL
   GET rest/<store_view_2>/V1/carts/mine/
   ```

<u>預期結果</u>：

來自新商店檢視的回應會顯示來自新商店檢視的產品名稱。

<u>實際結果</u>：

來自新商店檢視的回應會在預設商店檢視下顯示產品名稱設定。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
