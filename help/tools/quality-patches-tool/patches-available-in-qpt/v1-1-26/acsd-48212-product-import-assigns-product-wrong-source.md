---
title: ACSD-48212：產品匯入會將產品指派給錯誤的來源
description: 套用ACSD-48212修補程式來修正Adobe Commerce問題，此問題導致產品匯入將產品指派給錯誤的來源。
feature: Admin Workspace, Data Import/Export, Products
role: Admin
exl-id: d573d95b-95fc-4f59-b518-18088855a154
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-48212：產品匯入會將產品指派給錯誤的來源

ACSD-48212修補程式修正產品匯入將產品指派給錯誤來源的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.26時，即可使用此修補程式。 修補程式ID為ACSD-48212。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

產品匯入會將產品指派給錯誤的來源。

<u>要再現的步驟</u>：

1. 建立次要存貨來源。
1. 建立僅具有預設庫存來源的產品。
1. 匯出產品。
1. 執行`bin/magento cron:run`。
1. 開啟&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Prdoucts]**。
1. 從格線中選取產品。
1. 使用&#x200B;*[!UICONTROL mass action]*&#x200B;功能表取消指定庫存。
1. 執行`bin/magento cron:run`。
1. 使用&#x200B;*[!UICONTROL mass action]*&#x200B;功能表指派次要來源。
1. 執行`bin/magento cron:run`。
1. 使用&#x200B;*[!UICONTROL mass action]*&#x200B;功能表刪除產品。
1. 執行`bin/magento cron:run`。
1. 使用先前匯出的CSV匯入產品。
1. 檢查來源指派。

<u>預期結果</u>：

產品僅會指派給預設來源。

<u>實際結果</u>：

產品會同時指派給預設和次要來源。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
