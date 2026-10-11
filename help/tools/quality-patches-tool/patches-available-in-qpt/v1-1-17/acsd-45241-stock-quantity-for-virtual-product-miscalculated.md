---
title: ACSD-45241：虛擬產品的庫存數量計算錯誤
description: ACSD-45241修補程式修正建立銷退折讓單後，虛擬產品的庫存數量計算錯誤的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17時，即可使用此修補程式。 修補程式ID為ACSD-45241。 請注意，問題已在Adobe Commerce 2.4.4中修正。
feature: Orders, Products
role: Admin
exl-id: 447a84f0-aab4-4bb1-9f06-c056c006cd69
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '527'
ht-degree: 0%
---
# ACSD-45241：虛擬產品的庫存數量計算錯誤

ACSD-45241修補程式修正建立銷退折讓單後，虛擬產品的庫存數量計算錯誤的問題。 安裝[品質修補工具(QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.17時，即可使用此修補程式。 修補程式ID為ACSD-45241。 請注意，問題已在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.5 - 2.4.4

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

建立銷退折讓單後，虛擬產品的存貨數量計算錯誤。

<u>要再現的步驟</u>：

1. 在Commerce管理員中以虛擬產品作為子產品建立可設定產品。
1. 請確認在步驟一中建立的兩個產品均有庫存。
1. 將步驟1中建立的虛擬產品數量標示為100，同時保留可銷售數量100。
1. 將產品新增至購物車。
1. 使用在步驟一中建立的虛擬產品下訂單。
1. 將訂單狀態維持為「擱置中」。 無需處理付款。
1. 已在`inventory_reservation`中建立`order_created`筆記錄。 虛擬產品數量顯示100，可銷售數量為99。
1. 開啟訂單，並移至&#x200B;**發票** > **提交發票**。
1. 已在`inventory_reservation`中建立`invoice_created`筆記錄。 虛擬產品數量現在是99，而可銷售數量也是99。
1. 建立銷退折讓單，但不選取&#x200B;**退回存貨**。

<u>預期結果</u>：

`inventory_reservation`中未建立任何新記錄，且虛擬產品的庫存數量未變更。

<u>實際結果</u>：

已在`inventory_reservation`中建立`creditmemo_created`記錄，而虛擬產品庫存數量已調整為98，可銷售數量為99。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
