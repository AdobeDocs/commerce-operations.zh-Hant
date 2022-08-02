---
title: 自動配置主資料庫
description: 請參見有關自動配置拆分資料庫解決方案的指導。
source-git-commit: bda758381d8d1b9209110adb168c36e1d504c4fa
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 1%

---


# 自動配置主資料庫

{#ee-only}

{{deprecate-split-db}}

本主題討論如何通過以下方式開始使用拆分資料庫解決方案：

1. 使用單個主資料庫安裝Adobe Commerce(名為 `magento`)
1. 為建立兩個附加主資料庫 [簽出](https://glossary.magento.com/checkout) 和OMS(命名 `magento_quote` 和 `magento_sales`)
1. 配置Adobe Commerce以使用結帳和銷售資料庫

>[!INFO]
>
>本指南假定所有三個資料庫都與Commerce應用程式位於同一主機上，並且它們被命名 `magento`。 `magento_quote`, `magento_sales`。 但是，資料庫的位置及其名稱由您決定。 我們希望我們的示例使說明更容易遵循。

## 安裝Adobe Commerce軟體

安裝Adobe Commerce軟體後，可以隨時啟用拆分資料庫；換句話說，您可以將拆分資料庫添加到已經有簽出和訂購資料的Adobe Commerce系統。 使用Adobe Commerce自述檔案或 [安裝指南](https://devdocs.magento.com/guides/v2.4/install-gde/bk-install-guide.html) 使用單個主資料庫安裝Adobe Commerce軟體。

## 設定其他主資料庫

按如下方式建立簽出和OMS主資料庫：

1. 以任何用戶身份登錄到資料庫伺服器。
1. 輸入以下命令以進入MySQL命令提示符：

   ```bash
   mysql -u root -p
   ```

1. 輸入MySQL `root` 出現提示時的用戶密碼。
1. 按顯示的順序輸入以下命令以建立名為 `magento_quote` 和 `magento_sales` 使用相同的用戶名和密碼：

   ```shell
   create database magento_quote;
   ```

   ```shell
   GRANT ALL ON magento_quote.* TO magento_quote@localhost IDENTIFIED BY 'magento_quote';
   ```

   ```shell
   create database magento_sales;
   ```

   ```shell
   GRANT ALL ON magento_sales.* TO magento_sales@localhost IDENTIFIED BY 'magento_sales';
   ```

1. 輸入 `exit` 的子菜單。

1. 驗證資料庫，一次驗證一個：

   簽出資料庫：

   ```bash
   mysql -u magento_quote -p
   ```

   ```shell
   exit
   ```

   訂單管理系統資料庫：

   ```bash
   mysql -u magento_sales -p
   ```

   ```shell
   exit
   ```

   如果顯示MySQL監視器，則已正確建立資料庫。 如果顯示錯誤，請重複前面的命令。

## 將Commerce配置為使用主資料庫

在總共設定三個主資料庫後，使用命令行配置Commerce使用它們。 （此命令設定資料庫連接並在主資料庫之間分發表。）

### 第一步

請參閱 [運行命令](../cli/config-cli.md#running-commands) 登錄並運行CLI命令。

### 配置簽出資料庫

命令語法：

```bash
bin/magento setup:db-schema:split-quote --host="<checkout db host or ip>" --dbname="<name>" --username="<checkout db username>" --password="<password>"
```

例如，

```bash
bin/magento setup:db-schema:split-quote --host="localhost" --dbname="magento_quote" --username="magento_quote" --password="magento_quote"
```

顯示以下消息以確認成功安裝：

```terminal
Migration has been finished successfully!
```

### 配置OMS資料庫

命令語法：

```bash
bin/magento setup:db-schema:split-sales --host="<checkout db host or ip>" --dbname="<name>" --username="<checkout db username>" --password="<password>"
```

例如，

```bash
bin/magento setup:db-schema:split-sales --host="localhost" --dbname="magento_sales" --username="magento_sales" --password="magento_sales"
```

顯示以下消息以確認成功安裝：

```terminal
Migration has been finished successfully!
```
