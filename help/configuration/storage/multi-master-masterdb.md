---
title: 自動設定主要資料庫
description: 請參閱自動設定分割資料庫解決方案的指南。
recommendations: noCatalog
exl-id: a27ad097-de60-4cdd-81f9-eb1ae84587e4
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 1%

---

# 自動設定主要資料庫

{{ee-only}}

{{deprecate-split-db}}

本主題說明如何透過下列方式開始使用分割資料庫解決方案：

1. 使用單一Master資料庫（名為`magento`）安裝Adobe Commerce
1. 正在建立兩個額外的主資料庫，以用於簽出和OMS （名為`magento_quote`和`magento_sales`）
1. 設定Adobe Commerce使用結帳與銷售資料庫

>[!INFO]
>
>本指南假設所有三個資料庫與Commerce應用程式位於相同的主機上，且分別命名為`magento`、`magento_quote`和`magento_sales`。 不過，您可以自行選擇要在哪裡尋找資料庫以及命名資料庫的內容。 我們希望我們的範例能讓您更容易按照指示操作。

## 安裝Adobe Commerce軟體

安裝Adobe Commerce軟體後，您可以隨時啟用分割資料庫；換言之，您可以將分割資料庫新增至已具有結帳與訂購資料的Adobe Commerce系統。 使用Adobe Commerce README或[安裝指南](../../installation/overview.md)中的指示，使用單一master資料庫安裝Adobe Commerce軟體。

## 設定其他主要資料庫

建立簽出和OMS主資料庫，如下所示：

1. 以任何使用者身分登入您的資料庫伺服器。
1. 輸入下列命令以進入MySQL命令提示字元：

   ```bash
   mysql -u root -p
   ```

1. 出現提示時輸入MySQL `root`使用者的密碼。
1. 按照顯示的順序輸入以下命令，以建立具有相同使用者名稱和密碼的名為`magento_quote`和`magento_sales`的資料庫執行個體：

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

1. 輸入`exit`以結束命令提示字元。

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

   如果顯示MySQL監督器，表示您已正確建立資料庫。 如果顯示錯誤，請重複上述命令。

## 設定Commerce以使用主資料庫

在設定總計三個主要資料庫之後，請使用命令列來設定Commerce以使用這些資料庫。 （此指令會設定資料庫連線，並將表格分散到主要資料庫之間。）

### 首要步驟

請參閱[執行命令](../cli/config-cli.md#running-commands)以登入並執行CLI命令。

### 設定簽出資料庫

命令語法：

```bash
bin/magento setup:db-schema:split-quote --host="<checkout db host or ip>" --dbname="<name>" --username="<checkout db username>" --password="<password>"
```

例如，

```bash
bin/magento setup:db-schema:split-quote --host="localhost" --dbname="magento_quote" --username="magento_quote" --password="magento_quote"
```

系統會顯示下列訊息，確認設定成功：

```
Migration has been finished successfully!
```

### 設定OMS資料庫

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

系統會顯示下列訊息，確認設定成功：

```
Migration has been finished successfully!
```
