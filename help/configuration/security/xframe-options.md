---
title: X-Frame-Options標題
description: 使用X-Frame-Options來控制頁面呈現。
source-git-commit: db696b8ca501d128db655c5ebb161c654c6378a7
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---


# X-Frame-Options標題

幫助防止 [Clickjacking](https://owasp.org/www-community/attacks/Clickjacking) 利用漏洞，我們新增了使用 [X-Frame-Options](https://datatracker.ietf.org/doc/html/rfc7034) 向您的店面提出請求中的HTTP要求標題。

此 `X-Frame-Options` 標題可讓您指定是否應允許瀏覽器呈現 `<frame>`, `<iframe>`，或 `<object>` 如下所示：

- `DENY`:頁面無法顯示在框架中。
- `SAMEORIGIN`:（預設）頁面只能顯示在與頁面本身相同來源的框架中。

>[!WARNING]
>
>此 `ALLOW-FROM <uri>` 選項已淘汰，因為支援商務的瀏覽器不再支援。 請參閱 [瀏覽器相容性](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options#browser_compatibility).

>[!WARNING]
>
>基於安全考量，Adobe強烈建議不要在框架中執行Commerce商店。

## 實作 `X-Frame-Options`

設定 `X-Frame-Options` in `<project-root>/app/etc/env.php`. 預設值的設定如下：

```php
'x-frame-options' => 'SAMEORIGIN',
```

重新部署，以備 `env.php` 檔案生效。

>[!TIP]
>
>編輯 `env.php` 檔案來設定值。

## 驗證的設定 `X-Frame-Options`

若要驗證您的設定，請在任何店面頁面上檢視HTTP標題。 執行此操作有數種方法，包括使用Web瀏覽器檢查器。

下列範例使用curl，您可從任何可透過HTTP通訊協定連線至您的商務伺服器的電腦執行。

```bash
curl -I -v --location-trusted '<storefront-URL>'
```

尋找 `X-Frame-Options` 值。
