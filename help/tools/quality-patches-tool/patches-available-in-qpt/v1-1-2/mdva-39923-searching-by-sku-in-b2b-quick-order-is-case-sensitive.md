---
title: MDVA-39923：在B2B快速訂購功能中依SKU搜尋（區分大小寫）
description: MDVA-39923修補程式修正了客戶在B2B快速訂購功能中，依SKU搜尋訂單（與儲存名稱的大小寫不同）時出現錯誤的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2時，即可使用此修補程式。 修補程式ID為MDVA-39923。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。
feature: B2B, Catalog Management, Orders, Search
role: Admin
exl-id: 9bed5615-b398-42f5-8313-ae2acca59155
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# MDVA-39923：在B2B快速訂購功能中依SKU搜尋（區分大小寫）

MDVA-39923修補程式修正了客戶在B2B快速訂購功能中，依SKU搜尋訂單（與儲存名稱的大小寫不同）時出現錯誤的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2時，即可使用此修補程式。 修補程式ID為MDVA-39923。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.4.1-p1

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

在B2B快速訂購功能中依SKU搜尋會區分大小寫，且當使用與儲存SKU時不同的大小寫時，會顯示錯誤。

<u>必要條件</u>：

B2B模組已安裝。

<u>要再現的步驟</u>：

1. 登入管理員並移至&#x200B;**商店** > **設定** > **B2B**。
1. 啟用&#x200B;**共用目錄**&#x200B;和&#x200B;**快速訂購**。
1. 建立具有大寫SKU的產品，例如TEST20-1234
1. 將已建立的產品指派給&#x200B;**共用目錄**。
1. 以客戶身分登入，然後按一下&#x200B;**快速訂購**。
1. 以小寫輸入SKU，例如test20-1234。

<u>預期結果</u>：

無論使用何種大小寫，都應該找到產品。

<u>實際結果</u>：

收到下列錯誤訊息： *1個產品需要您注意*。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
