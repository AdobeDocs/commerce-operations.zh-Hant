---
title: 轉換佈局檔案
description: 轉換XML佈局檔案。
exl-id: 9852b735-9b4b-43ce-887f-5c37d398bbf7
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---

# 轉換XML佈局檔案

{{file-system-owner}}

如果更新相應的可擴展樣式表語言轉換(XSLT)樣式表，則使用此命令更新佈局XML檔案。

- [佈局說明](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-instructions/)
- [佈局檔案類型](https://developer.adobe.com/commerce/frontend-core/guide/layouts/types/)

命令選項：

```bash
bin/magento dev:xml:convert [-o|--overwrite] {xml file} {xslt stylesheet}
```

位置：

- `{xml file}` — 是要轉換的佈局XML檔案的完整路徑和檔案名（必需）
- `{xslt stylesheet}` — 是要用於轉換的XSLT樣式表檔案的完整路徑和檔案名（必需）
- `-o|--overwrite` — 包含此選項以覆蓋現有XML檔案
