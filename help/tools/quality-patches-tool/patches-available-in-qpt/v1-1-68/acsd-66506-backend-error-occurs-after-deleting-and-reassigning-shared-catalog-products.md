---
title: ACSD-66506：刪除並重新指派共用目錄產品後發生後端錯誤
description: 套用ACSD-66506修補程式來修正Adobe Commerce問題，其中後端擲回錯誤*要求的產品不存在。 請驗證產品，並在刪除先前指派的產品並將新產品指派至共用目錄後重試*。
feature: B2B
role: Admin, Developer
type: Troubleshooting
source-git-commit: 8f77101832ccfb415d040c202f0fc7221f97419a
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---


# ACSD-66506：刪除並重新指派共用目錄產品後發生後端錯誤

ACSD-66506修補程式修正後端擲回錯誤&#x200B;*要求的產品不存在的問題。 請驗證產品，並在刪除先前指派的產品並將新產品指派至共用目錄後重試*。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68時，即可使用此修補程式。 修補程式ID為ACSD-66506。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

刪除先前指派的產品並將新產品指派給&#x200B;**[!UICONTROL Shared Catalog]**&#x200B;後，後端傳回以下錯誤： *要求的產品不存在。 請驗證產品，然後再試一次*

<u>要再現的步驟</u>：

1. 使用效能工具組建立一些產品： `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`
1. 移至&#x200B;**[!UICONTROL [!DNL B2B] Features]**&#x200B;設定並將&#x200B;**[!UICONTROL Enable Company]**&#x200B;和&#x200B;**[!UICONTROL Enable Shared Catalog]**&#x200B;設定為`Yes`。
1. 建立新的共用目錄。
1. 將所有產生的產品指派給新建立的共用目錄。
1. 使用&#x200B;**[!UICONTROL Product Import]**&#x200B;刪除指派給共用目錄的產品。
   1. 匯出依SKU篩選的產品。
   1. 選取&#x200B;**[!UICONTROL Import Behavior: Delete]**，然後匯入相同的檔案。
1. 開啟&#x200B;**[!UICONTROL Shared Catalog]**&#x200B;並設定價格與結構。
   1. 選取&#x200B;**[!UICONTROL Set Pricing and Structure]**。
   1. 按一下&#x200B;**[!UICONTROL Next]**，然後按&#x200B;**[!UICONTROL Generate Catalog]**。
   1. 按一下&#x200B;**[!UICONTROL Save]**。

<u>預期結果</u>：

即使發生錯誤，也不會發生任何錯誤，產品仍會保留在共用目錄中。

<u>實際結果</u>：

發生錯誤： *要求的產品不存在。 驗證產品並再試一次*，所有產品都會從共用目錄中移除。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
