---
title: 轉換版面檔案
description: 瞭解如何使用Adobe Commerce命令列工具轉換XML配置檔案。 探索XSLT樣式表更新和檔案轉換程式。
exl-id: 9852b735-9b4b-43ce-887f-5c37d398bbf7
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 0%
---
# 轉換XML配置檔案

{{file-system-owner}}

如果您更新對應的可延伸樣式表語言轉換(XSLT)樣式表，請使用此指令來更新版面XML檔案。

- [配置指示](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-instructions)
- [配置檔案型別](https://developer.adobe.com/commerce/frontend-core/guide/layouts/#layout-files-types-and-conventions)

命令選項：

```shell
bin/magento dev:xml:convert [-o|--overwrite] {xml file} {xslt stylesheet}
```

其中：

- `{xml file}` — 是要轉換的配置XML檔案的完整路徑和檔案名稱（必要）
- `{xslt stylesheet}` — 是用於轉換的XSLT樣式表檔案的完整路徑和檔案名稱（必要）
- `-o|--overwrite` — 包含此選項以覆寫現有的XML檔案
