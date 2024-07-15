---
title: URN熒光筆
description: 瞭解如何在IDE中設定URN醒目提示。
exl-id: 6389ab58-af70-4b33-800e-be3191c5a4cc
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---

# URN熒光筆概述

{{file-system-owner}}

Commerce程式碼會以[統一資源名稱(URN)](https://www.ietf.org/rfc/rfc2141.txt)參照所有XSD結構描述。 如果您正在開發程式碼且需要參考XSD，這個指令會設定您的整合式開發人員環境(IDE)來辨識並反白顯示URN。 如此可讓開發更容易。

依預設，類似PhpStorm的IDE未設定為識別URN，因此它們會以紅色文字顯示，如下所示：

![PhpStorm未設定為識別URN](../../assets/configuration/urn-before.png)

`bin/magento dev:urn-catalog:generate`命令可讓您的IDE （目前只有PhpStorm和Visual Studio Code）識別並反白顯示如下的URN：

![啟用IDE以辨識URN](../../assets/configuration/urn-after.png)

具體來說，這個指令會建立下列PhpStorm組態：

![PhpStorm設定範例](../../assets/configuration/urn-settings.png)

## 設定IDE

目前僅支援PhpStorm和Visual Studio Code。

命令語法：

```bash
bin/magento dev:urn-catalog:generate <path>
```

其中`<path>`是PhpStorm `misc.xml`檔案的路徑，此檔案位於專案根目錄的相對位置。 通常，`<path>`是`.idea/misc.xml`。

>[!INFO]
>
>若要讓您的「結構描述和DTD」保持最新狀態，請每次新增、修改或移除包含`*.xsd`檔案的Commerce 2模組時執行`dev:urn-catalog:generate`命令。
