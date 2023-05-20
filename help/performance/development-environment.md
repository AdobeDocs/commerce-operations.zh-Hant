---
title: 發展環境Recommendations
description: 瞭解有關設定本地Adobe Commerce或Magento Open Source開發環境的效能建議。
exl-id: f57396c0-86be-4933-8066-eb51c42fb9e4
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---

# 發展環境建議

本頁為Commerce開發環境提供了建議。

## 清除快取，而不是禁用

許多開發人員傾向於禁用其開發人員實例上的所有快取。 我們建議只清除快取，而不禁用所有快取。 [!DNL Commerce] 在 [清除快取](../configuration/cli/manage-cache.md#clean-and-flush-cache-types) 而不是徹底使它們失去功能。 大多數快取類型在開發過程中很少無效。

如果 [禁用快取](../configuration/cli/manage-cache.md#enable-or-disable-cache-types)，建議在開發實例中僅禁用頁快取和塊快取。 切記在測試期間啟用所有快取。

## 在開發模式中要避免的命令

在開發模式下，不要運行編譯、代碼生成和靜態內容部署的命令。 這些命令僅用於生產模式。

**不運行** 開發模式下的生產命令：

* `setup:di:compile` 生成自動生成的類和優化的配置快取。

   ```bash
   bin/magento setup:di:compile
   ```

   在開發模式中，Magento按需生成；你不用跑。 如果修改了類的簽名，並且需要重新生成其自動生成的簽名 `factories/proxies/interceptors`，刪除這些類或 _生成_ 的子菜單。

* `setup:static-content:deploy` 部署儲存的靜態內容。

   ```bash
   bin/magento setup:static-content:deploy
   ```

   在開發模式中，Magento按需完成；你不用跑。

## 虛擬機上的正常頁面載入時間

如果在VM上開發並且載入Magento頁需要超過2秒，請查看環境設定。
