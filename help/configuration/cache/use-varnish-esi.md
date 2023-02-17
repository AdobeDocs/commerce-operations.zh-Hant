---
title: 清漆ESI塊
description: 了解Edge Side Includes，以及如何使用它們來內嵌網頁。
badge: label=」康斯坦丁·G供稿。」 type="Informity" url="https://github.com/goivvy" tooltip="Konstantin G."
source-git-commit: 90544452f5f0834e096ead6ea3df64dcb5eaea11
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---


# 清漆ESI塊

邊緣端包含(ESI)是特殊指示，可用於將網頁包含在其他網頁中。

範例：

```html
<div>
  <esi:include src="http://domain.com/index.php/page_cache/block/esi/blocks"/>
</div>
```

清漆從 `http://domain.com/index.php/page_cache/block/esi/blocks` 並替換 `<esi>` 標籤。

## Commerce和Quites ESI

當滿足以下條件時，Commerce框架將建立ESI標籤：

- 快取應用程式設定為 `Varnish Cache`
- XML佈局 `block` 元素已新增 `ttl` 屬性

### 範例

`cms_index_index.xml`:

```xml
  <referenceContainer name="content">
      <block class="Magento\Framework\View\Element\Template" template="Magento_Paypal::esi.phtml" ttl="30"/>
   </referenceContainer>
```

在上例中， `block` 元素會從 `esi.phtml` 首頁的範本，則清漆會每隔30秒自動更新一次。

## 限制

目前，Quiest不支援ESI over HTTPS，因此它會自動切換到HTTP。

`Magento\PageCache\Observer\ProcessLayoutRenderElement`:

```php
    private function _wrapEsi(
        \Magento\Framework\View\Element\AbstractBlock $block,
        \Magento\Framework\View\Layout $layout
    ) {
    ....
        // Varnish does not support ESI over HTTPS must change to HTTP
        $url = substr($url, 0, 5) === 'https' ? 'http' . substr($url, 5) : $url;
        return sprintf('<esi:include src="%s" />', $url);
    }
```
