---
title: 設定設定值
description: 瞭解如何在Adobe Commerce中設定設定值及變更鎖定的管理員值。 探索進階設定指令和技術。
exl-id: 1dc2412d-50b3-41fb-ab22-3eccbb086302
source-git-commit: 5e2d11330d3334df36ba8b3d176fbe2d8bfe0486
workflow-type: tm+mt
source-wordcount: '1116'
ht-degree: 0%

---

# 設定設定值

{{file-system-owner}}

本主題討論可用來執行下列作業的進階組態命令：

- 從命令列設定任何組態選項
- 可選擇鎖定任何設定選項，使其值無法在Admin中變更
- 變更在Admin中鎖定的設定選項

您可以使用這些命令來手動或使用指令碼設定Commerce設定。 您使用&#x200B;_組態路徑_&#x200B;設定組態選項，這是唯一識別該組態選項的`/`分隔字串。 您可在下列參照中找到組態路徑：

- [敏感和系統特定設定路徑參考](../reference/config-reference-sens.md)
- [付款設定路徑參考](../reference/config-reference-payment.md)
- [一般設定路徑參考](../reference/config-reference-general.md)
- [Commerce Enterprise B2B擴充功能設定路徑參考](../reference/config-reference-b2b.md)

您可以在下列時間設定值：

- 安裝Commerce之前，您只能為預設範圍設定設定設定值，因為這是唯一有效的範圍。

- 安裝Commerce後，您可以為任何網站或商店檢視範圍設定設定值。

使用下列命令：

- `bin/magento config:set`根據其設定路徑設定任何非敏感設定值
- `bin/magento config:sensitive:set`會依據其設定路徑設定任何敏感的設定值
- `bin/magento config:show`顯示已儲存的設定值；加密設定的值顯示為星號

## 先決條件

若要設定組態值，您必須至少知道下列其中一項：

- 設定路徑
- 若要設定特定範圍的組態值，您必須知道範圍代碼。

  若要設定預設範圍的設定值，您不需要執行任何動作。

### 尋找設定路徑

請參閱下列參考資料：

- [敏感和系統特定設定路徑參考](../reference/config-reference-sens.md)
- [付款設定路徑參考](../reference/config-reference-payment.md)
- [其他設定路徑參考](../reference/config-reference-general.md)
- [Commerce Enterprise B2B擴充功能設定路徑參考](../reference/config-reference-b2b.md)

### 尋找範圍代碼

您可以在Commerce資料庫或Commerce管理員中找到範圍代碼。

**若要在Admin**&#x200B;中尋找範圍代碼：

1. 以可檢視網站和商店檢視的使用者身分登入「管理員」。
1. 按一下「**[!UICONTROL Stores]** >設定> **[!UICONTROL All Stores]**」。
1. 在右窗格中，按一下網站或商店檢視的名稱，以檢視其程式碼。

   下圖顯示範例網站程式碼。

   ![從管理員取得網站或商店檢視代碼](../../assets/configuration/website-code.png)

