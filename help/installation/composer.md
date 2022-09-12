---
title: 快速啟動本地安裝
description: 請依照下列步驟，安裝Adobe Commerce或Magento Open Source至您擁有的基礎架構。
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '996'
ht-degree: 0%

---


# 快速啟動本地安裝

我們使用 [撰寫器](https://getcomposer.org/) 管理Adobe Commerce和Magento Open Source元件及其相依性。 使用撰寫器來取得Adobe Commerce和Magento Open Source [元包](https://glossary.magento.com/metapackage) 提供下列優點：

- 重複使用協力廠商程式庫，而不需與原始碼整合
- 使用元件型架構及強大的相依性管理，減少擴充功能衝突和相容性問題
- 堅持 [PHP-Framework互操作性組（圖）](https://www.php-fig.org/) 標準
- 使用其他元件重新封裝Magento Open Source
- 在生產環境中使用Adobe Commerce或Magento Open Source軟體

>[!NOTE]
>
>貢獻Magento Open Source的開發人員應使用 [git型](https://developer.adobe.com/commerce/contributor/guides/install/) 安裝方法。

## 必要條件

繼續之前，您必須執行下列操作：

- 全部完成 [先決條件任務](system-requirements.md).
- [安裝撰寫器](https://getcomposer.org/download/).
- 取得 [驗證金鑰](prerequisites/authentication-keys.md) 至Adobe Commerce和Magento Open Source撰寫器存放庫。

## 以檔案系統所有者身份登錄

了解我們的 [所有權和權限概觀主題](prerequisites/file-system/overview.md).

要切換到檔案系統所有者：

1. 以具有向檔案系統寫入權限的用戶身份或切換到該用戶身份登錄到應用程式伺服器。

   如果使用bash shell，則可以使用以下語法切換到檔案系統所有者並同時輸入命令：

   ```bash
   su <file system owner> -s /bin/bash -c <command>
   ```

   如果檔案系統擁有者不允許登入，您可以執行下列操作：

   ```bash
   sudo -u <file system owner>  <command>
   ```

1. 要從任何目錄運行CLI命令，請添加 `<app_root>/bin` 系統 `PATH`.

   由於殼的語法不同，因此請查詢引用，如 [unix.stackexchange.com](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables).

   CentOS的bash shell範例：

   ```bash
   export PATH=$PATH:/var/www/html/magento2/bin
   ```

   或者，您可以以下列方式運行命令：

   - `cd <app_root>/bin` 以 `./magento <command name>`
   - `app_root>/bin/magento <command name>`
   - `<app_root>` 是Web伺服器docroot的子目錄

## 獲取元包

若要取得Adobe Commerce或Magento Open Source元加法：

1. 以 [檔案系統所有者](prerequisites/file-system/overview.md).
1. 更改為Web伺服器域目錄或配置為虛擬主機域的目錄。
1. 使用Adobe Commerce或Magento Open Source元包建立撰寫器專案。

   **Magento Open Source**

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   出現提示時，輸入您的驗證密鑰。 公開金鑰和私密金鑰是在 [Commerce Marketplace](https://marketplace.magento.com/customer/account/login/).

   如果您遇到錯誤，例如 `Could not find package...` 或 `...no matching package found`，請確定您的命令中沒有錯字。 如果您仍遇到錯誤，表示您可能未獲得下載Adobe Commerce的授權。 連絡人 [Adobe Commerce支援](https://support.magento.com/hc/en-us) 來幫忙。

   請參閱 [疑難排解](https://support.magento.com/hc/en-us/articles/360033818091) 以取得錯誤的說明。

   >[!NOTE]
   >
   >Adobe Commerce客戶可在正式發行(GA)日期前兩週存取2.4.x和2.3.x修補程式。 搶鮮版套件僅可透過撰寫器使用。 在正式發行前，您無法存取開發人員入口網站或GitHub上的搶鮮版。 如果您在撰寫器中找不到這些套件，請聯絡Adobe Commerce支援。

### 範例 — 次要版本

次要版本包含新功能、品質修正和安全性修正。 使用撰寫器來指定次要版本。 例如，若要指定Adobe Commerce 2.4.3元資料包：

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.3 <install-directory-name>
```

### 範例 — 品質修補程式

質量補丁主要包含功能 _和_ 安全性修正。 不過，它們有時也可包含新的回溯相容功能。 使用撰寫器來下載品質修補程式。 例如，若要指定Adobe Commerce 2.4.3元資料包：

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.3 <install-directory-name>
```

### 示例 — 安全補丁

安全修補程式僅包含安全修正。 它們旨在讓升級流程更快更輕鬆。

安全修補程式使用撰寫器命名慣例 `2.4.3-px`. 使用撰寫器來指定修補程式。 例如，若要下載Adobe Commerce 2.4.3-p1元資料庫：

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.3-p1 <install-directory-name>
```

## 設定檔案權限

在安裝Adobe Commerce或Magento Open Source之前，必須為Web伺服器組設定讀寫權限。 這是必需的，這樣命令行才能將檔案寫入檔案系統。

```terminal
cd /var/www/html/<magento install directory>
find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
chown -R :www-data . # Ubuntu
chmod u+x bin/magento
```

## 安裝應用程式

您必須使用命令列來安裝Adobe Commerce或Magento Open Source。

本示例假定安裝目錄為 `magento2ee`, `db-host` 在同一台電腦上(`localhost`)，以及 `db-name`, `db-user`，和 `db-password` 全部 `magento`:

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
--search-engine=elasticsearch7 \
--elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200 \
--elasticsearch-index-prefix=magento2 \
--elasticsearch-timeout=15
```

>[!TIP]
>
>您可以使用 `--backend-frontname` 選項。 不過，我們建議省略此選項，並允許安裝命令自動生成隨機URI。 隨機URI對於駭客或惡意軟體來說更難以利用。 安裝完成後，控制台中會顯示URI。

>[!TIP]
>
>有關CLI安裝選項的完整說明，請參見 [從命令行安裝應用程式](advanced.md).

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

下表匯總了可用命令。 命令僅以摘要形式顯示。 有關命令的詳細資訊，請按一下「命令」列中的連結。

| 命令 | 說明 | 必要條件 |
|--- |--- |--- |
| `magento setup:install` | 安裝應用程式 | 無 |
| `magento setup:uninstall` | 移除應用程式。 | 已安裝應用程式 |
| `magento setup:upgrade` | 更新應用程式。 | 部署配置 |
| `magento maintenance:{enable/disable}` | 啟用或停用維護模式（在維護模式中，只有豁免的IP位址可以存取管理員或店面）。 | 已安裝應用程式 |
| `magento setup:config:set` | 建立或更新部署配置。 | 無 |
| `magento module:{enable/disable}` | 啟用或禁用模組。 | 無 |
| `magento setup:store-config:set` | 設定與店面相關的選項，如基本URL、語言、時區。 | 部署配置 |
| `magento setup:db-schema:upgrade` | 更新資料庫架構。 | 部署配置 |
| `magento setup:db-data:upgrade` | 更新資料庫資料。 | 部署配置 |
| `magento setup:db:status` | 檢查資料庫是否與代碼保持最新。 | 部署配置 |
| `magento admin:user:create` | 建立管理員用戶。 | 您可以為下列項目建立使用者：<br><br>部署配置<br><br>至少啟用 `Magento_User` 和 `Magento_Authorization` 模組<br><br>資料庫(最簡單的方式是使用 `bin/magento setup:upgrade`) |
| `magento list` | 列出所有可用命令。 | 無 |
| `magento help` | 為指定的命令提供幫助。 | 無 |

### 常見引數

以下參數是所有命令的常用參數。 可以在安裝應用程式之前或之後運行以下命令：

| 長版本 | 簡短版本 | 意義 |
|--- |--- |--- |
| `--help` | `-h` | 獲取任何命令的幫助。 例如， `./magento help setup:install` 或 `./magento help setup:config:set`. |
| `--quiet` | `-q` | 安靜模式；無輸出。 |
| `--no-interaction` | `-n` | 沒有互動式問題。 |
| `--verbose=1,2,3` | `-v, -vv, -vvv` | 詳細程度。 例如， `--verbose=3` 或 `-vvv` 顯示調試詳細程度，這是最詳細的輸出。 預設為 `--verbose=1` 或 `-v`. |
| `--version` | `-V` | 顯示此應用程式版本 |
| `--ansi` | n/a | 強制ANSI輸出 |
| `--no-ansi` | n/a | 禁用ANSI輸出 |

>[!NOTE]
>
>恭喜！ 您已完成快速安裝。 需要更多高級幫助嗎？ 看看我們的 [進階安裝](advanced.md) 指南。
