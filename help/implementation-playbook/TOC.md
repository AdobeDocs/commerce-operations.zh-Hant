---
user-guide-title: 實施行動手冊
user-guide-description: 了解成功Adobe Commerce網站的規劃與實作策略。
mini-toc-levels: 3
source-git-commit: 5559d412ab58d392098cfff7a4cabb473c38cb0d
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 0%

---


# 實施行動手冊 {#implementation-playbook}

- [概述](overview.md)
- 商務 {#intro}
   - [關於Adobe Commerce](intro/about-commerce.md)
   - [平台開發原則](intro/platform-development.md)
- 項目範圍 {#project-scope}
   - [知識就是力量](project-scope/knowledge.md)
   - [主要利害關係人](project-scope/key-stakeholders.md)
   - [程式和時間表](project-scope/process-timeline.md)
   - [交付件](project-scope/deliverables.md)
   - [需求核對表](project-scope/requirement-checklists.md)
- 開發 {#development}
   - [平台工具](development/platform-tools.md)
   - [專案管理工具](development/project-management-tools.md)
   - [項目實施方法](development/delivery.md)
   - [質量控制](development/quality-control.md)
- 規劃與治理 {#planning}
   - [交付和規劃方法](planning/delivery.md)
   - [責任和所有權](planning/ownership.md)
   - [專案控管](planning/governance.md)
- 架構與整合 {#architecture}
   - [功能](architecture/capabilities.md)
   - [整合策略](architecture/integration-strategy.md)
   - [可擴充性策略](architecture/extensibility-strategy.md)
   - [整合選項](architecture/integration-options.md)
   - [全局參考體系結構](architecture/global-reference.md)
   - 無頭商務 {#headless}
      - [優點](architecture/headless/benefits.md)
      - [無頭之旅](architecture/headless/journey-to-headless.md)
      - [微服務](architecture/headless/microservices.md)
      - [無頭進化](architecture/headless/evolution.md)
      - [耦合式店面結構](architecture/headless/legacy-storefront.md)
      - [無頭式架構](architecture/headless/adobe-commerce.md)
- 基礎架構和部署 {#infrastructure}
   - [概述](infrastructure/overview.md)
   - [內部基礎設施](infrastructure/on-premises.md)
   - 雲基礎架構 {#cloud}
      - [概述](infrastructure/cloud/overview.md)
      - [地區](infrastructure/cloud/regions.md)
      - [技術](infrastructure/cloud/technology.md)
      - [環境](infrastructure/cloud/environments.md)
      - [托管服務](infrastructure/cloud/managed-services.md)
      - [安全性和合規性](infrastructure/cloud/security.md)
   - 效能最佳化 {#performance}
      - [典型問題](infrastructure/performance/optimization.md)
      - [基準](infrastructure/performance/benchmarks.md)
      - [Recommendations](infrastructure/performance/recommendations.md)
- 啟動準備 {#launch}
   - [概述](launch/overview.md)
   - [啟動前步驟](launch/pre-launch-steps.md)
   - [啟動步驟](launch/launch-steps.md)
   - [啟動後步驟](launch/post-launch-steps.md)
- 維護與支援 {#maintenance}
   - [概述](maintenance/overview.md)
   - [Adobe Managed Services](maintenance/adobe-managed-services.md)
- 最佳實務 {#best-practices}
   - [概述](best-practices/phases.md)
   - 規劃 {#planning}
      - [概述](best-practices/planning/overview.md)
      - [站點、儲存和儲存視圖配置](best-practices/planning/sites-stores-store-views.md)
      - [報表設定](best-practices/planning/reporting-configuration.md)
      - [雲端部署的資料庫設&#x200B;定](best-practices/planning/database-on-cloud.md)
      - [MySQL從連接配&#x200B;置](best-practices/planning/configure-mysql-slave-connection-on-cloud.md)
      - [MySQL觸發器用法](best-practices/planning/mysql-triggers-usage.md)
      - [Redis服務配置](best-practices/planning/redis-service-configuration.md)
      - [OPcache記憶體大小](best-practices/planning/opcache-memory-size.md)
      - [Realpath快取大小](best-practices/planning/realpath-cache-size.md)
      - [類別](best-practices/planning/category-limits.md)
      - [產品](best-practices/planning/product-sku-limits.md)
      - [產品變數](best-practices/planning/product-variations.md)
      - [產品選項](best-practices/planning/product-options.md)
      - [產品屬性](best-practices/planning/product-attributes-and-options.md)
      - [產品清單分頁](best-practices/planning/product-listing-pagination.md)
      - [產品購物車限制](best-practices/planning/product-cart.md)
      - [促銷活動](best-practices/planning/product-cart-promotions.md)
      - [擴充功能](best-practices/planning/extensions.md)
      - [合作夥伴升級](best-practices/planning/partner-escalation.md)
      - [支付儲存處理](best-practices/planning/payment-processing-storage.md)
   - 開發 {#development}
      - [概述](best-practices/development/overview.md)
      - [影像最佳化](best-practices/development/image-optimization.md)
      - [疑難排解](best-practices/development/troubleshooting.md)
      - [最佳化CSS和JS檔案](best-practices/development/optimize-css-js-files.md)
      - [私人內容區塊](best-practices/development/private-content-block-configuration.md)
      - [靜態內容部署](best-practices/development/static-content-deployment.md)
      - [修改資料庫表](best-practices/development/modifying-core-and-third-party-tables.md)
   - Launch {#launch}
      - [概述](best-practices/launch/overview.md)
      - [Adobe安全通知服務](best-practices/launch/security-notification-service.md)
      - [配置robots.txt檔案](best-practices/launch/robots-txt.md)
      - [防止和應對安全事件](best-practices/launch/prevent-respond-security-incident.md)
   - 維護 {#maintenance}
      - [概述](best-practices/maintenance/overview.md)
      - [審計前期績效](best-practices/maintenance/frontend-performance.md)
      - [索引器配置](best-practices/maintenance/indexer-configuration.md)
      - [訂單處理](best-practices/maintenance/order-processing-configuration.md)
      - [在生產網站上排程管理員更新](best-practices/maintenance/scheduling-admin-updates-in-production.md)
      - [更新服務](best-practices/maintenance/update-services.md)
      - [升級檢查清單](best-practices/maintenance/upgrade-checklist.md)
      - [解決資料庫效能問題](best-practices/maintenance/resolve-database-performance-issues.md)
      - [MariaDB的升級先決條件](best-practices/maintenance/commerce-235-upgrade-prerequisites-mariadb.md)
- [返回操作指南](https://experienceleague.adobe.com/docs/commerce-operations/operational-guides/home.html)
