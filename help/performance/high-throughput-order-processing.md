---
title: 高吞吐量訂單處理
description: 優化您的Adobe Commerce或Magento Open Source部署的訂單投放和結帳體驗。
source-git-commit: c4c52baa9e04a4e935ccc29fcce2ac2745a454ee
workflow-type: tm+mt
source-wordcount: '927'
ht-degree: 0%

---


# 高吞吐量訂單處理

通過配置以下一組模組，您可以優化訂單放置和結帳體驗 **高吞吐量訂單處理**:

- [非同步順序](#asynchronous-order-placement) — 使用隊列非同步處理訂單。
- [延遲的總計計算](#deferred-total-calculation) — 在簽出開始之前，將定義訂單合計的計算。
- [報價載入時庫存檢查](#disable-inventory-check) — 選擇跳過購物車物料的庫存驗證。

所有功能（AsyncOrder、延遲總計計算和清單檢查）均獨立工作。 您可以同時使用所有三種功能，或在任意組合中啟用和禁用功能。

## 非同步訂單放置

的 _非同步順序_ 模組啟用非同步訂單放置，將訂單標籤為 `received`，將訂單置於隊列中，並按先入先出的基準處理來自隊列的訂單。 AsyncOrder為 **禁用** 預設值。

例如，客戶將產品添加到購物車中並選擇 **[!UICONTROL Proceed to Checkout]**。 他們填寫 **[!UICONTROL Shipping Address]** 窗體，選擇其首選 **[!UICONTROL Shipping Method]**，然後選擇付款方法並下訂單。 購物車已清除，訂單標籤為 **[!UICONTROL Received]**，但產品數量尚未調整，也未向客戶發送銷售電子郵件。 已接收訂單，但訂單詳細資訊尚未可用，因為訂單尚未完全處理。 它會一直保留在隊列中，直到 `placeOrderProcess` 消費者開始，與 [庫存檢查](#disable-inventory-check) 功能（預設啟用），並按如下方式更新順序：

- **產品可用** — 訂單狀態更改為 _待定_&#x200B;調整產品數量，向客戶發送包含訂單詳細資訊的電子郵件，成功的訂單詳細資訊可在 **訂單和退貨** 清單，其中包含可操作的選項，如重新排序。
- **產品庫存不足或供應不足** — 訂單狀態更改為 _已拒絕_，產品數量不會調整，將向客戶發送包含有關問題的訂單詳細資訊的電子郵件，拒絕的訂單詳細資訊將在 **訂單和退貨** 清單中沒有可操作的選項。

使用命令行介面啟用這些功能，或編輯 `app/etc/env.php` 檔案，根據中定義的相應README檔案 [_模組參考指南_][mrg]。

**啟用AsyncOrder**:

可以使用命令行介面啟用AsyncOrder:

```bash
bin/magento setup:config:set --checkout-async 1
```

的 `set` 命令將以下內容寫入 `app/etc/env.php` 檔案：

```conf
...
   'checkout' => [
       'async' => 1
   ]
```

請參閱 [非同步順序] 的 _模組參考指南_。

**禁用AsyncOrder**:

>[!WARNING]
>
>在禁用AsyncOrder模組之前，必須驗證 _全部_ 非同步訂單過程已完成。

可以使用命令行介面禁用AsyncOrder:

```bash
bin/magento setup:config:set --checkout-async 0
```

的 `set` 命令將以下內容寫入 `app/etc/env.php` 檔案：

```conf
...
   'checkout' => [
       'async' => 0
   ]
```

### AsyncOrder相容性

AsyncOrder支援有限集 [!DNL Commerce] 功能。

| 類別 | 支援的功能 |
|---------------- | -----------------------|
| 簽出類型 | OnePage簽出<br>標準簽出<br>B2B可轉讓報價 |
| 付款方法 | 支票/貨幣訂單<br>交貨現金<br>Braintree<br>PayPal PayFlow專業版 |
| 裝運方法 | 支援所有發運方法。 |

以下功能包括 **不** 受AsyncOrder支援，但繼續同步工作：

- 支援的功能清單中未包括的付款方法
- 多地址簽出
- 管理訂單建立

#### Web API支援

啟用AsyncOrder模組後，以下REST端點和GraphQL突變非同步運行：

**休息：**

- `POST /V1/carts/mine/payment-information`
- `POST /V1/guest-carts/:cartId/payment-information`
- `POST /V1/negotiable-carts/:cartId/payment-information`

**GraphQL:**

- [`placeOrder`](https://devdocs.magento.com/guides/v2.4/graphql/mutations/place-order.html)
- [`setPaymentMethodAndPlaceOrder`](https://devdocs.magento.com/guides/v2.4/graphql/mutations/set-payment-place-order.html)

>[!INFO]
>
>GraphQL不支援非同步下發可轉讓報價單。

#### 排除付款方法

開發人員可以通過將某些付款方法添加到 `Magento\AsyncOrder\Model\OrderManagement::paymentMethods` 陣列。 使用排除的付款方法的訂單將同步處理。

### 可轉讓報價非同步訂單

的 _可轉讓報價非同步訂單_ B2B模組使您能夠非同步保存訂單項 `NegotiableQuote` 功能。 您必須啟用AsyncOrder和CondigateQuote。

## 延遲的總計計算

的 _延遲的總計計算_ 模組通過延遲總計計算來優化結帳過程，直到為購物車請求總計計算或在最終結帳步驟期間。 啟用後，當客戶將產品添加到購物車時，只計算小計。

DeferredTotalCalculation為 **禁用** 預設值。 使用命令行介面啟用這些功能，或編輯 `app/etc/env.php` 檔案，根據中定義的相應README檔案 [_模組參考指南_][mrg]。

**啟用DeferedTotalCalculation**:

可以使用命令行介面啟用DeferredTotalCalculation:

```bash
bin/magento setup:config:set --deferred-total-calculating 1
```

的 `set` 命令將以下內容寫入 `app/etc/env.php` 檔案：

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 1
   ]
```

**禁用DeferredTotalCalculation**:

可以使用命令行介面禁用DeferredTotalCalculation:

```bash
bin/magento setup:config:set --deferred-total-calculating 0
```

的 `set` 命令將以下內容寫入 `app/etc/env.php` 檔案：

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 0
   ]
```

請參閱 [DeferredTotalCalculating] 的 _模組參考指南_。

### 固定產品稅

啟用DeferredTotalCalculation後，在將產品添加到購物車後，固定產品稅(FPT)不包括在迷你購物車的產品價格和購物車小計中。 將產品添加到迷你購物車時，FPT計算將被延遲。 在進行最終結帳後，FPT將正確顯示在購物車中。

## 禁用清單檢查

的 _啟用購物車裝載上的清單_ 全局設定確定在將產品裝入購物車時是否執行庫存檢查。 禁用庫存檢查流程可提高所有結帳步驟的效能，特別是在處理購物車中的批量產品時。

禁用時，在將產品添加到購物車時不會執行庫存檢查。 如果跳過此庫存檢查，則某些庫存不足方案可能會引發其他類型的錯誤。 庫存檢查 _總是_ 在訂單放置步驟中出現，即使禁用。

**啟用購物車裝貨時的庫存檢查** 在預設情況下啟用（設定為「是」）。 要在載入購物車時禁用庫存檢查，請設定 **[!UICONTROL Enable Inventory Check On Cart Load]** 至 `No` 在管理員UI中 **商店** > **配置** > **目錄** > **庫存** > **股票期權** 的子菜單。 請參閱 [配置全局選項][global] 和 [目錄清單][inventory] 的 _使用手冊_。

<!-- link definitions -->

[Apply patches]: https://devdocs.magento.com/cloud/project/project-patch.html
[global]: https://docs.magento.com/user-guide/catalog/inventory-options-global.html
[inventory]: https://docs.magento.com/user-guide/configuration/catalog/inventory.html
[Install extensions]: https://devdocs.magento.com/extensions/install/
[cloud-extensions]: https://devdocs.magento.com/cloud/howtos/install-components.html

[mrg]: https://devdocs.magento.com/guides/v2.4//mrg/intro.html
[非同步順序]: https://devdocs.magento.com/guides/v2.4/mrg/module-async-order.html
[DeferredTotalCalculating]: https://devdocs.magento.com/guides/v2.4/mrg/module-deferred-total-calculating.html
[NegotiableQuoteAsyncOrder]: https://devdocs.magento.com/guides/v2.4/mrg/module-negotiable-quote-async-order.html
