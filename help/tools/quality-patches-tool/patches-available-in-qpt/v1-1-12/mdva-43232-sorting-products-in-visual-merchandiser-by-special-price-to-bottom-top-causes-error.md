---
title: MDVA-43232：依特殊價格排序視覺化銷售器中的產品至頂端（或底部）會導致錯誤
description: MDVA-43232修補程式修正依特殊價格排序視覺化銷售器中的產品至頂端（或底部）時，導致儲存類別時發生錯誤的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12後，即可使用此修補程式。 修補程式ID為MDVA-43232。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
feature: Categories, Merchandising, Orders, Personalization, Products
role: Admin
exl-id: c977bec8-f99c-4799-abce-26aad49b77e8
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 58c984c2-e237-5c50-9718-500e40d1e82c
    internal-label: Merchandising
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: f37757d8-3174-5335-b977-1161792f965d
    internal-label: Personalization
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
subfeature_v2:
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 0%
---
# MDVA-43232：依特殊價格排序視覺化銷售器中的產品至頂端（或底部）會導致錯誤

MDVA-43232修補程式修正依特殊價格排序視覺化銷售器中的產品至頂端（或底部）時，導致儲存類別時發生錯誤的問題。 安裝[品質修補工具(QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.12時，即可使用此修補程式。 修補程式ID為MDVA-43232。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.4 - 2.4.3

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

依特殊價格排序視覺化銷售器中的產品至頂端（或底部）會在儲存類別時造成錯誤。

<u>要再現的步驟</u>：

1. 確定有兩個網站。
1. 導覽至&#x200B;**商店** > **設定** > **目錄** > **價格**，並設定目錄價格範圍=網站。
1. 再次導覽至&#x200B;**商店** > **設定** > **目錄** > **視覺化銷售工具** > **類別規則的可見屬性** >並新增特殊價格。
1. 建立簡單產品並將產品指派給兩個網站。
1. 新增特殊價格至產品的預設範圍。
1. 切換到其他商店的範圍並覆寫該產品的「價格」和「特殊價格」。
1. 執行`catalog_product_price`重新索引。
1. 移至&#x200B;**目錄** > **類別**&#x200B;並建立新類別。
1. 新增類別規則，以篩選具有特殊價格的產品。
1. 儲存類別。
1. 在「分類中的產品」區段下，將「排序順序=特殊價格」設定為「頂端（或底部）」。
1. 再次儲存類別。

<u>預期結果</u>：

類別儲存時不會發生錯誤。

<u>實際結果</u>：

系統擲回例外狀況：

```php
[2022-02-07T05:58:46.297621+00:00] report.CRITICAL: Exception: Item (Magento\Catalog\Model\Product\Interceptor) with the same ID "1" already exists. in /lib/internal/Magento/Framework/Data/Collection.php:407
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
