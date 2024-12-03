---
title: ACSD-61199： CMS頁面[!UICONTROL Hierarchy]索引標籤未顯示正確的樹狀結構
description: 套用ACSD-61199修補程式以修正Adobe Commerce問題，該問題導致CMS頁面的*[!UICONTROL Hierarchy]*索引標籤在編輯具有現有*[!UICONTROL Hierarchy]*的CMS頁面時未顯示正確的樹狀結構。
feature: Page Content
role: Admin, Developer
exl-id: f541d001-9680-431a-9a62-816c2d10b6d5
source-git-commit: 5568b2f574c7e90e641513c3c0ea4574648770ac
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# ACSD-61199： CMS頁面的[!UICONTROL Hierarchy]索引標籤未顯示正確的樹狀結構

ACSD-61199修補程式修正了在使用現有&#x200B;*[!UICONTROL Hierarchy]*&#x200B;編輯CMS頁面時，CMS頁面的&#x200B;*[!UICONTROL Hierarchy]*&#x200B;索引標籤未顯示正確樹狀結構的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54時，即可使用此修補程式。 修補程式ID為ACSD-61199。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

使用現有&#x200B;*[!UICONTROL Hierarchy]*&#x200B;編輯CMS頁面時，CMS頁面的&#x200B;*[!UICONTROL Hierarchy]*&#x200B;索引標籤未顯示正確的樹狀結構。

<u>要再現的步驟</u>：

1. 前往&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Pages]**。
1. 建立新的&#x200B;**[!UICONTROL CMS page]**。 已新增至&#x200B;*[!UICONTROL Hierarchy]*&#x200B;的網站根目錄。
1. 儲存頁面。
1. 前往&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Hierarchy]**。
1. 將任何其他現有頁面新增至&#x200B;*[!UICONTROL Hierarchy]*。
1. 儲存&#x200B;*[!UICONTROL Hierarchy]*。
1. 前往&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Pages]**。
1. 編輯任何現有頁面並開啟&#x200B;*[!UICONTROL Hierarchy]*。

<u>預期結果</u>：

*[!UICONTROL Hierarchy]*&#x200B;如預期般載入。

<u>實際結果</u>：

*[!UICONTROL Hierarchy]*&#x200B;未載入索引標籤。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

[[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
