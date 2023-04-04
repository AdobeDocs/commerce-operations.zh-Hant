---
title: 配置MySQL從連接的最佳做法
description: 了解如何為部署在雲基礎架構上的Adobe Commerce網站配置MySQL從連接。
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: cb86772e9ceabc580ec32ad6ae1206a71ea03946
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---


# 配置MySQL從連接的最佳做法

>[!NOTE]
>
>本文包含業界標準的軟體術語，有些術語可能會被認為是種族主義、性別歧視或壓迫性的，並可能使讀者感到受傷、受創或不受歡迎。 Adobe正致力於從我們的程式碼、檔案和使用者體驗中移除這些詞語。

對於部署在雲基礎架構Pro架構上的Adobe Commerce站點，Adobe建議預設情況下為資料庫啟用MYSQL從連接。

Adobe Commerce可以非同步讀取多個資料庫。 當啟用MYSQL從連接時，Adobe Commerce會使用資料庫的只讀連接來接收非主節點上的只讀通信。 當只有一個節點處理讀寫通信量時，通過負載平衡來提高效能。

## 受影響的版本

Adobe Commerce雲基礎架構，專業架構

## 配置MySQL從連接

在雲基礎架構上的Adobe Commerce中，您可以設定 [MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#mysql_use_slave_connection) 變數。 將此變數設為true ，以自動使用資料庫的唯讀連線。

**啟用MySQL從連接**:

1. 在本機工作站上，變更至專案目錄。

1. 在 `.magento.env.yaml` 檔案，設定 `MYSQL_USE_SLAVE_CONNECTION` 變成真。

   ```
   stage:
     deploy:
       MYSQL_USE_SLAVE_CONNECTION: true
   ```

1. 提交 `.magento.env.yaml` 檔案變更並推送至遠端環境。

   部署成功完成後，將為雲環境啟用MySQL從連接。

進一步了解如何透過覆寫現有的Commerce設定來自訂雲端環境 [環境變數](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html#environment-variables) 在 _Adobe Commerce雲端基礎架構指南_.

## 其他資訊

- [雲基礎架構上Adobe Commerce的MySQL高負載瓶頸](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/mysql-high-load-bottleneck-in-magento-commerce-cloud.html?lang=en)
- [Adobe Commerce雲端基礎架構資料庫最佳實務](database-on-cloud.md)
