---
user-guide-title: 實施行動手冊
user-guide-description: 了解規劃及實施成功 Adobe Commerce 網站的策略。
mini-toc-levels: 3
source-git-commit: 36a2a86cbafab1e4913573b1c8431524ba43dc6a
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 12%

---


# 實施行動手冊 {#implementation-playbook}

- [概觀](overview.md)
- 商務 {#intro}
   - [關於Adobe Commerce](intro/about-commerce.md)
   - [平台開發原則](intro/platform-development.md)
- 專案範圍 {#project-scope}
   - [知識就是力量](project-scope/knowledge.md)
   - [主要關係人](project-scope/key-stakeholders.md)
   - [流程和時間表](project-scope/process-timeline.md)
   - [交付專案](project-scope/deliverables.md)
   - [需求檢查清單](project-scope/requirement-checklists.md)
- 開發 {#development}
   - [平台工具](development/platform-tools.md)
   - [專案管理工具](development/project-management-tools.md)
   - [專案實作方法](development/delivery.md)
   - [品質控制](development/quality-control.md)
- 規劃與控管 {#planning}
   - [交付與規劃方法](planning/delivery.md)
   - [責任與擁有權](planning/ownership.md)
   - [專案治理](planning/governance.md)
- 架構與整合 {#architecture}
   - [企業參考](architecture/enterprise-blueprint.md)
   - 全球參考架構 {#global-reference-architecture}
      - [概觀](architecture/global-reference/overview.md)
      - [範例](architecture/global-reference/examples.md)
      - Composer開發 {#composer}
         - [概觀](architecture/global-reference/composer/overview.md)
         - [專案結構](architecture/global-reference/composer/project-structure.md)
         - [提示與秘訣](architecture/global-reference/composer/tips-and-tricks.md)
- 基礎結構和部署 {#infrastructure}
   - [概觀](infrastructure/overview.md)
   - 自行託管 {#self-hosting}
      - [概觀](infrastructure/self-hosting/overview.md)
      - [內部部署基礎結構](infrastructure/self-hosting/on-premises.md)
      - [安全性概念](infrastructure/self-hosting/security-concepts.md)
      - [監視遙測和工具](infrastructure/self-hosting/monitoring-tools.md)
      - [災難回覆概念](infrastructure/self-hosting/disaster-recovery-ideas.md)
      - [效能提示](infrastructure/self-hosting/performance-tips.md)
   - 雲端基礎結構 {#cloud}
      - [概觀](infrastructure/cloud/overview.md)
      - [地區](infrastructure/cloud/regions.md)
      - [技術](infrastructure/cloud/technology.md)
      - [安全性與合規性](infrastructure/cloud/security.md)
   - 效能最佳化 {#performance}
      - [典型問題](infrastructure/performance/optimization.md)
      - [基準](infrastructure/performance/benchmarks.md)
      - [Recommendations](infrastructure/performance/recommendations.md)
- Launch整備 {#launch}
   - [概觀](launch/overview.md)
   - [啟動前的步驟](launch/pre-launch-steps.md)
   - [啟動步驟](launch/launch-steps.md)
   - [啟動後的步驟](launch/post-launch-steps.md)
- 維護與支援 {#maintenance}
   - [概觀](maintenance/overview.md)
   - [AdobeManaged Services](maintenance/adobe-managed-services.md)
- 最佳實務 {#best-practices}
   - [概觀](best-practices/phases.md)
   - 規劃 {#planning}
      - [概觀](best-practices/planning/overview.md)
      - [目錄管理](best-practices/planning/catalog-management.md)
      - [網站、商店和商店檢視設定](best-practices/planning/sites-stores-store-views.md)
      - [報告設定](best-practices/planning/reporting-configuration.md)
      - [雲端部署的資料庫設定&#x200B;。](best-practices/planning/database-on-cloud.md)
      - [MySQL設定](best-practices/planning/mysql-configuration.md)
      - [Redis服務組態](best-practices/planning/redis-service-configuration.md)
      - [OPcache記憶體大小](best-practices/planning/opcache-memory-size.md)
      - [Realpath快取大小](best-practices/planning/realpath-cache-size.md)
      - [擴充功能](best-practices/planning/extensions.md)
      - [合作夥伴升級](best-practices/planning/partner-escalation.md)
      - [付款儲存處理](best-practices/planning/payment-processing-storage.md)
   - 開發 {#development}
      - [概觀](best-practices/development/overview.md)
      - [一般最佳實務](best-practices/development/general.md)
      - [程式碼管理](best-practices/development/code-management.md)
      - [程式碼檢閱](best-practices/development/code-review.md)
      - [偵錯](best-practices/development/debugging.md)
      - [例外狀況處理](best-practices/development/exception-handling.md)
      - [Git分支](best-practices/development/git-branching.md)
      - [目錄影像調整大小](best-practices/development/catalog-image-resizing.md)
      - [影像最佳化](best-practices/development/image-optimization.md)
      - [疑難排解](best-practices/development/troubleshooting.md)
      - [最佳化CSS和JS檔案](best-practices/development/optimize-css-js-files.md)
      - [私人內容區塊](best-practices/development/private-content-block-configuration.md)
      - [靜態內容部署](best-practices/development/static-content-deployment.md)
      - [修改資料庫表格](best-practices/development/modifying-core-and-third-party-tables.md)
      - [修改核心和第三方程式碼](best-practices/development/modifying-core-and-third-party-code.md)
   - Launch {#launch}
      - [概觀](best-practices/launch/overview.md)
      - [設定網頁編目程式](best-practices/launch/robots-txt.md)
      - [保護您的網站與基礎建設](best-practices/launch/security-best-practices.md)
   - 維護 {#maintenance}
      - [概觀](best-practices/maintenance/overview.md)
      - [稽核前端效能](best-practices/maintenance/frontend-performance.md)
      - [最佳化後端效能](best-practices/maintenance/backend-performance.md)
      - [索引器設定](best-practices/maintenance/indexer-configuration.md)
      - [大規模修補](best-practices/maintenance/patching-at-scale.md)
      - [訂單處理](best-practices/maintenance/order-processing-configuration.md)
      - [解決資料庫效能問題](best-practices/maintenance/resolve-database-performance-issues.md)
      - [回應安全性事件](best-practices/maintenance/respond-to-security-incident.md)
      - [正在排程生產網站上的管理員更新](best-practices/maintenance/scheduling-admin-updates-in-production.md)
      - [更新服務](best-practices/maintenance/update-services.md)
      - [升級檢查清單](best-practices/maintenance/upgrade-checklist.md)
      - [升級MariaDB的必要條件](best-practices/maintenance/mariadb-upgrade.md)
- [返回作業指南](https://experienceleague.adobe.com/docs/commerce-operations/operational-guides/home.html)
