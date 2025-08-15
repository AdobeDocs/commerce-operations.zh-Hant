---
title: ACSD-60590：提升Bestsellers每日彙總報表產生的效能
description: 套用ACSD-60590修補程式，修正Adobe Commerce問題：大量下單訂單的「最暢銷商品彙總每日報表」產生時間過長。
feature: Reporting
role: Admin, Developer
exl-id: 3b2b92eb-d4fc-4cd7-a117-a2c1caac72ec
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# ACSD-60590：提升Bestsellers每日彙總報表產生的效能

ACSD-60590修補程式修正Bestsellers Aggregated Daily Report耗費大量時間才能針對大量下單訂單產生的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=zh-Hant) 1.1.52時，即可使用此修補程式。 修補程式ID為ACSD-60590。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

「最暢銷商品彙總每日報表」需要相當長的時間才能針對大量下單訂單產生。

<u>必要條件</u>

大量訂單（例如： *500k*）。

<u>要再現的步驟</u>：

1. 執行以下命令：

   `update sales_order set created_at = DATE(DATE_SUB(NOW(), INTERVAL ROUND(RAND()*3650) DAY))  ;`

1. 執行`aggregate_sales_report_bestsellers_data`工作。

<u>預期結果</u>：

工作將在30秒內完成。

<u>實際結果</u>：

查詢大約需要10分鐘的時間來完成`created_at`個日期的每一個商店。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)：搜尋修補程式[!DNL Quality Patches Tool]。
