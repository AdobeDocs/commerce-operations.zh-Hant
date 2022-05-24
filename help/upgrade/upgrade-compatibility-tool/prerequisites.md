---
title: '"[!DNL Upgrade Compatibility Tool] 先決條件"'
description: '驗證您的系統是否滿足運行 [!DNL Upgrade Compatibility Tool] 你的Adobe Commerce計畫。 '
source-git-commit: 5ff08d231269ea0bcb69f8c80aa546b171a5e4a0
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---


# [!DNL Upgrade Compatibility Tool] 先決條件

{{commerce-only}}

運行 [!DNL Upgrade Compatibility Tool] 為：

| **要求** | **約束** |
|----------------|-----------------|
| PHP版本 | >= 7.3 |
| 作曲家 | 無 |
| Node.js | [節點.js](https://nodejs.org/) (`^12.22.0`。 `^14.17.0`或 `>=16.0.0`) |
| 記憶體限制 | 至少2GB RAM |
| Adobe Commerce訪問密鑰 | 無 |
| Adobe Commerce | 無 |

您可以運行 [!DNL Upgrade Compatibility Tool] 在多個作業系統中（不支援Windows）。 你不用 [!DNL Upgrade Compatibility Tool] 你的Adobe Commerce實例所在的位置。

對於 [!DNL Upgrade Compatibility Tool] 訪問Adobe Commerce實例的原始碼。 例如，您可以將其安裝在一台伺服器上，然後將其指向另一台伺服器上的Adobe Commerce安裝。 請參閱 [安裝](../upgrade-compatibility-tool/install.md) 的子菜單。

如果您運行 [!DNL Upgrade Compatibility Tool] 對於具有大模組和檔案的Adobe Commerce實例，該工具可能需要大量RAM（至少2GB）。 您可以使用 `[=MODULE-PATH]` 命令中的選項，用於指定模組路徑目錄以避免因記憶體不足而出現的問題：

```bash
bin/uct upgrade:check <dir> -m[=MODULE-PATH]
```

其中參數如下：

- `<dir>`:Adobe Commerce安裝目錄。
- `[=MODULE-PATH]`:特定模組路徑目錄。
