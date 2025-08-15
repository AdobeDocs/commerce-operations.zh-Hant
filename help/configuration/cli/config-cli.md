---
title: 命令列工具
description: 使用Commerce命令列工具執行安裝和設定工作。
exl-id: 44470ce1-a5a2-4c12-962e-e42d11a6bd15
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 0%

---

# 命令列工具

Commerce有一個命令列介面(CLI) — `<magento_root>/bin/magento` — 可執行安裝和設定工作，包括：

- 安裝Commerce （以及更新資料庫架構、建立部署設定等相關工作）
- 清除快取
- 管理索引，包括重新索引
- 建立翻譯字典和翻譯套件
- 為外掛程式產生不存在的類別（例如處理站和攔截器），為物件管理員產生相依性插入組態
- 部署靜態檢視檔案
- 從更少資源建立CSS

其他優點包括：

- 單一命令(`<magento_root>/bin/magento list`)列出所有可用的安裝和組態命令。
- 以Symfony為基礎的一致使用者介面。
- CLI可擴充，因此協力廠商開發人員可以「插入」至其中。 這還有消除使用者學習曲線的額外好處。
- 已停用模組的命令不顯示。

本主題說明如何使用CLI設定Adobe Commerce軟體。 如需有關安裝Commerce的資訊，請參閱[安裝指南](../../installation/overview.md)中的&#x200B;_安裝流程_。

## 先決條件

開始使用CLI之前，請確定：

1. 您的系統符合[安裝指南](../../installation/system-requirements.md)中的&#x200B;_系統需求_&#x200B;所討論的需求。
1. 您已完成[安裝指南](../../installation/prerequisites/overview.md)中&#x200B;_先決條件_&#x200B;中討論的所有先決條件工作。
1. 登入Commerce伺服器後，請切換為有權寫入Commerce檔案系統的使用者。 請參閱[安裝指南](../../installation/prerequisites/file-system/overview.md)中的&#x200B;_切換到檔案系統擁有者_。

## 正在執行命令

對於bash shell，請使用下列語法切換到檔案系統擁有者並同時輸入指令：

```bash
su <file system owner> -s /bin/bash -c <command>
```

如果檔案系統擁有者不允許登入，您可以使用下列專案：

```bash
sudo -u <file system owner> <command>
```

**若要從任何目錄執行CLI命令**：

新增`<magento_root>/bin`至您的系統`PATH`。

CentOS的bash shell範例：

```bash
export PATH=$PATH:/var/www/html/magento2/bin
```

您可以選擇執行下列動作：

- `cd <magento_root>/bin`並以`./magento <command name>`身分執行
- `<magento_root>/bin/magento <command name>`
- `<magento_root>`是網頁伺服器docroot的子目錄
