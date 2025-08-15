---
title: MDVA-40619：階層變更中斷CMS頁面內嵌編輯並擲回500錯誤
description: MDVA-40619修補程式解決CMS頁面階層變更中斷CMS頁面內嵌編輯並擲回「500錯誤」的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5時，即可使用此修補程式。 修補程式ID為MDVA-40619。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。
feature: CMS
role: Admin
exl-id: 148cb0a5-5a6c-4cfa-bf95-4bafc57beec6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# MDVA-40619：階層變更中斷CMS頁面內嵌編輯並擲回500錯誤

MDVA-40619修補程式解決CMS頁面階層變更中斷CMS頁面內嵌編輯並擲回「500錯誤」的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5時，即可使用此修補程式。 修補程式ID為MDVA-40619。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

CMS頁面階層變更中斷CMS頁面內嵌編輯並擲回「500錯誤」。

<u>要再現的步驟</u>：

1. 移至[管理面板] > **內容** > **階層**。
1. 選取「預設商店檢視」。
1. 取消勾選「使用父節點階層」。
1. 手動選取頁面，然後按一下&#x200B;**儲存**。
1. 然後前往&#x200B;**內容** > **頁面**。
1. 嘗試從格線編輯任何CMS頁面。
1. 按一下&#x200B;**儲存**。

<u>預期結果</u>：

頁面已成功儲存。

<u>實際結果</u>：

您會收到下列錯誤：

*伺服器的技術問題造成錯誤。 請再試一次，繼續您正在執行的動作。 如果問題仍然存在，請稍後再試。*

`Error: Call to a member function getData() on null in /magento2ee/app/code/Magento/VersionsCms/Controller/Adminhtml/Cms/Page/InlineEdit/Plugin.php:62`

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的「品質修補工具」[!DNL Quality Patches Tool]，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱QPT[中可用的](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)修補程式區段。
