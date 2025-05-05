---
title: ACSD-64149：僅編輯一個日期時，可以儲存具有[!UICONTROL Date range]條件的客戶區段
description: 套用ACSD-64149修補程式以修正Adobe Commerce問題，該問題導致僅編輯其中一個日期時，無法儲存具有**[!UICONTROL Date range]**條件的客戶區段。
feature: Customers, Admin Workspace
role: Admin, Developer
source-git-commit: c1c5256aee44ce65e9339cf3985e53f710fc7c8a
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---


# ACSD-64149：僅編輯一個日期時，可以儲存具有[!UICONTROL Date range]條件的客戶區段

ACSD-64149修補程式修正了僅編輯其中一個日期時，具有日期範圍條件的客戶區段可以儲存的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.60時，即可使用此修補程式。 修補程式ID為ACSD-64149。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p8

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

編輯現有客戶區段時，若該客戶區段具有由日期範圍指定的購物車內產品的條件，消費者`matchCustomerSegmentProcessor`會失敗並出現SQL錯誤。

<u>要再現的步驟</u>：

1. 確定消費者`matchCustomerSegmentProcessor`正在執行：

   ```bash
   $ bin/magento que:cons:st matchCustomerSegmentProcessor
   ```

1. 移至&#x200B;**[!UICONTROL Magento backend]**。
1. 前往&#x200B;**[!UICONTROL Customers]** > **[!UICONTROL Segments]**。
1. 按一下&#x200B;**[!UICONTROL Add Segment]**。
1. 輸入&#x200B;**[!UICONTROL Segment Name]**，在&#x200B;**[!UICONTROL Assigned to Website]**&#x200B;下選取網站，並確定&#x200B;**[!UICONTROL Status]**&#x200B;設定為&#x200B;*作用中*。
1. 按一下&#x200B;**[!UICONTROL Save and Continue Edit]**。
1. 移至&#x200B;**[!UICONTROL Conditions]**&#x200B;標籤並新增條件： *產品{} > {}產品清單*{*}*。
1. 為&#x200B;**[!UICONTROL Date range]**&#x200B;新增子條件並設定有效的&#x200B;**[!UICONTROL Date range]**。
1. 按一下&#x200B;**[!UICONTROL Date range]**&#x200B;旁的綠色確認按鈕。
1. 再按一下&#x200B;**[!UICONTROL Date range]**、選取日期選擇器、編輯其中一個日期值，並按一下綠色按鈕進行確認。

<u>預期結果</u>：

**[!UICONTROL Date range]**&#x200B;選擇器不應在編輯時新增時間至日期。

<u>實際結果</u>：

* **[!UICONTROL Date range]**&#x200B;選擇器會將時間新增至日期：
   * 一個日期只有日期，而另一個日期同時有指定的日期和時間。
* 記錄中出現下列錯誤：

  ```
  report.CRITICAL: SQLSTATE[42000]: Syntax error or access violation: 1064 You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ')' at line 2, query was: SELECT `item`.`quote_id` FROM `quote_item` AS `item`
  INNER JOIN `quote` AS `list` ON item.quote_id = list.entity_id WHERE (list.is_active = 1) AND () [] []
  ```


## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的升級和修補程式>套用修補程式。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
