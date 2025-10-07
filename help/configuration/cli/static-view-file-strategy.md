---
title: 靜態檢視檔案的部署策略
description: 瞭解Adobe Commerce應用程式中靜態檢視檔案的部署策略。 探索不同使用案例的最佳部署方法。
feature: Configuration, Deploy, Extensions
exl-id: 12ebbd36-f813-494f-9515-54ce697ca2e4
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# 靜態檢視檔案的部署策略

部署靜態檢視檔案時，您可以選擇三種可用策略之一。 其中每個選項都可針對不同使用案例提供最佳部署結果：

- [標準](#standard-strategy)：一般部署程式。
- [快速](#quick-strategy) （_預設_）：部署一個以上地區設定的檔案時，將部署所需的時間減至最少。
- [壓縮](#compact-strategy)：將發行檢視檔所佔用的空間減到最少。

以下各節說明每個策略的實作詳細資訊和功能。

## 標準策略

使用標準策略時，會部署所有套件的所有靜態檢視檔案，也就是由[`\Magento\Framework\App\View\Asset\Publisher`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/View/Asset/Publisher.php)處理。

如需詳細資訊，請參閱[部署靜態檢視檔案](../cli/static-view-file-deployment.md)。

## 快速策略

快速策略會執行下列動作：

1. 對於每個主題，選擇一個任意語言環境，並部署此語言環境的所有檔案，例如在標準策略中。
1. 對於主題的所有其他地區：

   1. 會定義並部署覆寫已部署地區設定的檔案。
   1. 對於所有語言環境，所有其他檔案都視為類似，並從已部署語言環境複製。

>[!INFO]
>
>按&#x200B;_similar_，我們是指與地區、佈景主題或區域無關的檔案。 這些檔案可能包含CSS、影像和字型。

雖然有許多檔案重複，但此方法可儘量減少多個區域設定所需的部署時間。

## 精簡策略

壓縮策略藉由將類似的檔案儲存在`base`子目錄中來避免檔案重複。

為獲得最佳化結果，已分配了三個可能相似性的範圍：區域、主題和地區設定。 會為這些範圍的所有組合建立`base`子目錄。

檔案會根據下列模式部署至這些子目錄。

| 圖樣 | 說明 |
| ------- | ----------- |
| `<area>/<theme>/<locale>` | 特定區域、佈景主題和區域設定的特定檔案 |
| `<area>/<theme>/default` | 特定區域特定主題的所有區域設定類似的檔案。 |
| `<area>/Magento/base/<locale>` | 特定區域和地區設定的特定檔案，但所有主題都類似。 |
| `<area>/Magento/base/default` | 特定區域的特定檔案，但所有主題和區域設定都類似。 |
| `base/Magento/base/<locale>` | 所有區域和主題的檔案都類似，但特定於特定地區設定。 |
| `base/Magento/base/default` | 所有區域、主題和區域設定都類似。 |

### 對應已部署的檔案

壓縮策略中使用的部署方法表示檔案繼承自基本主題和區域設定。 這些繼承關係會儲存在區域、主題和區域設定的每個組合的地圖檔案中。 PHP和JS有單獨的對應檔案：

- `map.php`
- `requirejs-map.js`

`map.php`[`Magento\Framework\View\Asset\Repository`已使用](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Asset/Repository.php)檔案來建置正確的URL。

`requirejs-map.js`由`baseUrlResolver`外掛程式用於RequireJS。

`map.php`的範例：

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

`requirejs-map.js`的範例：

```js
require.config({
    "config": {
       "baseUrlInterceptor": {
            "jquery.js": "../../../../base/Magento/base/en_US/"
        }
    }
});
```

## 擴充功能開發人員的提示

若要建置靜態檢視檔案的URL，請使用[`\Magento\Framework\View\Asset\Repository::createAsset()`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Asset/Repository.php#L211-L244)。

請勿使用URL串連來避免在頁面轉譯期間找不到且未顯示靜態檔案的問題。
