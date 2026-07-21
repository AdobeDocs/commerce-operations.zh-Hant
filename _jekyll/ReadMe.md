---
source-git-commit: 90e3f9cb6033c91be67947e84520d3e2537ca5d9
workflow-type: tm+mt
source-wordcount: '358'
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
