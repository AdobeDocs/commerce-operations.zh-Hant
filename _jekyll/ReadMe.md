---
source-git-commit: ca9e04d50e69b8a51ec4a6fbcf1d35f0fb363fab
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---
# 概觀

此專案包含數個Rake工作，以自動化工作流程的各個層面，例如產生新聞摘要的資料、演算範本化檔案、最佳化影像及產生地圖。 以下是Rakefile中定義的每個Rake工作的說明和使用准則。

## Rake任務

### `render`

轉譯`_jekyll/templates`目錄中包含`_jekyll/_data/`資料的樣板化檔案。 結果可在`help/includes/templated`目錄中找到。

**使用狀況：**

```sh
rake render
```

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

## 先決條件

- 已安裝Ruby和Bundler。
- Gemfile中指定的必要gems。
- `azure_regions`任務的Python、[PyGMT](https://www.pygmt.org/latest/install.html)和[pdf2svg](https://formulae.brew.sh/formula/pdf2svg)。

## 設定

1. 安裝必要的GEM：

   ```sh
   bundle install
   ```

2. 確保您已為`azure_regions`工作安裝Python、PyGMT和pdf2svg。 如需設定的詳細資訊，請參閱註解中的檔案，網址為[_scripts/azure_regions.py](_scripts/azure_regions.py)。
