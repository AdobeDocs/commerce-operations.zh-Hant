---
title: 配置訂單處理的最佳做法
description: 瞭解配置最佳實踐，以改進結帳和訂單處理效能。
role: Admin, User
feature: Best Practices
feature-set: Commerce
exl-id: d15fe845-670f-4f7e-9645-7e111e6e809f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---

# 配置訂單處理的最佳做法

隨著Commerce站點上訂單量的增加，您可以通過啟用以下儲存配置選項來優化簽出效能和訂單處理：

- **[!UICONTROL Asynchronous indexing]** — 啟用此選項可防止在同時下大量訂單時發生資料庫鎖定和處理速度減慢。
- **[!UICONTROL Asynchronous email notifications]** — 啟用此選項可通過以指定間隔發送簽出和訂購處理電子郵件通知而不是立即發送來加快簽出效能。
- **[!UICONTROL Enable Archiving]** — 啟用此選項可提高訂單、發票、發運和貸項通知單的效能，並使您的工作區不存在不必要的資訊，以便您可以專注於當前業務。 請參閱 [啟用存檔](https://docs.magento.com/user-guide/sales/order-archive.html#to-enable-archiving)。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 共：

- Adobe Commerce在雲基礎架構上
- Adobe Commerce內部

## 啟用非同步訂單處理

啟用非同步訂單處理的步驟取決於部署模式：

- 對於處於生產模式的Adobe Commerce雲基礎架構和內部站點，請使用以下MagentoCLI命令啟用非同步索引：

   ```php
   php bin/magento config:set dev/grid/async_indexing 1
   ```

- 對於處於預設或生產模式的Adobe Commerce本地站點，請通過更新管理中的網格設定配置來啟用非同步索引。

   請參閱 [啟用計畫網格更新和重新索引](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-scheduled-operations.html#enable-scheduled-grid-updates-and-reindexing)

   >[!WARNING]
   >
   >在更新生產環境之前，始終test登台環境中的配置更改。

## 其他資訊

- [配置最佳做法](../../../performance/configuration.md)
- [常規和高級配置路徑參考](../../../configuration/reference/config-reference-general.md)
- [高吞吐量訂單處理](../../../performance/high-throughput-order-processing.md)
