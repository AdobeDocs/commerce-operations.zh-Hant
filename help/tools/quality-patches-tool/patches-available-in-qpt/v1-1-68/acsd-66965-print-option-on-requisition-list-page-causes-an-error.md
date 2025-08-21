---
title: ACSD-66965： [!UICONTROL Print]頁面上的[!UICONTROL Requisition List]選項造成錯誤
description: 套用ACSD-66965修補程式以修正Adobe Commerce中，[!UICONTROL Print]頁面上的[!UICONTROL Requisition List]選項會導致錯誤的問題。
feature: B2B
role: Admin, Developer
type: Troubleshooting
source-git-commit: 7682a326a6c703a08dd6d0fac5319ac38e1bc3c8
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---


# ACSD-66965： **[!UICONTROL Print]**&#x200B;頁面上的&#x200B;**[!UICONTROL Requisition List]**&#x200B;選項造成錯誤

ACSD-66965修補程式修正&#x200B;**[!UICONTROL Print]**&#x200B;頁面上的&#x200B;**[!UICONTROL Requisition List]**&#x200B;選項造成錯誤的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68時，即可使用此修補程式。 修補程式ID為ACSD-66965。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.8

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

**[!UICONTROL Print]**&#x200B;頁面上的&#x200B;**[!UICONTROL Requisition List]**&#x200B;選項因為`Grid.php`中有null物件參考而造成錯誤。

<u>要再現的步驟</u>：

1. 前往「**[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**」。
1. 將&#x200B;**[!UICONTROL Enable Company]**、**[!UICONTROL Enable Shared Catalog]**&#x200B;和&#x200B;**[!UICONTROL Enable Requisition List]**&#x200B;設定為`Yes`。
1. 建立兩個簡單的產品。
1. 登入店面並開啟&#x200B;**[!UICONTROL My Account]**&#x200B;頁面。
1. 建立請購單清單。
1. 將兩個產品指定至請購單清單。
1. 存取請購單清單並列出產品。
1. 按一下&#x200B;**[!UICONTROL Print]**。

<u>預期結果</u>：

**[!UICONTROL Print]**&#x200B;頁面上的&#x200B;**[!UICONTROL Requisition List]**&#x200B;選項會顯示無錯誤的列印預覽。

<u>實際結果</u>：

出現下列錯誤訊息： *應用程式執行期間發生錯誤。 如需詳細資訊，請參閱例外狀況記錄檔。*

```
Call to a member function setCollection() on null in /vendor/magento/module-requisition-list/Block/Requisition/View/Items/Grid.php:146
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
