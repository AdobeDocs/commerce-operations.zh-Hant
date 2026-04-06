---
title: 最佳化CSS和JS資源檔案
description: 瞭解如何從管理員或命令列合併Adobe Commerce專案的CSS和JavaScript (JS)檔案並加以縮制。
role: Developer
feature: Best Practices
exl-id: ff0bc407-b563-418b-9d6a-7c1dc8f235df
source-git-commit: a08560eb307638a36fdc52224c41bdf2c5d47763
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# 最佳化資源檔案

若要獲得回應速度較快的Commerce網站，請最佳化CSS和JavaScript (JS)資源檔案，並消除阻礙轉譯器的資源。

- **最佳化CSS和JS檔案** — 透過設定Adobe Commerce以精簡和組合檔案，減少載入CSS和JavaScript (JS)檔案所需的時間。
- **消除轉譯器封鎖資源** — 請考慮傳遞重要的JS和CSS功能內嵌，並延遲所有非重要的JS/CSS樣式。 如需指引，請參閱[消除轉譯器封鎖的資源](https://web.dev/render-blocking-resources/)。

## 受影響的產品和版本

[所有支援的版本，2.3和更新版本](../../../release/versions.md)：

- 雲端基礎結構上的Adobe Commerce
- Adobe Commerce內部部署

## 合併或縮制CSS檔案

將CSS和JavaScript (JS)檔案合併、縮制及繫結至單一檔案，可減少載入CSS和JS檔案的時間。

>[!IMPORTANT]
>
>雲端基礎結構上的Adobe Commerce一律會在生產模式中執行，否則無法進行設定，因此您必須使用命令列方法來啟用合併、縮制和整合。

如果您的部署使用HTTP/2，請勿合併或合併檔案。 HTTP/2會以非同步方式下載靜態檔案。 瀏覽器必須先下載整個合併的檔案，才能處理檔案內容。

### 使用Admin

若要啟用CSS合併或縮制，請前往「**[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL CSS Settings]**」。

### 使用命令列

若要在雲端基礎結構的Adobe Commerce中啟用CSS合併功能：

1. 在本機執行此命令：

   ```bash
   bin/magento config:set --lock-config dev/css/merge_css_files 1
   ```

1. 認可對`app/etc/config.php`檔案的變更並重新部署。

若要在雲端基礎結構上的Adobe Commerce中啟用CSS縮制：

1. 在本機執行此命令：

   ```bash
   bin/magento config:set --lock-config dev/css/minify_files 1
   ```

1. 認可對`app/etc/config.php`檔案的變更並重新部署。

## 縮制JS檔案

### 使用[!UICONTROL Admin]

在[!UICONTROL Admin]側邊欄上，前往&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL JavaScript Settings]**。

### 使用命令列

若要在雲端基礎結構上的Adobe Commerce中啟用JS縮制：

1. 在本機執行此命令：

   ```bash
   bin/magento config:set --lock-config dev/js/minify_files 1
   ```

1. 認可對`app/etc/config.php`檔案的變更並重新部署。

## 捆綁JS檔案

您可以在Commerce [!UICONTROL Admin]中啟用組合： **[!UICONTROL Stores]** > ***[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL JavaScript Settings]**。

>[!NOTE]
>
>無法同時啟用合併和整合。

您也可以從命令列啟用Adobe Commerce內建套件組合（基本套件組合）：

```bash
php -f bin/magento config:set dev/js/enable_js_bundling 1
```

## 合併JS檔案（不建議） {#merge-js-files}

>[!WARNING]
>
>我們不建議啟用&#x200B;**[!UICONTROL Merge JavaScript Files]**。 此設定僅針對頁面的&#x200B;**[!UICONTROL HEAD]**&#x200B;區段中同步載入的JavaScript而設計，可能會導致套件組合和[!DNL RequireJS]邏輯無法正確運作。 其保留目的僅在於回溯相容性，啟用HTTP/2時無法提供效能優勢。
>
>如果您已啟用&#x200B;**[!UICONTROL Merge JavaScript Files]**&#x200B;且遇到問題，請嘗試在套用任何修補程式之前先停用它。 如果無法停用合併，請參閱[ACSD-67908](../../../tools/quality-patches-tool/patches-available-in-qpt/v1-1-73/acsd-67908.md)。

## 其他資訊

- [使用者端最佳化設定](../../../performance/configuration.md#client-side-optimization-settings)
- 在[組態最佳實務](../../../performance/configuration.md#bundling-tips)中的&#x200B;*套件組合提示* — 協力廠商套件組合工具、HTTP/2以及已棄用的JS和CSS合併指南
- [使用手冊：最佳化資源檔](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/developer-tools#optimizing-resource-files)
- [前端開發人員指南： CSS合併、縮制和網站效能](https://developer.adobe.com/commerce/frontend-core/guide/css/#css-merging-minification-and-performance)
- [進階JavaScript套件組合](../../../performance/advanced-js-bundling.md)
