---
title: 命令列工具
description: 使用Commerce命令行工具運行安裝和配置任務。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---


# 命令列工具

Commerce有一個命令行介面(CLI)—`<magento_root>/bin/magento` — 運行安裝和配置任務，包括：

- 安裝商務（以及相關任務，如更新資料庫架構、建立部署配置）
- 清除快取
- 管理索引，包括重新索引
- 建立翻譯字典和翻譯套件
- 生成不存在的類，例如工廠和用於插件的截取器，為對象管理器生成依賴項注入配置
- 部署靜態視圖檔案
- 從更少建立CSS

其他優點包括：

- 單一命令(`<magento_root>/bin/magento list`)列出所有可用的安裝和配置命令。
- 基於Symfony的一致用戶介面。
- CLI是可擴充的，因此協力廠商開發人員可以「外掛」CLI。 這還有消除用戶學習曲線的額外好處。
- 禁用模組的命令不顯示。

本主題討論如何使用CLI配置Adobe Commerce和Magento Open Source軟體。 如需安裝Commerce的相關資訊，請參閱 [安裝流程](../../installation/overview.md) 在 _安裝指南_.

## 必要條件

開始使用CLI之前，請確保：

1. 您的系統符合 [系統需求](../../installation/system-requirements.md) 在 _安裝指南_.
1. 您已完成中討論的所有先決條件任務 [必要條件](../../installation/prerequisites/overview.md) 在 _安裝指南_.
1. 登入商務伺服器後，切換至具有寫入商務檔案系統權限的使用者。 請參閱 [切換到檔案系統所有者](../../installation/prerequisites/file-system/overview.md) 在 _安裝指南_.

## 運行命令

對於bash shell，使用以下語法切換到檔案系統所有者並同時輸入命令：

```bash
su <file system owner> -s /bin/bash -c <command>
```

如果檔案系統擁有者不允許登入，您可以使用下列項目：

```bash
sudo -u <file system owner> <command>
```

**從任何目錄運行CLI命令**:

新增 `<magento_root>/bin` 系統 `PATH`.

CentOS的bash shell範例：

```bash
export PATH=$PATH:/var/www/html/magento2/bin
```

您可以視需要執行下列作業：

- `cd <magento_root>/bin` 以 `./magento <command name>`
- `<magento_root>/bin/magento <command name>`
- `<magento_root>` 是Web伺服器docroot的子目錄
