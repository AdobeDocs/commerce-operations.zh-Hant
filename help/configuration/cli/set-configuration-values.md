---
title: 設定配置值
description: 瞭解如何設定配置值和更改在管理中鎖定的值。
source-git-commit: ee2e446edf79efcd7cbbd67248f8e7ece06bfefd
workflow-type: tm+mt
source-wordcount: '985'
ht-degree: 0%

---


# 設定配置值

{{file-system-owner}}

本主題討論可用於以下操作的高級配置命令：

- 從命令行設定任何配置選項
- （可選）鎖定任何配置選項，以便在管理中無法更改其值
- 更改在管理員中鎖定的配置選項

可以使用這些命令手動或使用指令碼設定Commerce配置。 使用 _配置路徑_，這是 `/`唯一標識該配置選項的 — delimited字串。 可在以下參照中找到配置路徑：

- [敏感和特定於系統的配置路徑參考](../reference/config-reference-sens.md)
- [付款配置路徑引用](../reference/config-reference-payment.md)
- [常規配置路徑引用](../reference/config-reference-general.md)
- [Commerce Enterprise B2B擴展配置路徑參考](../reference/config-reference-b2b.md)

可以在以下時間設定值：

- 在安裝Commerce之前，您只能為預設範圍設定配置值，因為它是唯一有效的範圍。

