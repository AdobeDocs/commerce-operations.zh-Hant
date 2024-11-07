---
title: 「ACSD-59366：刪除團隊清單中看不到已停用使用者的團隊」
description: 套用ACSD-59366修補程式以修正Adobe Commerce問題，其中當您嘗試刪除團隊時會發生錯誤，該團隊包含未在團隊清單中顯示的已停用使用者。
feature: GraphQL, Companies
role: Admin, Developer
source-git-commit: 8037db7a89cd850385dc88750e881f68ae62172f
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-59366：刪除團隊清單中看不到已停用使用者的團隊

ACSD-59366修補程式修正了當您嘗試刪除團隊時會發生錯誤的問題，該團隊包含未在團隊清單中顯示的已停用使用者。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.52時，即可使用此修補程式。 修補程式ID為ACSD-59366。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.4.6

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當您刪除團隊時，該團隊包含未在團隊清單中顯示的已停用使用者。

<u>必要條件</u>：

Adobe Commerce B2B模組已安裝，且公司已啟用。

<u>要再現的步驟</u>：

1. 建立公司使用者並登入。
1. 在公司結構下，建立新團隊。
1. 在新團隊下，建立新使用者。
1. 編輯新使用者並停用。
1. 選取團隊並刪除。

<u>預期結果</u>：

團隊有一或多個非作用中的使用者。 刪除團隊將會取消指派這些使用者。 您可以在[!UICONTROL Company Users]區段中找到非作用中的使用者。

<u>實際結果</u>：

當您嘗試刪除具有已停用使用者的團隊時，會發生錯誤。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。


