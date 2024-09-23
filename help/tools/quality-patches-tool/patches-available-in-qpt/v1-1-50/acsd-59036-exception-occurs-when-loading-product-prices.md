---
title: 'ACSD-59036：載入上下限均設為$0的產品價格時發生例外狀況'
description: 套用ACSD-59036修補程式，修正Adobe Commerce載入產品價格（上下限皆設為*$0*）時發生例外狀況的問題。
feature: Categories, Products, Storefront, Search
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---

# ACSD-59036：載入上下限均設為&#x200B;*$0*&#x200B;的產品價格時發生例外狀況

ACSD-59036修補程式修正載入上下限均設為&#x200B;*$0*&#x200B;的產品價格時發生例外狀況的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.50時，即可使用此修補程式。 修補程式ID為ACSD-59036。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.4.7

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.7 - 2.4.7-p2

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

載入上下限皆設為&#x200B;*$0*&#x200B;的產品價格時發生例外狀況。

發生此問題是因為載入包含價格範圍的查詢時，演演算法不會考慮NULL值。 若要修正此問題，我們可以檢查上下範圍是否均為NULL，如果是，請為兩個限制指派值&#x200B;*0*。 這應該可以避免擲回任何錯誤。

<u>要再現的步驟</u>：

1. 建立&#x200B;*13*&#x200B;簡單產品。
1. 將所有&#x200B;*13*&#x200B;產品指派至類別。
1. 將一項產品的價格設定為&#x200B;*$1322.94*。
1. 將所有其他產品的價格設定為&#x200B;*$0*。
1. 將[!DNL OpenSearch]設定為搜尋引擎。
1. 移至&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Storefront]**，並將&#x200B;**[!UICONTROL PLP]**&#x200B;計數設為&#x200B;*16*。
1. 將&#x200B;**[!UICONTROL Price Navigation Step Calculation]**&#x200B;設定為&#x200B;*自動（平均產品計數）*。
1. 執行完整重新索引。
1. 開啟&#x200B;*[!UICONTROL Category]*&#x200B;頁面。

<u>預期結果</u>：

*[!UICONTROL Category]*&#x200B;頁面會顯示所有產品。

<u>實際結果</u>：

發生錯誤：

```JSON
report.CRITICAL: OpenSearch\Common\Exceptions\BadRequest400Exception: {"error":{"root_cause":[{"type":"x_content_parse_exception","reason":"[1:193] [bool] failed to parse field [must]"}],"type":"x_content_parse_exception","reason":"[1:193] [bool] failed to parse field [filter]","caused_by":{"type":"x_content_parse_exception","reason":"[1:193] [bool] failed to parse field [must]","caused_by":{"type":"illegal_argument_exception","reason":"field name is null or empty"}}},"status":400} in /vendor/opensearch-project/opensearch-php/src/OpenSearch/Connections/Connection.php:664
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
