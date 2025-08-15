---
title: 修改核心和第三方PHP程式碼的最佳作法
description: 瞭解如何以及何時修改核心Adobe Commerce和第三方PHP程式碼。
role: Developer, Architect
feature: Best Practices
last-substantial-update: 2023-12-8
exl-id: 32b3137d-fc00-4be8-ba02-5d8d48a51fe1
source-git-commit: d47567a8d69ccdae3db01e964f1db12e8ae26717
workflow-type: tm+mt
source-wordcount: '1747'
ht-degree: 0%

---

# 修改或覆寫核心和第三方PHP程式碼的最佳作法

本檔案旨在說明當您需要修改任何您未撰寫或未直接控制之程式碼的功能、結果或輸入時，的最佳作法。 換言之，核心程式碼和協力廠商程式碼。 本檔案主要著重於後端PHP程式碼。

## 修改程式碼的方法

修改程式碼時，請務必考量變更的範圍。 變更的「範圍」是指程式碼變更的影響範圍。 最佳實務是依據佔用空間最小且資源使用量最少的選項，來決定最終實作的完成方式。 程式碼覆寫範圍越廣，開發團隊就越是偏離核心Adobe Commerce功能，導致未來發生錯誤的可能性越大，維護程式碼基底的工作量也越大。

### 修補

修補程式是包含直接變更檔案中程式碼指示的檔案，而該檔案不在開發團隊的直接控制之下。 如果沒有其他選項，通常應將這個選項視為最後的手段。 修補程式是暫時的解決方案。 如果您必須建立修補程式，作為一般最佳作法，請在接下來的2-4週內移除修補程式，以採用更永久的解決方案。 

修補程式可輕易中斷。 如果更新修正程式目標的檔案，這通常會導致修正程式停止運作。 這是因為修補程式檔案包含行號和欄號，明確指示要由修補程式變更的內容。 如果有任何內容與修補程式的預期不符，它會停止套用並中斷程式碼。

```bash
diff --git a/vendor/magento/module-quote/Model/QuoteManagement.php b/vendor/magento/module-quote/Model/QuoteManagement.php
index 51b68411d40..ac4a3468322 100644
--- a/vendor/magento/module-quote/Model/QuoteManagement.php
+++ b/vendor/magento/module-quote/Model/QuoteManagement.php
@@ -424,8 +424,9 @@ class QuoteManagement implements CartManagementInterface
                 }
             }
             $quote->setCustomerIsGuest(true);
-            $groupId = $customer ? $customer->getGroupId() : GroupInterface::NOT_LOGGED_IN_ID;
-            $quote->setCustomerGroupId($groupId);
+            $quote->setCustomerGroupId(
+                $quote->getCustomerId() ? $customer->getGroupId() : GroupInterface::NOT_LOGGED_IN_ID
+            );
         }
  
         $remoteAddress = $this->remoteAddress->getRemoteAddress();
```

#### 修補程式可變更的專案

任何專案。 就字面上來說，任何目標檔案中的任何字元都可以變更。 修補程式並不限於任何特定檔案型別或程式碼語言。 一般而言，您會使用修補程式來鎖定`vendor`目錄中的檔案。 

#### 何時使用修補程式

如果您發現沒有其他選項存在。 例如，當廠商尚未發佈程式碼修正時，您可以使用修補程式暫時解決問題，同時等候永久解決方案。

#### 缺點

修補程式可輕易中斷。 目標程式碼變更時，修補程式就會停止運作。 這些只是短期解決方案。

### 偏好設定

偏好設定是設計至Adobe Commerce平台的概念。 它本質上是一個「PHP類別替代」。

Adobe Commerce平台使用「物件管理員」來例項化PHP類別，因為它不會像在傳統PHP應用程式中那樣使用新關鍵字例項化PHP類別。 相反地，物件管理員會互動參照要針對編譯組態例項化的PHP類別名稱，以決定是否有任何模組宣告原始類別的偏好設定。 如果找到PHP類別的偏好設定，物件管理員會改為例項化指定的類別。

應該注意的是（通常）取代原始PHP類別的新PHP類別會延伸/繼承原始PHP類別。 這麼做有兩個原因：

- 確保遵循相依性插入/型別提示。 否則，會發生嚴重錯誤且應用程式中斷。
- 允許最少量的程式碼寫入。 如果原始PHP類別包含10個方法，但您只需要覆寫一個方法，您通常可以單獨變更一個方法，而保留其他9個方法不變。 這很重要，因為平台升級至新版本時，請確定您沒有封鎖核心功能的更新。

#### 宣告偏好設定

宣告偏好設定是一個相當簡單的程式。 需要將一行程式碼新增至模組內的`di.xml`檔案。 這項工作可在全域或任何Adobe Commerce「區域」內完成，例如`frontend`、`adminhtml`、`graphql`、`webapi_rest`和`crontab`。

```xml
<preference for="Magento\Elasticsearch7\SearchAdapter\Adapter" type="Vendor\Namespace\Adapter\AlgoliaElasticSearch7Adapter"/>
```

