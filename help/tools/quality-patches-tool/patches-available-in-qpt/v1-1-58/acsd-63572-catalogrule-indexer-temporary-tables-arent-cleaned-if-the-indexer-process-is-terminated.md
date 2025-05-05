---
title: ACSD-63572：如果索引器處理序已終止，則不會清除「catalogrule」索引器暫存資料表
description: 套用ACSD-63572修補程式以修正Adobe Commerce問題，此問題發生在處理程式因系統升級或於[!UICONTROL CLI]中停止而終止時，未清除索引器資料表。
feature: System
Role: Admin, Developers
source-git-commit: 588a543a8c0bfb8067f81e7131d0a53e5cdc340a
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---


# ACSD-63572：如果索引器處理序已終止，則不會清除`catalogrule`索引器暫存資料表

ACSD-63572修補程式修正了在處理序因系統/升級或在[!UICONTROL CLI]中停止而終止時，未清除索引子臨時資料表的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58時，即可使用此修補程式。 修補程式ID為ACSD-63572。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p8

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當處理序因系統升級或在[!UICONTROL CLI]中停止而終止時，索引子暫存資料表沒有清除。

<u>要再現的步驟</u>：

1. 開啟[!UICONTROL CLI]。
1. 執行命令： `bin/magento indexer:reindex catalogrule_rule`。
1. 在程式完成之前取消程式，使用： `^C`。
1. 重設索引子，使用： `bin/magento indexer:reset catalogrule_rule catalogrule_product`。
1. 重複上述步驟多次。
1. 檢查下列已在資料庫中建立的暫存表格：

   ```
   catalogrule_product__temp*
   catalogrule_product_price__temp*
   ```

<u>預期結果</u>：

不需要舊臨時表格時會將其刪除。

<u>實際結果</u>：

不會移除舊的臨時表格。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
