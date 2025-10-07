---
title: 執行支援公用程式
description: 瞭解如何執行支援公用程式，以疑難排解您的Adobe Commerce專案。 探索內建診斷與支援工具。
exl-id: 021b795f-e00d-43b5-9cbb-5b57a4795be7
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# 執行支援公用程式

{{ee-only}}

{{file-system-owner}}

Adobe Commerce支援公用程式（也稱為[資料收集器](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/systems/tools/support#data-collector)）可讓使用者收集有關您的系統的疑難排解資訊，供我們的支援團隊使用。

Adobe Commerce使用這些備份（也稱為&#x200B;_傾印_）來分析需要存取您程式碼的問題。 典型的案例如下：

1. 您的Commerce商店發生問題，請聯絡Adobe Commerce支援。
1. 支援人員會判斷需要檢視您的程式碼或資料庫才能重現問題。
1. 將程式碼備份至`.tar.gz`檔案。

   此備份會排除您的媒體檔案，以加速處理過程，並產生更小的檔案(_E)。

1. 您將資料庫備份至`.tar.gz`檔案。

   依預設，進行備份時會雜湊敏感資料。

1. 您可以將備份上傳至檔案共用服務。
1. 支援人員會分析問題而不會影響您的開發或生產環境。

公用程式可能需要幾分鐘才能完成。

## 建立程式碼備份

這個命令會備份程式碼並壓縮成`tar.gz`格式。

{{tip-backup-command}}

命令選項：

```bash
bin/magento support:backup:code [--name=<file name>] [-o|--output=<path>] [-l|--logs]
```

其中：

- **`--name`**&#x200B;指定傾印檔案名稱（選擇性）。 如果您省略此引數，傾印檔案會加上時間和日期戳記。
- **`-o|--output=<path>`**&#x200B;是儲存備份的絕對檔案系統路徑（必要）。
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

其中：

- **`--name`**&#x200B;指定傾印檔案名稱（選擇性）。 如果您省略此引數，傾印檔案會加上時間和日期戳記。
- **`-o|--output=<path>`是儲存備份的絕對檔案系統路徑（必要）。
- **`-l|--logs`**&#x200B;包含記錄檔（選擇性）。
- **`-i|--ignore-sanitize`**&#x200B;表示資料會保留；建立備份時，請省略資料庫中儲存之雜湊敏感資料的標幟（選擇性）。

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

按照顯示的順序執行以下命令，以顯示支援公用程式和「資料收集器」所使用之應用程式的路徑：

1. 變更至Commerce安裝目錄。

   例如， `cd /var/www/magento2`

   >[!INFO]
   >
   >命令只能從您的安裝目錄&#x200B;_正確_&#x200B;執行。

1. `bin/magento support:utility:paths`建立`<magento_root>/var/support/Paths.php`，其中列出公用程式使用的所有應用程式的路徑。
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
