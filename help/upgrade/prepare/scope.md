---
title: 了解升級範圍
description: 了解在版本中向後不相容的變更，這些變更可能會影響Adobe Commerce、Magento Open Source自訂模組或協力廠商擴充功能。
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '916'
ht-degree: 0%

---


# 了解升級的範圍

檢閱 [發行說明](https://devdocs.magento.com/guides/v2.4/release-notes/bk-release-notes.html) 了解發行範圍，包括增強功能、錯誤修正，以及可能影響協力廠商和自訂模組的已知問題。

## 向後不相容的更改

Adobe Commerce和Magento Open Source發行可能包含不相容於回溯的變更。 請參閱我們不相容於回溯的變更檔案，請參閱下列內容：

- **[重大變更重點](https://devdocs.magento.com/guides/v2.4/release-notes/backward-incompatible-changes/index.html)** — 具有重大影響、需要詳細說明和特殊說明的更改，以確保第三方模組繼續工作。
- **[微幅變更參考](https://devdocs.magento.com/guides/v2.4/release-notes/backward-incompatible-changes/reference.html)** — 從代碼庫生成的參考文檔，該代碼庫描述對類、API成員資格、資料庫、依賴項插入、介面、佈局、系統和XSD的微幅更改。

## 協力廠商擴充功能

Adobe Commerce Marketplace的新相容性政策可確保 _all_ 列出的擴充功能與GA日期後30天內的最新發行版本相容。 因此，請務必盡可能透過Marketplace取得您的協力廠商擴充功能。

## 自訂模組

所有自訂模組都應根據您要升級的目標版本進行檢查。 這是最耗時和耗用資源的升級過程。 評估自訂模組時，您必須尋找不相容於後向的變更，並注意新作法，例如控制器分解。 您可以在 [發行說明](https://devdocs.magento.com/guides/v2.4/release-notes/bk-release-notes.html). 同時，請確定您 [最佳實務](https://devdocs.magento.com/guides/v2.4/ext-best-practices/extension-coding/common-programming-bp.html) 模組開發。

## 升級相容性工具

升級相容性工具是命令列工具，可分析您的執行個體以找出潛在的升級問題。 它會檢查您安裝的目前版本與您嘗試升級的版本之間是否有問題。

使用此工具可降低團隊了解升級範圍和影響所需的工作量。 可協助您避免升級時的常見程式碼問題，並提供解決已識別問題的明確指示。 它還有助於優先處理確保升級成功所需的最關鍵問題，在升級時既節省時間又節省成本。

請參閱以下章節，以開始使用升級相容性工具。 請參閱升級相容性工具 [指南](../upgrade-compatibility-tool/overview.md) 以取得更多技術詳細資訊和進階使用案例。

### 下載工具

使用撰寫器來下載工具。 它需要PHP 7.3或更新版本、至少2GB的RAM、Node.js（如果您正在檢查GraphQL相容性）和Adobe Commerce許可證。

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

### 執行工具

要分析實例並檢查錯誤、警告和嚴重問題：

```bash
bin/uct upgrade:check <dir> -c <coming version> 
```

>[!NOTE]
>
> 此 `<dir>` 參數是儲存代碼庫的目錄。 此 `-c` 選項會比較您的程式碼基底與指定的版本（例如2.4.4）。

要確定您的團隊要解決的最關鍵問題，請執行以下操作：

```bash
bin/uct upgrade:check /path/to/magento/ --ignore-current-compatibility-issues –min-issue-level critical --vanilla-dir /path/to/vanilla/code/ /path/to/magento/app/code/Vendor/
```

與此命令一起使用的其他選項有：

- `--ignore-current-version-compatibility-issues` — 隱藏針對當前版本的所有已知嚴重問題、錯誤和警告。 它只會針對您嘗試升級的版本提供錯誤。

- `--min-issue-level` — 可讓您設定最低問題級別，以便僅排定升級中最重要問題的優先順序。 選項是警告、錯誤和嚴重性，按嚴重性的升序排列。

- `-m | [=MODULE-PATH]` — 如果只想分析特定供應商、模組或甚至目錄，也可以指定路徑作為選項。

- `--vanilla-dir` — 可讓您檢查核心程式碼中是否有任何非標準的功能實施或自訂項目。 請務必事先清理。 系統會自動下載您版本的香草例項以供參考。

   >[!NOTE]
   >
   > 您也可以使用 `core:code:changes` 命令)。

### 分析輸出

升級相容性工具會匯出JSON檔案，識別受影響的程式碼或模組、嚴重性，以及所遇到每個問題的問題說明。 它也會輸出含有複雜度分數的摘要報表，讓您的團隊大致了解升級至最新版本所需的時間。 複雜性分數越低，執行升級就越輕鬆。

以下輸出顯示了示例摘要報告：

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

### 提示與建議

已識別工具的所有問題都會列在報表中，並附上特定的錯誤碼。 使用 [錯誤訊息參考](../upgrade-compatibility-tool/error-messages.md) 以取得每個問題的詳細資訊。 Adobe還提供修正每種問題類型的建議，以便您可以規劃修正步驟。

使用報表來預估更新升級程式碼所需的工作量。 根據您的經驗，您可以根據已識別的問題總數和問題的嚴重性，預估升級所需的工作量。 由於這是命令列工具，因此您可以將此工具併入自動測試和程式碼檢查套裝中，並使用JSON輸出產生您的報表。

建議您保存每個升級項目的結果，以便您可以將將來的升級結果與以前的結果進行比較。 透過持續使用，您將開始從工具提供的摘要報表中，充分了解升級至下一個版本所花費的心力。

我們也建議您在進行升級時定期執行工具，以便掌握您的進度。 問題數量應會隨著您修正而減少。 這也有助於您的團隊決定發佈工作的最佳方式。

該工具的未來版本將整合PHP 8.1相容性測試和自動修正，以幫助您盡快解決問題。
