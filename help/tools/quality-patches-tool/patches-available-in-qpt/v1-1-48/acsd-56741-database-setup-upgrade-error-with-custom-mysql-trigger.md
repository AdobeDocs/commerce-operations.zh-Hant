---
title: ACSD-56741：疑難排解自訂MySQL觸發器的資料庫設定錯誤
description: 套用ACSD-56741修補程式以修正Adobe Commerce問題，該問題導致在「setup：upgrade」期間出現錯誤訊息*嘗試存取型別為null*的值的陣列位移，這是因為資料庫中的自訂MySQL觸發程式與索引和 [!DNL MView]無關。
feature: Install
role: Admin, Developer
exl-id: 93a1c75f-8a45-49df-9fa4-6ba1234c822d
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-56741：疑難排解自訂MySQL觸發器的資料庫設定錯誤

ACSD-56741修補程式修正了以下問題：由於資料庫中的自訂MySQL觸發程式與索引和[!DNL MView]無關，因此在`setup:upgrade`期間出現錯誤訊息&#x200B;*嘗試存取型別為null*&#x200B;的值上的陣列位移。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.48時，即可使用此修補程式。 修補程式ID為ACSD-56741。 請注意，此問題已排程在Adobe Commerce 2.5.0中修正

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

`setup:upgrade`期間出現錯誤訊息&#x200B;*嘗試存取型別null*&#x200B;值的陣列位移，因為資料庫中的自訂MySQL觸發程式與索引和[!DNL MView]無關。

<u>要再現的步驟</u>：

1. 執行`php bin/magento indexer:set-mode schedule`。

   ```
   DELIMITER //
   CREATE TRIGGER trg_catalog_category_entity_before_delete_umis BEFORE DELETE ON catalog_category_entity FOR EACH ROW
       -> BEGIN
       -> UPDATE ewave_navigation_menu_item_info as nit INNER JOIN ewave_navigation_menu_category_type as ncmi ON nit.id = ncmi.menu_item_id AND ncmi.category_id = OLD.entity_id SET nit.status = 0;
       -> END //
   ```

1. 執行`php bin/magento c:f`。
1. 執行`php bin/magento setup:upgrade`。

<u>預期結果</u>：

安裝程式升級順利完成，沒有發生任何錯誤。

<u>實際結果</u>：

安裝程式升級結束，並出現錯誤訊息：

*警告：正在嘗試存取型別null*&#x200B;值的陣列位移。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
