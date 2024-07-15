---
title: 避免點選劫持利用漏洞
description: 使用「X-Frame-Options」標頭控制頁面呈現，以防止點選劫持攻擊。
feature: Configuration, Security
exl-id: 83cf5fd2-3eb8-4bd9-99e2-1c701dcd1382
source-git-commit: 6cc04211fedddab68087bcf2f3603ae0403862b9
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---

# 避免點選劫持利用漏洞

將[X-Frame-Options](https://datatracker.ietf.org/doc/html/rfc7034) HTTP要求標頭納入對店面的要求中，以防止[點選劫持](https://owasp.org/www-community/attacks/Clickjacking)利用。

`X-Frame-Options`標頭可讓您指定是否允許瀏覽器轉譯`<frame>`、`<iframe>`或`<object>`中的頁面，如下所示：

- `DENY`：頁面無法顯示在框架中。
- `SAMEORIGIN`： （預設）頁面只能在與頁面本身相同來源的框架中顯示。

>[!WARNING]
>
>`ALLOW-FROM <uri>`選項已過時，因為Commerce支援的瀏覽器不再支援。 檢視[瀏覽器相容性](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options#browser_compatibility)。

>[!WARNING]
>
>基於安全考量，Adobe強烈建議不要在框架中執行Commerce店面。

## 實作`X-Frame-Options`

在`<project-root>/app/etc/env.php`中設定`X-Frame-Options`的值。 預設值的設定如下：

```php
'x-frame-options' => 'SAMEORIGIN',
```

重新部署，使對`env.php`檔案所做的任何變更生效。

>[!TIP]
>
>編輯`env.php`檔案比在Admin中設定值更安全。

## 驗證`X-Frame-Options`的設定

若要驗證您的設定，請檢視任何店面頁面上的HTTP標題。 有數種方法可以達成此目的，包括使用網頁瀏覽器檢測器。

以下範例使用curl，您可以從任何可以透過HTTP通訊協定連線至您的Commerce伺服器的電腦上執行它。

```bash
curl -I -v --location-trusted '<storefront-URL>'
```

在標頭中尋找`X-Frame-Options`值。
