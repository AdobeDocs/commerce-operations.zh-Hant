---
title: ACSD-62629： Widget中的產品清單顯示不正確的類別
description: 套用ACSD-62629修補程式，修正Adobe Commerce中Widget使用的產品清單未遵守類別條件的問題。
feature: Page Content
role: Admin, Developer
exl-id: a7d6bd43-4b8b-48c4-ae9a-4093ac3a4110
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# ACSD-62629： Widget中的產品清單顯示不正確的類別

ACSD-62629修補程式修正Widget中使用的產品清單不符合類別條件的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57時，即可使用此修補程式。 修補程式ID為ACSD-62629。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

Widget中使用的產品清單不符合類別條件。

<u>要再現的步驟</u>：

1. 建立名為TEST的[!UICONTROL simple product]並將其新增到類別1。
1. 為TEST產品建立無結束日期的分段更新。 等到更新作用中為止。
1. 使用兩個子產品建立名為TEST 2的[!UICONTROL configurable product]並將其新增到類別2。
1. 建立另一個名為TEST 5的[!UICONTROL simple product]並將其新增到類別1。
1. 執行完整重新索引。
1. 導覽至「**[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]**」並編輯首頁。
1. 新增[!UICONTROL Products] Widget，其中將&#x200B;*[!UICONTROL Appearance]*&#x200B;設為&#x200B;*[!UICONTROL Product Carousel]*&#x200B;並將&#x200B;*[!UICONTROL Category]*&#x200B;設為「類別2」。 儲存頁面。
1. 前往前端並開啟首頁。

<u>預期結果</u>：

頁面上應只會出現TEST 2 （可設定）產品。

<u>實際結果</u>：

頁面上會顯示TEST 5 （簡單）和TEST 2 （可設定）產品。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。


## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
