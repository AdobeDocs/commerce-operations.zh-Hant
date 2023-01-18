---
title: 配置MySQL從連接的最佳做法
description: 了解如何為部署在雲基礎架構上的Adobe Commerce網站配置MySQL從連接。
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: 0866272e02a7a223d35e14842bfb42a827e0468d
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---


# 配置MySQL從連接的最佳做法

>!![NOTE]
我們知道，本文仍包含業界標準的軟體術語，有些人可能認為這些術語帶有種族主義、性別歧視或壓迫性，並可能使讀者感到受傷、受創或不受歡迎。 Adobe正致力於從我們的程式碼、檔案和使用者體驗中移除這些詞語。

對於部署在雲基礎架構Pro架構上的Adobe Commerce站點，Adobe建議預設情況下為資料庫啟用MYSQL從連接。

Adobe Commerce可以非同步讀取多個資料庫。  當啟用MYSQL從連接時，Adobe Commerce會使用資料庫的只讀連接來接收非主節點上的只讀通信。 這通過負載平衡提高了效能，因為只有一個節點需要處理讀寫通信量。

## 受影響的版本

Adobe Commerce雲基礎架構，專業架構

## 配置MySQL從連接

MYSQL從連接的配置由 [MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#mysql_use_slave_connection) 在Adobe Commerce上的雲端基礎架構環境設定檔案中部署變數， `.magento.env.yaml`. 將此變數設為 `true` 啟用連線。

要啟用MySQL從連接，請執行以下操作：

1. 編輯 `.magento.env.yaml` 檔案並驗證 `MYSQL_USE_SLAVE_CONNECTION` 啟用。

   ```
   stage:
      deploy:
      MYSQL_USE_SLAVE_CONNECTION: true
   ```

1. 提交任何更改，然後將其推送到環境分支以部署更新。

   部署成功完成後，雲基礎架構上將啟用MySQL從連接。

## 其他資訊

- [環境變數](https://devdocs.magento.com/cloud/env/variables-intro.html)
- [雲基礎架構上Adobe Commerce的MySQL高負載瓶頸](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/mysql-high-load-bottleneck-in-magento-commerce-cloud.html?lang=en)
- [Adobe Commerce雲端基礎架構資料庫最佳實務](database-on-cloud.md)
