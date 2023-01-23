---
title: 最佳化CSS和JS資源檔案
description: 了解如何從管理員或命令列，合併及縮制Adobe Commerce專案的CSS和JavaScript(JS)檔案。
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: e6e8a2d7ef059265dbcbfcd6be117828a639f6d6
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# 最佳化資源檔案

對於回應速度更快的商務網站，請最佳化CSS和JavaScript(JS)資源檔案，並消除轉譯封鎖資源。

- **最佳化CSS和JS檔案** — 將Adobe Commerce設定為將個別檔案合併、縮制和捆綁為單一檔案，以縮短載入CSS和JavaScript(JS)檔案所需的時間。
- **消除渲染阻止資源** — 考慮內嵌傳遞重要的JS和CSS功能，並延遲所有非關鍵的JS/CSS樣式。 如需指引，請參閱 [消除渲染阻止資源](https://web.dev/render-blocking-resources/).

## 受影響的產品和版本

[所有支援的2.3版和更新版本](../../../release/versions.md) 共：

- Adobe Commerce雲基礎架構
- Adobe Commerce內部
- Magento Open Source

## 合併或縮小CSS檔案

將個別檔案合併、縮制及整合為單一檔案，可縮短載入CSS和JavaScript(JS)檔案所需的時間。

>[!IMPORTANT]
>
>雲端基礎架構上的Adobe Commerce一律會在「生產」模式中執行，若不是，則無法加以設定，因此您必須使用命令列方法來啟用合併、縮制和捆綁。

### 使用管理

若要啟用CSS合併或縮制，請前往 [!UICONTROL **管理** > **商店** > **設定** > **設定** > **進階** > **開發人員** > **CSS設定**].

### 使用命令列

若要在雲端基礎架構上於Adobe Commerce中啟用CSS合併：

1. 在本地運行此命令：

   ```bash
   bin/magento config:set --lock-config dev/css/merge_css_files 1
   ```

1. 將更改提交到 `app/etc/config.php` 檔案和重新部署。

若要在雲端基礎架構上在Adobe Commerce中啟用CSS縮制：

1. 在本地運行此命令：

   ```bash
   bin/magento config:set --lock-config dev/css/minify_files 1
   ```

1. 將更改提交到 `app/etc/config.php` 檔案和重新部署。

## 縮小JS檔案

### 使用管理

在 *管理* 邊欄，轉到 **商店** > **設定** > **設定** > **進階** > **開發人員** > **JavaScript設定**.

### 使用命令列

若要在雲端基礎架構上於Adobe Commerce中啟用JS縮制：

1. 在本地運行此命令：

   ```bash
   bin/magento config:set --lock-config dev/js/minify_files 1
   ```

1. 將更改提交到 `app/etc/config.php` 檔案和重新部署。

## 合併和捆綁JS檔案

您可以在商務管理員中開啟合併或捆綁（合併和捆綁不能同時啟用）: [!UICONTROL **商店** > **設定** > **設定** > **進階** > **開發人員** > **JavaScript設定**].

您也可以從命令列啟用Adobe Commerce內建捆綁（基本捆綁）:

```bash
php -f bin/magento config:set dev/js/enable_js_bundling 1
```

## 其他資訊

- [用戶端最佳化設定](../../../performance/configuration.md#client-side-optimization-settings)
- [使用手冊：最佳化資源檔案](https://docs.magento.com/user-guide/system/file-optimization.html)
- [前端開發人員指南：CSS合併、縮制和網站效能](https://developer.adobe.com/commerce/frontend-core/guide/css/#css-merging-minification-and-performance)
- [進階JavaScript捆綁](../../../performance/advanced-js-bundling.md)

