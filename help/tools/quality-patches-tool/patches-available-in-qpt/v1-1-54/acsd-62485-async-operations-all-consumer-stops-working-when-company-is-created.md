---
title: ACSD-62485： 'async.operations.all'消費者在建立公司時停止運作
description: 套用ACSD-62485修補程式，修正Adobe Commerce中，建立B2B公司時，「async.operations.all」取用者停止運作的問題。
feature: B2B, Companies
role: Admin, Developer
exl-id: 99d20555-fe55-4a04-a067-5a2b104811f5
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# ACSD-62485：建立公司時，`async.operations.all`消費者停止工作

ACSD-62485修補程式修正建立B2B公司時`async.operations.all`取用者停止運作的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54時，即可使用此修補程式。 修補程式ID為ACSD-62485。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p7

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.6-p7、2.4.7 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

如果B2B公司是以非同步方式建立，當取用者仍在執行時，`async.operations.all`取用者會停止處理訊息。

<u>必要條件</u>：

B2B模組已安裝且已啟用。

<u>要再現的步驟</u>：

1. 建立兩個客戶。
1. 傳送REST大量請求以建立兩個公司，並將建立的客戶指派為公司管理員。
1. 使用下列命令啟動取用者：

   ``` bin/magento queue:consumer:start async.operations.all --max-messages=20000 ```

<u>預期結果</u>：

消費者處理20,000則訊息並成功結束。

<u>實際結果</u>：

取用者會在執行後立即停止工作。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
