---
title: 報表設定最佳作法
description: 如果您未使用報表模組，請移除該模組，以最佳化網站效能。
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 報表設定最佳實務

如果您的業務不需要報告或動態客戶區段功能，請停用 [報表功能](https://docs.magento.com/user-guide/configuration/general/reports.html) 來改善儲存效能。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 共：

- Adobe Commerce雲基礎架構
- Adobe Commerce內部

## 停用報告

如果您未使用「報表」或動態客戶區段，請停用「報表」功能。

1. 從管理員導覽至 **商店** > **設定** > **設定** > **一般** > **報表**.
1. 在 **一般選項**，設定 **啟用報表** to *否*.
1. 運行以刷新快取 `php bin/magento cache:flush` 或 **系統** > **工具** > **快取管理**.

## 其他資訊

- [在Adobe Commerce中產生報表](https://docs.magento.com/user-guide/reports.html)
- [客戶動態區段](https://docs.magento.com/user-guide/marketing/customer-segments.html)
