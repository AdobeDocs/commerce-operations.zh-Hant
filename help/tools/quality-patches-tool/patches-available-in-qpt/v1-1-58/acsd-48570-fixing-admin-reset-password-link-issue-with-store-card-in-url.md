---
title: ACSD-48570：修正URL中存放區代碼的管理員重設密碼連結問題
description: 套用ACSD-48570修補程式，以修正啟用[!UICONTROL Add Store Code to URLs]設定時，無法透過管理員重設密碼連結存取重設密碼頁面的Adobe Commerce問題。
feature: Security, User Account
role: Admin, Developer
exl-id: 049a82ff-80e3-46a1-8472-ac74de0e365f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-48570：修正URL中存放區代碼的管理員重設密碼連結問題

ACSD-48570修正程式，修正啟用&#x200B;*[!UICONTROL Add Store Code to URLs]*&#x200B;設定時，無法透過管理員重設密碼連結存取重設密碼頁面的Adobe Commerce問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58時，即可使用此修補程式。 修補程式ID為ACSD-48570。 請注意，問題已在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

啟用&#x200B;**[!UICONTROL Add Store Code to URLs]**&#x200B;設定時，管理員重設密碼功能無法正常運作。
在管理員使用者請求重設密碼並按一下電子郵件中的復原連結後，他們被重新導向到登入頁面或收到404錯誤，而不是被帶往重設密碼表單。 如此可防止管理員無需手動介入即可復原帳戶。

<u>要再現的步驟</u>：

1. 在&#x200B;**[!UICONTROL Add Store Code to URLs]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]**&#x200B;啟用&#x200B;**[!UICONTROL URL Options]**&#x200B;設定。
1. 從管理員面板登出，然後按一下管理員登入頁面上的&#x200B;**[!UICONTROL Forgot your password?]**&#x200B;連結。
1. 輸入管理員使用者的電子郵件、傳遞驗證碼，然後按一下&#x200B;**[!UICONTROL Retrieve Password]**。
1. 開啟密碼重設電子郵件，然後按一下密碼復原連結。

<u>預期結果</u>：

應顯示重設密碼表單。

<u>實際結果</u>：

此時會顯示登入頁面或404錯誤頁面，而非重設密碼表單。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
