---
title: MDVA-31590：無法使用MySQL非同步佇列大量更新屬性
description: MDVA-31590修補程式解決使用者無法使用MySQL非同步佇列大量更新屬性的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.3後，即可使用此修補程式。 修補程式ID為MDVA-31590。 請注意，問題已在Adobe Commerce 2.4.2中修正。
feature: Attributes, Services
role: Admin
exl-id: f8d1c3bd-e995-41ef-89e1-93eec6e8b1f1
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 0%

---

# MDVA-31590：無法使用MySQL非同步佇列大量更新屬性

MDVA-31590修補程式解決使用者無法使用MySQL非同步佇列大量更新屬性的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.3時，即可使用此修補程式。 修補程式ID為MDVA-31590。 請注意，問題已在Adobe Commerce 2.4.2中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.0

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.0-2.4.1-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用者無法使用MySQL非同步大量更新屬性。

<u>要再現的步驟</u>：

1. 在後端的產品格線上，執行大量動作以更新一些產品的屬性值。
   * 檢查產品，並從[動作]下拉式清單中選取&#x200B;**更新屬性**。
1. 設定必要屬性的值，並將產品指派至網站並儲存。
1. 頁面重新載入後，會顯示如下的訊息：
   *任務「更新N個所選產品的屬性」：已排定1個專案進行更新。*
1. 等候幾秒鐘，然後重新載入後端頁面。

<u>預期結果</u>：

1. 頁面顯示成功的更新訊息，例如： *1個專案已成功更新。*
1. 相關產品的屬性值會更新。
1. 在DB中，會在`magento_bulk`資料表和`magento_operation`資料表（與大量相關的作業）中建立新記錄。
1. 已在`queue_message`資料表中建立新記錄（與佇列`product_action_attribute.update`和/或`product_action_attribute.website.update`相關）。
1. `queue_message_status`資料表有狀態為「4」的記錄。
1. `system.log`中沒有錯誤。

<u>實際結果</u>：

1. 頁面仍會顯示類似以下內容的訊息：
   *任務「更新N個所選產品的屬性」：已排定1個專案進行更新。*
1. 產品的屬性值會更新。
1. 已在`message_bulk`資料表中建立新記錄，但`magento_operation`資料表中沒有相關記錄。
1. 已在`queue_message`和`queue_message_status`資料表中建立新記錄。
1. `queue_message_status`資料表有錯誤狀態的記錄（狀態值「6」）。
1. `system.log`包含類似下列的錯誤：

   ```sql
   *main.CRITICAL: Message has been rejected: SQLSTATE[23000]: Integrity constraint violation: 1048 Column 'operation_key' cannot be null, query was: INSERT INTO {{magento_operation}} ({{id}}, {{bulk_uuid}}, {{topic_name}}, {{serialized_data}}, {{result_serialized_data}}, {{status}}, {{error_code}}, {{result_message}}, {{operation_key}}) VALUES (?, ?, ?, ?, ?, ?, ?, ?, ?) [] []*
   ```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱QPT[&#128279;](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)中可用的修補程式區段。
