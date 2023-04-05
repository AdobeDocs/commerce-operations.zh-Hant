---
title: 自動配置主資料庫
description: 請參閱自動配置拆分資料庫解決方案的指南。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 自動配置主資料庫

{{ee-only}}

{{deprecate-split-db}}

本主題討論如何通過以下方法開始使用拆分資料庫解決方案：

1. 使用單一主資料庫安裝Adobe Commerce(名稱為 `magento`)
1. 為簽出和OMS建立兩個附加主資料庫(名為 `magento_quote` 和 `magento_sales`)
1. 配置Adobe Commerce以使用結帳和銷售資料庫

>[!INFO]
>
>本指南假設所有三個資料庫都與Commerce應用程式位於同一台主機上，並且它們命名為 `magento`, `magento_quote`，和 `magento_sales`. 但是，資料庫的位置及其名稱由您決定。 我們希望這些範例能讓指示更容易遵循。

## 安裝Adobe Commerce軟體

安裝Adobe Commerce軟體後，您可以隨時啟用拆分資料庫；換言之，您可以將分割資料庫新增至已具有結帳和訂購資料的Adobe Commerce系統。 使用Adobe Commerce自述檔案或 [安裝指南](../../installation/overview.md) 使用單一主資料庫安裝Adobe Commerce軟體。

## 設定其他主資料庫

按如下方式建立簽出和OMS主資料庫：

1. 以任何用戶身份登錄到資料庫伺服器。
1. 輸入以下命令以獲取MySQL命令提示：

   ```bash
   mysql -u root -p
   ```

1. 輸入MySQL `root` 提示時的用戶密碼。
1. 按如下順序輸入以下命令，以建立名為 `magento_quote` 和 `magento_sales` 使用相同的用戶名和密碼：

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

1. 輸入 `exit` 退出命令提示符。

1. 驗證資料庫，一次一個：

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

## 配置商務以使用主資料庫

設定了總共三個主資料庫之後，請使用命令行配置Commerce以使用它們。 （該命令設定資料庫連接並在主資料庫之間分配表。）

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

會顯示下列訊息以確認設定成功：

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

```bash
bin/magento setup:upgrade
```

會顯示下列訊息以確認設定成功：

```terminal
Migration has been finished successfully!
```
