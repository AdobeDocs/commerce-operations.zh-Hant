---
title: 資料遷移最佳做法
description: 遵循這些資料遷移最佳實踐，確保成功從Magento1升級到Magento2。
exl-id: 0cd51987-a514-434d-b21e-2739ada2ce85
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---

# 資料遷移最佳做法

本節提供了加速和簡化遷移的最佳建議，並指導您瞭解可能需要多長時間。

* **從Magento1實例使用資料庫的副本** 執行遷移測試時。 請勿使用Magento1儲存資料庫的生產實例。

* **刪除過時和冗餘的資料** 從Magento1資料庫進行遷移。

此類資料可能包括日誌、訂單報價、最近查看或比較的產品、訪問者、特定事件類別和促銷規則。

* **關注 [成功遷移的一般規則](migrate-data/overview.md#migration-overview)**。

* 為了提高效能， **啟用 `direct_document_copy` 選項** 在 `config.xml` 檔案：

   ```xml
   <direct_document_copy>1</direct_document_copy>
   ```

>[!NOTE]
>
>Magento1和Magento2資料庫必須位於同一MySQL伺服器上，並且資料庫帳戶必須具有訪問這兩個資料庫的權限。

## 基準評估

Adobe已在以下系統上測試了資料遷移：

* Virtual Box VM,CentOS 6,2.5 GB RAM, CPU 1內核2.6 GHz
* 資料庫包含177,000個產品、355,000個訂單和214,000個客戶

## 效能結果

* 設定遷移時間：約10分鐘
* 資料遷移時間：約9小時（除URL重寫外的所有資料，總資料的約85%）
* 站點停機估計：重新索引和更改DNS設定需要幾分鐘。 預熱頁面快取所需的額外時間。
