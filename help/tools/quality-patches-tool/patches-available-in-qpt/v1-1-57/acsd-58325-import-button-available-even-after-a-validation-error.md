---
title: ACSD-58325：即使在驗證錯誤後也可使用[!UICONTROL Import]按鈕
description: 套用ACSD-58325修補程式以修正Adobe Commerce問題，此問題導致[!UICONTROL Import]按鈕在驗證錯誤後仍可使用。
feature: Data Import/Export
role: Admin, Developer
exl-id: 551a9ac7-9b7f-49b5-9255-2014c330fb07
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# ACSD-58325：即使在驗證錯誤後也可使用[!UICONTROL Import]按鈕

ACSD-58325修補程式修正了在驗證錯誤後也可使用&#x200B;**[!UICONTROL Import]**&#x200B;按鈕的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57時，即可使用此修補程式。 修補程式ID為ACSD-58325。 請注意，問題已在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**
* Adobe Commerce （所有部署方法） 2.4.6-p3

**與Adobe Commerce版本相容：**
* Adobe Commerce （所有部署方法） 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

[!UICONTROL Import]按鈕即使在驗證錯誤後也可使用。

<u>要再現的步驟</u>：

1. 為產品匯入建立CSV檔案，該檔案中的影像名稱不正確。
1. 使用建立的CSV檔案建立排程產品匯入。
1. 等候執行排定的匯入。
1. 檢查[!UICONTROL Last outcome]格線中的&#x200B;**[!UICONTROL Scheduled Imports/Exports]**。

<u>預期結果</u>：

[!UICONTROL Last outcome]應為[!UICONTROL Failed]。

<u>實際結果</u>：

[!UICONTROL Last outcome]是[!UICONTROL Successful]。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。


## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
