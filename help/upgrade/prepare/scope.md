---
title: 瞭解升級範圍
description: 瞭解在可能影響Adobe Commerce或Magento Open Source自定義模組或第三方擴展的發行版中反向不相容的更改。
exl-id: dab2a14f-dbf0-422e-afb4-642e2220ec7a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '928'
ht-degree: 0%

---

# 瞭解升級範圍

查看 [發行說明](https://devdocs.magento.com/guides/v2.4/release-notes/bk-release-notes.html) 瞭解發行版的範圍，包括增強功能、錯誤修復以及可能影響第三方和自定義模組的已知問題。

## 向後不相容的更改

Adobe Commerce版和Magento Open Source版可能包含向後不相容的更改。 查看向後不相容的更改文檔，請參閱以下內容：

- **[主要變化重點](https://devdocs.magento.com/guides/v2.4/release-notes/backward-incompatible-changes/index.html)** — 具有重大影響並需要詳細說明和特別說明以確保第三方模組繼續工作的更改。
- **[次要更改引用](https://devdocs.magento.com/guides/v2.4/release-notes/backward-incompatible-changes/reference.html)** — 參考從代碼庫生成的文檔，該代碼庫描述對類、API成員資格、資料庫、依賴項注入、介面、佈局、系統和XSD的細微更改。

## 第三方擴展

Adobe CommerceMarketplace的新相容性政策確保 _全部_ 列出的擴展在GA日期30天內與最新發佈的版本相容。 因此，在可能的情況下通過市場獲取第三方擴展非常重要。

## 自定義模組

所有自定義模組都應根據您要升級到的目標版本進行檢查。 這是升級過程中耗費的時間和資源最多的過程。 在評估自定義模組時，必須查找向後不相容的更改，並瞭解新做法，如控制器分解。 您可以在 [發行說明](https://devdocs.magento.com/guides/v2.4/release-notes/bk-release-notes.html)。 另外，確保您正在 [最佳做法](https://developer.adobe.com/commerce/php/best-practices/extensions/) 模組開發。

## [!DNL Upgrade Compatibility Tool]

的 [!DNL Upgrade Compatibility Tool] 是一個命令行工具，用於分析實例的潛在升級問題。 它檢查您安裝的當前版本與您嘗試升級到的版本之間是否存在問題。

使用此工具可減少團隊瞭解升級的範圍和影響所需的工作量。 它有助於您避免在升級時出現常見的代碼問題，並就如何解決已發現的問題提供明確的指導。 它還有助於優先處理確保成功升級所需的最關鍵問題，從而節省升級時的時間和成本。

請參閱以下章節以開始 [!DNL Upgrade Compatibility Tool]。 查看 [!DNL Upgrade Compatibility Tool] [引導](../upgrade-compatibility-tool/overview.md) 的子菜單。

### 下載工具

使用Composer下載工具。 它需要PHP 7.3或更高版本、至少2GB的RAM、Node.js(如果您正在檢查GraphQL相容性)和Adobe Commerce許可證。

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

### 運行工具

要分析實例並檢查錯誤、警告和嚴重問題：

```bash
bin/uct upgrade:check <dir> -c <coming version> 
```

>[!NOTE]
>
> 的 `<dir>` argument是儲存代碼庫的目錄。 的 `-c` 選項將代碼庫與指定的版本進行比較。

要確定您團隊要解決的最關鍵問題：

```bash
bin/uct upgrade:check /path/to/magento/ --ignore-current-compatibility-issues –min-issue-level critical --vanilla-dir /path/to/vanilla/code/ /path/to/magento/app/code/Vendor/
```

與此命令一起使用的其他選項有：

- `--ignore-current-version-compatibility-issues` — 針對當前版本取消所有已知嚴重問題、錯誤和警告。 它僅針對您嘗試升級的版本提供錯誤。

- `--min-issue-level` — 允許您設定最小問題級別，以幫助您僅排定升級中最重要問題的優先順序。 這些選項按嚴重性的升序排列為警告、錯誤和嚴重。

- `-m | [=MODULE-PATH]` — 如果只要分析某個供應商、模組甚至目錄，也可以指定路徑作為選項。

- `--vanilla-dir` — 允許您檢查核心代碼中任何非標準實現的功能或定制。 必須事先清理。 您版本的香草實例將自動下載以供參考。

   >[!NOTE]
   >
   > 也可以使用 `core:code:changes` 的子菜單。

### 分析輸出

的 [!DNL Upgrade Compatibility Tool] 導出標識受影響代碼或模組、嚴重性以及它遇到的每個問題的問題說明的JSON檔案。 它還輸出具有複雜性分數的摘要報告，使您的團隊能夠大致瞭解升級到最新版本所需要的內容。 複雜性分數越低，執行升級就越容易。

以下輸出顯示了一個示例摘要報告：

```console
 ------------------------ --------
  Installed version        2.4.2
  Adobe Commerce version   2.4.3
  Running time             0m:48s
  Checked modules          14
  Core checked modules     0
  Core modified files      0
  % core modified files    0.00
  PHP errors found         109
  PHP warnings found       0
  GraphQL errors found     0
  GraphQL warnings found   0
  Total errors found       109
  Total warnings found     0
  Complexity score         218
 ------------------------ --------
```

### 提示和建議

工具識別的所有問題都列在報告中，並帶有特定錯誤代碼。 使用 [錯誤消息引用](../upgrade-compatibility-tool/error-messages.md) 獲取有關每個問題的詳細資訊。 Adobe還提供了修復每種問題類型的建議，以便您可以規劃修正步驟。

使用此報告可估計更新升級代碼所需的工作量。 根據您的經驗，您可以根據確定的問題總數和問題的嚴重性來估計升級所需的工作量。 由於這是命令行工具，因此您可以將此工具合併到自動測試和代碼檢查套件中，並使用JSON輸出生成報告。

我們建議保存每個升級項目的結果，以便您可以將將來的升級結果與以前的結果進行比較。 通過持續使用，您將開始充分瞭解僅從工具提供的摘要報告升級到下一個版本所需的工作量。

我們還建議您在進行升級時定期運行該工具，以便瞭解您的進度。 問題數在您修復時應減少。 這還有助於您的團隊確定分發工作的最佳方法。

的 [!DNL Upgrade Compatibility Tool] 今後的版本將繼續改進，並將包括自動修復等功能，以幫助您盡快解決問題。 2022年1月發佈的最新改進包括PHP 8.1相容性test和HTML可視化功能，這些功能可幫助您快速確定可能需要更多升級工作的領域。
