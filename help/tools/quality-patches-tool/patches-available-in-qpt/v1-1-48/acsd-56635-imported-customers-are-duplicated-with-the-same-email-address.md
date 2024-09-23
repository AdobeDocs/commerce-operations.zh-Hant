---
title: 'ACSD-56635：帳戶共用設為 [!DNL Global]時，匯入的客戶會重複'
description: 套用ACSD-56635修補程式以修正當匯入使用且帳戶共用設為 [!DNL Global]時，匯入的客戶使用相同電子郵件地址重複的Adobe Commerce問題。
feature: Customers, Attributes
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-56635：帳戶共用設為[!DNL Global]時，匯入的客戶會以相同的電子郵件地址重複

ACSD-56635修補程式修正使用匯入且帳戶共用設為[!DNL Global]時，匯入的客戶使用相同電子郵件地址重複的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.48時，即可使用此修補程式。 修補程式ID為ACSD-56635。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

帳戶共用設為[!DNL Global]時，匯入的客戶會以相同的電子郵件地址重複。

<u>要再現的步驟</u>：

1. 在Adobe Commerce (2.4-develop b2b) **[!UICONTROL Admin]**&#x200B;底下，存取&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Account Sharing Options]**。
1. 將&#x200B;*[!UICONTROL Share Customer Accounts]*&#x200B;設定設為&#x200B;*[!DNL Global]*。
1. 建立多個網站和商店：

   * ws1 > s11， s12 > sw111， sw122
   * ws2 > s21， s22 > sw211， sw212

1. 在管理員的&#x200B;*主要網站*&#x200B;下建立新客戶，電子郵件地址用作<adb@yormail.com>。
1. 在&#x200B;**[!UICONTROL Admin]**&#x200B;底下，瀏覽至&#x200B;**[!UICONTROL System]** > **[!UICONTROL Import]**。
1. 選取&#x200B;**[!UICONTROL Customer Entity Type]**&#x200B;作為&#x200B;*[!UICONTROL Customers Main File]*。
1. 在不同網站上使用與<adb@yormail.com>相同的電子郵件地址，例如ws1。 請參閱下方提供的範例CSV檔案customer.csv 。
1. 完成匯入後，即可檢視在&#x200B;*ws1*&#x200B;網站下建立的具有相同電子郵件地址的新使用者。

customer.csv內容：

```
email,_website,_store,confirmation,created_at,created_in,disable_auto_group_change,dob,firstname,gender,group_id,lastname,middlename,password_hash,prefix,rp_token,rp_token_created_at,store_id,suffix,taxvat,updated_at,website_id,password
adb@yopmail.com,ws1,sv111,,09/01/24 12:49,Default Store View,0,,newjon,,1,newDoe,,d708be3fe0fe0120840e8b13c8faae97424252c6374227ff59c05814f1aecd79:mgLqkqgTwLPLlCljzvF8hp67fNOOvOZb:1,,07e71459c137f4da15292134ff459cba,30/10/15 12:49,1,,,09/01/24 12:49,1,
```

<u>預期結果</u>：

會更新具有相同電子郵件地址的匯入客戶，而非進行複製。

<u>實際結果</u>：

使用客戶匯入時，系統會使用相同的電子郵件地址建立重複客戶。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
