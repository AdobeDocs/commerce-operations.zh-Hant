---
title: MDVA-41061：從管理員儲存產品時，庫存狀態會重設為可銷售
description: MDVA-41061修補程式修正從管理員儲存產品時，庫存狀態重設為可銷售的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.5時，即可使用此修補程式。 修補程式ID為MDVA-41061。 QPT 1.1.15提供最新的修補程式版本，並包含MDVA-41061-V3修補程式ID。 請注意，問題已在Adobe Commerce 2.4.4中修正。
feature: Admin Workspace, Orders, Products
role: Admin
exl-id: ddbc30ef-bc88-4878-8bd8-6880823819a2
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---

# MDVA-41061：從管理員儲存產品時，庫存狀態會重設為可銷售

MDVA-41061修補程式修正從管理員儲存產品時，庫存狀態重設為可銷售的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.5時，即可使用此修補程式。 修補程式ID為MDVA-41061。 QPT 1.1.15提供最新的修補程式版本，並包含MDVA-41061-V3修補程式ID。 請注意，問題已在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.4.2-p1

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.2 - 2.4.2-p2、2.4.3 - 2.4.3-p2

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

從管理員儲存產品時，庫存狀態會重設為「可銷售」。

<u>必要條件</u>：

已安裝清查模組。

<u>要再現的步驟</u>：

1. 建立數量= 1的簡單產品。
1. 使用步驟1中建立的產品下訂單。
1. 執行cron — 確認已執行`inventory.reservations.updateSalabilityStatus`佇列，且`cataloginventory_stock_status`表格中的產品庫存狀態已變更為零。
1. 檢查前端產品。 應標示為&#x200B;**缺貨**。
1. 將產品儲存在「管理員」中，不做任何變更。

<u>預期結果</u>：

* 庫存狀態不應更新。
* 產品前端應該是&#x200B;**缺貨**。

<u>實際結果</u>：

* 簡單產品在前端標示為&#x200B;**庫存**。
* 使用者收到&#x200B;*要求的數量無法使用*&#x200B;訊息（嘗試將其新增到購物車時）。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
