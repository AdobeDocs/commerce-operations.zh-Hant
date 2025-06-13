---
title: ACSD-50817：最佳化cron工作sales_clean_quotes以更快執行
description: 套用ACSD-50817修補程式，透過在報價表的'store_id'和'updated_at'欄上新增複合索引，最佳化cron工作'sales_clean_quotes'以更快地執行。
feature: Quotes
role: Admin
exl-id: b6cd412f-2f37-438b-9abc-d45de6ed54d6
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# ACSD-50817：最佳化cron工作`sales_clean_quotes`以更快執行

ACSD-50817修補程式會透過在引號表格中的`store_id`和`updated_at`欄上新增複合索引，最佳化cron工作`sales_clean_quotes`的執行速度。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.31時，即可使用此修補程式。 修補程式ID為ACSD-50817。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

cron工作`sales_clean_quotes`太慢。 透過此修補程式，已透過在引號表格的`store_id`和`updated_at`欄上新增複合索引，最佳化其執行速度。

<u>要再現的步驟</u>：

1. 產生50-80M的報價單，並將`updated_at`設定為小於30天的週期。
1. 在報價表上執行cron工作`sales_clean_quotes`或下列查詢：

   ```cron
   SELECT COUNT(*) FROM `quote` AS `main_table` WHERE (`store_id` = '1') AND (`updated_at` <= '2023-02-25') AND (`is_persistent` = '0')
   
   SELECT * FROM `quote` AS `main_table` WHERE (`store_id` = '1') AND (`updated_at` <= '2023-02-25') AND (`is_persistent` = '0') LIMIT 50
   ```

<u>預期結果</u>

Cron工作`sales_clean_quotes`已最佳化，藉由在引號表格中的`store_id`與`updated_at`欄上新增複合索引，以加快執行速度。

<u>實際結果</u>

查詢速度太慢。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
