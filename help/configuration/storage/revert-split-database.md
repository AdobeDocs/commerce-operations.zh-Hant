---
title: 還原分割資料庫
description: 從已棄用的分割資料庫實作還原為單一資料庫實作。
feature: Configuration, Storage
exl-id: 2ece24e0-1f85-445a-8e22-fb10611403ff
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 0%

---

# 從分割資料庫還原

{{ee-only}}

針對已實作[分割資料庫](multi-master.md)的Adobe Commerce客戶，下列主題說明如何回覆或移回單一資料庫。 我們建議Adobe Commerce商戶目前使用分割資料庫，並計畫升級至2.4.2和更新版本，檢閱這些步驟，以及我們關於計畫淘汰分割資料庫的[公告](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187)。

從分割資料庫回覆至單一資料庫時，必須先建立`magento_quote`和`magento_sales`資料庫的備份，然後再將其載入單一`magento_main`資料庫。

在此範例中，我們登入所有三個資料庫，這些資料庫與「root」使用者安裝在相同的主機(`magento2-mysql`)上。 您必須將這些值取代為您的資料庫適當的值。

1. 建立`magento_quote`資料庫的備份：

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_quote > ./quote.sql
   ```

1. 建立`magento_sales`資料庫的備份：

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_sales > ./sales.sql
   ```

1. 將`magento_quote`資料庫載入`magento_main`資料庫：

   ```bash
   mysql -h "magento2-mysql" -u root -p magento_main < ./quote.sql
   ```

1. 將`magento_sales`資料庫載入`magento_main`資料庫：

   ```bash
   mysql -h "magento2-mysql" -u root -p magento_main < ./sales.sql
   ```

1. 卸除`magento_sales`資料庫：

   ```bash
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_sales;"
   ```

1. 卸除`magento_quote`資料庫：

   ```bash
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_quote;"
   ```

1. 移除`checkout`檔案之`sales`和`connections`區段中`resources`和`env.php`的部署組態。
1. 還原外部索引鍵：

   ```bash
   bin/magento setup:upgrade
   ```

## 驗證您的工作

若要驗證您的單一資料庫實作是否正常運作，請使用如`magento_main`phpMyAdmin[的資料庫工具，執行下列工作，並驗證資料是否已新增至](../../installation/prerequisites/optional-software.md#phpmyadmin)資料庫表格：

1. 確認外部索引鍵已還原。 例如，`QUOTE_STORE_ID_STORE_STORE_ID`資料庫資料表中的`quote`索引鍵。
1. 確認客戶可以從店面下訂單。
1. 確認在將分割資料庫還原為單一資料庫之前建立的訂單可在Admin中使用。
