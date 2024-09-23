---
title: 'ACSD-56616：簡單存貨短缺期間套件式產品的店面展示'
description: 套用ACSD-56616修補程式，修正Adobe Commerce發生的問題，亦即當所有相關的簡單產品無存貨時，店面會意外出現套裝產品。
feature: Products
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# ACSD-56616：在簡單存貨短缺期間，店面會顯示套件式產品。

ACSD-56616修補程式修正所有相關簡單產品無庫存時，店面意外出現套件產品的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.45時，即可使用此修補程式。 修補程式ID為ACSD-56616。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在簡單存貨短缺期間，捆綁產品的店面顯示不正確。

<u>要再現的步驟</u>：

1. 建立新網站/商店/店面。
1. 建立新的來源。
1. 建立新庫存並將其指派給新建立的網站。
1. 設定索引子以依排程更新。
1. 產生兩個簡單產品，S1 （數量= 1）和S2 （數量= 1），並將它們指派給新庫存和新網站。
1. 建立&#x200B;*套件式1*&#x200B;產品並將其與新網站建立關聯，將其放入類別&#x200B;*類別*。
1. 定義兩個必要的下拉式清單選項，並將簡單產品&#x200B;*S1*&#x200B;連結至option1，並將簡單產品&#x200B;*S2*&#x200B;連結至option2。
1. 儲存產品。
1. 導覽至&#x200B;**[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]**，並啟用&#x200B;*新增商店代碼至URL* = *是*。
1. 開啟店面並購買隨附產品。
1. 執行cron兩次。
1. 返回&#x200B;*CAT*&#x200B;類別。

<u>預期結果</u>：

*bundle1*&#x200B;產品無庫存。

<u>實際結果</u>：

顯示&#x200B;*bundle1*&#x200B;產品，價格= *$0*。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
