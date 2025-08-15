---
title: ACSD-62118：未針對使用[!UICONTROL Purchase Order]方法下單的B2B訂單完全更新「sales_order_tax_item」表格
description: 套用ACSD-62118修補程式，修正使用[!UICONTROL Purchase Order]方法下達B2B訂單時，「sales_order_tax_item」表格未完全更新的Adobe Commerce問題。
feature: Purchase Orders, B2B
role: Admin, Developer
exl-id: 8ace73ad-f5a5-47ab-aca7-62c818775d2f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# ACSD-62118：使用`sales_order_tax_item`方法下達B2B訂單時，[!UICONTROL Purchase Order]資料表未完全更新

ACSD-62118修補程式修正使用`sales_order_tax_item`方法下達B2B訂單時，*[!UICONTROL Purchase Order]*&#x200B;表格未完全更新的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58時，即可使用此修補程式。 修補程式ID為ACSD-62118。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

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
* `applied_taxes`的API回應中的`item_applied_taxes`與&#x200B;*[!UICONTROL Purchase Order]*&#x200B;陣列是空的。
* 使用&#x200B;*[!UICONTROL Purchase Order]*&#x200B;付款方式時未顯示任何稅捐資料。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
