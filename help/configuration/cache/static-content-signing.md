---
title: 靜態內容快取
description: 瞭解靜態內容簽署以及如何啟用或停用此功能。
feature: Configuration, Cache, SCD
exl-id: b54ceea2-b3a1-4dbb-ba87-743f2af0d2fb
source-git-commit: d099d60bcf3c960b2e40b48c386041d8865cfb50
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# 靜態內容快取

為了改善效能，Commerce會為靜態資源(例如影像、JavaScript和CSS檔案)設定`Expires`標頭。
在靜態資源上設定`Expires`標頭，會告訴瀏覽器快取該URL上的資源，並提供快取的版本，直到它過期為止。
這是快取靜態資源的常見[最佳實務](https://developer.yahoo.com/performance/rules.html#expires=)。

當瀏覽器快取靜態資源，且該資源在伺服器上變更時，您必須清除瀏覽器快取，以便下載新版本。
如果您是網站管理員，手動清除瀏覽器快取可正常運作，但若您想要讓使用者下載靜態資源的新版本，則這不是適當的要求。

## 靜態內容簽署

靜態內容簽署是Commerce的一項功能，可讓您讓靜態資源的瀏覽器快取失效。
Commerce會將部署版本新增至靜態檔案的URL來達成此目的。

以下是以版本簽署的URL範例：

```terminal
http://magento2.com/pub/static/version1475604434/frontend/Magento/luma/en_US/images/logo.svg
```

當您執行命令[`setup:static-content:deploy`](../cli/static-view-file-deployment.md)以部署靜態內容時，Commerce會自動變更部署版本。
這會變更靜態檔案的URL，並強制瀏覽器載入檔案的新版本。

Commerce預設會啟用此功能，而Adobe建議啟用此功能，以防止瀏覽器處理舊靜態資源時出現問題。

靜態內容簽章的組態位於&#x200B;[**[!UICONTROL Stores]**>設定>組態>**[!UICONTROL Advanced]**>**[!UICONTROL Developer]**>**[!UICONTROL Static Files Settings]**](https://docs.magento.com/user-guide/system/static-file-signature.html)。

- **僅限內部部署**：如果您的網站是[生產模式](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html#production-mode)中的&#x200B;**非**，則可使用此設定。
- **雲端**：此設定已隱藏，因為生產模式是強制性的；因此，您必須使用命令列，如下所示。

![靜態檔案設定](../../assets/configuration/static-files-settings.png)

判斷狀態：

```bash
bin/magento config:show dev/static/sign
```

啟用或停用靜態內容簽署：

```bash
bin/magento config:set dev/static/sign <value>
```

其中`<value>`為1 （已啟用）或0 （已停用）。

## 版本簽章

Commerce會將版本簽章直接在靜態檢視檔案的基礎URL後附加為路徑元件，以保留靜態資源間相對URL的完整性。
這也會強制瀏覽器將相對URL解析為正確的已簽署來源，同時保持其內容與簽章值的存在/不存在無關。

當瀏覽器向伺服器請求已簽署的來源時，伺服器會使用URL重寫來從URL中移除簽名元件。

## 部署期間的使用情況

升級或修改靜態資源後，您必須執行`setup:static-content:deploy`命令以部署版本並更新靜態內容，這會強制瀏覽器載入更新的資源。

如果您將程式碼部署在單獨的伺服器上，並使用程式碼存放庫將其移至生產環境以減少停機時間，您也必須將檔案`pub/static/deployed_version.txt`新增到存放庫。
此檔案包含已部署靜態內容的新版本。
