---
title: ACSD-66404：由於 [!DNL Galera Cluster] 交易大小限制，Cron作業無法清除changelog表格
description: 套用ACSD-66404修補程式，修正cron工作無法清除變更記錄檔表格的Adobe Commerce問題，並在這些表格中有大量資料時造成 [!DNL Galera Cluster] 問題。
feature: System
role: Admin, Developer
type: Troubleshooting
source-git-commit: 42bd5934782ca65b891a36f61102083356c92e59
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---


# ACSD-66404：由於[!DNL Galera Cluster]個交易大小限制，Cron作業無法清除changelog表格

ACSD-66404修補程式修正cron工作無法清除changelog表格，在處理大量資料時導致[!DNL Galera Cluster]問題的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69時，即可使用此修補程式。 修補程式ID為ACSD-66404。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p6、2.4.7-p6

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

Cron工作未清除changelog表格，並在這些表格中有大量資料時造成[!DNL Galera Cluster]問題。

<u>要再現的步驟</u>：

1. 使用效能設定檔產生許多產品。
1. 對系統中的所有產品執行大量更新，因此`inventory_cl` DB表格中有許多專案。
1. 執行`indexer_clean_all_changelogs` cron工作。

<u>預期結果</u>：

`indexer_clean_all_changelogs` cron工作能夠在多個刪除查詢中對大型變更記錄檔(10+ GB)執行變更記錄檔清除，而不會造成[!DNL Galera Cluster]個問題。

<u>實際結果</u>：

`indexer_clean_all_changelogs` cron工作會在單一刪除查詢中的大型變更記錄檔(10+ GB)上執行變更記錄檔清理，造成[!DNL Galera Cluster]個問題。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]： Tools指南中用於品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具
