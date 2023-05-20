---
title: 優化CSS和JS資源檔案
description: 瞭解如何從Admin或命令行合併和精簡Adobe Commerce項目的CSS和JavaScript(JS)檔案。
role: Developer
feature: Best Practices
feature-set: Commerce
exl-id: ff0bc407-b563-418b-9d6a-7c1dc8f235df
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# 優化資源檔案

對於響應更快的Commerce站點，請優化CSS和JavaScript(JS)資源檔案，並消除呈現阻止資源。

- **優化CSS和JS檔案** — 通過配置Adobe Commerce將單獨的檔案合併、縮小和捆綁到單個檔案中，減少載入CSS和JavaScript(JS)檔案所需的時間。
- **消除渲染阻止資源** — 考慮內聯傳遞關鍵JS和CSS功能，並推遲所有非關鍵JS/CSS樣式。 有關指導，請參見 [消除渲染阻止資源](https://web.dev/render-blocking-resources/)。

## 受影響的產品和版本

[所有支援的2.3及更高版本](../../../release/versions.md) 共：

- Adobe Commerce在雲基礎架構上
- Adobe Commerce內部
- Magento Open Source

## 合併或縮小CSS檔案

通過合併、縮小和將單獨的檔案捆綁到單個檔案中，可以縮短載入CSS和JavaScript(JS)檔案所需的時間。

>[!IMPORTANT]
>
>Adobe Commerce雲基礎架構上的雲基礎架構始終運行在生產模式下，無法進行其他設定，因此您必須使用命令行方法來啟用合併、微型化和捆綁。

### 使用管理

要啟用CSS合併或縮小，請進入 [!UICONTROL **管理** > **商店** > **設定** > **配置** > **高級** > **開發人員** > **CSS設定**]。

### 使用命令行

要在雲基礎架構上啟用Adobe Commerce的CSS合併：

1. 本地運行此命令：

   ```bash
   bin/magento config:set --lock-config dev/css/merge_css_files 1
   ```

1. 提交對 `app/etc/config.php` 檔案和重新部署。

要在雲基礎架構上啟用Adobe Commerce的CSS小型化：

1. 本地運行此命令：

   ```bash
   bin/magento config:set --lock-config dev/css/minify_files 1
   ```

1. 提交對 `app/etc/config.php` 檔案和重新部署。

## 微型JS檔案

### 使用管理

在 *管理* 邊欄，轉到 **商店** > **設定** > **配置** > **高級** > **開發人員** > **JavaScript設定**。

### 使用命令行

要在雲基礎架構上啟用Adobe Commerce的JS小型化：

1. 本地運行此命令：

   ```bash
   bin/magento config:set --lock-config dev/js/minify_files 1
   ```

1. 提交對 `app/etc/config.php` 檔案和重新部署。

## 合併和捆綁JS檔案

您可以在Commerce Admin中啟用合併或綁定（不能同時啟用合併和綁定）: [!UICONTROL **商店** > **設定** > **配置** > **高級** > **開發人員** > **JavaScript設定**]。

您還可以從命令行啟用Adobe Commerce內置綁定（基本綁定）:

```bash
php -f bin/magento config:set dev/js/enable_js_bundling 1
```

## 其他資訊

- [客戶端優化設定](../../../performance/configuration.md#client-side-optimization-settings)
- [使用手冊：優化資源檔案](https://docs.magento.com/user-guide/system/file-optimization.html)
- [前端開發人員指南：CSS合併、縮小和站點效能](https://developer.adobe.com/commerce/frontend-core/guide/css/#css-merging-minification-and-performance)
- [高級JavaScript捆綁](../../../performance/advanced-js-bundling.md)
