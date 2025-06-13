---
title: ACSD-53925：無法以[!UICONTROL Product Carousel]儲存CMS區塊
description: 套用ACSD-53925修補程式以修正將「catalog_product_price」的維度模式設為網站時，管理員無法透過產品輪播儲存CMS區塊的Adobe Commerce問題。
feature: CMS, Page Builder, Price Indexer, Products
role: Admin, Developer
exl-id: f6d286ab-d904-4f08-8265-99632f74b88a
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# ACSD-53925：無法以&#x200B;*[!UICONTROL Product Carousel]*&#x200B;儲存CMS區塊

ACSD-53925修補程式修正當`catalog_product_price`的維度模式設定為網站時，管理員無法以&#x200B;*[!UICONTROL Product Carousel]*&#x200B;儲存CMS區塊的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.43時，即可使用此修補程式。 修補程式ID為ACSD-53925。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當`catalog_product_price`的維度模式設定為網站時，管理員無法儲存具有&#x200B;*[!UICONTROL Product Carousel]*&#x200B;的CMS區塊。

<u>要再現的步驟</u>：

1. 建立兩個簡單的產品：
   * 簡單1 - $10
   * 簡單2 - $20
1. 根據簡單產品SKU建立具有兩個選項的套件組合產品&#39;*bundle1-dyn*&#39;。
1. 設定產品價格索引器的維度模式：

   `bin/magento indexer:set-dimensions-mode catalog_product_price website`

1. 前往&#x200B;**[!UICONTROL Content]** > **[!UICONTROL Blocks]**，並建立新的CMS區塊。
1. 使用[!DNL Page Builder]編輯內容：
   * 新增&#x200B;*[!UICONTROL Row]*&#x200B;元素
   * 新增&#x200B;*[!UICONTROL Products]*&#x200B;元素
   * 選取&#x200B;*[!UICONTROL Product Carousel]*
   * 輸入產品SKU - *bundle1-dyn*
1. 儲存CMS區塊。

<u>預期結果</u>：

使用者可以新增產品輪播，不會發生錯誤。

<u>實際結果</u>：

* UI中擲回訊息： *很抱歉，產生此內容時發生錯誤*
* `var/log/exception.log`包含下列錯誤：

  ```
  [2023-08-18T20:58:14.533374+00:00] report.CRITICAL: PDOException: SQLSTATE[42S02]: Base table or view not found: 1146 Table 'username_dev.catalog_product_index_price_ws0' doesn't exist in /test/lib/internal/Magento/Framework/DB/Statement/Pdo/Mysql.php:90
  ```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
