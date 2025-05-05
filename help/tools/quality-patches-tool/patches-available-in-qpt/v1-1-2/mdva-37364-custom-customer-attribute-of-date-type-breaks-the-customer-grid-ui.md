---
title: MDVA-37364：日期型別的自訂客戶屬性破壞格線UI
description: MDVA-37364修補程式解決日期型別的自訂客戶屬性破壞客戶網格UI的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2時，即可使用此修補程式。 修補程式ID為MDVA-37364。 請注意，此問題已排程在Adobe Commerce 2.4.4版中修正。
feature: Attributes, Cache
role: Developer
exl-id: 5bd64004-06c4-49fd-8e56-e2c44008ca82
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---

# MDVA-37364：日期型別的自訂客戶屬性破壞格線UI

MDVA-37364修補程式解決日期型別的自訂客戶屬性破壞客戶網格UI的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2時，即可使用此修補程式。 修補程式ID為MDVA-37364。 請注意，此問題已排程在Adobe Commerce 2.4.4版中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.0-2.4.2-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

日期型別的自訂客戶屬性會中斷Customer Grid UI。

<u>要再現的步驟</u>：

1. 建立具有日期型別的自訂屬性：
   * 移至&#x200B;**商店** > **屬性** > **新增屬性**。
   * 將「輸入型別」設定為「日期」。
   * 將「新增至欄選項」設定為「是」。
   * 儲存屬性。
1. 移至&#x200B;**管理員** > **客戶** > **所有客戶**。
   * 從欄選項新增自訂屬性至格線。
1. 建立/編輯客戶並設定已建立自訂日期屬性欄位的值。
1. 儲存、重新索引和清除快取。
1. 移至&#x200B;**客戶** > **所有客戶**。
   * 勾選「客戶方格」。

<u>預期結果</u>：

Admin Customer Grid會顯示所有資料，包括新的日期自訂屬性，而不會中斷Customer Grid UI。

<u>實際結果</u>：

管理客戶網格UI損毀。

## 套用修補程式

若要套用個別修補程式，請根據您的部署型別使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：自助提供品質修補程式的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱QPT[&#128279;](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)中可用的修補程式區段。
