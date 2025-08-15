---
title: MDVA-42969：相關產品規則僅適用於客戶區段設為全部時
description: MDVA-42969修補程式修正了只有當客戶區段設為全部時，相關產品規則才能運作的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13後，即可使用此修補程式。 修補程式ID為MDVA-42969。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
feature: Customer Service, Marketing Tools, Products
role: Admin
exl-id: 121da040-4541-468a-aeaf-cf98094e1918
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# MDVA-42969：相關產品規則僅適用於客戶區段設為全部時

MDVA-42969修補程式修正了只有當客戶區段設為全部時，相關產品規則才能運作的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13時，即可使用此修補程式。 修補程式ID為MDVA-42969。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

相關產品規則僅適用於客戶區段設為全部時。

<u>要再現的步驟</u>：

1. 移至&#x200B;**商店** > **組態** > **目錄** > **規則型產品關係**，並設定&#x200B;**顯示相關產品** = **僅規則型**。
1. 移至&#x200B;**客戶** > **區段**&#x200B;並建立新區段： **套用至** = **訪客與註冊客戶**。
1. 移至&#x200B;**行銷** > **相關產品規則**&#x200B;並建立新規則。

   ```code block
   Apply To = Related Products
   Customer Segments = All
   Products to Match = SKU = <select a SKU>
   Products to Display = SKU +is one of+ Constant Value (specify 1-3 products)
   ```

1. 開啟店面中相符的產品，並確認已顯示產品。
1. 修改在步驟三中建立的規則，並從步驟二設定&#x200B;**客戶區段** = **特定** > **區段**。
1. 在店面開啟相符的產品。

<u>預期結果</u>：

規則型相關產品會針對產品上的訪客顯示在店面上，因為客戶區段是以下列設定所建立：

**套用至** = **訪客與註冊客戶**

<u>實際結果</u>：

沒有顯示相關產品。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的「品質修補工具」[!DNL Quality Patches Tool]，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)：搜尋修補程式[!DNL Quality Patches Tool]。
