---
title: 「ACSD-58471：排程相關目錄價格規則時，動態內容無法在產品詳細資料頁面上載入」
description: 套用ACSD-58471修補程式，修正排程相關目錄價格規則時，產品詳細資料頁面上無法載入動態內容的Adobe Commerce問題。
feature: Catalog Management
role: Admin, Developer
exl-id: 6ff68b74-67fc-400c-aa79-a1274fd19708
source-git-commit: 28390659fe180180c9b2c8d16239008a1f8a510b
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# ACSD-58471：排程相關型錄價格規則時，無法在產品詳細資料頁面上載入動態內容

ACSD-58471修補程式解決排程相關目錄價格規則時，產品詳細資料頁面上無法載入動態內容的問題。 系統現在會在產品詳細資料頁面上正確顯示與已排程型錄價格規則相關聯的動態內容。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55時，即可使用此修補程式。 修補程式ID為ACSD-58471。 請注意，此問題已排程在Adobe Commerce 2.5.0中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**
* Adobe Commerce （所有部署方法） 2.4.5-p4

**與Adobe Commerce版本相容：**
* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

已排程目錄價格規則時，產品詳細資料頁面上未載入動態內容。

<u>要再現的步驟</u>：

1. 在Commerce [!UICONTROL Admin] > **[!UICONTROL Content]** > **[!UICONTROL Dynamic Blocks]**&#x200B;中建立動態區塊。
1. 在[!UICONTROL Admin] > **[!UICONTROL Content]** > **[!UICONTROL Blocks]**&#x200B;中建立靜態區塊。 使用Widget新增內容。
1. 建立產品並將CMS區塊新增到說明中。
1. 透過排程更新建立目錄規則，並在「**[!UICONTROL Marketing]** >促銷活動> **[!UICONTROL Catalog Products Rules]**」中指派產品及建立的動態區塊。
1. 執行cron，並檢查產品詳細資料頁面是否在排程的開始時間後顯示動態內容。
1. 在沒有排程更新的情況下建立目錄規則，並在「**[!UICONTROL Marketing]** >促銷活動> **[!UICONTROL Catalog Products Rules]**」中指派產品和建立的動態區塊。
1. 執行cron並檢查產品詳細資料頁面是否在排程時間後顯示動態內容。


<u>預期結果</u>：

動態內容會在排程的開始時間後載入。

<u>實際結果</u>：

動態內容未載入。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。


## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
