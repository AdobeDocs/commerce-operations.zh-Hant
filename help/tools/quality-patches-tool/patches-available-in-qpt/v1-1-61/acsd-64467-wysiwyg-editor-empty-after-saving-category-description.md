---
title: ACSD-64467：在商店檢視層級儲存類別說明後，WYSIWYG編輯器空白
description: 套用ACSD-64467修補程式來修正Adobe Commerce問題，該問題導致在商店檢視層級儲存類別說明後，WYSIWYG編輯器顯示為空白。
feature: Page Content
role: Admin, Developer
exl-id: 8bc1794f-ace1-4719-9fff-194dbd701ab6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# ACSD-64467：在商店檢視層級儲存類別說明後，WYSIWYG編輯器空白

ACSD-64467修補程式修正了在商店檢視層級儲存類別說明後WYSIWYG編輯器顯示為空白的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61時，即可使用此修補程式。 修補程式ID為ACSD-64467。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在商店檢視層級儲存類別說明後，WYSIWYG編輯器會顯示為空白。

<u>要再現的步驟</u>：

1. 在商店檢視層級編輯Commerce管理員中的類別。
1. 取消選取類別說明旁邊的&#x200B;*[!UICONTROL Use default value]*&#x200B;核取方塊。
1. 在WYSIWYG編輯器中輸入說明。
1. 按一下&#x200B;**[!UICONTROL Save]**。

<u>預期結果</u>：

說明會儲存並正確顯示。

<u>實際結果</u>：

頁面重新載入後的說明為空白。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