- 安裝Commerce後，可以為任何網站或 [商店視圖](https://glossary.magento.com/store-view) 範圍。

使用以下命令：

- `bin/magento config:set` 通過配置路徑設定任何非敏感配置值
- `bin/magento config:sensitive:set` 按照配置路徑設定任何敏感配置值
- `bin/magento config:show` 顯示保存的配置值；加密設定的值顯示為星號

## 先決條件

要設定配置值，必須至少知道下列內容之一：

- 配置路徑
- 要為特定範圍設定配置值，必須知道範圍代碼。

   要為預設範圍設定配置值，無需執行任何操作。

### 查找配置路徑

請參閱以下參考：

- [敏感和特定於系統的配置路徑參考](../reference/config-reference-sens.md)
- [付款配置路徑引用](../reference/config-reference-payment.md)
- [其他配置路徑引用](../reference/config-reference-general.md)
- [Commerce Enterprise B2B擴展配置路徑參考](../reference/config-reference-b2b.md)

### 查找範圍代碼

您可以在Commerce資料庫或Commerce Admin中找到範圍代碼。

**在管理員中查找範圍代碼**:

1. 以可查看網站和儲存視圖的用戶身份登錄到管理員。
1. 按一下 **[!UICONTROL Stores]** >設定> **[!UICONTROL All Stores]**。
1. 在右窗格中，按一下網站或商店視圖的名稱以查看其代碼。

   下圖顯示了網站代碼示例。

   ![從管理員獲取網站或商店視圖代碼](../../assets/configuration/website-code.png)

1. 繼續 [設定值](#set-values)。

**在資料庫中查找作用域代碼**:

網站和儲存視圖的範圍代碼儲存在Commerce資料庫中 `store_website` 和 `store` 的下界。

1. 連接到Commerce資料庫。

   ```bash
   mysql -u <Commerce database username> -p
   ```

1. 輸入以下命令：

   ```shell
   use <Commerce database name>;
   ```

   ```shell
   SELECT * FROM store;
   ```

   ```shell
   SELECT * FROM store_website;
   ```

   示例結果如下：

   ```terminal
   [mysql]> SELECT * FROM store_website;
   +------------+-------+--------------+------------+------------------+------------+
   | website_id | code  | name         | sort_order | default_group_id | is_default |
   +------------+-------+--------------+------------+------------------+------------+
   |          0 | admin | Admin        |          0 |                0 |          0 |
   |          1 | base  | Main Website |          0 |                1 |          1 |
   |          2 | test1 | Test Website |          0 |                3 |          0 |
   +------------+-------+--------------+------------+------------------+------------+
   ```

   使用 `code` 的雙曲餘切值。

1. 繼續下一節。

## 設定值

**設定系統特定的配置值**:

```bash
bin/magento config:set [--scope="..."] [--scope-code="..."] [-le | --lock-env] [-lc | --lock-config] path value
```

**設定敏感配置值**:

```bash
bin/magento config:sensitive:set [--scope="..."] [--scope-code="..."] path value
```

下表介紹了 `set` 命令參數：

| 參數 | 說明 |
| --- | --- |
| `--scope` | 配置的範圍。 可能的值為 `default`。 `website`或 `store`。 預設值為 `default`。 |
| `--scope-code` | 配置的範圍代碼（網站代碼或儲存視圖代碼） |
| `-le or --lock-env` | 要麼鎖定該值，使其無法在管理中編輯，要麼更改已在管理中鎖定的設定。 命令將值寫入 `<Commerce base dir>/app/etc/env.php` 的子菜單。 |
| `-lc or --lock-config` | 要麼鎖定該值，使其無法在管理中編輯，要麼更改已在管理中鎖定的設定。 命令將值寫入 `<Commerce base dir>/app/etc/config.php` 的子菜單。 的 `--lock-config` 選項覆蓋 `--lock-env` 選項。 |
| `path` | _必需_。 配置路徑 |
| `value` | _必需_。 配置的值 |

>[!INFO]
>
>截至2.2.4日， `--lock-env` 和 `--lock-config` 選項替換 `--lock` 的雙曲餘切值。
>
>如果使用 `--lock-env` 或 `--lock-config` 選項來設定或更改值，必須 [`bin/magento app:config:import` 命令](../cli/import-configuration.md) 在您訪問管理或儲存前導入設定。

如果輸入的配置路徑不正確，此命令將返回錯誤

```text
The "wrong/config/path" does not exist
```

有關詳細資訊，請參閱以下部分之一：

- [設定可在管理中編輯的配置值](#set-configuration-values-that-can-be-edited-in-the-admin)
- [設定無法在管理中編輯的配置值](#set-configuration-values-that-cannot-be-edited-in-the-admin)

### 設定可在管理中編輯的配置值

使用 `bin/magento config:set` _無_ `--lock-env` 或 `--lock-config` 將值寫入資料庫。 可以在管理員中編輯以這種方式設定的值。

下面是設定儲存庫基URL的一些示例：

設定預設作用域的基URL:

```bash
bin/magento config:set web/unsecure/base_url http://example.com/
```

為 `base` 網站：

```bash
bin/magento config:set --scope=websites --scope-code=base web/unsecure/base_url http://example2.com/
```

為 `test` 儲存視圖：

```bash
bin/magento config:set --scope=stores --scope-code=test web/unsecure/base_url http://example3.com/
```

### 設定無法在管理中編輯的配置值

如果使用 `--lock-env`  選項，命令將配置值保存在 `<Commerce base dir>/app/etc/env.php` 並禁用「管理」中編輯此值的欄位。

```bash
bin/magento config:set --lock-env --scope=stores --scope-code=default web/unsecure/base_url http://example3.com
```

您可以使用 `--lock-env` 的子菜單。 但是，您只能為預設範圍設定值。

>[!INFO]
>
>的 `env.php` 檔案是系統特定的。 您不應將其轉移到其他系統。 可以使用它覆蓋資料庫中的配置值。 例如，可以從另一個系統獲取資料庫轉儲並覆蓋 `base_url` 和其他值，因此您不必修改資料庫。

如果使用 `--lock-config` 選項，配置值保存在 `<Commerce base dir>/app/etc/config.php`。 禁用了在管理中編輯此值的欄位。

```bash
bin/magento config:set --lock-config --scope=stores --scope-code=default web/url/use_store 1
```

您可以使用 `--lock-config` 設定配置值。 但是，您只能為預設範圍設定值。

>[!INFO]
>
>您可以 `config.php` 到另一個系統以使用相同的配置值。 例如，如果您有測試系統，則使用 `config.php` 意味著您不必再設定相同的配置值。

## 顯示配置設定的值

命令選項：

```bash
bin/magento config:show [--scope[="..."]] [--scope-code[="..."]] path
```

何處

- `--scope` 是配置範圍（預設、網站、商店）。 預設值為 `default`
- `--scope-code` 是配置的範圍代碼（網站代碼或儲存視圖代碼）
- `path` 格式為first_part/second_part/third_part/etc的配置路徑(_要求_)

>[!INFO]
>
>的 `bin/magento config:show` 命令顯示任何 [加密值](../reference/config-reference-sens.md) 星號： `******`。

### 示例

**顯示所有已保存的配置**:

```bash
bin/magento config:show
```

結果：

```terminal
web/unsecure/base_url - http://example.com/
general/region/display_all - 1
general/region/state_required - AT,BR,CA,CH,EE,ES,FI,LT,LV,RO,US
catalog/category/root_id - 2
analytics/subscription/enabled - 1
```

**顯示所有已保存的配置 `base` 網站**:

```bash
bin/magento config:show --scope=websites --scope-code=base
```

結果：

```terminal
web/unsecure/base_url - http://example-for-website.com/
general/region/state_required - AT,BR,CA
```

**顯示預設作用域的基URL**:

```bash
bin/magento config:show web/unsecure/base_url
```

結果：

```terminal
web/unsecure/base_url - http://example.com/
```

**顯示的基URL `base` 網站**:

```bash
bin/magento config:show --scope=websites --scope-code=base web/unsecure/base_url
```

結果：

```terminal
web/unsecure/base_url - http://example-for-website.com/
```

**顯示的基URL `default` 商店**:

```bash
bin/magento config:show --scope=stores --scope-code=default web/unsecure/base_url
```

結果：

```terminal
web/unsecure/base_url - http://example-for-store.com/
```
