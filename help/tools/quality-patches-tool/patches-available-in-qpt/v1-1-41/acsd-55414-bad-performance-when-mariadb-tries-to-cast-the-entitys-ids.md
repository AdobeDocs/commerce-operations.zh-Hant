---
title: ACSD-55414：當MariaDB嘗試轉換entitys_ids時，效能不佳
description: 套用ACSD-55414修補程式以修正Adobe Commerce問題，當MariaDB嘗試將&grave;entitys_ids&grave;從字串轉換為整數時，這會阻礙重新索引的效能。
feature: Attributes
role: Admin, Developer
exl-id: 76309cef-559e-4a55-a27b-7d807ef9f74e
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# ACSD-55414：當MariaDB嘗試轉換`entitys_ids`時效能不佳

ACSD-55414修補程式修正了MariaDB嘗試將`entitys_ids`從字串轉換為整數時，重新索引效能受損的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.41時，即可使用此修補程式。 修補程式ID為ACSD-55414。 請注意，問題已在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.5-p5

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當MariaDB嘗試將`entitys_ids`從字串轉換為整數時，重新索引的效能會受阻。

<u>要再現的步驟</u>：

1. 透過設定`setup/performance-toolkit/profiles/ce/small.xml`50000 *簡單產品來更新*。
1. 透過執行命令來產生此設定檔： `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`。
1. 執行重新索引： `bin/magento indexer:reindex catalog_product_attribute`。

<u>預期結果</u>：

重新索引需要合理的時間才能完成。

<u>實際結果</u>：

重新索引需要太多時間才能完成。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)：搜尋修補程式[!DNL Quality Patches Tool]。
