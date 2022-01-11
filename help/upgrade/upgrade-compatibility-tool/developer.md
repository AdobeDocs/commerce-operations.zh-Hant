---
title: 升級相容性工具開發人員資訊
description: 使用API索引整合來自訂升級相容性工具。
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---


# 升級相容性工具開發人員資訊

本主題包含開發人員的相關資訊，這些開發人員與Adobe Commerce程式碼密切合作，並想了解升級相容性工具的詳細資訊。 您可以使用此知識來自訂工具的元件。

## Adobe Commerce API索引整合

Adobe Commerce API索引整合是內部整合解決方案，包含一組工具，可探索由Adobe、Adobe Commerce合作夥伴和第三方廠商根據靜態程式碼分析所開發的Adobe Commerce擴充功能。

與Adobe Commerce API索引的整合是透過下列方式完成：

`sut\Domain\MRay\MRayInterface`

這會透過 `config/services.yaml` 檔案。 其值會決定方法的回應位置 `api()` 和 `modules()` 來自。

編輯此檔案以根據您的安裝自訂回應。 替換分配給的值 `sut\Domain\MRay\MRayInterface`:

### 自訂值範例

`sut\Domain\MRay\MRayInterface : "@sut_mray_mock"`

在上一個示例中，升級相容性工具使用 `@sut_mray_mock` 作為 `MRayInterface` 實作。 來自 `api()` 和 `modules()` 方法來自下列檔案：

- `dev/mray_mock_files/api.json`
- `dev/mray_mock_files/modules.json`

>[!NOTE]
>
>當您變更 `services.yaml` 檔案，刪除 `var/cache/` 資料夾來正確套用變更。

## 單元測試

要運行單元測試，請執行以下命令之一：

- `vendor/bin/phpunit tests/unit`
- `vendor/bin/phpunit -c tests/unit/phpunit.xml.dist tests/unit`
- `vendor/bin/phpunit -c tests/unit/phpunit.xml.dist --testsuite=unit-tests`

## 整合測試

要運行整合測試，請執行以下命令之一：

- `vendor/bin/phpunit -c tests/integration/phpunit.xml.dist tests/integration`
- `vendor/bin/phpunit -c tests/integration/phpunit.xml.dist --testsuite=integration-tests`

## 驗收測試

1. 在執行接受測試之前，您必須在 `phpunit` 設定檔。
1. 複製預設值 `tests/acceptance/phpunit.xml` 檔案（不帶.dist尾碼）。
1. 變更 `TESTS_BASE_URL` 值，以指向您要測試的Adobe Commerce URL。
1. 要運行接受測試，請執行以下命令之一：

   - `vendor/bin/phpunit -c tests/acceptance/phpunit.xml tests/acceptance`
   - `vendor/bin/phpunit -c tests/acceptance/phpunit.xml --testsuite=acceptance-tests`

## GraphQL單元測試和ESLint代碼分析

### 需求

>[!NOTE]
>
>您的系統上必須有Node.js，請參閱 [Node.js檔案](https://nodejs.dev/learn/how-to-install-nodejs).

下列為適用於MacOS系統的指示：

1. 開啟終端機，並導覽至專案的根目錄。
1. 安裝項目依賴項：

   ```bash
   npm install
   ```

### GraphQL單元測試

此 [Jest](https://jestjs.io/docs/getting-started) framework用於建立以下JS單元測試：

測試在內 `dev/tests/Js`.

測試的字串結構位於內部 `dev/tests/Acceptance/_files/graphql_schemas`.

運行單元測試或 `jest` 如下所示：

```bash
./node_modules/.bin/jest --verbose --rootDir=dev/tests/Js/
```

### ESLint代碼分析

[ESLint](https://eslint.org/docs/user-guide/getting-started) 是一種靜態程式碼分析工具，用於識別JavaScript程式碼中發現的有問題模式，目的是讓程式碼更一致並避免錯誤。

執行 `eslint` 程式碼分析如下：

```bash
./node_modules/.bin/eslint -c dev/tests/Static/.eslintrc --rulesdir vendor/magento/magento-coding-standard/eslint/rules path/to/analyse
```

## 複雜性分數

此 **複雜性分數** 是一個圖，可指出從目前版本升級至新版本可能有多困難。 數量越少表示升級越容易。

>[!NOTE]
>
>複雜性分數介於0和∞之間。

此分數以從分析中擷取的結果為基礎：

- 已查明的問題數
- 已發現問題的嚴重性

升級相容性工具會根據以下複雜性分數公式計算此分數。

### 複雜度分數公式

`Complexity Score = (Critical issues * 3) + (Errors *2) + Warnings`

>[!WARNING]
>
>這些是絕對值。
