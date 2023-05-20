---
title: 配置MySQL從連接的最佳做法
description: 瞭解如何為部署在雲基礎架構上的Adobe Commerce站點配置MySQL從連接。
role: Developer
feature-set: Commerce
feature: Best Practices
exl-id: d65bc80a-c4ec-4ea4-aff1-110592838201
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---

# 配置MySQL從連接的最佳做法

>[!NOTE]
>
>本文包含一些行業標準軟體術語，這些術語可能會讓讀者感到種族主義、性別歧視或壓迫性，並可能讓讀者感到受傷、受創或不受歡迎。 Adobe正在努力從我們的代碼、文檔和用戶體驗中刪除這些術語。

對於部署在雲基礎架構Pro體系結構上的Adobe Commerce站點，Adobe建議預設啟用資料庫的MYSQL從連接。

Adobe Commerce可以非同步讀取多個資料庫。 啟用MYSQL從連接時，Adobe Commerce使用到資料庫的只讀連接來接收非主節點上的只讀通信。 當只有一個節點處理讀寫通信時，通過負載平衡，效能得到改善。

## 受影響的版本

Adobe Commerce雲基礎架構，專業架構

## 配置MySQL從連接

在Adobe Commerce雲基礎架構中，通過設定 [MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#mysql_use_slave_connection) 變數。 將此變數設定為true可自動使用到資料庫的只讀連接。

**啟用MySQL從連接**:

1. 在本地工作站上，更改到項目目錄。

1. 在 `.magento.env.yaml` 檔案，設定 `MYSQL_USE_SLAVE_CONNECTION` 是真的。

   ```
   stage:
     deploy:
       MYSQL_USE_SLAVE_CONNECTION: true
   ```

1. 提交 `.magento.env.yaml` 檔案更改並推送到遠程環境。

   部署成功完成後，將為雲環境啟用MySQL從連接。

瞭解有關通過將現有Commerce配置替換為 [環境變數](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html#environment-variables) 的 _Adobe Commerce雲基礎架構指南_。

## 其他資訊

- [MySQL在雲基礎架構上的Adobe Commerce高負載瓶頸](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/mysql-high-load-bottleneck-in-magento-commerce-cloud.html?lang=en)
- [針對Adobe Commerce的雲基礎架構資料庫最佳做法](database-on-cloud.md)
