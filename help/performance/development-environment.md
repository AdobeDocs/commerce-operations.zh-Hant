---
title: 開發環境Recommendations
description: 了解設定本機Adobe Commerce或Magento Open Source開發環境的效能建議。
source-git-commit: 2e1a06b59fda7db4a9b32d000e1b2a3ca88926d3
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---


# 開發環境建議

本頁面提供商務開發環境的建議。

## 清除快取，而非停用

許多開發人員傾向於停用其開發人員執行個體上的所有快取。 建議僅清除快取，不禁用所有快取。 [!DNL Commerce] 在 [清除快取](../configuration/cli/manage-cache.md#clean-and-flush-cache-types) 而不是完全禁用它們。 大部分快取類型在開發期間很少失效。

若您 [禁用快取](../configuration/cli/manage-cache.md#enable-or-disable-cache-types)，我們建議僅停用開發例項中的頁面和區塊快取。 請記得在測試期間啟用所有快取。

## 在開發模式中避免的命令

在開發模式中，不運行編譯、代碼生成和靜態內容部署的命令。 這些命令的建立僅用於生產模式。

**不運行** 在開發模式下生產命令：

* `setup:di:compile` 生成自動生成的類和優化的配置快取。

   ```bash
   bin/magento setup:di:compile
   ```

   在開發模式下，Magento按需進行生成；您不需要運行它。 如果修改了類的簽名，並且需要重新生成其自動生成的 `factories/proxies/interceptors`，移除這些類別或 _產生_ 檔案夾。

* `setup:static-content:deploy` 為商店部署靜態內容。

   ```bash
   bin/magento setup:static-content:deploy
   ```

   在開發模式下，Magento按需執行；您不需要運行它。

## 虛擬機上的正常頁面載入時間

如果您在VM上開發，並且載入Magento頁面所花費的時間超過2秒，請查看您的環境設定。
