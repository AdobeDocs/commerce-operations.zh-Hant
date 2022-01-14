---
title: 修補程式如何工作
description: 了解Adobe Commerce和Magento Open Source的不同類型修補程式及其工作方式。
source-git-commit: 38b054bbae8ba116557ce367c8397c646c837558
workflow-type: tm+mt
source-wordcount: '619'
ht-degree: 0%

---


# 修補程式如何運作

>[!WARNING]
>
>我們強烈建議先在測試環境或開發環境中測試所有修補程式，然後再部署到生產環境。 我們還強烈建議您在應用修補程式之前備份資料。 請參閱 [備份並回滾檔案系統](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-backup.html).

修補程式（或diff）檔案是注意以下內容的文本檔案：

- 要變更的檔案。
- 要開始更改的行號和要更改的行數。
- 要交換的新代碼。

當 [修補程式](https://en.wikipedia.org/wiki/Patch_(Unix)) 程式運行，此檔案被讀入，並對檔案進行指定的更改。

有三種類型的修補程式：

- **Hotfix**-Adobe在 [安全中心](https://magento.com/security/patches).
- **個別修補程式**-Adobe Commerce支援按個別方式建立和分發的修補程式。
- **自定義修補程式** — 可從Git提交建立的非官方修補程式。

## Hotfix

Hotfix是修補程式，包含影響許多商家的高影響安全性或品質修正。 這些修正會套用至適用次要版本的下一個修補程式版本。 Adobe會視需要發行Hotfix。

您可以在 [安全中心](https://magento.com/security/patches). 根據您的版本和安裝類型，按照頁面上的說明下載修補程式檔案。 使用 [命令行](../patches/apply.md#) 或 [撰寫器](../patches/apply.md) 應用修補程式。

>[!NOTE]
>
>Hotfix可包含不相容的後向變更。

## 個別修補程式

單個修補程式包含針對特定問題的低影響質量修正。 這些修正會套用至最近支援的次要版本（例如2.4.x），但可能會從先前支援的次要版本（例如2.3.x）中遺失。 Adobe會視需要發行個別修補程式。

使用 [質量修補工具](https://devdocs.magento.com/quality-patches/tool.html) 應用單個修補程式。

>[!NOTE]
>
>單個修補程式不包含向後不相容的更改。

## 自定義修補程式

有時候，Adobe工程團隊需要一段時間，才能在Adobe Commerce或Magento Open Source撰寫器版本中納入GitHub上所做的錯誤修正。 同時，您也可以從GitHub建立修補程式，並使用 [`cweagans/composer-patches`](https://github.com/cweagans/composer-patches/) 外掛程式來將其套用至您以撰寫器為基礎的安裝。

使用 [命令行] 或 [撰寫器] 應用自定義修補程式。

建立自定義修補程式檔案的方法有很多。 以下範例著重於從已知的git提交建立修補程式。

要建立自定義修補程式：

1. 建立 `patches/composer` 目錄。
1. 識別用於修補程式的GitHub提交或提取請求。 此範例使用 [`2d31571`](https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede) 提交，連結至GitHub問題 [#6474](https://github.com/magento/magento2/issues/6474).
1. 附加 `.patch` 或 `.diff` 擴充功能。 使用 `.diff` 檔案大小較小時，才會使用此工具。 例如： [https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede.diff](https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede.diff)
1. 將頁面儲存為 `patches/composer` 目錄。 例如， `github-issue-6474.diff`.
1. 編輯檔案並移除 `app/code/<VENDOR>/<PACKAGE>` 以便它們相對於 `vendor/<VENDOR>/<PACKAGE>` 目錄。

   >[!NOTE]
   >
   >自動移除尾端空白字元或新增行的文字編輯器可能會中斷修補程式。 使用簡單的文字編輯器進行這些變更。

以下示例顯示了在刪除的所有實例後前面提到的DIFF檔案 `app/code/Magento/Payment`:

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

- [質量修補工具](https://devdocs.magento.com/quality-patches/tool.html)
- [命令列](../patches/apply.md#command-line)
- [撰寫器](../patches/apply.md#composer)

>[!NOTE]
>
>若要在雲端基礎架構專案上將修補程式套用至Adobe Commerce，請參閱 [應用修補程式](https://devdocs.magento.com/cloud/project/project-patch.html) 在 _雲端指南_.
