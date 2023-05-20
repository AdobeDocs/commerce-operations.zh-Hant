---
title: 清漆ESI塊
description: 瞭解「邊緣端包括」以及如何使用它們嵌入網頁。
badge: label="康斯坦丁G提供。" type="Informative" url="https://github.com/goivvy" tooltip="Konstantin G."
exl-id: 7dccafa5-df79-4690-be5c-ff774c66bb2a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---

# 清漆ESI塊

邊緣端包括(ESI)是特殊指令，可用於將網頁包括在其它網頁中。

例如：

```html
<div>
  <esi:include src="http://domain.com/index.php/page_cache/block/esi/blocks"/>
</div>
```

清漆從中提取內容 `http://domain.com/index.php/page_cache/block/esi/blocks` 並替換 `<esi>` 帶著它。

## 商務與清漆ESI

當滿足以下條件時，Commerce框架將建立ESI標籤：

- 快取應用程式設定為 `Varnish Cache`
- XML佈局 `block` 元素與 `ttl` 屬性

### 示例

`cms_index_index.xml`:

```xml
  <referenceContainer name="content">
      <block class="Magento\Framework\View\Element\Template" template="Magento_Paypal::esi.phtml" ttl="30"/>
   </referenceContainer>
```

在上例中， `block` 元素添加來自 `esi.phtml` 模板到首頁，清漆每30秒自動更新一次。

## 限制

目前，Wishet不支援HTTPS上的ESI，因此它會自動切換到HTTP。

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
