---
title: ACSD-47910：個別實體網格中遺漏的訂單、商業發票、出貨、銷退折讓單
description: 套用ACSD-47910修補程式，修正個別實體網格中遺失訂單、商業發票、出貨及銷退折讓單的Adobe Commerce問題。
feature: Admin Workspace, Invoices, Orders, Returns, Shipping/Delivery
role: Admin
exl-id: 09115cf3-62c3-425e-bc99-e8971398dd20
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-47910：個別實體網格中遺漏的訂單、商業發票、出貨及銷退折讓單

ACSD-47910修補程式修正個別實體網格中遺失訂單、商業發票、出貨及銷退折讓單的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.25時，即可使用此修補程式。 修補程式ID為ACSD-47910。 尚未提供將修正此問題的版本。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**
* Adobe Commerce （所有部署方法） 2.4.4-p1

**與Adobe Commerce版本相容：**
* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.5-p4

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

個別實體網格中遺漏訂單、商業發票、出貨及銷退折讓單。

<u>要再現的步驟</u>：

1. 在&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL Grid Settings]**&#x200B;啟用&#x200B;**[!UICONTROL Asynchronous indexing]**。
1. 下兩張訂單。
1. 執行cron將這些訂單同步至網格。
1. 開啟其中一個訂單，使其準備好開立商業發票。 尚未提交商業發票。
1. 建立可放在前端的新訂單。 請勿點選「下訂單」按鈕。
1. 在`foreach`的`NotSyncedDataProvider::L43`新增`sleep(30)`。
1. 執行`bin/magento cron:run`。
1. 現在下新訂單。
1. 為上一張訂單開立商業發票。
1. 再次執行cron，預期新訂單將同步。
1. 前往「管理員」中的訂單格線。

<u>預期結果</u>：

新訂單應會出現在訂單格線上。

<u>實際結果</u>：

先前的訂單更新已同步至格線(**[!UICONTROL status: Processing]**)。 新順序絕不會出現在格線上。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
