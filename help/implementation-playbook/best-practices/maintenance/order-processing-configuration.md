---
title: 訂單處理的設定最佳實務
description: 了解設定最佳實務，以改善結帳和訂單處理效能。
role: Admin, User
feature: Best Practices
feature-set: Commerce
source-git-commit: fbeaa486d32d77135ab97f4819ef4df9e64c6471
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---

# 訂單處理的設定最佳實務

當您的商務網站上的訂購量增加時，您可以啟用下列商店設定選項，以最佳化結帳效能和訂單處理：

- **[!UICONTROL Asynchronous indexing]** — 啟用此選項可防止同時下大量訂單時可能發生的資料庫鎖定和處理速度減慢。
- **[!UICONTROL Asynchronous email notifications]** — 啟用此選項，以指定間隔傳送結帳和訂單處理電子郵件通知，而非立即傳送，借此加快結帳效能。
- **[!UICONTROL Enable Archiving]** — 啟用此選項可改善「訂單」、「發票」、「發運」和「貸項通知單」網格的效能，並使您的工作區不存在不必要的資訊，以便您能夠專注於當前業務。 請參閱 [啟用歸檔](https://docs.magento.com/user-guide/sales/order-archive.html#to-enable-archiving).

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 共：

- Adobe Commerce雲基礎架構
- Adobe Commerce內部

## 啟用非同步訂單處理

啟用非同步訂單處理的步驟取決於部署模式：

- 對於在雲基礎架構和生產模式下的本地站點上的Adobe Commerce，請使用以下MagentoCLI命令啟用非同步索引：

   ```php
   php bin/magento config:set dev/grid/async_indexing 1
   ```

- 對於預設或生產模式下的Adobe Commerce內部部署網站，請更新「管理員」中的「格線設定」組態，以啟用非同步索引。

   請參閱 [啟用計畫網格更新和重新索引](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-scheduled-operations.html#enable-scheduled-grid-updates-and-reindexing)

   >[!WARNING]
   >
   >在更新生產環境之前，請一律在測試環境中測試設定變更。

## 其他資訊

- [設定最佳實務](../../../performance/configuration.md)
- [一般和進階設定路徑參考](../../../configuration/reference/config-reference-general.md)
- [高吞吐量訂單處理](../../../performance/high-throughput-order-processing.md)
