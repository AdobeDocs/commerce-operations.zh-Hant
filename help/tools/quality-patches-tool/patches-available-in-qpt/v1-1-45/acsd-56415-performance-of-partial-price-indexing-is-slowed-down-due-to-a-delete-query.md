---
title: ACSD-56415：由於「DELETE」查詢，[!UICONTROL Partial Price Indexing]的效能變慢
description: 套用ACSD-56415修補程式來修正Adobe Commerce問題，該問題導致資料庫含有大量要編制索引的部分價格資料時，[!UICONTROL Partial Price Indexing]的效能因「DELETE」查詢而降低。
feature: Catalog Service
role: Admin, Developer
exl-id: c877844e-79d3-4756-97a5-de44e6fb5170
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# ACSD-56415：由於`DELETE`查詢，[!UICONTROL Partial Price Indexing]的效能變慢

ACSD-56415修補程式修正了資料庫含有大量部分價格資料索引時，[!UICONTROL Partial Price Indexing]由於`DELETE`查詢而效能變慢的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.45時，即可使用此修補程式。 修補程式ID為ACSD-56023。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當資料庫含有大量部分價格資料索引時，[!UICONTROL Partial Price Indexing]的效能會因為`DELETE`查詢而減慢。

<u>要再現的步驟</u>：

1. 使用大型效能設定檔建立&#x200B;*300000產品*&#x200B;和&#x200B;*10個網站*。
1. 登入「管理面板」。
1. 建立&#x200B;*10個客戶群組*。
1. 執行以下查詢以將產品新增到`_cl`資料表：

   &grave;&grave;
    insert into catalog_product_price_cl (entity_id) select entity_id from catalog_product_entity
 &grave;&grave;

1. 執行以下命令以觸發部分價格索引程式：

   &grave;&grave;
    bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
 &grave;&grave;

<u>預期結果</u>：

快速執行來自`catalog_product_index_price`的SQL查詢DELETE `main_table`。

<u>實際結果</u>：

來自`catalog_product_index_price`的SQL查詢DELETE `main_table`執行速度非常慢。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)

## 相關閱讀

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用
* [在Commerce實作行動手冊中修改資料庫表格的最佳實務](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
