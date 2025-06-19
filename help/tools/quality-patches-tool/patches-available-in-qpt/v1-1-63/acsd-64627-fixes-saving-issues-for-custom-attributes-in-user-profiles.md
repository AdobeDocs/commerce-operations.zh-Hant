---
title: ACSD-64627：無法在[!UICONTROL Company Structure]中儲存自訂客戶屬性
description: 套用ACSD-64627修補程式以修正Adobe Commerce在[!UICONTROL Company Structure]內新增或編輯使用者時無法儲存自訂客戶屬性的問題。
feature: B2B
role: Admin, Developer
exl-id: 8e7dd72e-c21e-46cf-8e2b-9dccedfd8b04
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-64627：無法在[!UICONTROL Company Structure]中儲存自訂客戶屬性

ACSD-64627修補程式修正在&#x200B;**[!UICONTROL Company Structure]**&#x200B;頁面中新增或編輯使用者時，無法儲存自訂客戶屬性的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.63時，即可使用此修補程式。 修補程式ID為ACSD-64627。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p3、2.4.7-p4、2.4.8

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.6-p8、2.4.7-p3、2.4.7-p4、2.4.8

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在&#x200B;**[!UICONTROL Company Structure]**&#x200B;頁面上新增或編輯使用者時，未儲存自訂客戶屬性。

<u>要再現的步驟</u>：

1. 安裝已啟用B2B功能的Adobe Commerce執行個體。
1. 建立名為&#x200B;*custom_upload*&#x200B;且將&#x200B;**[!UICONTROL Input Type]**&#x200B;設為&#x200B;*[!UICONTROL File (attachment)]*&#x200B;的新客戶屬性。
1. 建立另一個名為&#x200B;*image_attachment*&#x200B;的客戶屬性，並將&#x200B;**[!UICONTROL Input Type]**&#x200B;設為&#x200B;*[!UICONTROL Image File]*。
1. 將&#x200B;**[!UICONTROL Show on Storefront]**&#x200B;設定為&#x200B;*是*&#x200B;讓這兩個屬性都顯示在店面上。 選取所有表單：
   * 客戶註冊
   * 客戶帳戶編輯
   * 管理員簽出
1. 建立及啟用新公司。
1. 以公司管理員身分登入店面。
1. 導覽至&#x200B;**[!UICONTROL Customer Account]** > **[!UICONTROL Company Structure]**&#x200B;或&#x200B;**[!UICONTROL Customer Account]** > **[!UICONTROL Company Users]**。
1. 按一下&#x200B;**[!UICONTROL Add New User]**。
1. 按一下&#x200B;*custom_upload*&#x200B;屬性的&#x200B;**[!UICONTROL Upload]**。
1. 按一下&#x200B;*image_attachment*&#x200B;屬性的&#x200B;**[!UICONTROL Select file]**。

<u>預期結果</u>：

檔案總管會開啟兩個屬性。 儲存時，會儲存值並成功上傳檔案。

<u>實際結果</u>：

按鈕無回應。 不會開啟檔案總管或儲存資料。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
