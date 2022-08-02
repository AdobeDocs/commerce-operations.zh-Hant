---
title: URN螢光筆
description: 瞭解如何在IDE中設定URN突出顯示。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---


# URN螢光筆概述

{{file-system-owner}}

商務代碼將所有XSD架構引用為 [統一資源名稱(URN)](https://www.ietf.org/rfc/rfc2141.txt)。 如果您正在開發代碼並需要引用XSD，則此命令將整合開發環境(IDE)配置為識別並突出顯示URN。 這使發展更容易。

預設情況下，PhpStorm等IDE未配置為識別URN，因此它們以紅色文本顯示，如下所示：

![PhpStorm未配置為識別URN](../../assets/configuration/urn-before.png)

的 `bin/magento dev:urn-catalog:generate` 命令允許IDE（當前僅PhpStorm和Visual Studio代碼）識別並突出顯示URN，如下所示：

![啟用IDE以識別URN](../../assets/configuration/urn-after.png)

具體而言，此命令將建立以下PhpStorm配置：

![PhpStorm配置示例](../../assets/configuration/urn-settings.png)

## 配置IDE

目前僅支援PhpStorm和Visual Studio代碼。

命令語法：

```bash
bin/magento dev:urn-catalog:generate <path>
```

位置 `<path>` 是通往PhpStorm的路徑 `misc.xml` 檔案，它相對於項目根目錄位置。 通常， `<path>` 是 `.idea/misc.xml`。

>[!INFO]
>
>要使「架構和DTD」保持最新，請運行 `dev:urn-catalog:generate` 命令，每次添加、修改或刪除包含 `*.xsd` 的子菜單。
