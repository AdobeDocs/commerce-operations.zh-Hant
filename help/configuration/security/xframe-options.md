---
title: X — 幀 — 選項標題
description: 使用X-Frame-Options控制頁面呈現。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---


# X — 幀 — 選項標題

幫助防止 [點擊劫持](https://owasp.org/www-community/attacks/Clickjacking) efloits，我們添加了一個選項 [X幀選項](https://datatracker.ietf.org/doc/html/rfc7034) 請求到您的店面的HTTP請求標頭。

的 `X-Frame-Options` 標題允許您指定是否允許瀏覽器在 `<frame>`。 `<iframe>`或 `<object>` 如下：

- `DENY`:無法在框架中顯示頁面。
- `SAMEORIGIN`:（預設）頁面只能顯示在與頁面本身位於同一原點的框架中。

>[!WARNING]
>
>的 `ALLOW-FROM <uri>` 選項已棄用，因為支援Commerce的瀏覽器不再支援它。 請參閱 [瀏覽器相容性](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options#browser_compatibility)。

>[!WARNING]
>
>出於安全原因，Adobe強烈建議不要在框架中運行Commerce商店。

## 實施 `X-Frame-Options`

為 `X-Frame-Options` 在 `<magento_root>/app/etc/env.php`。 預設值如下：

```php
'x-frame-options' => 'SAMEORIGIN',
```

>[!TIP]
>
>編輯 `env.php` 設定管理中的值。

## 驗證您的設定 `X-Frame-Options`

要驗證設定，請查看任何儲存前頁上的HTTP標頭。 有幾種方法可以執行此操作，包括使用Web瀏覽器檢查器。

以下示例使用curl ，您可以從通過HTTP協定連接到Commerce伺服器的任何電腦中運行curl。

使用以下命令：

```bash
curl -I -v --location-trusted '<your storefront URL>'
```

查找 `X-Frame-Options` 值。
