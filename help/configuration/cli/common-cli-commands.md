---
title: 常用命令
description: 查看常用Commerce CLI命令和用法的示例。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---


# 常用命令

下面總結了一些可用命令。

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
| [`magento cron:run`](../cli/configure-cron-jobs.md) | 運行Commerce cron作業 |
| [`magento setup:di:compile`](../cli/code-compiler.md) | 編譯所有不存在的代理和工廠；預編譯一個儲存和網站的類定義、繼承資訊和插件定義。 |
| [`magento info:dependencies:{show-modules/show-modules-circular/show-framework}`](../cli/dependency-reports.md) | 模組依賴項、循環依賴項和Commerce框架依賴項。 |
| [`magento i18n:{collect-phrases/pack/uninstall}`](../cli/localization.md) | 建立翻譯字典或翻譯包 |
| [`magento setup:static-content:deploy`](../cli/static-view-file-deployment.md) | 部署靜態視圖檔案 |
| [`magento dev:source-theme:deploy`](../cli/create-symlinks.md) | 從LESS建立CSS |
| [`magento dev:tests:run`](../cli/unit-tests.md) | 運行自動test |
| [`magento dev:xml:convert`](../cli/convert-layout-files.md) | 更新佈局XML檔案以匹配新的可擴展樣式表語言轉換(XSLT)樣式表 |
| [`magento setup:perf:generate-fixtures`](../cli/generate-data.md) | 生成用於效能測試的資料。 |
| [`magento sampledata:install`](https://devdocs.magento.com/guides/v2.4/install-gde/install/sample-data.html) | 在安裝Commerce應用程式後安裝可選示例資料。<br><br>有關示例資料的詳細資訊，請參見 [可選示例資料](https://devdocs.magento.com/guides/v2.4/install-gde/install/sample-data.html)。 |
| [`magento config:{set/sensitive:set/show/}`](../cli/set-configuration-values.md) | 管理後端配置 |
| [`magento admin:user:{create/unlock}`](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-admin.html) | 建立/編輯/解鎖管理員用戶。 |
| [`magento dev:template-hints:{enable/disable}`](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/themes/debug-theme.html) | 啟用/禁用開發人員模板提示。 |

## 常見參數

以下參數是所有命令的通用參數。 在安裝Commerce軟體之前或之後可以運行以下命令：

| 長版本 | 短版本 | 意義 |
|--- |--- |--- |
| `--help` | `-h` | 獲取任何命令的幫助。 比如說， `./magento help setup:install` 或 `./magento help setup:config:set`。 |
| `--quiet` | `-q` | 安靜模式；沒有輸出。 |
| `--no-interaction` | `-n` | 沒有互動問題。 |
| `--verbose=1,2,3` | `-v, -vv, -vvv` | 詳細級別。 比如說， `--verbose=3` 或 `-vvv` 顯示debug verbosity ，這是最詳細的輸出。 預設值為 `--verbose=1` 或 `-v`。 |
| `--version` | `-V` | 顯示此應用程式版本 |
| `--ansi` | n/a | 強制ANSI輸出 |
| `--no-ansi` | n/a | 禁用ANSI輸出 |
