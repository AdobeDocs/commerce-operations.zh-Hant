---
title: ACSD-48366： [!UICONTROL Back to Stock]電子郵件範本上未顯示產品影像
description: 套用ACSD-48366修補程式以修正產品庫存警示電子郵件中未顯示產品縮圖影像的Adobe Commerce問題。
feature: Admin Workspace, Communications, Orders, Products
role: Admin
exl-id: a721f399-f50a-4a13-9f5d-17ae7f3985f6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-48366： [!UICONTROL Back to Stock]電子郵件範本上未顯示產品影像

ACSD-48366修補程式修正了產品庫存警報電子郵件中未顯示產品縮圖影像的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.26時，即可使用此修補程式。 修補程式ID為ACSD-48366。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.6

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

產品影像未顯示在[!UICONTROL Back to Stock]電子郵件範本上。

<u>要再現的步驟</u>：

1. 前往&#x200B;**[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Alert]** > **[!UICONTROL Allow Alert When Product Comes Back in Stock]** = *[!UICONTROL Yes]*，為&#x200B;*[!UICONTROL Back in Stock]*&#x200B;啟用&#x200B;*[!UICONTROL Product Alert]*。
1. 前往&#x200B;**[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Display Out of Stock]** = *[!UICONTROL Yes]*&#x200B;來啟用&#x200B;*[!UICONTROL Display Out of Stock Products]*。
1. 建立數量= 0的簡單產品。
1. 從店面建立客戶並訂閱上述產品，以便在有存貨時收到產品提醒。
1. 讓產品有貨。
1. 執行產品警示確認。

   ```
   n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

1. 啟動客戶的產品警示。

   ```
   bin/magento queue:consumers:start product_alert
   ```

1. 檢查電子郵件。 庫存警示電子郵件現在應該可以在郵件收集器中使用。

<u>預期結果</u>：

產品影像會顯示在庫存警示電子郵件中。

<u>實際結果</u>：

庫存警示電子郵件中無法使用產品影像。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
