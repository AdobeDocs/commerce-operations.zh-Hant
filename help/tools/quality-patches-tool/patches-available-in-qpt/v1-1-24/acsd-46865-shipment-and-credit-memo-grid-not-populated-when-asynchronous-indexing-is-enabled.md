---
title: ACSD-46865：啟用[!UICONTROL asynchronous indexing]時未填入[!UICONTROL shipment]和[!UICONTROL credit memo]
description: 套用ACSD-46865修補程式以修正Adobe Commerce在啟用[!UICONTROL asynchronous indexing]時未填入[!UICONTROL shipment]和[!UICONTROL credit memo]網格的問題。
feature: Cache, Orders, Returns, Shipping/Delivery
role: Admin
exl-id: 6f84f5b6-6c34-476c-aae5-9a8ba306f8e4
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-46865：啟用[!UICONTROL asynchronous indexing]時未填入[!UICONTROL shipment]和[!UICONTROL credit memo]

ACSD-46865修補程式修正啟用[!UICONTROL asynchronous indexing]時未填入[!UICONTROL shipment]和[!UICONTROL credit memo]網格的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.24時，即可使用此修補程式。 修補程式ID為ACSD-46865。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

啟用[!UICONTROL asynchronous indexing]時未填入[!UICONTROL Shipment]和[!UICONTROL credit memo]網格。

<u>要再現的步驟</u>：

1. 在[!DNL Commerce]管理員中，移至&#x200B;**[!UICONTROL Set Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL Grid Settings]** > **[!UICONTROL Asynchronous indexing Enable]** = *是*。
2. 再次移至&#x200B;**[!UICONTROL Set Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoices]** > **[!UICONTROL Shipments]** > **[!UICONTROL Credit Memos Archiving]** > **[!UICONTROL Enable Archiving]** = *[!UICONTROL YES]*。
3. 清除設定快取。
4. 為簡單產品下新的賓客訂單。
5. 執行cron。
6. 在[!UICONTROL Commerce]管理員中開啟訂單，方法是前往&#x200B;**[!UICONTROL Sales]** > **[!UICONTROL Orders]**&#x200B;並產生發票與銷退折讓單。
7. 將訂單移至[!UICONTROL Archive]。
8. 建立簡單產品的其他訂單。
9. 執行cron。
10. 移至新訂單，並產生新的出貨、商業發票及銷退折讓單。
11. 執行cron。
12. 檢查管理員中的[!UICONTROL shipments]、[!UICONTROL invoices]和[!UICONTROL credit memo]格線。

<u>預期結果</u>：

顯示新的[!UICONTROL shipment]、[!UICONTROL invoice]和[!UICONTROL credit memo]。

<u>實際結果</u>：

未顯示新的[!UICONTROL shipment]、[!UICONTROL invoice]和[!UICONTROL credit memo]。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
