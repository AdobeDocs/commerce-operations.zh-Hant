---
title: 程式碼檢閱最佳實務
description: 瞭解Adobe Commerce專案開發階段的程式碼檢閱最佳實務。
feature: Best Practices
role: Developer
source-git-commit: 291c3f5ea3c58678c502d34c2baee71519a5c6dc
workflow-type: tm+mt
source-wordcount: '1168'
ht-degree: 0%

---


# Adobe Commerce的程式碼檢閱最佳作法

程式碼檢閱的主要目標是從效能、架構和安全的角度驗證實作的功能是否以最佳方式符合需求。

此外，程式碼檢閱旨在確保程式碼符合Adobe Commerce開發最佳實務、易於理解和維護，並遵循程式碼標準。 大部分的編碼標準應該由適當的工具自動檢查。

## 建議的程式碼檢閱程式

在高層面上，程式碼檢閱程式應包含下列步驟：

1. 本機開發環境上的簽出功能分支。
1. 如果從提交程式碼以供檢閱到現在已有一段時間，請合併來自目標分支（通常是QA分支）的最新變更，並將更新推送到遠端功能分支（如果有的話）。
1. 進行高階檢閱，以驗證程式碼是否實作所有需求。 如果發生重大差異，請聯絡開發人員以澄清問題。
1. 執行程式碼是選擇性的，但如果您懷疑程式碼是否如預期運作，或它有助於提高處理效率，請測試實作功能在主要使用案例中是否如預期般運作。 如果發生重大問題，請停止稽核程式，並以適當的註釋重新開啟票證。
1. 徹底檢閱以驗證程式碼是否實作所有需求。 如果有任何問題，請新增適當的註解至提取請求，然後重新開啟票證。
1. 如果一切正常，請合併提取請求(或傳遞至下一個程式碼檢閱層級（如果已建立）。

此外，在實作程式碼檢閱程式時，請考慮以下幾點：

- 程式碼檢閱是團隊內溝通和知識轉移的主要工具。 即使提取請求未包含重大問題且實作必要的商業邏輯，您仍可藉此機會在合併後提出更多改善建議。

- 平均而言，程式碼檢閱耗費的開發工作不應超過10%到20%。 也就是說，開發團隊是由一起運作良好的資深工程師所組成。 如果程式碼檢閱需要更長的時間，則可能影響專案預算和時間表。

- 識別根本原因，解決程式碼檢閱所需耗費太多精力的問題。 通常是因為需求未妥善轉換為開發票證（由於溝通問題、不良的使用者故事）或它是一個指導問題。 在第一種情況下，建議的緩解措施是確保票證有足夠的資訊供團隊成員有效率地滿足要求。 在第二個案例中，您可能需要調整團隊結構以包含更多資深工程師，或獲得外部指導與指導的核准。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 之：

- 雲端基礎結構上的Adobe Commerce
- Adobe Commerce內部部署

## 在程式碼檢閱中尋找什麼

### 樣式

執行PhpStorm檢查可自動測試樣式（請參閱下文）。

請務必設定 [PHPMD與PHPC](https://developer.adobe.com/commerce/php/best-practices/phpstorm/code-inspection/) 並執行 [編碼標準](https://github.com/magento/magento-coding-standard) 工具從CLI （也位於下方）。 有一些重疊，但也有獨特的測試。

### 慣例和結構

慣例和結構的檢閱是手動完成的。

- 類別功能是否僅限於單一責任？
- 目錄結構是否有意義？
- 功能是否可在適當層級（伺服器、使用者端、CSS、JS、資料庫、架構、基礎架構）執行。
- 版本設定是否正確？
- 程式碼看起來是否不同尋常，或像是以錯誤的方式試圖繞過問題？
- 模組名稱、封裝名稱和存放庫名稱的命名慣例是否正確套用？
- 確認全域CSS樣式已妥善套用，且不會過度使用。

### 完整性

完整性的檢閱是手動完成的。

- 程式碼可否由設定啟用或停用，以及所有必要的程式碼是否都會如預期般運作？
- 是否有票證中提及的所有設定？ 檢查範圍、資料型別、驗證、轉譯及預設值。
- 是否一律會在最低層級（商店檢視層級、網站層級或全域層級）擷取設定？ 設定擷取必須符合中範圍的定義 `system.xml` 檔案。
- 是否涵蓋技術規格流程圖中的所有路徑？ 是否涵蓋所有其他技術規格？
- 是否為新功能定義ACL？
- PhpDocs是否清晰？ 認可訊息是否清除？
- 是否有任何程式碼被註釋掉，或者您是否看到偵錯程式碼？

### 效能

效能的檢閱是手動完成的，如有疑問，程式碼執行可協助您進行。

- 查詢是否在回圈中執行？ 此回圈可以在已編輯檔案之外。
- 您能發現任何 `cachable="false"` 屬性？ 它們是否正確套用？

### 安全性

安全性檢閱是手動完成的，可透過文字搜尋加以協助。 部分安全性檢查由自動化測試處理。

- 需要時是否會記錄例外狀況？ 是否使用正確的例外型別？
- 可以 `around` 要避免外掛程式？
- 外掛程式是否傳回正確的資料型別？
- 您可以找到任何應該使用資料庫抽象層建立的原始SQL查詢嗎？
- 是否有任何新型別的資料公開給任何型別的使用者、管理員或前端？ 這是否會帶來安全性風險？
- 是否驗證使用者產生的資料？ 來自瀏覽器的所有內容都視為使用者產生，包括Cookie值和伺服器標頭。

### 隱私權與GDPR

檢閱隱私權和 [GDPR](../../../security-and-compliance/privacy/gdpr.md) 手動完成。

- 程式碼會處理客戶資料或電子郵件嗎？ 請特別注意。
- 如果這個程式碼可以在回圈中執行，它是否可以將客戶資料從一個回圈循環洩漏到另一個回圈循環？
- 風險指標包括匯入、cron工作、異動電子郵件和批次佇列處理常式。
- 請確定在回圈中隔離使用者資料。 Adobe建議使用工廠或存放庫在回圈循環中建立模型，這些模型無法在回圈外部存取。

### 指導

導師服務的檢閱是手動完成的。

- 尋找分享知識的地方，以達到教育團隊的目標。
- 如果您的評論純屬教育性質，但對達到標準來說並不重要，請指出作者並非強制必須解決此問題。
- 如果您看到一些好的東西，請告訴開發人員，特別是當他們以好的方式回應您的其中一個評論時。 程式碼檢閱通常聚焦於錯誤，但也應鼓勵和讚賞良好實務。 在指導方面，有時候告訴開發人員他們做了什麼正確比告訴他們做了什麼錯誤更有價值。

## 自動化

開發人員可以使用自動化來檢閱DI編譯、資料庫架構、撰寫器驗證以及是否符合編碼標準：

- DI編譯 — 執行下列CLI指令來檢視程式碼是否可以編譯而不會出現任何問題。

  ```bash
  bin/magento module:disable -n -q --all || exit;
  bin/magento module:enable -n -q --all || exit;
  bin/magento cache:enable -n -q || exit;
  bin/magento cache:flush -n -q || exit;
  rm -rf generated/*
  rm -rf var/view_preprocessed/*
  rm -rf pub/static/*
  rm -rf var/cache/*
  bin/magento deploy:mode:set --skip-compilation production || exit;
  bin/magento setup:di:compile -vv || exit;
  bin/magento setup:static-content:deploy en_US || exit;
  bin/magento deploy:mode:set developer || exit;
  ```

- 資料庫結構描述 `whitelist.json` — 執行下列CLI命令，並驗證 `db_schema_whitelist.json` 不會新增或變更檔案。

  ```bash
  bin/magento setup:db-declaration:generate-whitelist --module-name[=MODULE-NAME]
  ```

- Composer驗證 — 驗證 `composer.json` 在包含下列內容的目錄中執行下列CLI指令以建立檔案： `composer.json` 檔案。

  ```bash
  composer validate
  ```

- 編碼標準 — 安裝並執行「編碼標準」工具，並對您的模組執行它。 以下檔案顯示如何透過輸入 `mcs ./app/code/Vendor/Module/`.

  ```bash
  #!/usr/bin/env bash
  $HOME/web/magento/magento-coding-standard/vendor/bin/phpcs --standard=Magento2 "$@"
  ```

- Phpstan

  ```bash
  ./vendor/bin/phpstan analyze app/code/Vendor/Module
  ```

- PhpStorm檢查

- PhpStorm PHP複製/貼上偵測器
