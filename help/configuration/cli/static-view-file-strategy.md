---
title: 靜態視圖檔案的部署策略
description: 閱讀有關Commerce應用程式的部署策略的資訊。
source-git-commit: 96fe0c5eeaa029347c829c39547ee5e473c8d04d
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%

---


# 靜態視圖檔案的部署策略

部署靜態視圖檔案時，您可以選擇三個可用策略之一。 每個應用程式都為不同的使用情形提供最佳部署結果：

- [標準](#standard-strategy):常規部署過程。
- [快速](#quick-strategy) (_預設_):將部署多個區域設定的檔案時所需的時間降至最低。
- [緊湊](#compact-strategy):最小化已發佈視圖檔案佔用的空間。

以下各節介紹了每個策略的實施詳細資訊和功能。

## 標準策略

使用標準策略時，將部署所有包的所有靜態視圖檔案，即由 [`\Magento\Framework\App\View\Asset\Publisher`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/View/Asset/Publisher.php)。

有關詳細資訊，請參見 [部署靜態視圖檔案](../cli/static-view-file-deployment.md)。

## 快速策略

快速策略執行以下操作：

1. 對於每個主題，都會選擇一個任意區域設定，並部署此區域設定的所有檔案，如在標準策略中。
1. 對於主題的所有其他區域設定：

   1. 定義並部署覆蓋已部署區域設定的檔案。
   1. 對於所有語言環境，所有其他檔案都被視為類似，並從部署的語言環境複製。

>[!INFO]
>
>按 _相似_，我們指與區域設定、主題或區域無關的檔案。 這些檔案可能包括CSS、影像和字型。

此方法將多個語言環境所需的部署時間降至最低，儘管複製了大量檔案。

## 緊湊策略

壓縮策略通過將相似檔案儲存在 `base` 子目錄。

對於最佳化的結果，分配了三個可能的相似性範圍：區域、主題和區域設定。 的 `base` 為這些作用域的所有組合建立子目錄。

檔案將按照以下模式部署到這些子目錄。

| 圖案 | 說明 |
| ------- | ----------- |
| `<area>/<theme>/<locale>` | 特定區域、主題和區域設定的檔案 |
| `<area>/<theme>/default` | 與特定區域特定主題的所有語言環境類似的檔案。 |
| `<area>/Magento/base/<locale>` | 特定於特定區域和區域設定的檔案，但與所有主題類似。 |
| `<area>/Magento/base/default` | 特定區域的檔案，但所有主題和區域設定都類似。 |
| `base/Magento/base/<locale>` | 所有區域和主題的檔案相似，但特定於特定區域設定。 |
| `base/Magento/base/default` | 所有區域、主題和區域設定都類似。 |

### 映射已部署的檔案

壓縮策略中使用的部署方法意味著檔案是從基本主題和語言環境繼承的。 這些繼承關係儲存在區域、主題和區域設定的每個組合的映射檔案中。 PHP和JS有單獨的映射檔案：

- `map.php`
- `requirejs-map.js`

的 `map.php` 檔案由 [`Magento\Framework\View\Asset\Repository`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Asset/Repository.php) 以生成正確的URL。

的 `requirejs-map.js` 由 `baseUrlResolver` RequireJS的插件。

示例 `map.php`:

```php?start_inline=1
return [
    'Magento_Checkout::cvv.png' => [
        'area' => 'frontend',
        'theme' => 'Magento/luma',
        'locale' => 'en_US',
    ],
    '...' => [
        'area' => '...',
        'theme' => '...',
        'locale' => '...'
    ]
];
```

示例 `requirejs-map.js`:

```js
require.config({
    "config": {
       "baseUrlInterceptor": {
            "jquery.js": "../../../../base/Magento/base/en_US/"
        }
    }
});
```

## 擴展開發人員的提示

要生成靜態視圖檔案的URL，請使用 [`\Magento\Framework\View\Asset\Repository::createAsset()`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Asset/Repository.php#L211-L244)。

請勿使用URL連接來避免在頁面呈現過程中找不到或未顯示靜態檔案的問題。
