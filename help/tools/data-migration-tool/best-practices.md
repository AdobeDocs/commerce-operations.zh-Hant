---
title: 資料移轉最佳實務
description: 請依照這些資料移轉最佳實務，確保成功從Magento1升級至Magento2。
exl-id: 0cd51987-a514-434d-b21e-2739ada2ce85
feature: Best Practices, Configuration
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---

# 資料移轉最佳實務

本節提供加速及簡化移轉的最佳建議，以及可能需要多久時間的指引。

* **使用Magento1執行處理的資料庫復本** 執行移轉測試時。 請勿使用Magento1存放區資料庫的生產執行個體。

* **移除過時和備援的資料** 移轉前從您的Magento1資料庫取得。

這類資料可能包括記錄、訂單報價、最近檢視或比較的產品、訪客、事件特定類別和促銷規則。

* **請遵循 [成功移轉的一般規則](migrate-data/overview.md#migration-overview)**.

* 提升效能， **啟用 `direct_document_copy` 選項** 在您的 `config.xml` 檔案：

  ```xml
  <direct_document_copy>1</direct_document_copy>
  ```

>[!NOTE]
>
>Magento1和Magento2資料庫必須位於相同的MySQL伺服器上，而且資料庫帳戶必須能夠存取這兩個資料庫。

## 基準估算

Adobe已在下列系統上測試資料移轉：

* Virtual Box VM，CentOS 6,2.5 GB RAM，CPU 1核心2.6 GHz
* 擁有177,000項產品、355,000筆訂單和214,000名客戶的資料庫

## 效能結果

* 設定移轉時間：約10分鐘
* 資料移轉時間：約9小時（URL重寫以外的所有資料，佔總資料約85%）
* 網站停機時間預估值：需要數分鐘的時間來重新索引和變更DNS設定。 預熱頁面快取所需的額外時間。
