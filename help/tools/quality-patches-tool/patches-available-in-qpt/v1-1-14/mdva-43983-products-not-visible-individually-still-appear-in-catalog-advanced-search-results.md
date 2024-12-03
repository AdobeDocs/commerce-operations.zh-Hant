---
title: MDVA-43983：設為「個別不可見」的產品會出現在搜尋結果中
description: MDVA-43983修補程式可解決設定為「無法個別顯示」的產品仍會出現在目錄進階搜尋結果中的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.14時，即可使用此修補程式。 修補程式ID為MDVA-43983。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
feature: Catalog Management, Products, Search
role: Admin
exl-id: d494d263-016b-43fd-aa87-0d74eadc4a6a
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# MDVA-43983：設為「個別不可見」的產品會出現在搜尋結果中

MDVA-43983修補程式可解決設定為「無法個別顯示」的產品仍會出現在目錄進階搜尋結果中的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.14時，即可使用此修補程式。 修補程式ID為MDVA-43983。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.4

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

設定為「無法個別顯示」的產品仍會出現在目錄進階搜尋結果中。

<u>要再現的步驟</u>：

1. 為存放區擁有者&#x200B;**建立具有**&#x200B;目錄輸入型別的屬性，做為&#x200B;**下拉式清單**&#x200B;或&#x200B;**視覺色票** （例如，顏色）。
1. 將&#x200B;**在搜尋中使用**&#x200B;設為&#x200B;**是**，將&#x200B;**在進階搜尋中可見**&#x200B;設為&#x200B;**是**。
1. 新增一些屬性選項。
1. 建立具有&#x200B;**可見性**&#x200B;的產品，因為&#x200B;**不個別可見**。
1. 指定色彩屬性選項。
1. 前往店面的&#x200B;**目錄進階搜尋**&#x200B;頁面。
1. 從「顏色」屬性欄位中只選取「顏色」屬性選項，其餘欄位則保留空白或原樣。
1. 提交進階搜尋表單。
1. 觀察搜尋結果。

<u>預期結果</u>：

設定為「不可個別顯示」的產品不會出現在目錄進階搜尋結果中。

<u>實際結果</u>：

設定為「不可個別顯示」的產品會出現在目錄進階搜尋結果中。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
