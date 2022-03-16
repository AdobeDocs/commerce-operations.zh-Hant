---
title: 修補程式的工作方式
description: 瞭解Adobe Commerce和Magento Open Source的不同類型的修補程式以及它們的工作原理。
source-git-commit: 06ac3169a5e3813e4f50246f54f91998e14b5985
workflow-type: tm+mt
source-wordcount: '619'
ht-degree: 0%

---


# 修補程式的工作方式

>[!WARNING]
>
>我們強烈建議在部署到生產環境之前，在轉移或開發環境中測試所有修補程式。 我們還強烈建議在應用修補程式之前備份您的資料。 請參閱 [備份並回滾檔案系統](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-backup.html)。

修補（或diff）檔案是注意以下內容的文本檔案：

- 要更改的檔案。
- 開始更改的行號和要更改的行數。
- 要交換的新代碼。

當 [補丁](https://en.wikipedia.org/wiki/Patch_(Unix)) 程式運行，此檔案被讀入，並對檔案進行指定的更改。

有三種類型的修補程式：

- **修補程式**-Adobe在 [安全中心](https://magento.com/security/patches)。
- **單個修補程式**-Adobe Commerce支援根據個別情況建立和分發的修補程式。
- **自定義修補程式** — 可以從Git提交建立的非官方修補程式。

## 修補程式

修補程式是包含影響許多商家的高影響安全性或高質量修補程式的修補程式。 這些修復程式將應用於適用次版本的下一個修補程式版本。 Adobe根據需要釋放修補程式。

在 [安全中心](https://magento.com/security/patches)。 根據您的版本和安裝類型，請按照頁面上的說明下載修補程式檔案。 使用 [命令行](../patches/apply.md#) 或 [作曲家](../patches/apply.md) 應用熱修復補丁程式。

>[!NOTE]
>
>熱修復程式可能包含向後不相容的更改。

## 單個修補程式

單個修補程式包含針對特定問題的低影響質量修復。 這些修復程式應用於最近支援的次版本（例如2.4.x），但可能在以前支援的次版本（例如2.3.x）中缺失。 Adobe根據需要發佈單個修補程式。

使用 [質量修補程式工具](https://devdocs.magento.com/quality-patches/tool.html) 應用單個修補程式。

>[!NOTE]
>
>單個修補程式不包含向後不相容的更改。

## 自定義修補程式

有時，Adobe工程團隊需要一段時間才能在Adobe Commerce或Magento Open Source作曲家版本中包含在GitHub上建立的錯誤修復程式。 同時，您可以從GitHub建立修補程式，並使用 [`cweagans/composer-patches`](https://github.com/cweagans/composer-patches/) 插件，用於將其應用到基於Composer的安裝。

使用 [命令行] 或 [作曲家] 來應用自定義修補程式。

建立自定義修補程式檔案的方法有很多。 以下示例重點介紹從已知Git提交建立修補程式。

要建立自定義修補程式：

1. 建立 `patches/composer` 的子菜單。
1. 標識用於修補程式的GitHub提交或拉入請求。 此示例使用 [`2d31571`](https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede) 提交，連結到GitHub問題 [#6474](https://github.com/magento/magento2/issues/6474)。
1. 追加 `.patch` 或 `.diff` 提交URL的擴展。 使用 `.diff` 檔案大小。 例如： [https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede.diff](https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede.diff)
1. 將頁面另存為 `patches/composer` 的子菜單。 比如說， `github-issue-6474.diff`。
1. 編輯檔案並刪除 `app/code/<VENDOR>/<PACKAGE>` 從所有路徑中 `vendor/<VENDOR>/<PACKAGE>` 的子菜單。

   >[!NOTE]
   >
   >自動刪除尾隨空格或添加新行的文本編輯器可以中斷修補程式。 使用簡單的文本編輯器進行這些更改。

以下示例顯示了刪除所有實例後前面提到的DIFF檔案 `app/code/Magento/Payment`:

```diff
diff --git a/view/frontend/web/js/view/payment/iframe.js b/view/frontend/web/js/view/payment/iframe.js
index c8a6fef58d31..7d01c195791e 100644
--- a/view/frontend/web/js/view/payment/iframe.js
+++ b/view/frontend/web/js/view/payment/iframe.js
@@ -154,6 +154,7 @@ define(
              */
             clearTimeout: function () {
                 clearTimeout(this.timeoutId);
+                this.fail();
 
                 return this;
             },
```

## 應用修補程式

可以使用以下任何方法應用修補程式：

- [質量修補程式工具](https://devdocs.magento.com/quality-patches/tool.html)
- [命令行](/help/upgrade/patches/apply.md#command-line)
- [作曲家](/help/upgrade/patches/apply.md#composer)

>[!NOTE]
>
>要在雲基礎架構項目上將修補程式應用到Adobe Commerce，請參閱 [應用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) 的 _雲指南_。
