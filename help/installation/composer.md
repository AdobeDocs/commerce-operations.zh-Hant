---
title: 快速啟動本地安裝
description: 按照以下步驟在您擁有的基礎架構上安裝Adobe Commerce或Magento Open Source。
exl-id: a93476e8-2b30-461a-91df-e73eb1a14d3c
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '990'
ht-degree: 0%

---

# 快速啟動本地安裝

我們使用 [作曲家](https://getcomposer.org/) 管理Adobe Commerce和Magento Open Source元件及其依賴項。 使用Composer獲取Adobe Commerce和Magento Open Source元包具有以下優點：

- 重新使用第三方庫，而不將其與原始碼捆綁在一起
- 通過使用具有強健依賴關係管理的基於元件的體系結構減少擴展衝突和相容性問題
- 堅持 [PHP-Framework互操作性組(FIG)](https://www.php-fig.org/) 標準
- 重新封裝與其他元件的Magento Open Source
- 在生產環境中使用Adobe Commerce或Magento Open Source軟體

>[!NOTE]
>
>為Magento Open Source作出貢獻的開發商應使用 [基於Git](https://developer.adobe.com/commerce/contributor/guides/install/) 安裝方法。

## 先決條件

在繼續之前，必須執行以下操作：

- 全部完成 [必備任務](system-requirements.md)。
- [安裝合成器](https://getcomposer.org/download/)。
- 獲取 [身份驗證密鑰](prerequisites/authentication-keys.md) Adobe Commerce和Magento Open Source作曲家資料庫。

## 以檔案系統所有者身份登錄

瞭解我們中的所有權、權限和檔案系統所有者 [所有權和權限概述主題](prerequisites/file-system/overview.md)。

切換到檔案系統所有者：

1. 以具有向檔案系統寫入權限的用戶身份或切換到身份登錄到應用程式伺服器。

   如果使用bash shell，則可以使用以下語法切換到檔案系統所有者並同時輸入命令：

   ```bash
   su <file system owner> -s /bin/bash -c <command>
   ```

   如果檔案系統所有者不允許登錄，可以執行以下操作：

   ```bash
   sudo -u <file system owner>  <command>
   ```

1. 要從任何目錄運行CLI命令，請添加 `<app_root>/bin` 到系統 `PATH`。

   由於shell的語法不同，因此請參考引用，如 [unix.stackexchange.com](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables)。

   CentOS的bash shell示例：

   ```bash
   export PATH=$PATH:/var/www/html/magento2/bin
   ```

   （可選）您可以通過以下方式運行命令：

   - `cd <app_root>/bin` 把它們 `./magento <command name>`
   - `app_root>/bin/magento <command name>`
   - `<app_root>` 是Web伺服器docroot的子目錄

## 獲取暗喻

要獲得Adobe Commerce或Magento Open Source暗喻：

1. 以或切換到的應用程式伺服器 [檔案系統所有者](prerequisites/file-system/overview.md)。
1. 更改為Web伺服器docroot目錄或您已配置為虛擬主機docroot的目錄。
1. 使用Adobe Commerce或Magento Open Source元包建立Composer項目。

   **Magento Open Source**

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   出現提示時，輸入您的驗證密鑰。 在您的 [Commerce Marketplace](https://marketplace.magento.com/customer/account/login/)。

   如果遇到錯誤，例如 `Could not find package...` 或 `...no matching package found`，確保命令中沒有拼寫錯誤。 如果您仍然遇到錯誤，則可能無權下載Adobe Commerce。 聯繫人 [Adobe Commerce支援](https://support.magento.com/hc/en-us) 的雙曲餘切值。

   請參閱 [故障排除](https://support.magento.com/hc/en-us/articles/360033818091) 的子例行程式。

   >[!NOTE]
   >
   >Adobe Commerce客戶可在正式上市(GA)日期前兩週訪問修補程式。 預發行包僅通過Composer提供。 在正式啟動之前，您無法訪問開發人員門戶或GitHub上的預發行版。 如果在Composer中找不到這些包，請與Adobe Commerce支援部門聯繫。

### 示例 — 次要版本

次要版本包含新功能、質量修復和安全修復。 使用Composer指定次要版本。 例如，要指定Adobe Commerce2.4.5元包：

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.5 <install-directory-name>
```

### 示例 — 質量補丁

質量修補程式主要包含功能 _和_ 安全修復。 但是，它們有時也可包含新的、向後相容的功能。 使用Composer下載質量修補程式。 例如，要指定Adobe Commerce2.4.5元包：

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.5 <install-directory-name>
```

### 示例 — 安全修補程式

安全修補程式僅包含安全修復。 它們旨在使升級過程更快、更輕鬆。

安全修補程式使用Composer命名約定 `2.4.5-px`。 使用Composer指定修補程式。 例如，要下載Adobe Commerce2.4.5-p1元包：

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.5-p1 <install-directory-name>
```

## 設定檔案權限

在安裝Adobe Commerce或Magento Open Source之前，必須設定Web伺服器組的讀寫權限。 這是必需的，以便命令行可以將檔案寫入檔案系統。

```terminal
cd /var/www/html/<magento install directory>
find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
chown -R :www-data . # Ubuntu
chmod u+x bin/magento
```

## 安裝應用程式

必須使用命令行來安裝Adobe Commerce或Magento Open Source。

此示例假定安裝目錄的名稱 `magento2ee`，也請參見Wiki頁。 `db-host` 在同一台電腦上(`localhost`)，而且 `db-name`。 `db-user`, `db-password` 全部 `magento`:

```bash
bin/magento setup:install \
--base-url=http://localhost/magento2ee \
--db-host=localhost \
--db-name=magento \
--db-user=magento \
--db-password=magento \
--admin-firstname=admin \
--admin-lastname=admin \
--admin-email=admin@admin.com \
--admin-user=admin \
--admin-password=admin123 \
--language=en_US \
--currency=USD \
--timezone=America/Chicago \
--use-rewrites=1 \
--search-engine=opensearch \
--opensearch-host=os-host.example.com \
--opensearch-port=9200 \
--opensearch-index-prefix=magento2 \
--opensearch-timeout=15
```

>[!TIP]
>
>可以使用 `--backend-frontname` 的雙曲餘切值。 但是，我們建議省略此選項並允許安裝命令自動生成隨機URI。 隨機URI對駭客或惡意軟體來說更難利用。 安裝完成後，URI將顯示在控制台中。

>[!TIP]
>
>有關CLI安裝選項的完整說明，請參見 [從命令行安裝應用程式](advanced.md)。

## 命令摘要

要顯示命令的完整清單，請輸入：

```bash
bin/magento list
```

要獲取特定命令的幫助，請輸入：

```bash
bin/magento help <command>
```

例如：

```bash
bin/magento help setup:install
```

```bash
bin/magento help cache:enable
```

下表概述了可用命令。 命令僅以摘要形式顯示。 有關命令的詳細資訊，請按一下「命令」列中的連結。

| 命令 | 說明 | 先決條件 |
|--- |--- |--- |
| `magento setup:install` | 安裝應用程式 | 無 |
| `magento setup:uninstall` | 刪除應用程式。 | 已安裝應用程式 |
| `magento setup:upgrade` | 更新應用程式。 | 部署配置 |
| `magento maintenance:{enable/disable}` | 啟用或禁用維護模式（在維護模式下，只有免除的IP地址才能訪問管理或店面）。 | 已安裝應用程式 |
| `magento setup:config:set` | 建立或更新部署配置。 | 無 |
| `magento module:{enable/disable}` | 啟用或禁用模組。 | 無 |
| `magento setup:store-config:set` | 設定與儲存前端相關的選項，如基本URL、語言、時區。 | 部署配置 |
| `magento setup:db-schema:upgrade` | 更新資料庫架構。 | 部署配置 |
| `magento setup:db-data:upgrade` | 更新資料庫資料。 | 部署配置 |
| `magento setup:db:status` | 檢查資料庫是否與代碼保持最新。 | 部署配置 |
| `magento admin:user:create` | 建立管理員用戶。 | 您可以為以下項建立用戶：<br><br>部署配置<br><br>至少啟用 `Magento_User` 和 `Magento_Authorization` 模組<br><br>資料庫(最簡單的方法是使用 `bin/magento setup:upgrade`) |
| `magento list` | 列出所有可用命令。 | 無 |
| `magento help` | 提供指定命令的幫助。 | 無 |

### 常見參數

以下參數是所有命令的通用參數。 這些命令可以在安裝應用程式之前或之後運行：

| 長版本 | 短版本 | 意義 |
|--- |--- |--- |
| `--help` | `-h` | 獲取任何命令的幫助。 比如說， `./magento help setup:install` 或 `./magento help setup:config:set`。 |
| `--quiet` | `-q` | 安靜模式；沒有輸出。 |
| `--no-interaction` | `-n` | 沒有互動問題。 |
| `--verbose=1,2,3` | `-v, -vv, -vvv` | 詳細級別。 比如說， `--verbose=3` 或 `-vvv` 顯示debug verbosity ，這是最詳細的輸出。 預設值為 `--verbose=1` 或 `-v`。 |
| `--version` | `-V` | 顯示此應用程式版本 |
| `--ansi` | n/a | 強制ANSI輸出 |
| `--no-ansi` | n/a | 禁用ANSI輸出 |

>[!NOTE]
>
>恭喜！ 您已完成快速安裝。 需要更高級的幫助嗎？ 看看我們 [高級安裝](advanced.md) 的子菜單。
