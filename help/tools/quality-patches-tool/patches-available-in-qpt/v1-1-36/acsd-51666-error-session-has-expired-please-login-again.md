---
title: ACSD-51666： 「工作階段已過期，請重新登入」錯誤。 在您登入後
description: 套用ACSD-51666修補程式以修正錯誤*工作階段已過期的Adobe Commerce問題，請重新登入。*會在您嘗試登入後發生。
feature: Customers
role: Admin, Developer
exl-id: 8968b314-6625-45fa-9733-20560cca7089
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---

# ACSD-51666：錯誤&#x200B;*工作階段已過期，請重新登入。*&#x200B;在您登入之後

ACSD-51666修補程式修正錯誤&#x200B;*工作階段已過期的問題，請重新登入。*&#x200B;在您嘗試登入後發生。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.36時，即可使用此修補程式。 修補程式ID為ACSD-51666。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

您收到錯誤&#x200B;*工作階段已過期，請重新登入。*&#x200B;在重設其他裝置上的密碼後，嘗試從一部裝置使用新密碼登入。 只有在自訂模組新增的頁面上有其他Ajax要求時，才會發生這種情況。

<u>要再現的步驟</u>：

1. 安裝自訂模組，在店面的每個頁面上新增Ajax請求。
1. 建立新帳戶。
1. 登出並返回登入頁面。
1. 在不同瀏覽器中開啟&#x200B;*忘記密碼*&#x200B;連結，並傳送&#x200B;*重設密碼*&#x200B;電子郵件。
1. 在第一個瀏覽器中開啟重設密碼電子郵件，並設定新密碼。
1. 請嘗試使用第二個瀏覽器登入。

<u>預期結果</u>：

第一次嘗試時，您就能成功登入。

<u>實際結果</u>：

* 您看到&#x200B;*工作階段已過期，請重新登入。*&#x200B;錯誤。
* 您並未登入，且已重新導向至首頁。
* 您的第二次登入嘗試成功。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
