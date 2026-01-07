---
source-git-commit: 4589c405bab743001e967a9825d578ee1a03c216
workflow-type: tm+mt
source-wordcount: '672'
ht-degree: 0%

---
# 概觀

此專案包含數個Rake工作，以自動化工作流程的各個層面，例如產生新聞摘要的資料、演算範本化檔案、最佳化影像及產生地圖。 以下是Rakefile中定義的每個Rake工作的說明和使用准則。

## Rake任務

### `render`

轉譯`_jekyll/templates`目錄中包含`_jekyll/_data/`資料的樣板化檔案。 結果可在`help/includes/templated`目錄中找到。 此任務在呈現後自動維護包含關係和時間戳記。

**使用狀況：**

```sh
rake render
```

**它的功能：**
- 執行轉譯器指令碼以產生樣板化檔案
- 執行`includes:maintain_all`以更新包含關係和時間戳記
- 確保呈現後所有包含中繼資料都是最新的

### `image_optim`

最佳化修改後未認可檔案中的影像。 對於其他影像，請使用`path`引數來指定目錄或檔案。

**使用狀況：**

```sh
rake image_optim
```

**具有`path`引數：**

```sh
rake image_optim path=../path/to/dir/or/file
```

### `whatsnew`

產生新聞摘要的資料。 預設時間範圍為自上次更新以來的時間。 您可以使用`since`引數指定不同的句號。

**使用狀況：**

```sh
rake whatsnew
```

**具有`since`引數：**

```sh
rake whatsnew since="jul 4"
```

### `whatsnew_bp`

在最佳實務中產生新聞摘要的資料。 預設時間範圍為自上次更新以來的時間。 您可以使用`since`引數指定不同的句號。

**使用狀況：**

```sh
rake whatsnew_bp
```

**具有`since`引數：**

```sh
rake whatsnew_bp since="jul 4"
```

### `azure_regions`

產生Azure區域地圖。 輸入資料檔案應置於`_jekyll/tmp/azure-regions.json`中。 將在`_jekyll/tmp/azure-regions.svg`中找到結果。 請注意，您必須安裝Python、[PyGMT](https://www.pygmt.org/latest/install.html)和[pdf2svg](https://formulae.brew.sh/formula/pdf2svg)。

**使用狀況：**

```sh
rake azure_regions
```

### `get_released_versions`

從`magento/magento2`存放庫取得最後10個已發行版本。 需要安裝及驗證[GitHub CLI](https://cli.github.com/)。

**使用狀況：**

```sh
rake get_released_versions
```

**輸出：**&#x200B;產生具有發行標籤名稱和日期的`tmp/core-release.txt`。

### `first_merge_date`

取得第一次合併至指定分支的日期。 需要安裝及驗證[GitHub CLI](https://cli.github.com/)。

**使用狀況：**

```sh
rake first_merge_date base=develop
```

**引數：**

- `base` （必要）：要檢查合併的目標分支名稱。

### `includes:maintain_relationships`

使用模式`include-relationships.yml`掃描`help`目錄中的所有Markdown檔案以尋找包含陳述式，以探索並更新`{{$include /help/_includes/filename.md}}`檔案。 此工作會自動維護主要內容檔案與其包含檔案之間的關係。

**使用狀況：**

```sh
rake includes:maintain_relationships
```

**它的功能：**
- 從`help/_includes`目錄讀取現有的包含檔案清單
- 搜尋所有主要Markdown檔案，找出參照各檔案的檔案
- 使用`{{$include /help/_includes/filename.md}}`模式來識別參考
- 以探索到的關係更新`include-relationships.yml`檔案
- 提供所做變更的摘要，並識別未參考的專案，包括

### `includes:maintain_timestamps`

將最新的包含檔案變更時間戳記新增至主要檔案，以維護包含時間戳記。 此工作會讀取`include-relationships.yml`檔案、檢查每個包含檔案的Git歷程記錄，以及在主要檔案結尾新增或更新時間戳記。

**使用狀況：**

```sh
rake includes:maintain_timestamps
```

**它的功能：**
- 載入包含來自`include-relationships.yml`的關係
- 對於每個主要檔案，在其包含檔案中尋找最新的Git認可日期
- 在主檔案結尾以時間戳記新增或更新HTML註解
- 使用格式： `<!-- Last updated from includes: YYYY-MM-DD HH:MM:SS -->`
- 提供詳細輸出，顯示已檢查哪些包含檔案及其時間戳記

**範例輸出：**

```console
Processing installation/advanced.md...
  Latest include change: 2024-04-16 09:42:31
  Include files checked: help/_includes/cli-consumers.md (2022-09-12 09:38:25), help/_includes/secure-install.md (2022-09-08 11:33:05), help/_includes/sensitive-data.md (2024-04-16 09:42:31)
  Added new timestamp
```

### `includes:maintain_all`

同時依序執行`includes:maintain_relationships`和`includes:maintain_timestamps`的便利工作。 這是維護包含關係和時間戳記的建議方法。

**使用狀況：**

```sh
rake includes:maintain_all
```

### `unused_includes`

在`help/_includes`目錄中尋找未由任何Markdown檔案參考的包含檔案。 這有助於識別可安全移除的孤立包含檔案。

**使用狀況：**

```sh
rake unused_includes
```

## 列出可用工作

若要檢視所有可用的Rake工作及其說明，請使用：

```sh
rake --tasks
```

如需特定工作的詳細資訊，請使用：

```sh
rake -T [task_name]
```

## 包含管理任務

所有與包含相關的任務都會在`includes`名稱空間下組織，以便擁有更好的組織：

```sh
# Discover and maintain include relationships
rake includes:maintain_relationships

# Add/update timestamps based on include file changes
rake includes:maintain_timestamps

# Do both operations in sequence (recommended)
rake includes:maintain_all
```

## 包含關係檔案格式

`include-relationships.yml`檔案追蹤主要內容檔案與其包含檔案之間的關係。 此檔案由`maintain_include_relationships` Rake工作自動維護，透過讀取現有的包含檔案並尋找參照它們的主要檔案來探索關係。

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
- Gemfile中指定的必要GEM （核心相依性由`adobe-comdox-exl-rake-tasks`提供）。
- [GitHub CLI](https://cli.github.com/)用於`get_released_versions`和`first_merge_date`工作。
- [任務的Python、](https://www.pygmt.org/latest/install.html)PyGMT[和](https://formulae.brew.sh/formula/pdf2svg)pdf2svg`azure_regions`。

## 設定

1. 安裝必要的GEM：

   ```sh
   bundle install
   ```

2. 確保您已為`azure_regions`工作安裝Python、PyGMT和pdf2svg。 如需設定的詳細資訊，請參閱註解中的檔案，網址為[_scripts/azure_regions.py](_scripts/azure_regions.py)。
