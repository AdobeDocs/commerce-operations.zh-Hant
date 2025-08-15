---
title: ACSD-48417：建立排程變更後發生SQL錯誤
description: 套用ACSD-48417修補程式來修正Adobe Commerce問題，建立產品的排程變更並儲存另一個產品後，出現SQL錯誤。
feature: Storage
role: Admin
exl-id: c8e7c7aa-ac53-4218-8c3c-ea2240af17c9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# ACSD-48417：建立排程變更後發生SQL錯誤

ACSD-48417修補程式修正建立產品的排程變更並儲存另一個產品後出現SQL錯誤的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.26時，即可使用此修補程式。 修補程式ID為ACSD-48417。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.1-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

建立產品的排程變更並儲存另一個產品後，會出現SQL錯誤。

<u>要再現的步驟</u>：

1. 安裝Magento 2.4-develop EE +範例資料。
1. 前往管理面板> **[!UICONTROL Catalog]** > **[!UICONTROL Products]**。
1. 編輯任何產品（例如Joust Duffle Bag [SKU： 24-MB01]）。
1. 排程新的更新：
   * 選取&#x200B;**[!UICONTROL Save as a New Update]**
   * 更新名稱： &quot;Update 1&quot;
   * 開始日期：目前時間+1分鐘
   * 結束日期：目前時間+1小時
   * 將產品名稱修改為：「Joust Duffle Bag 2」
   * 儲存產品。
1. 前往CLI並執行cron，然後等待套用排程。

   ```
   bin/magento cron:run && bin/magento cron:run
   ```

1. 再次移至&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Products]**&#x200B;並編輯任何可設定的產品（例如Chaz Kangeroo Hoodie [SKU： MH01]）。

   * 停用所有變體。 移至[動作]欄> **[!UICONTROL Select]** > **[!UICONTROL Disable Product]**。
   * 儲存可設定的。

<u>預期結果</u>：

儲存產品時沒有錯誤。

<u>實際結果</u>：

發生下列錯誤：

```SQL
SQLSTATE[23000]: Integrity constraint violation: 1048 Column 'sku' cannot be null, query was: INSERT INTO `catalog_product_entity` (`entity_id`, `sku`, `row_id`, `created_in`, `updated_in`) VALUES (?, ?, ?, ?, ?)
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)：搜尋修補程式[!DNL Quality Patches Tool]。
