---
title: MDVA-41399：如果客戶將產品新增到願望清單，則無法存取管理購物車
description: MDVA-41399修補程式解決如果客戶將產品新增至願望清單，管理員使用者無法存取「管理購物車」頁面的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6後，即可使用此修補程式。 修補程式ID為MDVA-41399。 請注意，問題已在Adobe Commerce 2.4.2中修正。
feature: Orders, Products, Shopping Cart
role: Admin
exl-id: 81a128b5-0c38-4f8f-b297-1f264952d431
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# MDVA-41399：如果客戶將產品新增到願望清單，則無法存取管理購物車

MDVA-41399修補程式解決如果客戶將產品新增至願望清單，管理員使用者無法存取「管理購物車」頁面的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6時，即可使用此修補程式。 修補程式ID為MDVA-41399。 請注意，問題已在Adobe Commerce 2.4.2中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.3.3-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.3 - 2.4.1-p1

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

如果客戶將產品新增到願望清單，則管理員使用者無法存取「管理購物車」頁面。

<u>必要條件</u>：

1. 建立兩個或多個產品。
1. 建立客戶。
1. 啟用開發人員模式。

<u>要再現的步驟</u>：

1. 前往Storefront，從先決條件以客戶身分登入。
1. 將產品新增至願望清單。
1. 移至[管理]面板，並導覽至已建立的客戶編輯頁面，然後按一下[管理購物車] **按鈕。**

<u>預期結果</u>：

管理員使用者能夠管理購物車。

<u>實際結果</u>：

管理員使用者收到錯誤訊息： *發生錯誤。 檢視錯誤記錄檔以取得詳細資料。*

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的「品質修補工具」[!DNL Quality Patches Tool]，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱QPT[中可用的](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)修補程式區段。
