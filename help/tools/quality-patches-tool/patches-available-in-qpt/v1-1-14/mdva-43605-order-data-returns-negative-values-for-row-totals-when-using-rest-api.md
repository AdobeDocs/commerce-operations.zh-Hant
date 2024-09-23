---
title: 'MDVA-43605：使用Rest API時，訂單資料傳回資料列總計的負值'
description: MDVA-43605修補程式修正了使用Rest API時，訂單資料傳回負值的列總計問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.14時，即可使用此修補程式。 修補程式ID為MDVA-43605。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
feature: REST, Orders
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# MDVA-43605：使用Rest API時，訂單資料會傳回列總計的負值

MDVA-43605修補程式修正了使用Rest API時，訂單資料傳回負值的列總計問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.14時，即可使用此修補程式。 修補程式ID為MDVA-43605。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.1 - 2.4.4

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用Rest API時，訂單資料會傳回列總計的負值。

<u>要再現的步驟</u>：

1. 啟用免費送貨。
1. 導覽至&#x200B;**設定** > **目錄** > **價格** >並設定目錄價格範圍=網站。
1. 瀏覽至&#x200B;**組態** > **銷售** > **稅捐**&#x200B;並更新：
   * 出貨的稅捐類別=應稅貨品
   * 計算設定：
      * 型錄價格=含稅
      * 送貨價格=包含價格
      * 套用價格折扣=含稅
   * 價格顯示設定：包含稅捐（所有欄位）
   * 購物車顯示設定：包含稅捐（所有欄位）
   * 訂單、商業發票、銷退折讓單：
      * 顯示出貨金額=含稅
1. 建立美國的稅率（州= &#39;*&#39;），稅率百分比= 24.00
1. 建立具有上述稅率的稅捐規則。
1. 建立具有特定優惠券的購物車價格規則，並且折扣= $50是整個購物車的固定金額。
1. 使用下列價格建立四種產品：$8.90、$5.90、$6.90和$5.95。
1. 使用上一步建立的優惠券代碼，建立包括其中四個產品的管理訂單。 使用免運費。
1. 由於優惠券代碼涵蓋購物車總計，因此不需要付款。
1. 擷取剛透過Rest API端點建立的訂單：

   ```json
   GET rest/V1/orders/1
   ```

<u>預期結果</u>：

回應中的`base_row_total`和`base_row_total_incl_tax`值為零。

<u>實際結果</u>：

回應中的`base_row_total`和`base_row_total_incl_tax`欄位具有負值。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
