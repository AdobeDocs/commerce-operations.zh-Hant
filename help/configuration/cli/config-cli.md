---
title: 命令行工具
description: 使用Commerce命令行工具運行安裝和配置任務。
source-git-commit: c65c065c5f9ac2847caa8898535afdacf089006a
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---


# 命令行工具

Commerce有一個命令行介面(CLI)—`<magento_root>/bin/magento` — 運行安裝和配置任務，包括：

- 安裝Commerce（以及相關任務，如更新資料庫架構、建立部署配置）
- 清除快取
- 管理索引，包括重新索引
- 建立翻譯詞典和翻譯包
- 生成不存在的類，如工廠和插件的截取器，為對象管理器生成依賴項注入配置
- 部署靜態視圖檔案
- 從較少建立CSS

其他好處包括：

- 單個命令(`<magento_root>/bin/magento list`)列出所有可用的安裝和配置命令。
- 基於Symfony的一致用戶介面。
- CLI是可擴展的，因此第三方開發人員可以「插入」它。 這具有消除用戶學習曲線的額外好處。
- 不顯示禁用模組的命令。

本主題討論使用CLI配置Adobe Commerce和Magento Open Source軟體。 有關安裝Commerce的資訊，請參見 [安裝流](https://devdocs.magento.com/guides/v2.4/install-gde/install-flow-diagram.html) 的 _安裝指南_。

## 先決條件

在開始使用CLI之前，請確保：

1. 您的系統符合中討論的要求 [系統要求](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html) 的 _安裝指南_。
1. 您已完成中討論的所有先決條件任務 [先決條件](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/prereq-overview.html) 的 _安裝指南_。
1. 登錄到Commerce伺服器後，切換到有權寫入Commerce檔案系統的用戶。 請參閱 [切換到檔案系統所有者](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html) 的 _安裝指南_。

## 運行命令

對於bash shell，使用以下語法切換到檔案系統所有者並同時輸入命令：

```bash
su <file system owner> -s /bin/bash -c <command>
```

如果檔案系統所有者不允許登錄，則可以使用以下命令：

```bash
sudo -u <file system owner> <command>
```

**從任何目錄運行CLI命令**:

添加 `<magento_root>/bin` 到系統 `PATH`。

CentOS的bash shell示例：

```bash
export PATH=$PATH:/var/www/html/magento2/bin
```

（可選）您可以運行以下程式：

- `cd <magento_root>/bin` 把它們 `./magento <command name>`
- `<magento_root>/bin/magento <command name>`
- `<magento_root>` 是Web伺服器docroot的子目錄
