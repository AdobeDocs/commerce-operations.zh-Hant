---
title: ACSD-63793：匯入程式會在不同的瀏覽器分頁中互相干擾
description: 套用ACSD-63793修補程式，修正Adobe Commerce中匯入程式在不同瀏覽器分頁中互相干擾的問題。
feature: Data Import/Export
role: Admin, Developer
source-git-commit: 60ad8dff5a3f26d0eab536d8824cb6579cb88a5a
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---


# ACSD-63793：匯入程式會在不同的瀏覽器分頁中互相干擾

ACSD-63793修補程式修正了匯入程式在不同瀏覽器標籤中互相干擾的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59時，即可使用此修補程式。 修補程式ID為ACSD-63793。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

透過Admin UI匯入資料會干擾另一個匯入，導致來自一個匯入的資料會在另一個匯入中處理。

<u>要再現的步驟</u>：

1. 前往&#x200B;**[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Import]**。
1. 將&#x200B;**[!UICONTROL Entity Type]**&#x200B;設為&#x200B;*[!UICONTROL Customers and Addresses]（單一檔案）*。
1. 將&#x200B;**[!UICONTROL Import Behavior]**&#x200B;設為&#x200B;*[!UICONTROL Add/Update]*。
1. 選取要匯入的有效檔案。
1. 按一下&#x200B;**[!UICONTROL Check Data]**&#x200B;按鈕。
1. 保持此標籤開啟。
1. 開啟新索引標籤，並使用包含無效資料的檔案重複這些步驟（例如，針對不同客戶的兩封相同的電子郵件）。
1. 切換回第一個索引標籤。
1. 按一下底部的&#x200B;**[!UICONTROL Import]**&#x200B;按鈕。

<u>預期結果</u>：

匯入程式不應互相干擾。

<u>實際結果</u>：

匯入程式已完成，且報表檔案可供下載。 這表示第二列發生錯誤，即使初始驗證順利通過且沒有任何錯誤，系統仍會處理來自其他匯入的資料。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
