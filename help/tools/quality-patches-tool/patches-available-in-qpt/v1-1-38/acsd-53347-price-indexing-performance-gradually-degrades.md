---
title: ACSD-53347：價格指數效能逐漸降低
description: 套用ACSD-53347修補程式，修正重新索引大型產品目錄的價格時，效能逐漸降低的Adobe Commerce問題。
feature: Price Indexer
role: Admin
exl-id: 8986b685-55e4-47c7-852c-aca18e3b02e9
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# ACSD-53347：價格指數效能逐漸降低

ACSD-53347修補程式修正重新索引大型產品目錄的價格時，效能逐漸降低的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.38時，即可使用此修補程式。 修補程式ID為ACSD-53347。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當重新索引大型產品目錄的價格時，在索引過程中執行的查詢效能會逐漸降低。

<u>要再現的步驟</u>：

1. 建立大型簡單目錄並將自訂選項指派給這些產品（自訂選項在索引編制期間使用臨時表格）。
1. 建立至少200個或更多客戶群組以提高問題的可見度。
1. 建立10個以上的網站，並將所有產品指派給每一個。
1. 請注意，匯入的產品幾乎完全相同，只是SKU和名稱不同。
1. 啟用&#x200B;**[!UICONTROL DB Logging]**。
1. 執行`bin/magento index:reindex catalog_product_price`命令。
1. 檢查`db.log`中來自&#x200B;`catalog_product_index_price_opt_agr_temp`*的* DELETE。

<u>預期結果</u>：

*DB查詢*&#x200B;的執行有效率。

<u>實際結果</u>：

臨時表格上&#x200B;*DB查詢*&#x200B;的效能逐漸變慢，因此價格索引表格需要花很長時間才能完成。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* 在[!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)

## 相關閱讀

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用
* [在Commerce實作行動手冊中修改資料庫表格的最佳實務](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
