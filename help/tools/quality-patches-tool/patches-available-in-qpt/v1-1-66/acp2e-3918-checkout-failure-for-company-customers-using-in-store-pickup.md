---
title: ACP2E-3918：使用店內取貨的公司客戶簽出失敗
description: 套用ACP2E-3918修補程式，修正使用無預設帳單地址店內見面交收的登入公司客戶無法結帳的Adobe Commerce問題。
feature: B2B, Companies, Purchase Orders
role: Admin, Developer
type: Troubleshooting
exl-id: b3a01d6d-4e25-4089-9f47-e898a8d7a76e
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e9004f3c-09ae-5d24-acd2-fa0987fdb66e
    internal-label: Companies
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: 2d6d41d4-a5c1-5baf-8dbe-bf7300b68bb3
    internal-label: Purchase Orders
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%
---
# ACP2E-3918：使用店內取貨的公司客戶簽出失敗

ACP2E-3918修補程式修正登入公司客戶在沒有預設帳單地址的情況下使用店內見面交收服務時無法結帳的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66時，即可使用此修補程式。 修補程式ID為ACP2E-3918。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.5 - 2.4.8

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

當沒有預設地址的登入公司客戶嘗試使用店內見面交收發出採購訂單時，結帳失敗。

<u>要再現的步驟</u>：

1. 啟用&#x200B;**[!UICONTROL Purchase Orders]**。
1. 建立&#x200B;**[!UICONTROL Company]**&#x200B;並為其啟用&#x200B;**[!UICONTROL Purchase Orders]**。
1. 建立不含已儲存地址的&#x200B;**[!UICONTROL Company User]**。
1. 啟用&#x200B;**[!UICONTROL In-Store Delivery]**&#x200B;送貨方法。
1. 新增詳細目錄來源。
1. 新增詳細目錄存貨。
1. 指派產品詳細目錄。
1. 在前，以公司使用者的身分登入。
1. 將產品新增至&#x200B;**[!UICONTROL Cart]**。
1. 繼續結帳。
1. 在送貨步驟中選取&#x200B;**[!UICONTROL In-Store Pick Up]**。
1. 繼續付款。

<u>預期結果</u>：

結帳時付款步驟應該會成功載入，而且瀏覽器主控台中應該不會出現任何錯誤。

<u>實際結果</u>：

付款步驟未載入，且瀏覽器主控台顯示以下JavaScript錯誤：

```text
        Uncaught TypeError: Unable to process binding "text: function(){return currentBillingAddress().street.join(', ') }"
        Message: Cannot read properties of undefined (reading 'join')
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
