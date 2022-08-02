---
title: 還原剝離資料庫
description: 從不建議使用的拆分資料庫實現還原為單個資料庫實現。
source-git-commit: bda758381d8d1b9209110adb168c36e1d504c4fa
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---


# 從拆分資料庫還原

{{ee-only}}

針對已實施的Adobe Commerce客戶 [拆分資料庫](multi-master.md)，以下主題介紹如何還原或遷移回單個資料庫。 我們建議Adobe Commerce商家當前使用剝離資料庫並計畫升級到2.4.2及以後查看這些步驟，以及我們 [公告](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187) 拆分資料庫的計畫棄用。

從拆分資料庫還原到單個資料庫涉及建立 `magento_quote` 和 `magento_sales` 資料庫，然後將其載入到單個 `magento_main` 資料庫。

在本示例中，我們登錄到安裝在同一主機上的所有三個資料庫(`magento2-mysql`)。 必須用資料庫的相應值替換這些值。

1. 建立 `magento_quote` 資料庫：

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_quote > ./quote.sql
   ```

1. 建立 `magento_sales` 資料庫：

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_sales > ./sales.sql
   ```

1. 載入 `magento_quote` 資料庫 `magento_main` 資料庫：

   ```bash
   mysql -h "magento2-mysql" -u root -p magento_main < ./quote.sql
   ```

1. 載入 `magento_sales` 資料庫 `magento_main` 資料庫：

   ```bash
   mysql -h "magento2-mysql" -u root -p magento_main < ./sales.sql
   ```

1. 刪除 `magento_sales` 資料庫：

   ```bash
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_sales;"
   ```

1. 刪除 `magento_quote` 資料庫：

   ```bash
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_quote;"
   ```

1. 刪除的部署配置 `checkout` 和 `sales` 的 `connections` 和 `resources` 的 `env.php` 的子菜單。
1. 還原外鍵：

   ```bash
   bin/magento setup:upgrade
   ```

## 驗證您的工作

要驗證單個資料庫實現是否正常工作，請執行以下任務並驗證資料是否已添加到 `magento_main` 資料庫表使用資料庫工具，如 [phpMyAdmin](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/optional.html#install-optional-phpmyadmin):

1. 驗證外鍵是否已還原。 例如， `QUOTE_STORE_ID_STORE_STORE_ID` 的 `quote` 資料庫表。
1. 驗證客戶是否可以從店面下訂單。
1. 驗證在將拆分資料庫還原為單個資料庫之前建立的訂單是否在管理員中可用。
