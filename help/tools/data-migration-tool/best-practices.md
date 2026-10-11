---
title: 資料移轉最佳實務
description: 請依照這些資料移轉最佳實務，以確保成功從Magento 1升級至Magento 2。
exl-id: 0cd51987-a514-434d-b21e-2739ada2ce85
feature: Best Practices, Configuration
topic: Commerce, Migration
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%
---
# 資料移轉最佳實務

本節提供加速及簡化移轉的最佳建議，以及可能需要多久時間的指引。

* **執行移轉測試時，請使用Magento 1執行個體的資料庫復本**。 請勿使用Magento 1存放區資料庫的生產執行個體。

* **在移轉之前，從您的Magento 1資料庫移除過時和備援的資料**。

這類資料可能包括記錄、訂單報價、最近檢視或比較的產品、訪客、事件特定類別和促銷規則。

* **請遵循[一般規則以成功移轉](migrate-data/overview.md#migration-overview)**。

* 若要提升效能，請&#x200B;**啟用您`config.xml`檔案中的`direct_document_copy`選項**：

  ```xml
  <direct_document_copy>1</direct_document_copy>
  ```

>[!NOTE]
>
>Magento 1和Magento 2資料庫必須位於同一個MySQL伺服器上，而且資料庫帳戶必須能夠存取這兩個資料庫。

## 基準估算

Adobe已在下列系統上測試資料移轉：

* Virtual Box VM、CentOS 6、2.5 GB RAM、CPU 1核心2.6 GHz
* 擁有177,000項產品、355,000筆訂單和214,000名客戶的資料庫

## 效能結果

* 設定移轉時間：約10分鐘
* 資料移轉時間：約9小時（URL重寫以外的所有資料，佔總資料約85%）
* 網站停機時間預估值：需要數分鐘的時間來重新索引和變更DNS設定。 預熱頁面快取所需的額外時間。
