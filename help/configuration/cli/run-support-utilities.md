---
title: 運行支援實用程式
description: 使用內置支援實用程式對Commerce項目進行故障排除。
exl-id: 021b795f-e00d-43b5-9cbb-5b57a4795be7
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# 運行支援實用程式

{{ee-only}}

{{file-system-owner}}

Adobe Commerce支援實用程式 — 也稱為 [資料收集器](https://docs.magento.com/user-guide/system/support-data-collector.html) — 使用戶能夠收集有關您的系統的故障排除資訊，這些資訊可供我們的支援團隊使用。

Adobe Commerce使用這些備份，也稱為 _轉儲_&#x200B;分析需要訪問代碼的問題。 典型情形如下：

1. 您的Commerce商店出現問題，請與Adobe Commerce支援部門聯繫。
1. 支援確定他們需要查看您的代碼或資料庫才能重現問題。
1. 將代碼備份到 `.tar.gz` 的子菜單。

   此備份排除媒體檔案以加快進程並生成一個小得多的檔案(_E)。

1. 將資料庫備份到 `.tar.gz` 的子菜單。

   預設情況下，在進行備份時會對敏感資料進行散列處理。

1. 將備份上載到檔案共用服務。
1. 支援分析您的問題而不影響您的開發或生產環境。

這些實用程式可能需要幾分鐘才能完成。

## 建立代碼備份

此命令將代碼備份並壓縮到 `tar.gz` 的子菜單。

{{tip-backup-command}}

命令選項：

```bash
bin/magento support:backup:code [--name=<file name>] [-o|--output=<path>] [-l|--logs]
```

位置：

- **`--name`** 指定轉儲檔案名（可選）。 如果忽略此參數，則轉儲檔案是時間戳和日期戳。
- **`-o|--output=<path>`** 是用於儲存備份的絕對檔案系統路徑（必需）。
- **`-l|--logs`** 包括日誌檔案（可選）。

例如，要建立名為 `/var/www/html/magento2/var/log/mycodebackup.tar.gz`:

```bash
bin/magento support:backup:code --name mycodebackup -o /var/www/html/magento2/var/log
```

命令完成後，為Adobe Commerce支援提供代碼備份。

## 建立資料庫備份

此命令備份Commerce資料庫，並將其壓縮到 `tar.gz` 的子菜單。

{{tip-backup-command}}

命令選項：

```bash
bin/magento support:backup:db [--name=<name>] [-o|--output=<path>] [-l|--logs] [-i|--ignore-sanitize]
```

位置：

- **`--name`** 指定轉儲檔案名（可選）。 如果忽略此參數，則轉儲檔案是時間戳和日期戳。
- **`-o|--output=<path>` 是用於儲存備份的絕對檔案系統路徑（必需）。
- **`-l|--logs`** 包括日誌檔案（可選）。
- **`-i|--ignore-sanitize`** 即資料被保留；在建立備份時，省略標籤以散列儲存在資料庫中的敏感資料（可選）。

敏感資料包括來自以下資料庫表的客戶資訊：

```terminal
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

命令完成後，為Adobe Commerce支援提供資料庫備份。

## 故障排除：顯示實用程式和路徑

我們提供命令，顯示「資料收集器」(Data Collector)和命令行所需的實用程式的路徑。 例如，如果Admin或命令行中顯示以下錯誤，則可以使用這些命令：

```terminal
Utility lsof not found
```

按顯示的順序運行以下命令，以顯示支援實用程式和資料收集器使用的應用程式的路徑：

1. 更改到Commerce安裝目錄。

   比如說， `cd /var/www/magento2`

   >[!INFO]
   >
   >命令運行正常 _僅_ 從安裝目錄。

1. `bin/magento support:utility:paths` 建立 `<magento_root>/var/support/Paths.php`，其中列出了該實用程式使用的所有應用程式的路徑。
1. `bin/magento support:utility:check` 顯示檔案系統路徑。

示例如下：

```terminal
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

要解決運行工具時的問題，請確保這些應用程式已安裝並位於Web伺服器用戶的 `$PATH` 環境變數。
