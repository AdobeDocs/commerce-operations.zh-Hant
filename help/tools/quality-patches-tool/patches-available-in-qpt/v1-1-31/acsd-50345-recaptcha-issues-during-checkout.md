---
title: ACSD-50345：結帳期間出現reCAPTCHA問題
description: 套用ACSD-50345修補程式以修正Adobe Commerce問題，其中在下訂單時和結帳期間，reCAPTCHA v2和v3驗證失敗。
feature: Checkout, Orders
role: Admin
exl-id: eae9a6ad-0999-4581-b3c0-7667ee7beb54
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# ACSD-50345：結帳期間出現reCAPTCHA問題

ACSD-50345修補程式修正了下訂單時和結帳期間reCAPTCHA v2和v3驗證失敗的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.31時，即可使用此修補程式。 修補程式ID為ACSD-50345。 請注意，Adobe Commerce 2.4.6已部分修正此問題，Adobe Commerce 2.4.7已排程完全修正此問題。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.3 - 2.4.5-p2

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

**案例#1**

Google reCAPTCHA v2在提交失敗的付款後未重新載入。

<u>要再現的步驟</u>

1. 設定&#x200B;**[!UICONTROL Google reCAPTCHA v2]** （*我不是自動機制*）。
1. 啟用&#x200B;**[!UICONTROL reCAPTCHA]**&#x200B;以進行簽出。
1. 嘗試下單而不按一下&#x200B;**[!UICONTROL reCAPTCHA]**。
1. 一旦使用者收到遺失reCAPTCHA （*reCAPTCHA驗證失敗，請再試一次*），按一下&#x200B;**[!UICONTROL reCAPTCHA]**，然後嘗試下訂單。

<u>預期結果</u>

使用不正確的reCAPTCHA將不會下訂單。

<u>實際結果</u>

擲回錯誤 — *reCAPTCHA驗證失敗，請再試一次*，*沒有識別碼= 4*&#x200B;的購物車

**案例#2**

Google reCAPTCHA v3 Visible無法用於結帳，因此無法下訂單。 未觸發`PlaceOrder`事件。

<u>要再現的步驟</u>

1. 從&#x200B;**[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Security]**&#x200B;設定&#x200B;**[!UICONTROL reCAPTCHA v3 Invisible]**。
1. 啟用&#x200B;**[!UICONTROL reCAPTCHA v3 Invisible]**&#x200B;以在&#x200B;**[!UICONTROL Storefront]**&#x200B;標籤下結帳/下訂單。
1. 嘗試使用[!UICONTROL Check/Money order]付款方式下訂單。

<u>預期結果</u>

訂單應在&#x200B;**[!UICONTROL reCAPTCHA]**&#x200B;開啟的情況下下達。

<u>實際結果</u>

按一下「**[!UICONTROL Place Order]**」按鈕後，此動作會停用，不會再發生任何動作。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
