---
title: 常用命令
description: 查看常見Commerce CLI命令和用法的抽樣。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%

---


# 常用命令

下面概述了一些可用命令。

**顯示命令的完整清單**:

```bash
bin/magento list
```

幫助命令示例：

```bash
bin/magento help <command>
```

```bash
bin/magento help cache:enable
```

命令僅以摘要形式顯示；有關命令的詳細資訊，請按一下「命令」列中的連結。

| 命令 | 說明 |
|--- |--- |
| [`magento cache:{enable/disable/clean/flush/status}`](../cli/manage-cache.md) | 管理快取 |
| [`magento indexer:{status/show-mode/set-mode/reindex/info/reset/show-dimensions-mode/set-dimensions-mode}`](../cli/manage-indexers.md) | 管理索引器 |
| [`magento cron:run`](../cli/configure-cron-jobs.md) | 運行Commerce Cron作業 |
| [`magento setup:di:compile`](../cli/code-compiler.md) | 編製所有不存在的代理和工廠；和會預先編譯一個商店和網站的類別定義、繼承資訊和外掛程式定義。 |
| [`magento info:dependencies:{show-modules/show-modules-circular/show-framework}`](../cli/dependency-reports.md) | 模組相依性、循環相依性和Commerce架構相依性。 |
| [`magento i18n:{collect-phrases/pack/uninstall}`](../cli/localization.md) | 建立翻譯字典或翻譯套件 |
| [`magento setup:static-content:deploy`](../cli/static-view-file-deployment.md) | 部署靜態檢視檔案 |
| [`magento dev:source-theme:deploy`](../cli/create-symlinks.md) | 從較少建立CSS |
| [`magento dev:tests:run`](../cli/unit-tests.md) | 執行自動化測試 |
| [`magento dev:xml:convert`](../cli/convert-layout-files.md) | 更新佈局XML檔案以匹配新的可擴展樣式表語言轉換(XSLT)樣式表 |
| [`magento setup:perf:generate-fixtures`](../cli/generate-data.md) | 生成用於效能測試的資料。 |
| [`magento sampledata:install`](../../installation/sample-data/overview.md) | 安裝商務應用程式後，安裝可選的範例資料。<br><br>如需範例資料的詳細資訊，請參閱 [可選範例資料](../../installation/sample-data/overview.md). |
| [`magento config:{set/sensitive:set/show/}`](../cli/set-configuration-values.md) | 管理後端配置 |
| [`magento admin:user:{create/unlock}`](../../installation/tutorials/admin.md#create-edit-or-unloack-an-administrator-account) | 建立/編輯/解除鎖定管理員使用者。 |
| [`magento dev:template-hints:{enable/disable}`](https://developer.adobe.com/commerce/frontend-core/guide/themes/debug/) | 啟用/禁用開發人員模板提示。 |

## 常見引數

以下參數是所有命令的常用參數。 可以在安裝Commerce軟體之前或之後運行以下命令：

| 長版本 | 簡短版本 | 意義 |
|--- |--- |--- |
| `--help` | `-h` | 獲取任何命令的幫助。 例如， `./magento help setup:install` 或 `./magento help setup:config:set`. |
| `--quiet` | `-q` | 安靜模式；無輸出。 |
| `--no-interaction` | `-n` | 沒有互動式問題。 |
| `--verbose=1,2,3` | `-v, -vv, -vvv` | 詳細程度。 例如， `--verbose=3` 或 `-vvv` 顯示調試詳細程度，這是最詳細的輸出。 預設為 `--verbose=1` 或 `-v`. |
| `--version` | `-V` | 顯示此應用程式版本 |
| `--ansi` | n/a | 強制ANSI輸出 |
| `--no-ansi` | n/a | 禁用ANSI輸出 |