```php
<?php

declare(strict_types=1);

namespace Vendor\Namespace\Adapter;

class AlgoliaElasticSearchAdapter extends \Magento\Elasticsearch7\SearchAdapter\Adapter
{
}
```

#### 使用偏好設定可變更的專案

只有偏好設定可以覆寫PHP類別。 在PHP類別中，您可以修改公用和受保護的方法和屬性。 對於公用和受保護的方法，您可以完全覆寫方法，或者修改傳入（或傳出）原始父方法的引數。

技術上無法覆寫私用方法。 不過，您可以建立自己的取代原始私有方法。 您甚至可以為它指定任意名稱，也可以使用原始名稱。 這無關緊要，因為私有方法只存在於包含它的實際檔案中。 若要覆寫私用方法，您必須覆寫或修改呼叫原始私用方法的公用或受保護方法，而且必須取代您自己的功能。

#### 何時使用偏好設定

再次強調，當沒有其他選項存在，且無法透過相依性插入、外掛程式或觀察者完成目標時，您應使用偏好設定。 如果您需要修改或覆寫私用或受保護的方法或屬性，有時您可能需要偏好設定。 請注意，偏好設定應謹慎使用。 變更應用程式時，它們是相當「貪婪」的方法，而且您實際上擁有了PHP類別的所有權。 這可能會導致與協力廠商模組衝突，並且可能會封鎖核心類別的更新，並導致難以診斷的錯誤。 Adobe Commerce平台的設計宗旨是包含其他途徑，以便以更少的空間變更基礎程式碼。

#### 缺點

偏好設定是修改程式碼的貪婪方式，只應在其他選項不存在時使用。 偏好設定經常會導致程式碼基底內發生衝突，而且更糟糕的是，它們可能會封鎖隨著平台升級發生的核心更新。 

### 觀察者

觀察者是一種事件偵聽程式的概念，在許多應用程式、平台、程式庫和程式碼語言中都可找到。 這個概念並非Adobe Commerce平台所特有。 從Magento 1時代起，觀察者就一直在平台內實作，且被視為如何修改核心程式碼和協力廠商程式碼的主要選擇。 

核心程式碼基底和任何協力廠商模組都可以在程式碼中的選定位置傳送事件。 在`events.xml`檔案中宣告且正在以名稱接聽分派事件的觀察者，可以在全域層級上運作或受限於任何Adobe Commerce「區域」，例如`frontend`、`adminhtml`、`graphql`、`webapi_rest`和`crontab`。

#### 如何宣告觀察者

可以在全域或區域特定的`events.xml`檔案中設定觀察者。

```xml
    <event name="sales_model_service_quote_submit_before">
        <observer name="set_reward_flag_order" instance="Adobe\RewardAdjustments\Observer\SetOrderRewardFlag" />
    </event>
```

```php
<?php

declare(strict_types=1);

namespace Adobe\RewardAdjustments\Observer;

use Magento\Framework\Event\ObserverInterface;
use Magento\Framework\Event\Observer;
use Magento\Quote\Model\Quote;
use Magento\Sales\Api\Data\OrderInterface;

class SetOrderRewardFlag implements ObserverInterface
{
    /**
     * @param Observer $observer
     * @return void
     */
    public function execute(Observer $observer)
    {
        $event = $observer->getEvent();
        /* @var $order OrderInterface */
        $order = $event->getOrder();
        /** @var $quote Quote $quote */
        $quote = $event->getQuote();

        // do something to the order and/or quote object here
    }
}
```

#### 可以使用觀察者變更的內容

觀察者僅適用於Adobe Commerce平台中的PHP程式碼。 您只能修改隨事件分派傳遞的特定資料和物件。

#### 何時使用觀察者

只要有空就可以！ 如果觀察者更廣泛地提供和靈活，那麼觀察者將佔據此清單的第二位。 觀察者的處理開銷比外掛程式少，而且可用性較低，也較不靈活。

#### 缺點

雖然觀察者非常適合攔截及修改程式碼，但必須將事件傳送新增至核心或協力廠商程式碼，以供您的程式碼監聽。 這使得使用觀察者的概念有點受限。 僅限開發人員有遠見卓識的事件納入程式碼中。

此外，觀察者的另一個限制因素是，已傳送事件僅提供開發人員決定隨事件傳遞的特定資料和物件的存取權。

### 外掛程式

外掛程式是Adobe Commerce平台中推出的彈性概念。 它可讓您擷取、取代和修改任何公用PHP方法。 外掛程式可讓您在執行目標方法之前修改進入方法的引數、在執行目標方法之後修改結果，或完全取代目標方法。 您可以在單一外掛程式檔案中修改目標PHP類別的許多方法。 此外，您可以使用`$subject`引數來執行目標PHP類別中存在的任何公用方法。

#### 如何宣告外掛程式

外掛程式可以在全域或區域特定的`di.xml`檔案中設定。

```xml
    <type name="Magento\Catalog\Api\CategoryRepositoryInterface">
        <plugin name="Adobe\CatalogAdjustments\Plugin\CategoryRepositoryPlugin" type="Adobe\CatalogAdjustments\Plugin\CategoryRepositoryPlugin"/>
    </type>
```

