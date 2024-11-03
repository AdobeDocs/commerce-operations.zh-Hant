---
title: 'MDVA-37897：從「最近檢視的專案」新增產品時，重新導向不正確'
description: MDVA-37897修補程式可解決使用者嘗試使用最近檢視的Widget中的選項新增產品時，所發生的重新導向錯誤問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.1後，即可使用此修補程式。 修補程式ID為MDVA-37897。 請注意，此問題已排程在Adobe Commerce 2.4.4版中修正。
feature: Products
role: Admin
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# MDVA-37897：從「最近檢視的專案」新增產品時，重新導向不正確

MDVA-37897修補程式可解決使用者嘗試使用最近檢視的Widget中的選項新增產品時，所發生的重新導向錯誤問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.1時，即可使用此修補程式。 修補程式ID為MDVA-37897。 請注意，此問題已排程在Adobe Commerce 2.4.4版中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* 雲端基礎結構上的Adobe Commerce 2.4.1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.0 - 2.4.2-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當使用者嘗試從最近檢視的區段新增具有所需選項的產品時，使用者將被重新導向到產品清單頁面而不是產品詳細資訊頁面。

<u>要再現的步驟</u>：

1. 使用可自訂的選項建立簡單產品（型別：選項按鈕）。
1. 設定最近檢視的Widget以顯示產品。
1. 瀏覽具有可自訂選項的產品，使其顯示在「最近檢視的Widget」中。
1. 在「最近檢視的」Widget中，按一下其中一個產品上的&#x200B;**「加入購物車」**。

<u>預期結果</u>：

系統會將您重新導向至產品詳細資料頁面，以選擇選項。

<u>實際結果</u>：

系統會將您重新導向至產品清單頁面。

## 套用修補程式

若要套用個別修補程式，請根據您的部署型別使用下列連結：

* Adobe Commerce內部部署：開發人員檔案中的[軟體更新指南>套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 我們的雲端基礎結構上的Adobe Commerce：開發人員檔案中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解Adobe Commerce的品質修補程式，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)中可用的[修補程式區段。
