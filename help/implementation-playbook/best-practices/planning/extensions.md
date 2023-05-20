---
title: 擴展最佳做法
description: 瞭解如何避免第三方Adobe Commerce擴展導致的效能問題。
role: Admin
feature: Best Practices
feature-set: Commerce
exl-id: 95d2c7bf-fd2f-4c98-8293-96d69b86341f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%

---

# 擴展最佳做法

Adobe Commerce第三方擴展（模組）有可能導致各種問題，從而對店面效能產生負面影響。 您可以遵循以下最佳做法來避免這些問題：

- 從受信任的源(如 [Commerce Marketplace](https://marketplace.magento.com/extensions.html)。
- 將所有第三方擴展更新為最新版本。
- 如果無法更新第三方擴展，請考慮使用不同的擴展。
- 計畫升級到新版本的Adobe Commerce時，驗證安裝的第三方擴展是否與新版本相容，並根據需要升級擴展。

>[!NOTE]
>
> Adobe Commerce市場上的所有擴展都需要與新的Commerce版本保持相容。 請參閱 [版本相容性](https://developer.adobe.com/commerce/marketplace/guides/sellers/compatibility/releases/)。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 共：

- Adobe Commerce在雲基礎架構上
- Adobe Commerce內部

## 其他資訊

- [規劃升級的最佳做法](../../../upgrade/prepare/best-practices.md)
- 在雲基礎架構上將第三方擴展與Adobe Commerce配合使用
   - [技術和要求 — 開發和測試](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-devtest)
   - [為什麼要在整合和轉移中進行完全test?](https://devdocs.magento.com/cloud/live/live.html#whytest)
