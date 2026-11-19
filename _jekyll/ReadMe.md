---
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 63e52c8451f368e2d2a36096fc11c7ead62ee94e
workflow-type: tm+mt
source-wordcount: '704'
ht-degree: 0%
---

# 概觀

此專案使用Rake任務來自動化部分檔案工作流程。 大部分的任務會在ExL Commerce檔案存放庫之間共用，且來自[`adobe-comdox-exl-rake-tasks`](https://github.com/commerce-docs/adobe-comdox-exl-rake-tasks) gem。 以下的一些任務特定於此存放庫。

**如需常見工作（轉譯範本、管理包含、最佳化/稽核影像、產生「新增功能」摘要），請參閱[adobe-comdox-exl-rake-tasks README](https://github.com/commerce-docs/adobe-comdox-exl-rake-tasks/blob/main/README.md)。**

> 以下所有`bundle exec rake`命令都必須從`_jekyll/`目錄中執行，因為這是Gemfile和Rakefile的所在位置。

## 存放庫特定的Rake工作

### `whatsnew_bp`

在最佳實務中產生新聞摘要的資料。 預設時間範圍為自上次更新以來的時間。 您可以使用`since`引數指定不同的句號。

**使用狀況：**

```sh
bundle exec rake whatsnew_bp
```

**具有`since`引數：**

```sh
bundle exec rake whatsnew_bp since="jul 4"
```

### `whatsnew_consolidated`

將已發佈的Commerce檔案專案的新功能表格合併至`help/_includes/automated/whatsnew/consolidated.md`。

```sh
bundle exec rake whatsnew_consolidated
```

設定[`_config.yml`](_config.yml)中`whatsnew_consolidated.projects`下的專案。 每個專案都需要存放庫名稱、專案標題和絕對HTTP(S)網站URL：

```yaml
whatsnew_consolidated:
  projects:
    - repo: commerce-operations.en
      title: Adobe Commerce operational guides
      website: https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/operational-guides/home
    - repo: commerce-webapi
      title: Adobe Commerce web APIs
      website: https://developer.adobe.com/commerce/webapi/
    - repo: commerce.en
      title: Adobe Commerce
      website: https://experienceleague.adobe.com/zh-hant/docs/commerce
```

移動專案以變更節順序。 您可以從兩個平台自由地交替使用專案。 以`.en`結尾的存放庫名稱使用ExL來源路徑`help/_includes/templated/whats-new.md`。 所有其他存放庫都使用DevSite來源路徑`src/pages/_includes/templated/whats-new.md`。

任務會從`AdobeDocs` GitHub組織擷取公開`main`檔案。 它以純文字標題顯示每個專案標題，並引入每個表格和一個句子，將專案標題連結到在`website`中設定的檔案首頁，作為「新增功能」更新的來源。 它全程使用`Description | Type | Date/source`資料表標題。 僅適用於DevSite專案，逸出的`\<br/\>`標籤會變成`<br/>`。 否則，內文列、重複專案、連結和來源列順序會維持不變。 每個來源會定義自己的時段。

具有已識別的no-update訊息的專案將被忽略。 如果每個專案都沒有專案，「包含」會包含一則整體的「不更新」訊息。 設定、擷取、剖析或寫入失敗會使工作失敗，而不會取代現有的包含。

任務沒有排程產生或更新消耗頁面。

焦點測試套件包含載入`_jekyll` Rakefile並透過Bundler執行的Rake進入點測試。 請先安裝套件組合和`_jekyll`套件：

```sh
cd _jekyll && bundle install
```

然後從存放庫根目錄執行測試：

```sh
ruby _jekyll/test/consolidated_whatsnew_test.rb
```

### `whatsnew_feedback`

透過篩選現有的本機`help/_includes/automated/whatsnew/consolidated.md`包含來建立`help/_includes/automated/whatsnew/consolidated-feedback.md`。

```sh
bundle exec rake whatsnew_feedback
```

工作比對`Feedback`做為完整、逗號分隔的Type值，忽略大小寫和周圍的空格。 已包括`Feedback, technical`等組合型別。 說明、來源連結或部分型別名稱中的提及不符合條件。

相符的列、重複專案、純文字專案標題、出現時的來源句子以及專案和列順序維持不變。 沒有相符專案的專案會被忽略。 如果沒有任何相符專案，輸出會包含一個整體無回饋訊息。

輸入必須已存在。 當您要重新整理`bundle exec rake whatsnew_consolidated`時，請個別執行。 意見反應工作不會擷取遠端內容、讀取專案設定或重新產生其輸入。

遺失或格式錯誤的輸入會使工作失敗，而不會取代現有的篩選包含。 輸入檔案永遠不會被修改，而且篩選的輸出會自動發佈。

### `get_released_versions`

從`magento/magento2`存放庫取得最後10個已發行版本。 需要安裝及驗證[GitHub CLI](https://cli.github.com/)。

**使用狀況：**

```sh
bundle exec rake get_released_versions
```

**輸出：**&#x200B;產生具有發行標籤名稱和日期的`tmp/core-release.txt`。

### `first_merge_date`

取得第一次合併至指定分支的日期。 需要安裝及驗證[GitHub CLI](https://cli.github.com/)。

**使用狀況：**

```sh
bundle exec rake first_merge_date base=develop
```

**引數：**

- `base` （必要）：要檢查合併的目標分支名稱。

## 列出可用工作

若要檢視所有可用的Rake工作及其說明，請使用：

```sh
bundle exec rake --tasks
```

如需特定工作的詳細資訊，請使用：

```sh
bundle exec rake -T [task_name]
```

## 包含關係檔案格式

`include-relationships.yml`檔案追蹤主要內容檔案與其包含檔案之間的關係。 此檔案由`includes:maintain_relationships`工作自動維護（請參閱[adobe-comdox-exl-rake-tasks的README](https://github.com/commerce-docs/adobe-comdox-exl-rake-tasks/blob/main/README.md)以取得工作使用方式），它會透過讀取現有的包含檔案並尋找參照它們的主要檔案來探索關係。

**檔案結構：**

```yaml
---
metadata:
  last_updated: '2025-08-22 14:04:37'
  description: 'Index of main files and their included files for automatic timestamp updates'
  total_relationships: 57
  auto_discovered: true
  discovery_date: '2025-08-22 14:04:37'
relationships:
  configuration/deployment/example-environment-variables.md:
    - "/help/_includes/config-save-config.md"
    - "/help/_includes/config-update-build-system.md"
    - "/help/_includes/config-update-prod-system.md"
  # ... more relationships
```

**欄位：**
- `metadata.last_updated`：上次更新的時間戳記
- `metadata.total_relationships`：包含的主要檔案總數
- `metadata.auto_discovered`：表示檔案是自動產生的
- `metadata.discovery_date`：首次探索關係的日期
- `relationships`：主要檔案對應至其包含的檔案

**Include陳述式格式：**
主要內容檔案使用以下語法來包含其他檔案：

```markdown
{{$include /help/_includes/filename.md}}
```

## 先決條件

- 已安裝Ruby和Bundler。
- Gemfile中指定的必要GEM （一般工作由`adobe-comdox-exl-rake-tasks`提供；`whatsnew`工作另外需要`whatsup_github`）。
- [GitHub CLI](https://cli.github.com/)用於`get_released_versions`和`first_merge_date`工作。

## 設定

安裝必要的GEM：

```sh
bundle install
```
