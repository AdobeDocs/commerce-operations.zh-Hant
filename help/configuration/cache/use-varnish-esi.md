---
title: 清漆ESI區塊
description: 瞭解Edge Side Include以及如何使用它們來內嵌網頁。
badge: label="康斯坦丁G供稿。" type="Informative" url="https://github.com/goivvy" tooltip="康斯坦丁G."
feature: Configuration, Cache
exl-id: 7dccafa5-df79-4690-be5c-ff774c66bb2a
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 0%

---

# 清漆ESI區塊

Edge Side Include (ESI)是特殊指示，可用來將網頁包含在其他網頁中。

範例：

```html
<div>
  <esi:include src="http://domain.com/index.php/page_cache/block/esi/blocks"/>
</div>
```

清漆會從`http://domain.com/index.php/page_cache/block/esi/blocks`擷取內容，並以其取代`<esi>`標籤。

## Commerce與清漆ESI

Commerce架構會在符合下列條件時建立ESI標籤：

- 快取應用程式設定為`Varnish Cache`
- 已新增具有`block`屬性的XML配置`ttl`專案

### 範例

`cms_index_index.xml`：

```xml
  <referenceContainer name="content">
      <block class="Magento\Framework\View\Element\Template" template="Magento_Paypal::esi.phtml" ttl="30"/>
   </referenceContainer>
```

在上述範例中，`block`元素從`esi.phtml`範本新增內容至首頁，Varnish每30秒自動更新一次。

## 限制

目前Varnish不支援HTTPS上的ESI，因此會自動切換至HTTP。

`Magento\PageCache\Observer\ProcessLayoutRenderElement`：

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
