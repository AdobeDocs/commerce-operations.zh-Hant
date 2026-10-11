---
title: 報告設定的最佳實務
description: 如果您未使用報表模組，請將其移除，以最佳化網站效能。
role: Admin
feature: Best Practices, Configuration
exl-id: 8c991b8a-affb-4a9e-9383-671f595ff89e
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
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 1%
---
# 報告設定的最佳實務

如果您的企業不需要報告或動態客戶區段功能，請停用[報告功能](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/config/general/reports)以改善商店效能。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md)：

- 雲端基礎結構上的Adobe Commerce
- Adobe Commerce內部部署

## 停用報告

如果您未使用「報表」或動態客戶區段，請停用「報表」功能。

1. 從管理員中，瀏覽至&#x200B;**商店** > **設定** > **設定** > **一般** > **報告**。
1. 在&#x200B;**一般選項**&#x200B;下，將&#x200B;**啟用報表**&#x200B;設定為&#x200B;*否*。
1. 執行`php bin/magento cache:flush`或在&#x200B;**系統** > **工具** > **快取管理**&#x200B;下的管理員中排清快取。

## 其他資訊

- [在Adobe Commerce中產生報表](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/start/reporting/reports-menu)
- [客戶動態區段](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/customers/segments/customer-segments)
