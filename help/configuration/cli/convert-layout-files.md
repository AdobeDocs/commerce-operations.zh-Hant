---
title: 轉換版面檔案
description: 轉換XML佈局檔案。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---


# 轉換XML佈局檔案

{{file-system-owner}}

如果更新相應的可擴展樣式表語言轉換(XSLT)樣式表，請使用此命令更新佈局XML檔案。

- [版面指示](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-instructions/)
- [配置檔案類型](https://developer.adobe.com/commerce/frontend-core/guide/layouts/types/)

命令選項：

```bash
bin/magento dev:xml:convert [-o|--overwrite] {xml file} {xslt stylesheet}
```

其中：

- `{xml file}` — 是要轉換的佈局XML檔案的完整路徑和檔案名（必要）
- `{xslt stylesheet}` — 是要用於轉換的XSLT樣式表檔案的完整路徑和檔案名（必需）
- `-o|--overwrite` — 包含此選項以覆蓋現有的XML檔案