```php
<?php

declare(strict_types=1);

namespace Adobe\CatalogAdjustments\Plugin;

class CategoryRepositoryPlugin
{
    /**
     * @param \Magento\Catalog\Api\CategoryRepositoryInterface $subject
     * @param int $categoryId
     * @param int $storeId
     *
     * @return array
     */
    public function beforeGet($subject, $categoryId, $storeId = null): array
    {
        // modify the $categoryId or $storeId arguments or perform some other functionality prior to execution of the `get` method
        return [$categoryId, $storeId];
    }

    /**
     * @param \Magento\Catalog\Api\CategoryRepositoryInterface $subject
     * @param \Closure $origMethod
     * @param int $categoryId
     * @param int $storeId
     *
     * @return \Magento\Catalog\Api\Data\CategoryInterface
     */
    public function aroundGet($subject, $origMethod, $categoryId, $storeId = null): \Magento\Catalog\Api\Data\CategoryInterface
    {
        // here you can do something before calling the original method
        $result = $origMethod($categoryId, $storeId);
        // here you can do something after calling the original method
        // you can also NOT call the original method at all and instead, substitute our own functionality

        return $result;
    }

    /**
     * @param \Magento\Catalog\Api\CategoryRepositoryInterface $subject
     * @param \Magento\Catalog\Api\Data\CategoryInterface $result
     * @param int $categoryId
     * @param int $storeId
     *
     * @return \Magento\Catalog\Api\Data\CategoryInterface
     */
    public function afterGet($subject, $result, $categoryId, $storeId = null): \Magento\Catalog\Api\Data\CategoryInterface
    {
        // here you modify the result produced by the original `get` function or you can execute some other functionality
        // note that you also have access to the original function arguments. it's too late to modify them, but if needed, they are available for reading

        return $result;
    }
}
```

#### 外掛程式可以變更的專案

此功能僅適用於目標PHP類別。 您可以變更公用方法的輸入或輸出，也可以使用外掛程式來觸發其他功能。 如果有多個外掛程式以相同的PHP類別為目標，則可以設定外掛程式執行的排序順序，以允許您的外掛程式在其他外掛程式之前或之後執行。

#### 何時使用外掛程式

當相依性取代無法使用時。 外掛程式通常用於核心程式碼基底、協力廠商程式碼中，也常用於您自己的自訂程式碼中。 通常，當您必須修改自訂程式碼未擁有或控制的功能時，外掛程式是可行的做法。

#### 缺點

無法修改受保護的方法或屬性。 處理開銷高於觀察者。 這並非不使用外掛程式的引數，差異微不足道。 不過，請謹記以下事項。

### 相依性取代

相依性插入是一種標準的物件導向編碼概念，您可以在其中使用建構函式將所需的相依性傳遞到類別中。 不過，Adobe Commerce平台提供多種方式，以XML取代相依性，進一步邁出第一步。 基本上是相依性取代。 相依性取代不適用於所有情況，但可允許最低限度的程式碼寫入、較低的額外負荷，而且您可以僅將精確的目標程式碼片段。 您可以使用相依性取代來修改私有和保護方法。

#### 如何使用相依性取代

相依性取代可在全域或區域特定基礎上完成。

```php
<?php

class SomeClass
{
    public function __construct(
        private readonly AllowedCountries $allowedCountriesReader
    ) {}

    /**
     * Check is address allowed for store
     *
     * @param AddressInterface $address
     * @param int|null $storeId
     * @return bool
     */
    private function isAddressAllowedForWebsite(AddressInterface $address, $storeId): bool
    {
        $allowedCountries = $this->allowedCountriesReader->getAllowedCountries(ScopeInterface::SCOPE_STORE, $storeId);

        return in_array($address->getCountryId(), $allowedCountries);
    }
}
```

```php
<?php

use Magento\Store\Model\ScopeInterface;

class OverrideAllowedCountries extends AllowedCountries
{
    /**
     * Retrieve all allowed countries for scope or scopes
     *
     * @param string $scope
     * @param string|null $scopeCode
     * @return array
     * @since 100.1.2
     */
    public function getAllowedCountries(
        $scope = ScopeInterface::SCOPE_WEBSITE,
        $scopeCode = null
    ) {
        // do some stuff here
        // you can call the original method or override it completely
        
        return $something;
    }
}
```

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
    <type name="Vendor\Namespace\SomeClass">
        <arguments>
            <argument name="allowedCountriesReader" xsi:type="object">OverrideAllowedCountries</argument>
        </arguments>
    </type>
</config>
```

執行這些步驟後，您將會成功修改私有方法的行為。

#### 相依性取代可以變更的專案

公用、受保護及私用方法可透過相依性取代來變更。 如同使用外掛程式，您可以修改傳入的引數、完全取代函式，或修改函式的輸出。

#### 何時使用相依性取代

這是很不錯的首選選項，當它實際可達成所需目標時，假設不必太複雜就能實作。

#### 缺點

不多。 並非在所有情況下都可使用。 主要缺點是，您必須擴充包含要修改之功能的原始類別。 這違背了「構成超過繼承」的原則。
