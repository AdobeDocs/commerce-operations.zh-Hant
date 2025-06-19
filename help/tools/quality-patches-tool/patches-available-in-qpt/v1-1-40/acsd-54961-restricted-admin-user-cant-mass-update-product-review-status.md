---
title: ACSD-54961：受限制的管理員使用者無法大量更新[!UICONTROL Product Review status]
description: 套用ACSD-54961修補程式以修正Adobe Commerce中受限制的管理員使用者無法大量更新產品評論狀態的問題。
feature: Products
role: Admin, Developer
exl-id: d303365c-d7c7-4aca-9f33-75d67bcbe573
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACSD-54961：受限制的管理員使用者無法大量更新[!UICONTROL Product Review status]

ACSD-54961修補程式修正受限制的管理員使用者無法大量更新[!UICONTROL Product Review status]的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.40時，即可使用此修補程式。 修補程式ID為ACSD-54961。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p4

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

受限制的管理員使用者無法大量更新[!UICONTROL Product Review status]。

<u>要再現的步驟</u>：

1. 建立其他網站、商店和商店檢視。
1. 將產品新增到第2個商店，然後新增評論。
1. 建立僅能存取第2個商店的受限制管理員使用者。
1. 以受限制的管理員使用者身分登入，然後前往&#x200B;**[!UICONTROL &#x200B; Marketings]** > **[!UICONTROL Reviews]** > **[!UICONTROL Mass Update]**，並將&#x200B;**狀態**&#x200B;設定為&#x200B;*已核准*&#x200B;或&#x200B;*擱置中*。

<u>預期結果</u>：

受限制的管理員使用者可以使用&#x200B;**[!UICONTROL Mass Update]**&#x200B;動作更新評論。

<u>實際結果</u>：

使用&#x200B;**[!UICONTROL Mass Update]**&#x200B;動作更新評論時發生錯誤。<br>
`var/log/exception.log`包含類似的錯誤：

```
report.CRITICAL: TypeError: array_intersect(): Argument #1 ($array) must be of type array, null given in app/code/Magento/AdminGws/Model/Models.php:439
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
