---
title: 轉換佈局檔案
description: 轉換XML佈局檔案。
source-git-commit: 02f02393878d04b4a0fcdae256ac1ac5dd13b7f6
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---


# 轉換XML佈局檔案

{{file-system-owner}}

如果更新相應的可擴展樣式表語言轉換(XSLT)樣式表，則使用此命令更新佈局XML檔案。

- [佈局說明](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/layouts/xml-instructions.html)
- [佈局檔案類型](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/layouts/layout-types.html)

命令選項：

```bash
bin/magento dev:xml:convert [-o|--overwrite] {xml file} {xslt stylesheet}
```

位置：

- `{xml file}` — 是要轉換的佈局XML檔案的完整路徑和檔案名（必需）
- `{xslt stylesheet}` — 是要用於轉換的XSLT樣式表檔案的完整路徑和檔案名（必需）
- `-o|--overwrite` — 包含此選項以覆蓋現有XML檔案
