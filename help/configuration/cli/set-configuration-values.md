---
title: 設定配置值
description: 了解如何設定設定值及變更「管理員」中鎖定的值。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 設定配置值

{{file-system-owner}}

本主題討論了可用於以下操作的高級配置命令：

- 從命令行設定任何配置選項
- （可選）鎖定任何設定選項，使其值無法在管理員中變更
- 變更在「管理員」中鎖定的設定選項

您可以使用這些命令手動或使用指令碼來設定商務配置。 您可使用 _配置路徑_，此 `/`可唯一識別該設定選項的 — delimited字串。 您可以在下列參考中找到設定路徑：

- [敏感和系統特定配置路徑參考](../reference/config-reference-sens.md)
- [付款配置路徑參考](../reference/config-reference-payment.md)
- [一般配置路徑參考](../reference/config-reference-general.md)
- [商務企業B2B擴充功能組態路徑參考](../reference/config-reference-b2b.md)

您可以在下列時間設定值：

- 在安裝商務之前，您只能為預設範圍設定配置值，因為它是唯一的有效範圍。

- 安裝商務後，您可以為任何網站或商店檢視範圍設定設定值。

使用下列命令：

- `bin/magento config:set` 按配置路徑設定任何非敏感配置值
- `bin/magento config:sensitive:set` 通過配置路徑設定敏感配置值
- `bin/magento config:show` 顯示保存的配置值；加密設定的值以星號顯示

## 必要條件

若要設定設定值，您至少必須知道下列其中一項：

- 配置路徑
- 要為特定範圍設定配置值，必須知道範圍代碼。

   要設定預設作用域的配置值，您不需要執行任何操作。

### 查找配置路徑

請參閱下列參考資料：

- [敏感和系統特定配置路徑參考](../reference/config-reference-sens.md)
- [付款配置路徑參考](../reference/config-reference-payment.md)
- [其他設定路徑參考](../reference/config-reference-general.md)
- [商務企業B2B擴充功能組態路徑參考](../reference/config-reference-b2b.md)

### 查找範圍代碼

您可以在商務資料庫或商務管理員中找到範圍代碼。

**在管理員中查找範圍代碼**:

1. 以可檢視網站和儲存檢視的使用者身分登入管理員。
1. 按一下 **[!UICONTROL Stores]** >設定> **[!UICONTROL All Stores]**.
1. 在右窗格中，按一下網站名稱或商店檢視以查看其程式碼。

   下圖顯示網站程式碼範例。

   ![從管理員取得網站或商店檢視代碼](../../assets/configuration/website-code.png)

