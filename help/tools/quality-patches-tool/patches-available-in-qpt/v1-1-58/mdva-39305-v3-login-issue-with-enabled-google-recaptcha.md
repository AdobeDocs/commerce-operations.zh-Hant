---
title: MDVA-39305-V3：已啟用 [!DNL Google reCAPTCHA]的登入問題
description: 套用MDVA-39305-V3修補程式，修正啟用 [!DNL Google reCAPTCHA] 時註冊客戶無法登入的Adobe Commerce問題。 此修補程式也修正了在 [!DNL Google reCAPTCHA] 完整載入之前提交表單的問題。 此外，它修正了在CMS頁面的非預設位置中使用區塊時，*在null*上呼叫成員函式isDisabled()的錯誤。
feature: Console
role: Admin
exl-id: 63e880aa-9a2e-4c34-9ead-20bfc5204f2c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# MDVA-39305-V3：已啟用[!DNL Google reCAPTCHA]的登入問題

>[!NOTE]
>
>此修補程式是[MDVA-39305](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-1/mdva-39305-login-issues-with-enabled-google-recaptcha.md)修補程式的更新。

MDVA-39305-V3修補程式修正啟用[!DNL Google reCAPTCHA]時註冊客戶無法登入的問題。 此修補程式也修正了在[!DNL Google reCAPTCHA]完全載入之前提交表單的問題。 此外，它修正了在CMS頁面的非預設位置中使用區塊時，在null *上呼叫isDisabled()成員函式所發生的錯誤*。

此修補程式已新增至[品質修補工具(QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.48版本。 QPT 1.1.58版本已更新為包含新的Adobe Commerce版本2.4.7 - 2.4.7-p4。 修補程式ID為MDVA-39305-V3。 請注意，Adobe Commerce 2.4.4、2.4.5-p2和2.4.7版已修正問題。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4、2.4.5-p2、2.4.7

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4-p1 - 2.4.7-p4

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

### 案例I

1. 已註冊的客戶無法使用已啟用的[!DNL Google reCAPTCHA]登入。
1. 表單可在[!DNL Google reCAPTCHA]完全載入前提交。

<u>要再現的步驟</u>：

1. 前往「**[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Security]** > **[!DNL Google reCAPTCHA Storefront]**」並啟用&#x200B;***[!DNL Google reCAPTCHA]***。
1. 前往前端。
1. 在瀏覽器中開啟&#x200B;**[!UICONTROL Developer Tool Console]**。

<u>預期結果</u>：

主控台中沒有CSP警告。

<u>實際結果</u>：

主控台中的CSP警告。

### 案例二

在CMS頁面的非預設位置中使用區塊時，會擲回錯誤訊息，指出&#x200B;*在null*&#x200B;上呼叫成員函式isDisabled()。

<u>要再現的步驟</u>：

1. 使用下列內容建立靜態區塊：

   ```
   {{block class="Magento\Newsletter\Block\Subscribe" name="home.form.subscribe"
   template="Magento_Newsletter::subscribe.phtml"}}
   ```

1. 從&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Pages]** > **[!UICONTROL Add/Edit CMS page]** > **[!UICONTROL Content]**，將靜態區塊新增至CMS頁面。
1. 儲存頁面。

<u>預期結果</u>：

頁面載入時沒有任何錯誤。

<u>實際結果</u>：

店面的頁面上發生500錯誤。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
