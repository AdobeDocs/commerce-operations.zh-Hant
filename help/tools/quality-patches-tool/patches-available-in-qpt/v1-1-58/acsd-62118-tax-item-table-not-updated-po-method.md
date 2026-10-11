---
title: ACSD-62118：未針對使用[!UICONTROL Purchase Order]方法下單的B2B訂單完全更新「sales_order_tax_item」表格
description: 套用ACSD-62118修補程式，修正使用[!UICONTROL Purchase Order]方法下達B2B訂單時，「sales_order_tax_item」表格未完全更新的Adobe Commerce問題。
feature: Purchase Orders, B2B
role: Admin, Developer
exl-id: 8ace73ad-f5a5-47ab-aca7-62c818775d2f
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: 2d6d41d4-a5c1-5baf-8dbe-bf7300b68bb3
    internal-label: Purchase Orders
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%
---
# ACSD-62118：使用[!UICONTROL Purchase Order]方法下達B2B訂單時，`sales_order_tax_item`資料表未完全更新

ACSD-62118修補程式修正使用&#x200B;*[!UICONTROL Purchase Order]*&#x200B;方法下達B2B訂單時，`sales_order_tax_item`表格未完全更新的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58時，即可使用此修補程式。 修補程式ID為ACSD-62118。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用&#x200B;*[!UICONTROL Purchase Order]*&#x200B;方法下達B2B訂單時，`sales_order_tax_item`資料表未完全更新。 此問題會影響稅捐計算與訂單處理。 尤其是，透過API查詢訂單時，`applied_taxes`陣列是空的，而且`tax_item_amount`和`tax_item_percent`都是NULL。

<u>要再現的步驟</u>：

1. 為&#x200B;**[!UICONTROL Product]**&#x200B;和&#x200B;**[!UICONTROL Shipping]**&#x200B;新增稅捐規則。
1. 啟用公司設定中的&#x200B;**[!UICONTROL Purchase Order]**&#x200B;方法。
1. 以公司管理員使用者身分登入。
1. 使用離線付款方式放置&#x200B;**[!UICONTROL Purchase Order]**。
1. 自動核准[!UICONTROL Purchase Order]並轉換為訂單後，請透過`sales_order_tax_item`表格和REST API檢查稅捐資料。

<u>預期結果</u>：

* `sales_order_tax_item`資料表應包含`tax_item`資料。
* `applied_taxes`陣列應在採購單的API回應中顯示正確的稅捐資訊，類似於其他付款方式（例如，支票/匯票）。

<u>實際結果</u>：

* `sales_order_tax_item`資料表不包含任何`tax_item`資料。
* *[!UICONTROL Purchase Order]*&#x200B;的API回應中的`applied_taxes`與`item_applied_taxes`陣列是空的。
* 使用&#x200B;*[!UICONTROL Purchase Order]*&#x200B;付款方式時未顯示任何稅捐資料。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
