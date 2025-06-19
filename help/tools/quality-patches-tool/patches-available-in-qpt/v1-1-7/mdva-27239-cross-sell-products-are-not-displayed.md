---
title: MDVA-27239：不顯示交叉銷售產品
description: MDVA-27239修補程式修正未顯示交叉銷售產品的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.7時，即可使用此修補程式。 請注意，問題已在Adobe Commerce 2.3.6中修正。
feature: Products
role: Admin
exl-id: ab8fe64d-adbe-4756-be43-1a35ba6b4123
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# MDVA-27239：不顯示交叉銷售產品

MDVA-27239修補程式修正未顯示交叉銷售產品的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.7時，即可使用此修補程式。 請注意，問題已在Adobe Commerce 2.3.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.3.4、2.4.0

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.3.0 - 2.3.5-p2、2.4.0 - 2.4.0-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

交叉銷售產品不會顯示在購物車頁面的交叉銷售區塊中。

<u>必要條件</u>：

1. 停用Magento_TargetRule模組或從配置區塊Magento\TargetRule\Block\Checkout\Cart\Crosssell中移除。
1. 建立產品1。
1. 為「產品1」建立排程更新，使新建立的產品具有與entity_id不同的row_id。
1. 建立產品2、產品3和產品4。
1. 將產品3設為產品4的交叉銷售。
1. 將產品4設為產品2的交叉銷售。

<u>要再現的步驟</u>：

1. 將產品4和產品2新增到購物車。
1. 檢查購物車頁面。

<u>預期結果</u>：

產品3會顯示在交叉銷售區塊中。

<u>實際結果</u>：

交叉銷售區塊是空的。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
