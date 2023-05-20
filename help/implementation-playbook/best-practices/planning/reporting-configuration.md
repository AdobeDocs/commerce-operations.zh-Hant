---
title: 報告配置的最佳做法
description: 如果未使用報告模組，請通過刪除該模組來優化站點效能。
role: Admin
feature: Best Practices
feature-set: Commerce
exl-id: 8c991b8a-affb-4a9e-9383-671f595ff89e
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---

# 報告配置的最佳做法

如果您的業務不需要報告或動態客戶細分功能，請禁用 [報告功能](https://docs.magento.com/user-guide/configuration/general/reports.html) 提高儲存效能。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 共：

- Adobe Commerce在雲基礎架構上
- Adobe Commerce內部

## 禁用報告

如果不使用報表或動態客戶段，請禁用報表功能。

1. 從管理員導航到 **商店** > **設定** > **配置** > **常規** > **報告**。
1. 下 **常規選項**。 **啟用報告** 至 *否*。
1. 通過運行刷新快取 `php bin/magento cache:flush` 或在管理下 **系統** > **工具** > **快取管理**。

## 其他資訊

- [在Adobe Commerce生成報告](https://docs.magento.com/user-guide/reports.html)
- [客戶動態細分](https://docs.magento.com/user-guide/marketing/customer-segments.html)
