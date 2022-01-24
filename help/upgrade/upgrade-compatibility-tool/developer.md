---
title: '[!DNL Upgrade Compatibility Tool] 開發人員資訊'
description: 自定義 [!DNL Upgrade Compatibility Tool] 使用API索引整合。
source-git-commit: 3d9a721e33621b78f03f16b932a1ba2904ae4010
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---


# [!DNL Upgrade Compatibility Tool] 開發者資訊

本主題包含與Adobe Commerce代碼密切合作並希望瞭解有關 [!DNL Upgrade Compatibility Tool]。 您可以使用此知識定制工具的元件。

## Adobe CommerceAPI索引整合

Adobe CommerceAPI索引整合是一種內部整合解決方案，它包含一組工具，用於探索由Adobe、Adobe Commerce合作夥伴和第三方供應商基於靜態代碼分析開發的Adobe Commerce擴展。

與Adobe CommerceAPI索引的整合通過以下方式完成：

`sut\Domain\MRay\MRayInterface`

通過 `config/services.yaml` 的子菜單。 它的值決定了方法的響應位置 `api()` 和 `modules()` 來自

編輯此檔案以根據安裝自定義響應。 替換分配給 `sut\Domain\MRay\MRayInterface`:

### 自定義值的示例

`sut\Domain\MRay\MRayInterface : "@sut_mray_mock"`

在上例中， [!DNL Upgrade Compatibility Tool] 使用 `@sut_mray_mock` 的 `MRayInterface` 執行。 來自 `api()` 和 `modules()` 方法來自以下檔案：

- `dev/mray_mock_files/api.json`
- `dev/mray_mock_files/modules.json`

>[!NOTE]
>
>當您更改 `services.yaml` 檔案，刪除 `var/cache/` 資料夾以正確應用更改。

## 單元測試

要運行設備test，請執行以下命令之一：

- `vendor/bin/phpunit tests/unit`
- `vendor/bin/phpunit -c tests/unit/phpunit.xml.dist tests/unit`
- `vendor/bin/phpunit -c tests/unit/phpunit.xml.dist --testsuite=unit-tests`

## 整合測試

要運行整合test，請執行以下命令之一：

- `vendor/bin/phpunit -c tests/integration/phpunit.xml.dist tests/integration`
- `vendor/bin/phpunit -c tests/integration/phpunit.xml.dist --testsuite=integration-tests`

## 驗收測試

1. 在執行接受test之前，必須在 `phpunit` 配置檔案。
1. 複製預設 `tests/acceptance/phpunit.xml` 檔案（不帶.dist尾碼）。
1. 更改 `TESTS_BASE_URL` 值以指向要test的Adobe CommerceURL。
1. 要運行接受test，請執行以下命令之一：

   - `vendor/bin/phpunit -c tests/acceptance/phpunit.xml tests/acceptance`
   - `vendor/bin/phpunit -c tests/acceptance/phpunit.xml --testsuite=acceptance-tests`

## GraphQL單元測試與ESLint代碼分析

### 要求

>[!NOTE]
>
>必須在系統上具有Node.js，請參閱 [Node.js文檔](https://nodejs.dev/learn/how-to-install-nodejs)。

以下說明適用於MacOS系統：

1. 開啟終端並導航到項目的根目錄。
1. 安裝項目依賴項：

   ```bash
   npm install
   ```

### GraphQL單元測試

的 [耶斯特](https://jestjs.io/docs/getting-started) 框架用於建立以下JS單元test:

test在裡面 `dev/tests/Js`。

要測試的字串架構位於內部 `dev/tests/Acceptance/_files/graphql_schemas`。

運行設備test或 `jest` 如下：

```bash
./node_modules/.bin/jest --verbose --rootDir=dev/tests/Js/
```

### ESLint代碼分析

[ESLint](https://eslint.org/docs/user-guide/getting-started) 是一種靜態代碼分析工具，用於識別JavaScript代碼中發現的問題模式，目的是使代碼更一致並避免錯誤。

運行 `eslint` 代碼分析如下：

```bash
./node_modules/.bin/eslint -c dev/tests/Static/.eslintrc --rulesdir vendor/magento/magento-coding-standard/eslint/rules path/to/analyse
```

## 複雜性評分

的 **複雜度分析** 是一個圖，表示從當前版本升級到新版本可能有多難。 數字越低，升級越容易。

>[!NOTE]
>
>複雜性分值範圍在0到∞。

此分數基於從分析中提取的結果：

- 確定的問題數
- 確定問題的嚴重性

的 [!DNL Upgrade Compatibility Tool] 根據下面的複雜性得分公式計算此得分。

### 複雜度得分公式

`Complexity Score = (Critical issues * 3) + (Errors *2) + Warnings`

>[!WARNING]
>
>這些是絕對值。
