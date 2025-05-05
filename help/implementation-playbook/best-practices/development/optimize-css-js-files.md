---
title: 最佳化CSS和JS資源檔案
description: 瞭解如何從管理員或命令列合併Adobe Commerce專案的CSS和JavaScript (JS)檔案並加以縮制。
role: Developer
feature: Best Practices
exl-id: ff0bc407-b563-418b-9d6a-7c1dc8f235df
source-git-commit: 79c8a15fb9686dd26d73805e9d0fd18bb987770d
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# 最佳化資源檔案

若要獲得回應速度較快的Commerce網站，請最佳化CSS和JavaScript (JS)資源檔案，並消除阻礙轉譯器的資源。

- **最佳化CSS與JS檔案** — 透過設定Adobe Commerce將個別檔案合併、縮制及繫結至單一檔案，減少載入CSS與JavaScript (JS)檔案所需的時間。
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

若要啟用CSS合併或縮制，請移至&#x200B;[!UICONTROL **管理員** > **存放區** > **設定** > **設定** > **進階** > **開發人員** > **CSS設定**]。

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

### 使用Admin

在&#x200B;*管理員*&#x200B;側邊欄上，移至&#x200B;**商店** > **設定** > **設定** > **進階** > **開發人員** > **JavaScript設定**。

### 使用命令列

若要在雲端基礎結構上的Adobe Commerce中啟用JS縮制：

1. 在本機執行此命令：

   ```bash
   bin/magento config:set --lock-config dev/js/minify_files 1
   ```

1. 認可對`app/etc/config.php`檔案的變更並重新部署。

## 合併及捆綁JS檔案

您可以在Commerce Admin中開啟合併或整合（合併和整合無法同時啟用）： [!UICONTROL **存放區** > **設定** > **設定** > **進階** > **開發人員** > **JavaScript設定**]。

您也可以從命令列啟用Adobe Commerce內建套件組合（基本套件組合）：

```bash
php -f bin/magento config:set dev/js/enable_js_bundling 1
```

## 其他資訊

- [使用者端最佳化設定](../../../performance/configuration.md#client-side-optimization-settings)
- [使用手冊：最佳化資源檔](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/systems/tools/developer-tools#optimizing-resource-files)
- [前端開發人員指南： CSS合併、縮制和網站效能](https://developer.adobe.com/commerce/frontend-core/guide/css/#css-merging-minification-and-performance)
- [進階JavaScript套件組合](../../../performance/advanced-js-bundling.md)
