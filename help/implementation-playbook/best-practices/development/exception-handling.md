---
title: 例外狀況處理最佳實務
description: 瞭解開發Adobe Commerce專案時記錄例外狀況的建議方法。
feature: Best Practices
role: Developer
exl-id: e7ad685b-3eaf-485b-8ab1-702f2e7ab89e
source-git-commit: 4bf8dd5c5320cc9a34cfaa552ec5e91d517d3617
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 0%

---

# 例外狀況處理最佳實務

如果例外狀況未寫入 `exception.log` 將例外狀況模型作為上下文的檔案，在New Relic或其他相容於PSR-3獨白的記錄檔儲存體中，無法正確識別和分析。 僅記錄例外狀況的一部分（或將其記錄到錯誤的檔案）會在忽略例外狀況時導致生產中的錯誤。

## 正確的例外狀況處理

下列檢查清單提供範例，示範如何正確處理例外狀況。

### ![正確](../../../assets/yes.svg) 寫入例外記錄

使用下列模式寫入例外記錄檔，不考慮進一步的動作，除非有令人信服的理由不這樣做。

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e);
}
```

此方法會自動儲存 `$e->getMessage` 至記錄訊息及 `$e` 物件至前後關聯，請遵循 [PSR-3內容標準](https://www.php-fig.org/psr/psr-3/#13-context). 這是在中完成 `\Magento\Framework\Logger\Monolog::addRecord`.

### ![正確](../../../assets/yes.svg) 將訊號設為靜音

不記錄屬於預期作業流程一部分的例外狀況，將訊號設為靜音。 發生例外狀況時不需要進行後續動作，因此發生例外狀況時不需要記錄和分析。 新增註解，說明將訊號靜音的原因，以及這是刻意為之。 結合 `phpcs:ignore`.

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) { // phpcs:ignore Magento2.CodeAnalysis.EmptyBlock.DetectedCatch
    // Product already removed
}
```

### ![正確](../../../assets/yes.svg) 降級例外狀況

依下列方式降級例外狀況 [PSR-3內容標準](https://www.php-fig.org/psr/psr-3/#13-context).

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->debug($e->getMessage(), ['exception' => $e]);
}
```

### ![正確](../../../assets/yes.svg) 永遠先記錄

最佳實務是永遠先在程式碼中記錄，以防止在寫入記錄檔之前擲回另一個例外狀況或嚴重錯誤的情況。

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e);
    $this->alternativeProcedure();
}
```

### ![正確](../../../assets/yes.svg) 記錄訊息和整個例外狀況追蹤

依照下列步驟，記錄訊息和整個例外狀況追蹤 [PSR-3內容標準](https://www.php-fig.org/psr/psr-3/#13-context).

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e->getMessage(), ['exception' => $e, 'trace' => $e->getTrace()]);
}
```

## 不正確的例外狀況處理

下列範例示範不正確的例外狀況處理。

### ![不正確](../../../assets/no.svg) 記錄前的邏輯

記錄前的邏輯可能會導致另一個例外狀況或嚴重錯誤，這會防止例外狀況被記錄，因此應該取代為 [正確範例](#logging-always-comes-first).

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
    $this->alternativeProcedure();
    $this->logger->critical($e);
}
```

### ![不正確](../../../assets/no.svg) 空白 `catch`

空白 `catch` 區塊可能是非預期靜音的標誌，應取代為 [正確範例](#mute-signals).

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
}
```

### ![不正確](../../../assets/no.svg) 雙重本地化

如果攔截到的當地語系化例外狀況尚未轉譯，請在第一次擲回例外狀況的位置解決問題。

```php
try {
    $this->productRepository->getById($sku);
} catch (LocalizedException $e) {
    throw new LocalizedException(__($e->getMessage()));
}
```

### ![不正確](../../../assets/no.svg) 記錄訊息並追蹤至不同的記錄檔

下列程式碼會將例外狀況的棧疊追蹤錯誤記錄為記錄檔的字串。

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->error($e->getMessage());
    $this->logger->debug($e->getTraceAsString());
}
```

此方法在訊息中引入了分行符號，這與PSR-3不相容。 例外狀況（包括棧疊追蹤）必須屬於訊息內容的一部分，以確保其能正確與訊息一起儲存在New Relic或其他PSR-3單一記錄檔相容的記錄儲存體中。

請依照中顯示的正確範例取代程式碼，以修正此問題 [寫入例外記錄](#write-to-the-exception-log) 或 [降級例外狀況](#downgrade-exceptions).

### ![不正確](../../../assets/no.svg) 無內容的降級例外狀況

例外狀況會降級為錯誤，不允許傳遞物件，但只能傳遞字串，因此 `getMessage()`. 這會導致追蹤遺失，且應該以中顯示的正確範例取代 [寫入例外記錄](#write-to-the-exception-log) 或 [降級例外狀況](#downgrade-exceptions).

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->error($e->getMessage());
}
```

### ![不正確](../../../assets/no.svg) 僅將訊息記錄到例外狀況記錄檔

不要傳遞物件 `$e`，僅限 `$e->getMessage()` 已通過。 這會導致追蹤遺失，且應該以顯示的正確範例取代 [寫入例外記錄](#write-to-the-exception-log) 或 [降級例外狀況](#downgrade-exceptions).

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->critical($e->getMessage());
}
```

### ![不正確](../../../assets/no.svg) 遺失 `// phpcs:ignore Magento2.CodeAnalysis.EmptyBlock.DetectedCatch`

省略 `phpcs:ignore` line會在PHPCS中觸發警告，且不應傳遞您的CI。 此資訊應該由下列正確範例取代： [將訊號設為靜音](#mute-signals).

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
    // Product already removed
}
```
