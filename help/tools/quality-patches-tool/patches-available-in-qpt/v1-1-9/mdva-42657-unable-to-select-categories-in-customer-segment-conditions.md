---
title: MDVA-42657：無法在客戶區段條件中選取類別
description: MDVA-42657修補程式解決管理員使用者無法在客戶區段條件中選取類別的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.9後，即可使用此修補程式。 修補程式ID為MDVA-42657。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
feature: Categories, Console, Customer Service
role: Admin
exl-id: 115bad99-a603-4940-897e-034974ed1a6c
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 0%

---

# MDVA-42657：無法在客戶區段條件中選取類別

MDVA-42657修補程式解決管理員使用者無法在客戶區段條件中選取類別的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.9時，即可使用此修補程式。 修補程式ID為MDVA-42657。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

管理員使用者無法在客戶區段條件中選取類別。

<u>要再現的步驟</u>：

1. 移至&#x200B;**客戶** > **區段**。
1. 建立新區段。
1. 前往新建立的區段，然後按一下左側導覽中的&#x200B;**條件**。
1. 按一下綠色加號。
1. 選取「產品」下的「產品歷史記錄」。
1. 將「已檢視」變更為「已訂購」。
1. 將「全部」變更為「任何」。
1. 按一下巢狀綠色加號並選取「類別」。
1. 按一下&#x200B;**...**&#x200B;符號，然後按一下選擇器圖示（核取記號左側）。
1. 開啟瀏覽器開發主控台。
1. 勾選任何/多個類別的核取方塊，並注意主控台中擲回的javascript錯誤。
1. 按一下&#x200B;**儲存**&#x200B;按鈕。
1. 導覽回條件，並檢查選取的類別是否已儲存。

<u>預期結果</u>：

檢視/編輯區段條件時，會儲存及選取選取的類別。

<u>實際結果</u>：

缺少選取的類別，且未正確儲存。 您在主控台中收到下列錯誤：

```
category-checkbox-tree.js:249 Uncaught TypeError: Cannot set properties of undefined (setting 'value')
    at Ext.tree.TreePanel.Enhanced.<anonymous> (category-checkbox-tree.js:249)
    at Ext.util.Event.fire (ext-tree.js:29)
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
