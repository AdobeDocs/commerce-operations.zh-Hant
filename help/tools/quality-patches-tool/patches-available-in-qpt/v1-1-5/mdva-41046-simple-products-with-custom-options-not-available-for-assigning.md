---
title: MDVA-41046：無法指派包含自訂選項的簡單產品
description: MDVA-41046修補程式解決具有自訂選項的簡單產品無法指派給可設定/分組產品的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.5時，即可使用此修補程式。 修補程式ID為MDVA-41046。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。
feature: Products
role: Developer
exl-id: 7fd7a9db-f834-4aea-a9d7-6e9535c037c8
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# MDVA-41046：無法指派包含自訂選項的簡單產品

MDVA-41046修補程式解決具有自訂選項的簡單產品無法指派給可設定/分組產品的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.5時，即可使用此修補程式。 修補程式ID為MDVA-41046。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

具有自訂選項的簡單產品無法指派給可設定/分組的產品。

<u>要再現的步驟</u>：

1. 使用可自訂選項建立簡單產品，並設定可設定屬性的值。
   * 使用&#x200B;*Color*&#x200B;作為可設定的屬性，並選取&#x200B;*Yellow*&#x200B;作為色彩值。
1. 儲存簡單產品。
1. 現在前往建立可設定的產品頁面。
1. 執行[建立設定]精靈，並確定選取&#x200B;*黃色*&#x200B;作為屬性顏色。
1. 如果不儲存可設定的產品，請從「選取」下拉式清單中選取「選擇不同的產品」選項。
1. 這會開啟依顏色屬性黃色篩選的產品格線。 現在選取先前使用可自訂選項建立的簡單產品。
1. 儲存可設定的產品。

<u>預期結果</u>：

在步驟6中，具有自訂選項的簡單產品可用於指派（顯示在格線中）。

<u>實際結果</u>：

設定區段是空的。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱QPT[&#128279;](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)中可用的修補程式區段。
