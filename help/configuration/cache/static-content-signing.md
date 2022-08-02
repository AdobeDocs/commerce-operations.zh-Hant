---
title: 靜態內容快取
description: 瞭解靜態內容簽名以及如何啟用或禁用該功能。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# 靜態內容快取

要提高效能，Commerce將 `Expires` 靜態資源（如影像、JavaScript和CSS檔案）的標頭。
設定 `Expires` 靜態資源上的標題指示瀏覽器在該URL上快取資源，並在快取版本過期之前提供服務。
這是常見的 [最佳實踐](https://developer.yahoo.com/performance/rules.html#expires=) 用於快取靜態資源。

當瀏覽器快取靜態資源並且該資源在伺服器上發生更改時，必須清除瀏覽器快取，以便它可以下載新版本。
如果您是 [網站](https://glossary.magento.com/website) 管理員，但當您希望用戶下載靜態資源的新版本時，這不是對用戶發出的適當請求。

## 靜態內容簽名

[靜態內容](https://glossary.magento.com/static-content) 簽名是一種Commerce功能，允許您使靜態資源的瀏覽器快取失效。
Commerce通過向URL添加部署版本來實現此目的 [靜態檔案](https://glossary.magento.com/static-files)。

以下是使用版本簽名的URL的示例：

```terminal
http://magento2.com/pub/static/version1475604434/frontend/Magento/luma/en_US/images/logo.svg
```

運行命令時 [`setup:static-content:deploy`](../cli/static-view-file-deployment.md) 要部署靜態內容，Commerce會自動更改部署版本。
這將更改靜態檔案的URL，並強制瀏覽器載入新版本的檔案。

預設情況下，Commerce啟用此功能，而Adobe建議保持此功能的啟用，以防止與瀏覽器服務舊靜態資源相關的問題。

您可以在 [**[!UICONTROL Stores]**>設定>配置>**[!UICONTROL Advanced]**>**[!UICONTROL Developer]**>**[!UICONTROL Static Files Settings]**](https://docs.magento.com/user-guide/system/static-file-signature.html)。

![靜態檔案設定](../../assets/configuration/static-files-settings.png)

確定狀態：

```bash
bin/magento config:show dev/static/sign
```

啟用或禁用靜態內容簽名：

```bash
bin/magento config:set dev/static/sign <value>
```

位置 `<value>` 為1（已啟用）或0（已禁用）。

## 版本簽名

Commerce將版本簽名作為路徑元件直接附加在靜態視圖檔案的基本URL之後，以保留靜態資源中相對URL的完整性。
這還會強制瀏覽器解析指向正確簽名源的相對URL，同時保持其內容與簽名值的存在/不存在無關。

當瀏覽器從伺服器請求籤名源時，伺服器使用URL重寫將簽名元件從URL中刪除。

## 部署期間的使用情況

升級或修改靜態資源後，必須運行 `setup:static-content:deploy` 命令以部署版本和更新靜態內容，這將強制瀏覽器載入更新的資源。

如果在單獨的伺服器上部署代碼並使用代碼儲存庫將其移動到生產環境中以減少停機時間，則還必須添加該檔案 `pub/static/deployed_version.txt` 到儲存庫。
此檔案包含已部署靜態內容的新版本。
