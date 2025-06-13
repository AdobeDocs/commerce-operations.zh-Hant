---
title: ACSD-51890：可以按多次[!UICONTROL Submit review]按鈕
description: 套用ACSD-51890修補程式以修正Adobe Commerce問題，該問題導致使用者可在不進行 [!DNL Google reCAPTCHA v3] 驗證的情況下多次點選[!UICONTROL Submit Review]按鈕。
feature: Products
role: Admin
exl-id: db69ccdc-c66e-4bdb-9783-772f2af0d33f
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# ACSD-51890：可以按多次&#x200B;**[!UICONTROL Submit Review]**&#x200B;按鈕，而不需要&#x200B;**[!DNL Google reCAPTCHA v3]**&#x200B;驗證

>[!NOTE]
>
>此修補程式已由[ACSD-55112](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-42/acsd-55112-submit-review-button-can-be-clicked-multiple-times.md)取代。

ACSD-51890修補程式修正可多次點選「**[!UICONTROL Submit Review]**」按鈕而無&#x200B;**[!DNL Google reCAPTCHA v3]**&#x200B;驗證的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.35時，即可使用此修補程式。 修補程式ID為ACSD-51890。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在不進行&#x200B;**[!DNL Google reCAPTCHA v3]**&#x200B;驗證的情況下，可以按多次&#x200B;**[!UICONTROL Submit Review]**&#x200B;按鈕。

<u>要再現的步驟</u>：

1. 啟用&#x200B;**[!DNL Google reCAPTCHA v3]**&#x200B;以供產品檢閱。
1. 開啟產品頁面並導覽至&#x200B;**[!UICONTROL Review]**&#x200B;區段，並確認可以看到[!DNL reCAPTCHA]。
1. 填寫稽核表單，並儘快多次按一下「**[!UICONTROL Submit Review]**」按鈕。
1. 從管理員開啟&#x200B;**[!UICONTROL Review]**&#x200B;區段。

<u>預期結果</u>

不會建立重複的稽核。

<u>實際結果</u>

會建立重複的稽核。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant>)。
