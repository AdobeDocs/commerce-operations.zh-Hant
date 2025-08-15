---
title: ACSD-63323：解析[!UICONTROL Select All]功能，並增強產品類別快顯視窗中的分頁和記錄計數
description: 套用ACSD-63323修補程式以修正Adobe Commerce將產品新增至類別時，[!UICONTROL Select All]選項無法運作的問題。 此外，透過快顯視窗格線將產品新增至類別時，它可確保分頁和紀錄計數標籤正確運作。
feature: Products
role: Admin, Developer
exl-id: 96e318fd-f1dd-4b15-b171-78ae1c8e4e0d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-63323：解析[!UICONTROL Select All]功能，並增強產品類別快顯視窗中的分頁和記錄計數

ACSD-63323修補程式修正將產品新增至類別時，**[!UICONTROL Select All]**&#x200B;選項無法運作的問題。 此外，透過快顯視窗格線將產品新增至類別時，它可確保分頁和紀錄計數標籤正確運作。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.60時，即可使用此修補程式。 修補程式ID為ACSD-63323。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**
* Adobe Commerce （所有部署方法） 2.4.7-p2

**與Adobe Commerce版本相容：**
* Adobe Commerce （所有部署方法） 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

修正「**[!UICONTROL Select All]**」選項在「管理員> **[!UICONTROL Categories]** >選擇類別> **[!UICONTROL Products in Category]** > **[!UICONTROL Add Products]**」中無法運作的問題。 透過快顯視窗格線將產品新增至類別時，還有助於分頁和記錄計數標籤正常運作。


<u>要再現的步驟</u>：

1. 使用下列命令產生&#x200B;*1200*&#x200B;產品：

   ```bash
   bin/magento setup:perf:generate-fixtures ./setup/performance-toolkit/profiles/ce/small.xml
   ```

1. 開啟&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Products]**，並檢視產品數目：找到&#x200B;*1200*&#x200B;筆記錄。
1. 開啟預設類別> **[!UICONTROL Products in Category]** > **[!UICONTROL Add Products]**。
1. 按一下&#x200B;**[!UICONTROL Assign]** > **[!UICONTROL Select All]**。
1. 將頁面上的產品數目變更為值= *5*。


**預期結果**：

*訊息應為：找到1200筆記錄（已選取1200筆）*

**實際結果**：

* 分頁無法運作。
* 顯示錯誤的訊息：找到&#x200B;*5*&#x200B;筆記錄（已選取&#x200B;*20*&#x200B;筆）

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。


## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
