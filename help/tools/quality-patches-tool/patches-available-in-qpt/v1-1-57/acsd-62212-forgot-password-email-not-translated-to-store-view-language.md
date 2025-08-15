---
title: ACSD-62212： [!UICONTROL Forgot Password]電子郵件未翻譯成存放區檢視語言
description: 套用ACSD-62212修補程式以修正*[!UICONTROL Forgot Password]*電子郵件的內容未翻譯成商店檢視語言的Adobe Commerce問題。
feature: GraphQL
role: Admin, Developer
exl-id: 29e6f2fa-574f-4ab1-82f5-88e1eb1de83e
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# ACSD-62212： *[!UICONTROL Forgot Password]*&#x200B;電子郵件未翻譯成存放區檢視語言

ACSD-62212修補程式修正&#x200B;*[!UICONTROL Forgot Password]*&#x200B;電子郵件的內容未翻譯成商店檢視語言的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 1.1.57時，即可使用此修補程式。 修補程式ID為ACSD-62212。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在已註冊商店檢視以外的商店檢視中透過GraphQL重設密碼時，重設密碼連結與從中起始密碼的商店檢視不符。

<u>要再現的步驟</u>：

1. 在&#x200B;*[!UICONTROL Main Website Store]*&#x200B;下建立次要存放區檢視。
1. 在次要存放區檢視範圍中將&#x200B;*[!UICONTROL Locale]*&#x200B;切換為&#x200B;*[!UICONTROL French (France)]*。
1. 安裝法文語言套件以取得翻譯。
1. 建立客戶帳戶。
1. 將下列GraphQL突變搭配次要存放區檢視程式碼的&#x200B;*存放區*&#x200B;標頭使用。

   ```
   mutation {
       requestPasswordResetEmail(
           email: "test@gmail.com"
       )
   }
   ```

1. 檢查電子郵件。

<u>預期結果</u>：

* 電子郵件主旨、連結及其內容的語言與商店檢視地區設定一致。
* 無論請求中的商店標頭為何，密碼重設請求都會從客戶帳戶實際註冊的商店傳送。

<u>實際結果</u>：

在電子郵件中可觀察到以下情況：

* 重設密碼連結有「預設」存放區代碼。
* 主旨為英文。
* 內容為法文。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
