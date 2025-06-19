---
title: MDVA-39305：已啟用Google reCAPTCHA的登入問題
description: 套用MDVA-39305修補程式，修正啟用Adobe Commerce reCAPTCHA時註冊客戶無法登入的Google問題。
feature: Console
role: Admin
exl-id: c40fd84a-73dc-42bd-8cda-58738615fbba
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# MDVA-39305：已啟用Google reCAPTCHA的登入問題

>[!NOTE]
>
>此修補程式已更新，最新的修補程式ID為MDVA-39305-V3。 新修補程式是針對Adobe Commerce 2.4.4、2.4.5-p2和2.4.7版建立的。如需詳細資訊，請參閱[MDVA-39305-V3](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-58/mdva-39305-v3-login-issue-with-enabled-google-recaptcha)修補程式文章。

MDVA-39305修補程式修正啟用Google reCAPTCHA時，已註冊客戶無法登入的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.1時，即可使用此修補程式。 修補程式ID為MDVA-39305。 請注意，Adobe Commerce 2.4.4和2.4.7版已修正問題。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* 雲端基礎結構上的Adobe Commerce 2.4.2-p1、2.4.3-p3、2.4.5-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.1-p1 - 2.4.3-p3、2.4.4-p1 - 2.4.4-p5、2.4.5 - 2.4.6-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

註冊客戶無法使用已啟用的Google reCAPTCHA登入。

<u>要再現的步驟</u>：

1. 移至&#x200B;**存放區** > **組態** > **安全性** > **Google reCAPTCHA存放區**&#x200B;並啟用&#x200B;**Google reCAPTCHA**。
1. 移至&#x200B;**前端**。
1. 在瀏覽器中開啟&#x200B;**開發人員工具主控台**。

<u>預期結果</u>：

主控台中沒有CSP警告。

<u>實際結果</u>：

主控台中的CSP警告。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
