---
title: 設定清漆ESI區塊
description: 瞭解Varnish Edge Side Include (ESI)以及如何內嵌Adobe Commerce的網頁。 探索ESI區塊實施與最佳化。
badge: label="康斯坦丁G供稿。" type="Informative" url="https://github.com/goivvy" tooltip="康斯坦丁G."
feature: Configuration, Cache
exl-id: 7dccafa5-df79-4690-be5c-ff774c66bb2a
badgePaas: label="內部部署" type="Informative" url="https://experienceleague.adobe.com/zh-hant/docs/commerce/user-guides/product-solutions" tooltip="僅適用於Adobe Commerce內部部署專案。"
autotag-review: '2026-06-22T22:02:08.706Z'
TQID: 'https://experienceleague.adobe.com/hzsfaZyHuUhzfb86anO43PfP-62WRPOoMbYOh-H1vqo'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: ab2a9ef6d4c3ed692f4a6a66323ab5e3d5c6673a
workflow-type: tm+mt
source-wordcount: 159
ht-degree: 0%

---

# 設定清漆ESI區塊 {#varnish-esi-block}

{{varnish-config-cloud}}

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
- 已新增具有`ttl`屬性的XML配置`block`專案

### 範例

`cms_index_index.xml`:

```xml
  <referenceContainer name="content">
      <block class="Magento\Framework\View\Element\Template" template="Magento_Paypal::esi.phtml" ttl="30"/>
   </referenceContainer>
```

在上述範例中，`block`元素從`esi.phtml`範本新增內容至首頁，Varnish每30秒自動更新一次。

## 限制

目前Varnish不支援HTTPS上的ESI，因此會自動切換至HTTP。

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
