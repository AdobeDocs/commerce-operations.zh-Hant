---
title: 高吞吐量訂單處理
description: 針對您的Adobe Commerce或Magento Open Source部署，最佳化訂單位置和結帳體驗。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '1046'
ht-degree: 0%

---


# 高吞吐量訂單處理

您可以為 **高吞吐量訂單處理**:

- [AsyncOrder](#asynchronous-order-placement) — 使用隊列非同步處理訂單。
- [延期的總計計算](#deferred-total-calculation) — 預先計算訂單總計，直到結帳開始。
- [報價載入時的庫存檢查](#disable-inventory-check) — 選擇跳過購物車項目的庫存驗證。

所有功能（AsyncOrder、Deferred Total Calculation和Inventory Check）均獨立工作。 您可以同時使用這三個功能，或以任何組合來啟用和停用功能。

## 非同步訂單放置

此 _非同步順序_ 模組會啟用非同步訂單放置，這會將訂單標示為 `received`，會將訂單放入佇列中，並以先入先出的方式處理佇列中的訂單。 AsyncOrder為 **停用** 依預設。

例如，客戶新增產品至購物車並選取 **[!UICONTROL Proceed to Checkout]**. 他們把 **[!UICONTROL Shipping Address]** 表單，選擇其首選 **[!UICONTROL Shipping Method]**，請選擇付款方法並下訂單。 購物車已清除，訂單標示為 **[!UICONTROL Received]**，但產品數量尚未調整，也未傳送銷售電子郵件給客戶。 已接收訂單，但訂單詳細資訊尚未提供，因為訂單尚未完全處理。 會保留在佇列中，直到 `placeOrderProcess` 消費者開始，驗證訂單 [詳細目錄檢查](#disable-inventory-check) 功能（預設為啟用），並依照下列順序更新：

- **可用產品** — 訂單狀態更改為 _待定_，產品數量會調整，並傳送包含訂單詳細資料的電子郵件給客戶，而成功的訂單詳細資料便可在 **訂購與退貨** 清單中包含可操作的選項，例如重新排序。
- **產品無存貨或供應不足** — 訂單狀態更改為 _已拒絕_，產品數量不會調整，會傳送包含問題訂單詳細資料的電子郵件給客戶，而拒絕的訂單詳細資料可在 **訂購與退貨** 清單，沒有可操作的選項。

使用命令行介面啟用這些功能，或編輯 `app/etc/env.php` 檔案，根據 [_模組參考指南_][mrg].

**啟用AsyncOrder的方式**:

您可以使用命令列介面來啟用AsyncOrder :

```bash
bin/magento setup:config:set --checkout-async 1
```

此 `set` 命令會將下列內容寫入 `app/etc/env.php` 檔案：

```conf
...
   'checkout' => [
       'async' => 1
   ]
```

請參閱 [AsyncOrder] 在 _模組參考指南_.

**停用AsyncOrder的方式**:

>[!WARNING]
>
>在停用AsyncOrder模組之前，您必須確認 _all_ 非同步訂單流程已完成。

您可以使用命令列介面停用AsyncOrder :

```bash
bin/magento setup:config:set --checkout-async 0
```

此 `set` 命令會將下列內容寫入 `app/etc/env.php` 檔案：

```conf
...
   'checkout' => [
       'async' => 0
   ]
```

### AsyncOrder相容性

AsyncOrder支援有限的 [!DNL Commerce] 功能。

| 類別 | 支援的功能 |
|---------------- | -----------------------|
| 結帳類型 | OnePage結帳<br>標準結帳<br>B2B可轉讓報價 |
| 付款方法 | 支票/貨幣訂單<br>交付時現金<br>Braintree<br>PayPal PayFlow Pro |
| 運送方法 | 支援所有運送方法。 |

下列功能為 **not** Order支援，但可繼續同步運作：

- 支援的功能清單中未包含的付款方法
- 多地址結帳
- 建立管理順序

#### 網頁API支援

啟用AsyncOrder模組後，以下REST端點和GraphQL突變會以非同步方式運行：

**休息：**

- `POST /V1/carts/mine/payment-information`
- `POST /V1/guest-carts/:cartId/payment-information`
- `POST /V1/negotiable-carts/:cartId/payment-information`

**GraphQL:**

- [`placeOrder`](https://devdocs.magento.com/guides/v2.4/graphql/mutations/place-order.html)
- [`setPaymentMethodAndPlaceOrder`](https://devdocs.magento.com/guides/v2.4/graphql/mutations/set-payment-place-order.html)

>[!INFO]
>
>GraphQL不支援以非同步方式下單。

#### 排除付款方法

開發人員可將某些付款方法新增至 `Magento\AsyncOrder\Model\OrderManagement::paymentMethods` 陣列。 使用排除付款方法的訂單會同步處理。

### 非同步報價

此 _非同步報價_ B2B模組可讓您以非同步方式儲存 `NegotiableQuote` 功能。 您必須啟用AsyncOrder和PonageQuote。

## 延期的總計計算

此 _延期的總計計算_ 模組會延遲計算總計，直到購物車請求或最終結帳步驟為止，借此最佳化結帳程式。 啟用後，只有小計會計算為客戶新增產品至購物車。

DeferredTotalCalculation為 **停用** 依預設。 使用命令行介面啟用這些功能，或編輯 `app/etc/env.php` 檔案，根據 [_模組參考指南_][mrg].

**啟用DeferedTotalCalculation**:

您可以使用命令行介面啟用DeferredTotalCalculation:

```bash
bin/magento setup:config:set --deferred-total-calculating 1
```

此 `set` 命令會將下列內容寫入 `app/etc/env.php` 檔案：

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

此 `set` 命令會將下列內容寫入 `app/etc/env.php` 檔案：

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 0
   ]
```

請參閱 [DeferredTotalCalculating] 在 _模組參考指南_.

### 固定產品稅

啟用DeferredTotalCalculation後，在將產品新增至購物車後，固定產品稅(FPT)不會包含在迷你購物車的產品價格和購物車小計中。 將產品新增至迷你購物車時，會延遲FPT計算。 繼續進行最後結帳後，FPT會正確顯示在購物車中。

## 禁用清單檢查

此 _啟用購物車載入時的庫存_ 全域設定決定在購物車中載入產品時是否執行庫存檢查。 停用庫存檢查程式可改善所有結帳步驟的效能，尤其是處理購物車中的大量產品時。

停用時，將產品新增至購物車時不會進行庫存檢查。 如果跳過此庫存檢查，某些庫存不足的情況可能會引發其他類型的錯誤。 清單檢查 _always_ 會在訂單放置步驟發生，即使停用亦然。

**對購物車載入啟用庫存檢查** 預設為啟用（設為「是」）。 若要在載入購物車時停用庫存檢查，請設定 **[!UICONTROL Enable Inventory Check On Cart Load]** to `No` 在管理員UI中 **商店** > **設定** > **目錄** > **庫存** > **股票期權** 區段。 請參閱 [配置全局選項][global] 和 [目錄清單][inventory] 在 _使用手冊_.

## 負載平衡

通過為MySQL資料庫和Redis實例啟用輔助連接，可以幫助平衡不同節點間的負載。

Adobe Commerce可以非同步讀取多個資料庫或Redis例項。 如果您在雲端基礎架構上使用Commerce，則可編輯 [MYSQL_USE_SLAVE_CONNECTION](https://devdocs.magento.com/cloud/env/variables-deploy.html#mysql_use_slave_connection) 和 [REDIS_USE_SLAVE_CONNECTION](https://devdocs.magento.com/cloud/env/variables-deploy.html#redis_use_slave_connection) 值 `.magento.env.yaml` 檔案。 只需要一個節點來處理讀寫通信量，因此將變數設定為 `true` 導致為只讀流量建立輔助連接。 將值設定為 `false` 從 `env.php` 檔案。

範例 `.magento.env.yaml` 檔案：

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true
```

<!-- link definitions -->

[global]: https://docs.magento.com/user-guide/catalog/inventory-options-global.html
[inventory]: https://docs.magento.com/user-guide/configuration/catalog/inventory.html
[mrg]: https://developer.adobe.com/commerce/php/module-reference/
[AsyncOrder]: https://developer.adobe.com/commerce/php/module-reference/module-async-order/
[DeferredTotalCalculating]: https://developer.adobe.com/commerce/php/module-reference/module-deferred-total-calculating/
