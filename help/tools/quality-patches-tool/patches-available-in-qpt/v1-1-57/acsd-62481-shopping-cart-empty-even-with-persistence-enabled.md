---
title: ACSD-62481：即使啟用[!UICONTROL Persistence]，購物車仍保持空白
description: 套用ACSD-62481修補程式，修正結帳期間使用登入快顯視窗時，永久購物車功能無法運作的Adobe Commerce問題。
feature: Shopping Cart, Checkout
role: Admin, Developer
exl-id: 79fb3161-f56e-45f3-9933-cf95703f1554
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: df8eaa0e-dd74-553a-8ad5-28129f8e8d3d
    internal-label: Shopping Cart
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
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
source-wordcount: '441'
ht-degree: 0%
---
# ACSD-62481：即使啟用&#x200B;*[!UICONTROL Persistence]*，購物車仍保持空白

ACSD-62481修補程式修正了在結帳時使用登入快顯視窗時，持續購物車功能失敗，因為它缺少&#x200B;*[!UICONTROL Remember Me]*&#x200B;核取方塊，導致產品在登出後從購物車中消失的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57時，即可使用此修補程式。 修補程式ID為ACSD-62481。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.7-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

永久購物車功能在結帳時使用登入快顯視窗時失敗，因為它缺少&#x200B;*[!UICONTROL Remember Me]*&#x200B;核取方塊。 這會導致產品在登出後從購物車中消失。

<u>要再現的步驟</u>：

1. 在admin中，設定來賓帳戶和持續購物車設定，如下所示：

   * 導覽至&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]**，並將&#x200B;*[!UICONTROL Allow Guest Checkout]*&#x200B;設為&#x200B;*否*。

     * 按一下&#x200B;**[!UICONTROL Save Config]**。

   * 導覽至&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Persistent Shopping Cart]** > **[!UICONTROL General Options]**，並將&#x200B;*[!UICONTROL Enable Persistence]*&#x200B;設為&#x200B;*是*。
   * 保留所有其他設定為預設值，但將&#x200B;*[!UICONTROL Clear Persistence on Sign Out]*&#x200B;變更為&#x200B;*否*。

     * 按一下&#x200B;**[!UICONTROL Save Config]**。

1. 前往「**[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add product]**」將簡單產品加入目錄。

   * 填寫所需的最低詳細資訊，並確保已有庫存。

1. 在前端使用主要表單`(../customer/account/create/)`建立客戶帳戶並登出。
1. 將產品以訪客身分新增到購物車。
1. 開啟迷你購物車，右上角的圖示並按一下&#x200B;**[!UICONTROL View and Edit Cart]**。
1. 繼續結帳。
1. 透過出現的快顯對話方塊登入新的客戶帳戶並登出。

<u>預期結果</u>：

購物車會保留先前登入使用者的產品。

<u>實際結果</u>：

* 購物車是空的。
* 彈出式登入對話方塊不顯示&#x200B;*[!UICONTROL Remember Me]*&#x200B;選項。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的升級和修補程式>套用修補程式。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