1. 繼續 [設定值](#set-values).

**在資料庫中查找範圍代碼**:

網站和儲存檢視的範圍代碼會儲存在 `store_website` 和 `store` 表格。

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

   在 `code` 欄。

1. 繼續下一節。

## 設定值

**設定系統特定配置值**:

```bash
bin/magento config:set [--scope="..."] [--scope-code="..."] [-le | --lock-env] [-lc | --lock-config] path value
```

**設定敏感配置值**:

```bash
bin/magento config:sensitive:set [--scope="..."] [--scope-code="..."] path value
```

下表說明 `set` 命令參數：

| 參數 | 說明 |
| --- | --- |
| `--scope` | 配置的範圍。 可能的值包括 `default`, `website`，或 `store`. 預設為 `default`. |
| `--scope-code` | 設定的範圍代碼（網站代碼或商店查看代碼） |
| `-e or --lock-env` | 鎖定值，使其無法在「管理員」中編輯，或變更已在「管理員」中鎖定的設定。 命令會將值寫入 `<Commerce base dir>/app/etc/env.php` 檔案。 |
| `-c or --lock-config` | 鎖定值，使其無法在「管理員」中編輯，或變更已在「管理員」中鎖定的設定。 命令會將值寫入 `<Commerce base dir>/app/etc/config.php` 檔案。 此 `--lock-config` 選項覆寫 `--lock-env` 如果指定兩個選項。 |
| `path` | _必填_. 配置路徑 |
| `value` | _必填_. 設定的值 |

>[!INFO]
>
>自Commerce 2.2.4起， `--lock-env` 和 `--lock-config` 選項會取代 `--lock` 選項。
>
>如果您使用 `--lock-env` 或 `--lock-config` 選項來設定或變更值，您必須使用 [`bin/magento app:config:import` 命令](../cli/import-configuration.md) 先匯入設定，再存取「管理員」或「店面」。

如果輸入錯誤的配置路徑，此命令將返回錯誤

```text
The "wrong/config/path" does not exist
```

如需詳細資訊，請參閱下列其中一節：

- [設定可在「管理員」中編輯的設定值](#set-configuration-values-that-can-be-edited-in-the-admin)
- [設定無法在管理員中編輯的設定值](#set-configuration-values-that-cannot-be-edited-in-the-admin)

### 設定可在「管理員」中編輯的設定值

使用 `bin/magento config:set` _無_ `--lock-env` 或 `--lock-config` 將值寫入資料庫。 您可以在「管理員」中編輯以此方式設定的值。

以下是設定商店基礎URL的一些範例：

設定預設範圍的基礎URL:

```bash
bin/magento config:set web/unsecure/base_url http://example.com/
```

設定 `base` 網站：

```bash
bin/magento config:set --scope=websites --scope-code=base web/unsecure/base_url http://example2.com/
```

設定 `test` 商店檢視：

```bash
bin/magento config:set --scope=stores --scope-code=test web/unsecure/base_url http://example3.com/
```

### 設定無法在管理員中編輯的設定值

如果您使用 `--lock-env`  選項，命令會將配置值保存在 `<Commerce base dir>/app/etc/env.php` 和會停用「管理員」中用於編輯此值的欄位。

```bash
bin/magento config:set --lock-env --scope=stores --scope-code=default web/unsecure/base_url http://example3.com
```

您可以使用 `--lock-env` 選項，以在未安裝Commerce時設定設定值。 但是，您只能為預設範圍設定值。

>[!INFO]
>
>此 `env.php` 檔案是系統特定的。 您不應將其轉移至其他系統。 您可以使用它來覆寫資料庫中的配置值。 例如，您可以從另一個系統取用資料庫傾印並覆寫 `base_url` 和其他值，因此您不必修改資料庫。

如果您使用 `--lock-config` 選項，設定值會儲存於 `<Commerce base dir>/app/etc/config.php`. 「管理員」中用於編輯此值的欄位已停用。

```bash
bin/magento config:set --lock-config --scope=stores --scope-code=default web/url/use_store 1
```

您可以使用 `--lock-config` 設定配置值（如果未安裝Commerce）。 但是，您只能為預設範圍設定值。

>[!INFO]
>
>您可以轉移 `config.php` 到另一個系統，使用相同的配置值。 例如，如果您有測試系統，則使用相同的 `config.php` 表示您不必再設定相同的設定值。

## 顯示配置設定的值

命令選項：

```bash
bin/magento config:show [--scope[="..."]] [--scope-code[="..."]] path
```

where

- `--scope` 是設定範圍（預設、網站、商店）。 預設值為 `default`
- `--scope-code` 是設定的範圍代碼（網站代碼或商店檢視代碼）
- `path` 是格式為first_part/second_part/third_part/etc的配置路徑(_必填_)

>[!INFO]
>
>此 `bin/magento config:show` 命令顯示任何 [加密值](../reference/config-reference-sens.md) 星號： `******`.

### 範例

**顯示所有保存的配置**:

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

**顯示 `base` 網站**:

```bash
bin/magento config:show --scope=websites --scope-code=base
```

結果：

```terminal
web/unsecure/base_url - http://example-for-website.com/
general/region/state_required - AT,BR,CA
```

**顯示預設範圍的基URL**:

```bash
bin/magento config:show web/unsecure/base_url
```

結果：

```terminal
web/unsecure/base_url - http://example.com/
```

**顯示 `base` 網站**:

```bash
bin/magento config:show --scope=websites --scope-code=base web/unsecure/base_url
```

結果：

```terminal
web/unsecure/base_url - http://example-for-website.com/
```

**顯示 `default` 商店**:

```bash
bin/magento config:show --scope=stores --scope-code=default web/unsecure/base_url
```

結果：

```terminal
web/unsecure/base_url - http://example-for-store.com/
```
