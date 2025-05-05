---
title: 修補程式的運作方式
description: 瞭解Adobe Commerce的各種修補程式型別及其運作方式。
exl-id: d7072ed4-7d51-41fe-881a-aae3b2000b55
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# 修補程式的運作方式

>[!WARNING]
>
>我們強烈建議先在中繼或開發環境中測試所有修補程式，然後再部署到生產環境。 我們也強烈建議您在套用修補程式前先備份資料。 請參閱[備份並復原檔案系統](../../installation/tutorials/backup.md)。

修補程式（或差異）檔案是文字檔，註明：

- 要變更的檔案。
- 要開始變更的行號以及要變更的行數。
- 要交換的新程式碼。

執行修補程式時，會讀取此檔案，並對檔案進行指定的變更。

有三種型別的修補程式：

- **修補程式**—Adobe在[安全中心](https://magento.com/security/patches)發佈的修補程式。
- **個別的修補程式**—Adobe Commerce支援以個別為基礎建立和分發的修補程式。
- **自訂修補程式** — 您可以從Git認可建立的非正式修補程式。

## Hotfix

Hotfix是包含高影響力安全性或品質修正（會影響到許多商家）的修補程式。 這些修正會套用至適用次要版本的下一個修補程式發行版本。 Adobe會視需要發行hotfix。

您可以在[安全中心](https://magento.com/security/patches)找到Hotfix。 根據您的版本和安裝型別，依照頁面上的指示下載修補程式檔案。 使用[命令列](../patches/apply.md#)或[撰寫器](../patches/apply.md)套用Hot Fix修補程式。

>[!NOTE]
>
>Hot Fix可能包含回溯不相容的變更。

## 個別修補程式

個別修補程式包含特定問題的低影響品質修正。 這些修正會套用至最近支援的次要版本（例如2.4.x），但可能從先前支援的次要版本（例如2.3.x）中遺失。 Adobe會視需要發行個別修補程式。

使用[[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant){target="_blank"}套用個別修補程式。

>[!NOTE]
>
>個別修補程式不包含回溯不相容的變更。

## 自訂修補程式

有時Adobe工程團隊需要一點時間，才能在Adobe Commerce Composer版本中加入GitHub上的錯誤修正。 同時，您可以從GitHub建立修補程式，並使用[`cweagans/composer-patches`](https://github.com/cweagans/composer-patches/)外掛程式將其套用至您的Composer式安裝。

使用[命令列](apply.md#command-line)或[撰寫器](apply.md#composer)套用自訂修補程式。

建立自訂修補檔的方法有很多種。 下列範例著重於從已知的Git認可建立修補程式。

若要建立自訂修補程式：

1. 在本機專案中建立`patches/composer`目錄。
1. 識別要用於修補程式的GitHub認可或提取請求。 此範例使用[`2d31571`](https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede)認可，連結至GitHub問題[#6474](https://github.com/magento/magento2/issues/6474)。
1. 將`.patch`或`.diff`副檔名附加至認可URL。 使用`.diff`以縮小檔案大小。 例如： [https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede.diff](https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede.diff)
1. 將頁面儲存為`patches/composer`目錄中的檔案。 例如，`github-issue-6474.diff`。
1. 編輯檔案並從所有路徑中移除`app/code/<VENDOR>/<PACKAGE>`，使其相對於`vendor/<VENDOR>/<PACKAGE>`目錄。

   >[!NOTE]
   >
   >自動移除尾端空白字元或新增行的文字編輯器可能會破壞修補程式。 使用簡單的文字編輯器即可進行這些變更。

下列範例顯示移除`app/code/Magento/Payment`的所有執行個體之後，先前提及的DIFF檔案：

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

## 套用修補程式

您可以使用下列任一方法來套用修補程式：

- [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant){target="_blank"}
- [命令列](/help/upgrade/patches/apply.md#command-line)
- [作曲者](/help/upgrade/patches/apply.md#composer)

>[!NOTE]
>
>若要將修補程式套用至雲端基礎結構專案上的Adobe Commerce，請參閱&#x200B;_雲端上的Commerce指南_&#x200B;中的[套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。
