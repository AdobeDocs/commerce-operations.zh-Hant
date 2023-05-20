---
title: 建立指向LESS檔案的符號連結
description: 瞭解如何建立指向LESS檔案的符號連結。
exl-id: 58a6123a-28b4-445b-b3f9-f524233ac127
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---

# 建立指向LESS檔案的符號連結

{{file-system-owner}}

要建立指向LESS檔案的符號連結：

命令選項：

```bash
bin/magento dev:source-theme:deploy [--type="..."] [--locale="..."] [--area="..."] [--theme="..."] [file1] ... [fileN]
```

>[!INFO]
>
>在開發過程中，此命令將為 `var/view_preprocessed` 和 `pub/static` 資料夾。 此過程不將LESS檔案編譯為CSS檔案。

下表說明了此命令的參數和值。

| 參數 | 值 | 需要？ |
| --------- | ----- | --------- |
| `--type` | 源檔案類型： [少] （預設值）「減」)<br>目前，LESS是唯一支援的檔案類型。 | 否 |
| `--locale` | 區域設定代碼。<br>要顯示區域設定代碼清單，請輸入 `bin/magento info:language:list` | 否 |
| `--area` | 區域(`adminhtml` 行政區， `frontend` 店面)。 | 否 |
| `--theme` | 主題名稱 `<VendorName>/<theme-name>` 的子菜單。 比如說， `Magento/blank` 或 `Magento/backend`。 | 否 |
| `<file>` | CSS檔案的空格分隔清單，該清單將轉換為LESS，而不帶CSS副檔名。 (預設值為 `css/styles-m css/styles-l`，用於adminhtml類型 `css/styles css/styles-old`) | 否 |

例如，為名為的前端主題建立LESS檔案 `VendorName/themeName` 的 `en_US` 使用名為的CSS檔案的區域設定 `<magento_root>/pub/static/frontend/VendorName/themeName/en_US/css/styles-l.css`，輸入以下命令：

```bash
bin/magento dev:source-theme:deploy --type="less" --locale="en_US" --area="frontend" --theme="VendorName/themeName" css/styles-l
```

顯示以下消息以確認成功：

```terminal
Processed Area: frontend, Locale: en_US, Theme: VendorName/themeName, File type: less.
-> css/styles-l.less
Successfully processed.
```

要為adminhtml建立LESS檔案，請執行以下操作：

```bash
bin/magento dev:source-theme:deploy --locale="en_US" --area="adminhtml" --theme="Magento/backend" css/styles css/styles-old
```
