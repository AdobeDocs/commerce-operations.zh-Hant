---
title: 執行支援公用程式
description: 使用內建的支援公用程式疑難排解您的Commerce專案。
exl-id: 021b795f-e00d-43b5-9cbb-5b57a4795be7
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# 執行支援公用程式

{{ee-only}}

{{file-system-owner}}

Adobe Commerce支援公用程式（也稱為[資料收集器](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/systems/tools/support#data-collector)）可讓使用者收集有關您的系統的疑難排解資訊，供我們的支援團隊使用。

Adobe Systems Commerce 使用這些備份（也稱為 _轉儲_）來分析需要訪問您的代碼的問題。 典型場景如下：

1. 您的商務商店發生問題，請聯絡Adobe Systems商務支援。
1. 支持人員確定他們需要查看您的代碼或資料庫才能重現問題。
1. 將代碼備份到 `.tar.gz` 檔中。

   此備份_excludes您的媒體文件，以加快該過程並生成更小的文件。

1. 將資料庫備份到檔 `.tar.gz` 。

   依預設，進行備份時會雜湊敏感資料。

1. 您可以將備份上傳至檔案共用服務。
1. 支援人員會分析問題而不會影響您的開發或生產環境。

公用程式可能需要幾分鐘才能完成。

## 建立代碼備份

此命令備份代碼並將其壓縮 `tar.gz` 為 格式。

{{tip-backup-command}}

命令選項：

```bash
bin/magento support:backup:code [--name=<file name>] [-o|--output=<path>] [-l|--logs]
```

哪裡：

- **`--name`** 指定轉儲檔名（可選）。 如果省略此參數，轉儲檔將帶有時間和日期戳。
- **`-o|--output=<path>`** 是商店備份（必需）的絕對文件系統路徑。
- **`-l|--logs`**&#x200B;包含記錄檔（選擇性）。

例如，若要建立名為`/var/www/html/magento2/var/log/mycodebackup.tar.gz`的程式碼備份：

```bash
bin/magento support:backup:code --name mycodebackup -o /var/www/html/magento2/var/log
```

命令完成後，將程式碼備份至Adobe Commerce支援。

## 建立資料庫備份

這個命令會備份Commerce資料庫，並以`tar.gz`格式壓縮。

{{tip-backup-command}}

命令選項：

```bash
bin/magento support:backup:db [--name=<name>] [-o|--output=<path>] [-l|--logs] [-i|--ignore-sanitize]
```

哪裡：

- **`--name`** 指定轉儲檔名（可選）。 如果省略此參數，轉儲檔將帶有時間和日期戳。
- `-o|--output=<path>`** 是商店備份的絕對文件系統路徑（必需）。
- **`-l|--logs`** 包括紀錄檔（選擇）。
- **`-i|--ignore-sanitize`** 意味著數據被保留;创建備份時省略標幟以雜湊存儲在資料庫中的敏感数据（可選）。

敏感資料包含來自下列資料庫表格的客戶資訊：

```
'customer_entity',
'customer_entity_varchar',
'customer_address_entity',
'customer_address_entity_varchar',
'customer_grid_flat',
'quote',
'quote_address',
'sales_order',
'sales_order_address',
'sales_order_grid'
```

命令完成後，將資料庫備份提供給Adobe Commerce支援。

## 疑難排解：顯示公用程式和路徑

我們提供指令來顯示「資料收集器」和指令行所需的公用程式路徑。 例如，如果管理員或命令列顯示類似以下錯誤，您便可以使用這些命令：

```
Utility lsof not found
```

按顯示的順序運行以下命令，以顯示支援實用程式和資料收集器使用的應用程式的路徑：

1. 更改為商務安裝目錄。

   例如， `cd /var/www/magento2`

   >[!INFO]
   >
   >這些命令僅在&#x200B;_安裝目錄中正常運行_。

1. `bin/magento support:utility:paths` 建立 `<magento_root>/var/support/Paths.php`，其中列出了公用程式使用的所有應用程式的路徑。
1. `bin/magento support:utility:check`顯示檔案系統路徑。

範例如下：

```
   gzip => /bin/gzip
   lsof => /usr/sbin/lsof
   mysqldump => /usr/bin/mysqldump
   nice => /bin/nice
   php => /usr/bin/php
   tar => /bin/tar
   sed => /bin/sed
   bash => /bin/bash
   mysql => /usr/bin/mysql
```

若要解決執行工具時的問題，請確定已安裝這些應用程式，且位於網頁伺服器使用者的`$PATH`環境變數中。
