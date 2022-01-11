---
title: 升級相容性工具必要條件
description: '確認您的系統符合為Adobe Commerce專案執行升級相容性工具所需的需求。 '
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---


# 升級相容性工具先決條件

運行升級相容性工具可幫助您確定必須執行的操作 **befor** 升級您的Adobe Commerce版本。

運行升級相容性工具的最低要求為：

| **需求** | **限制** |
|----------------|-----------------|
| PHP版本 | >= 7.3 |
| 撰寫器 | 無 |
| Node.js | [Node.js](https://nodejs.org/) (`^12.22.0`, `^14.17.0`，或 `>=16.0.0`) |
| 記憶體限制 | 至少2GB RAM |
| Adobe Commerce存取金鑰 | 無 |
| Adobe Commerce（開放原始碼或企業版） | 無 |

您可以在任何作業系統中運行升級相容性工具。 不需要執行Adobe Commerce執行個體所在的升級相容性工具。

升級相容性工具必須能存取Adobe Commerce執行個體的原始碼。 例如，您可以將其安裝在一台伺服器上，並將其指向另一台伺服器上的Adobe Commerce安裝。 請參閱 [安裝](../upgrade-compatibility-tool/install.md) 主題以取得詳細資訊。
