---
title: 建立指向LESS檔案的符號連結
description: 瞭解如何為Adobe Commerce開發建立LESS檔案的符號連結。 探索樣式表連結和開發工作流程最佳化。
exl-id: 58a6123a-28b4-445b-b3f9-f524233ac127
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 0%

---

# 建立指向LESS檔案的符號連結

{{file-system-owner}}

若要建立LESS檔案的符號連結：

命令選項：

```bash
bin/magento dev:source-theme:deploy [--type="..."] [--locale="..."] [--area="..."] [--theme="..."] [file1] ... [fileN]
```

>[!INFO]
>
>在開發期間，這個命令會為`var/view_preprocessed`和`pub/static`資料夾中的LESS檔案建立符號連結。 此程式不會將LESS檔案編譯成CSS檔案。

下表說明此命令的引數和值。

| 引數 | 值 | 必填？ |
| --------- | ----- | --------- |
| `--type` | 來源檔案型別： [less] （預設值： &quot;less&quot;）<br>目前，僅支援LESS檔案型別。 | 否 |
| `--locale` | 地區代碼。<br>若要顯示地區設定代碼清單，請輸入`bin/magento info:language:list` | 否 |
| `--area` | 區域（`adminhtml`代表管理區域，`frontend`代錶店面）。 | 否 |
| `--theme` | `<VendorName>/<theme-name>`格式的主題名稱。 例如，`Magento/blank`或`Magento/backend`。 | 否 |
| `<file>` | 要轉換成LESS而沒有CSS副檔名的CSS檔案清單（以空格分隔）。 （adminhtml型別`css/styles-m css/styles-l`的預設值為`css/styles css/styles-old`） | 否 |

例如，若要使用名為`VendorName/themeName`的CSS檔案，在`en_US`地區設定中為名為`<magento_root>/pub/static/frontend/VendorName/themeName/en_US/css/styles-l.css`的前端主題建立LESS檔案，請輸入下列命令：

```bash
bin/magento dev:source-theme:deploy --type="less" --locale="en_US" --area="frontend" --theme="VendorName/themeName" css/styles-l
```

下列訊息會顯示以確認成功：

```
Processed Area: frontend, Locale: en_US, Theme: VendorName/themeName, File type: less.
-> css/styles-l.less
Successfully processed.
```

若要為管理員建立LESS檔案：

```bash
bin/magento dev:source-theme:deploy --locale="en_US" --area="adminhtml" --theme="Magento/backend" css/styles css/styles-old
```