1. 繼續設定[值](#set-values)。

**若要在資料庫**&#x200B;中尋找範圍代碼：

網站和存放區檢視的範圍程式碼分別儲存在`store_website`和`store`表格的Commerce資料庫中。

1. 連線至Commerce資料庫。

   ```bash
   mysql -u <Commerce database username> -p
   ```

1. 輸入下列命令：

   ```shell
   use <Commerce database name>;
   ```

   ```shell
   SELECT * FROM store;
   ```

   ```shell
   SELECT * FROM store_website;
   ```

   範例結果如下：

   ```
   [mysql]> SELECT * FROM store_website;
   +------------+-------+--------------+------------+------------------+------------+
   | website_id | code  | name         | sort_order | default_group_id | is_default |
   +------------+-------+--------------+------------+------------------+------------+
   |          0 | admin | Admin        |          0 |                0 |          0 |
   |          1 | base  | Main Website |          0 |                1 |          1 |
   |          2 | test1 | Test Website |          0 |                3 |          0 |
   +------------+-------+--------------+------------+------------------+------------+
   ```

   使用`code`欄中的值。

1. 繼續下一節。

## 設定值

**若要設定系統特定組態值**：

```bash
bin/magento config:set [--scope="..."] [--scope-code="..."] [-le | --lock-env] [-lc | --lock-config] path value
```

**若要設定敏感的組態值**：

```bash
bin/magento config:sensitive:set [--scope="..."] [--scope-code="..."] path
```

下表說明`set`命令引數：

| 引數 | 說明 |
| --- |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `--scope` | 設定的範圍。 可能的值為`default`、`website`或`store`。 預設值為`default`。 |
| `--scope-code` | 設定的範圍代碼（網站代碼或商店檢視代碼） |
| `-e or --lock-env` | 鎖定值，使其無法在管理員中編輯，或變更已在管理員中鎖定的設定。 命令會將值寫入`<Commerce base dir>/app/etc/env.php`檔案。 |
| `-c or --lock-config` | 鎖定值，使其無法在管理員中編輯，或變更已在管理員中鎖定的設定。 命令會將值寫入`<Commerce base dir>/app/etc/config.php`檔案。 如果您同時指定兩個選項，`--lock-config`選項會覆寫`--lock-env`。 |
| `path` | _必要_。 設定路徑 |
| `value` | _必要_。 設定的值。 雖然可以在CLI命令中作為個別引數傳遞，但Adobe建議您不要在原始命令中指定它。 請改為執行不含值的命令，然後在出現提示時輸入值。 使用此方法可防止將敏感的存取值寫入bash_history，這是設定組態最安全的方法。 |

>[!INFO]
>
>截至Commerce 2.2.4，`--lock-env`和`--lock-config`選項會取代`--lock`選項。 若您使用其中一個選項，值會直接寫入`app/etc/env.php`或`app/etc/config.php`檔案，且在Admin中成為唯讀。 若要將這些檔案的組態變更匯入資料庫，請執行`bin/magento app:config:import`命令，例如，在手動編輯或重新部署檔案之後。

如果您輸入的設定路徑不正確，這個命令會傳回錯誤

```text
The "wrong/config/path" does not exist
```

如需詳細資訊，請參閱下列其中一節：

- [設定可在Admin中編輯的設定值](#set-configuration-values-that-can-be-edited-in-the-admin)
- [設定無法在Admin中編輯的設定值](#set-configuration-values-that-cannot-be-edited-in-the-admin)

### 設定可在Admin中編輯的設定值

使用`bin/magento config:set` _（不含_ `--lock-env`或`--lock-config`）將值寫入資料庫。 您以這種方式設定的值可在Admin中編輯。

設定存放區基底URL的部分範例如下：

設定預設範圍的基底URL：

```bash
bin/magento config:set web/unsecure/base_url http://example.com/
```

設定`base`網站的基底URL：

```bash
bin/magento config:set --scope=websites --scope-code=base web/unsecure/base_url http://example2.com/
```

設定`test`存放區檢視的基本URL：

```bash
bin/magento config:set --scope=stores --scope-code=test web/unsecure/base_url http://example3.com/
```

### 設定無法在Admin中編輯的設定值

如果您依下列方式使用`--lock-env`選項，該命令會將組態值儲存在`<Commerce base dir>/app/etc/env.php`中，並停用Admin中用於編輯此值的欄位。

```bash
bin/magento config:set --lock-env --scope=stores --scope-code=default web/unsecure/base_url http://example3.com
```

如果未安裝Commerce，您可以使用`--lock-env`選項來設定組態值。 不過，您只能設定預設範圍的值。

>[!INFO]
>
>`env.php`檔案是系統特定的。 請勿將其傳輸到其他系統。 您可以使用它來覆寫資料庫中的組態值。 例如，您可以從另一個系統取得資料庫傾印並覆寫`base_url`和其他值，因此您不必修改資料庫。

如果您依下列方式使用`--lock-config`選項，組態值會儲存在`<Commerce base dir>/app/etc/config.php`中。 在管理員中編輯此值的欄位已停用。

```bash
bin/magento config:set --lock-config --scope=stores --scope-code=default web/url/use_store 1
```

如果未安裝Commerce，您可以使用`--lock-config`來設定組態值。 不過，您只能設定預設範圍的值。

>[!INFO]
>
>您可以將`config.php`傳輸到另一個系統，以便在該處使用相同的組態值。 例如，如果您有測試系統，使用相同的`config.php`表示您不必再次設定相同的設定值。

## 顯示組態設定的值

命令選項：

```bash
bin/magento config:show [--scope[="..."]] [--scope-code[="..."]] path
```

位置

- `--scope`是設定的範圍（預設、網站、商店）。 預設值為`default`
- `--scope-code`是設定的範圍代碼（網站代碼或商店檢視代碼）
- `path`是格式為first_part/second_part/third_part/etc (_required_)的設定路徑

>[!INFO]
>
>`bin/magento config:show`命令會將任何[加密值](../reference/config-reference-sens.md)的值顯示為一系列星號： `**&#x200B;**&#x200B;**`。

### 範例

**若要顯示所有儲存的組態**：

```bash
bin/magento config:show
```

結果：

```
web/unsecure/base_url - http://example.com/
general/region/display_all - 1
general/region/state_required - AT,BR,CA,CH,EE,ES,FI,LT,LV,RO,US
catalog/category/root_id - 2
analytics/subscription/enabled - 1
```

**若要顯示`base`網站**&#x200B;的所有已儲存設定：

```bash
bin/magento config:show --scope=websites --scope-code=base
```

結果：

```
web/unsecure/base_url - http://example-for-website.com/
general/region/state_required - AT,BR,CA
```

**若要顯示預設範圍**&#x200B;的基本URL：

```bash
bin/magento config:show web/unsecure/base_url
```

結果：

```
web/unsecure/base_url - http://example.com/
```

**若要顯示`base`網站**&#x200B;的基本URL：

```bash
bin/magento config:show --scope=websites --scope-code=base web/unsecure/base_url
```

結果：

```
web/unsecure/base_url - http://example-for-website.com/
```

**若要顯示`default`存放區**&#x200B;的基本URL：

```bash
bin/magento config:show --scope=stores --scope-code=default web/unsecure/base_url
```

結果：

```
web/unsecure/base_url - http://example-for-store.com/
```

>[!INFO]
>
>範圍代碼只能包含字母（a-z或A-Z）、數字(0-9)和底線(_)。 此外，第一個字元必須是字母。 如果在建立網站或商店檢視時使用大寫或駝峰式大小寫，則內部比對不區分大小寫，以透過環境變數來適應設定覆寫。 請參閱[使用環境變數覆寫組態設定](../reference/override-config-settings.md#environment-variables)。

