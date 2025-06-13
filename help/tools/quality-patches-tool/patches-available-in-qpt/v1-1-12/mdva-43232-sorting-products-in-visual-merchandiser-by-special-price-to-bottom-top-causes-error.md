---
title: MDVA-43232：依特殊價格排序視覺化銷售器中的產品至頂端（或底部）會導致錯誤
description: MDVA-43232修補程式修正依特殊價格排序視覺化銷售器中的產品至頂端（或底部）時，導致儲存類別時發生錯誤的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12後，即可使用此修補程式。 修補程式ID為MDVA-43232。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
feature: Categories, Merchandising, Orders, Personalization, Products
role: Admin
exl-id: c977bec8-f99c-4799-abce-26aad49b77e8
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 0%

---

# MDVA-43232：依特殊價格排序視覺化銷售器中的產品至頂端（或底部）會導致錯誤

MDVA-43232修補程式修正依特殊價格排序視覺化銷售器中的產品至頂端（或底部）時，導致儲存類別時發生錯誤的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12時，即可使用此修補程式。 修補程式ID為MDVA-43232。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.4 - 2.4.3

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

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
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
