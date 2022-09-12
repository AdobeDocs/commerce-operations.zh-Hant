---
title: 還原剝離資料庫
description: 從已棄用的分割資料庫實作還原為單一資料庫實作。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---


# 從拆分資料庫還原

{{ee-only}}

已實作的Adobe Commerce客戶 [拆分資料庫](multi-master.md)，以下主題說明如何還原或遷移回單一資料庫。 我們建議目前使用分割資料庫的Adobe Commerce商戶，並計畫升級至2.4.2和更新版本，以及檢閱這些步驟，以及我們的 [公告](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187) 關於剝離資料庫的計畫淘汰。

從拆分資料庫還原為單個資料庫涉及建立 `magento_quote` 和 `magento_sales` 資料庫，然後再將它們載入到單一 `magento_main` 資料庫。

在此示例中，我們登錄到安裝在同一台主機(`magento2-mysql`)作為「根」使用者。 必須用資料庫的適當值替換這些值。

1. 建立備份 `magento_quote` 資料庫：

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_quote > ./quote.sql
   ```

1. 建立備份 `magento_sales` 資料庫：

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

1. 放置 `magento_sales` 資料庫：

   ```bash
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_sales;"
   ```

1. 放置 `magento_quote` 資料庫：

   ```bash
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_quote;"
   ```

1. 移除 `checkout` 和 `sales` 在 `connections` 和 `resources` 區段 `env.php` 檔案。
1. 還原外鍵：

   ```bash
   bin/magento setup:upgrade
   ```

## 驗證您的工作

要驗證單個資料庫實施是否正常工作，請執行以下任務並驗證資料是否已添加到 `magento_main` 使用資料庫工具(如 [phpMyAdmin](../../installation/prerequisites/optional-software.md#phpmyadmin):

1. 驗證已恢復外鍵。 例如， `QUOTE_STORE_ID_STORE_STORE_ID` 鍵 `quote` 資料庫表。
1. 確認客戶可以從店面下訂單。
1. 驗證在將拆分資料庫還原為單個資料庫之前建立的訂單在管理員中是否可用。
