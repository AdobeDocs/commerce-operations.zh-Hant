---
title: ACSD-62971：以非數字數量值匯入的庫存來源會導致數量設為0
description: 套用ACSD-62971修補程式以修正Adobe Commerce的問題，即在「數量」欄中匯入具有非數值的庫存來源會導致數量設為0。
feature: Data Import/Export, Inventory
role: Admin, Developer
exl-id: ece23153-4932-4ac5-b46e-49327a8e84a1
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# ACSD-62971：以非數字數量值匯入的庫存來源會導致數量設為0

ACSD-62971修補程式修正了在「數量」欄中匯入具有非數值的庫存來源導致數量設為0的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56時，即可使用此修補程式。 修補程式ID為ACSD-62971。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

修正匯入&#x200B;**[!UICONTROL Quantity]**&#x200B;欄中有非數值的庫存來源時，導致數量設為0的問題。

<u>要再現的步驟</u>：

1. 建立&#x200B;**[!UICONTROL Simple Product]**，數量為100
1. 使用數量有誤(「abc」)的檔案執行&#x200B;**[!UICONTROL Stock Sources]**&#x200B;匯入

   ```table
   source_code    sku    status    quantity
     default     simple    1         abc
   ```

1. 檢查匯入後的數量。

<u>預期結果</u>：
匯入資料驗證應該會失敗。

<u>實際結果</u>：
簡單產品的數量已變成0，而產品已更新為[!UICONTROL Out of Stock]。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
