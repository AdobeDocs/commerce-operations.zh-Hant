---
title: 開發系統設定
description: 瞭解如何設定Commerce應用程式的開發系統。
exl-id: 242e9a38-2eb2-4090-8f59-3fd588f7ad3a
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
source-wordcount: '131'
ht-degree: 0%
---
# 開發系統設定

您可以擁有任意數量的開發系統，但前提是以下所有系統皆為真：

- 他們都執行Commerce 2.2或更新版本
- 所有Commerce程式碼都在與組建和生產系統相同的存放庫中進行原始檔控制
- 每個開發系統都應該使用[預設模式](../bootstrap/application-modes.md#default-mode)或[開發人員模式](../bootstrap/application-modes.md#developer-mode)
- 它已經設定檔案系統擁有權和許可權，如[您的開發、組建和生產系統的先決條件](../deployment/technical-details.md)中所述。
- 確定下列所有專案皆已從原始檔控制中排除&#x200B;_1&rbrace;：_

  - `vendor`目錄（和子目錄）
  - `generated`目錄（和子目錄）
  - `pub/static`目錄（和子目錄）
  - `app/etc/env.php`檔案

- 確定`app/etc/config.php`是&#x200B;_包含在原始檔控制中_

若您使用Git，`.gitignore`檔案會提供前述大部分內容。 檢視[`.gitignore`參考](../reference/config-reference-gitignore.md)。
