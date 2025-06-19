---
title: ACSD-51636：公司管理員無法從客戶帳戶區段新增使用者
description: 套用ACSD-51636修補程式以修正Adobe Commerce問題，其中公司管理員無法從客戶帳戶區段新增使用者，儘管其擁有所有必要的角色和許可權。
feature: Admin Workspace, B2B, Companies, Customer Service
role: Admin
exl-id: 46e79ae3-ea24-4cb2-b06e-e82cec33b16c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# ACSD-51636：公司管理員無法從客戶帳戶區段新增使用者

ACSD-51636修補程式修正了公司管理員無法從客戶帳戶區段新增使用者（儘管擁有所有必要的角色和許可權）的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.34時，即可使用此修補程式。 修補程式ID為ACSD-51636。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

公司管理員無法從「客戶帳戶」區段新增使用者，儘管擁有所有必要的角色和許可權。

先決條件：

* B2B模組已安裝。
* 已啟用公司功能。

<u>要再現的步驟</u>：

1. 建立新公司。
1. 前往&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**。
1. 編輯&#x200B;*客戶*&#x200B;的&#x200B;**[!UICONTROL Company Admin]**&#x200B;型別。
1. 以客戶身分登入。
1. 前往「**[!UICONTROL My Account]** > **[!UICONTROL Company Users]** > **[!UICONTROL Add User]**」，新增使用者的詳細資料並將其設定為使用中。
1. 儲存新使用者。

<u>預期結果</u>

管理員使用者可以新增使用者。

<u>實際結果</u>

* 管理員使用者收到錯誤訊息： *發生錯誤*。
* 管理員使用者無法建立新客戶。
* 記錄檔包含下列錯誤：

  ```PHP
      report.CRITICAL: Error: Call to a member function __toArray() on null in app/code/Magento/LoginAsCustomerLogging/Observer/LogSaveCustomerObserver.php:123
  ```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>)。
