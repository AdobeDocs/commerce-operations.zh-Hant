---
title: 結帳效能最佳實務
description: 瞭解如何最佳化Adobe Commerce網站上結帳體驗的效能。
feature: Best Practices, Orders
exl-id: dc2d0399-0d7f-42d8-a6cf-ce126e0b052d
source-git-commit: e4c1832076bb81cd3e70ff279a6921ffb29ea631
workflow-type: tm+mt
source-wordcount: '1132'
ht-degree: 0%

---


# 結帳效能最佳實務

此 [簽出](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/point-of-purchase/checkout/checkout-process) Adobe Commerce中的程式是店面體驗的關鍵層面。 此功能需仰賴內建的 [購物車](https://experienceleague.adobe.com/en/docs/commerce-admin/start/storefront/storefront#shopping-cart) 和 [簽出](https://experienceleague.adobe.com/en/docs/commerce-admin/start/storefront/storefront#checkout-page) 功能。

效能是維持良好使用者體驗的關鍵。 檢閱 [效能基準摘要](../implementation-playbook/infrastructure/performance/benchmarks.md) 以進一步瞭解效能期望。 您可以配置下列選項以最佳化簽出效能 **高輸送量訂單處理**：

- [AsyncOrder](#asynchronous-order-placement) — 使用佇列以非同步方式處理訂單。
- [遞延總計計算](#deferred-total-calculation) — 將訂單總計的計算延遲到結帳開始。
- [購物車載入時的詳細目錄檢查](#disable-inventory-check) — 選擇略過購物車專案的詳細目錄驗證。
- [負載平衡](#load-balancing) — 啟用MySQL資料庫和Redis執行個體的次要連線。

AsyncOrder、延遲總計計算及購物車載入庫存檢查組態選項都可獨立運作。 您可以同時使用全部三個功能，或以任何組合來啟用和停用功能。

>[!NOTE]
>
>請勿使用自訂PHP程式碼來自訂內建購物車和出庫功能。 除了潛在的效能問題之外，使用自訂PHP程式碼還可能導致複雜的升級和維護挑戰。 這些問題會增加您的總擁有成本。 如果無法避免以PHP為基礎的購物車和結帳自訂，請使用 [Adobe Commerce Marketplace](https://commercemarketplace.adobe.com/)僅核准的擴充功能。 所有Marketplace擴充功能皆須遵守 [廣泛檢閱](https://developer.adobe.com/commerce/marketplace/guides/sellers/extension-quality-program/) 以確認其符合Adobe Commerce編碼標準和最佳實務。

## 非同步下單

此 _非同步順序_ 模組會啟用非同步下單，這會將訂單標示為 `received`，可將訂單放入佇列中，並以先進先出原則處理佇列中的訂單。 非同步順序為 **已停用** 依預設。

例如，客戶將產品新增至購物車並選取 **[!UICONTROL Proceed to Checkout]**. 他們填寫 **[!UICONTROL Shipping Address]** 表單，選取其偏好設定 **[!UICONTROL Shipping Method]**，選取付款方式並下訂單。 購物車已清除，訂單已標籤為 **[!UICONTROL Received]**，但產品數量尚未調整，也不會傳送銷售電子郵件給客戶。 已收到訂單，但由於訂單尚未完全處理，因此尚未提供訂單詳細資料。 它會保留在佇列中，直到 `placeOrderProcess` 消費者開始，驗證訂單 [詳細目錄檢查](#disable-inventory-check) 功能（預設為啟用），並依照以下方式更新順序：

- **可用的產品** — 訂單狀態變更為 _擱置中_，則會調整產品數量，傳送一封包含訂單詳細資料的電子郵件給客戶，而成功的訂單詳細資料則可在 **訂購與退貨** 列出可操作選項，例如重新排序。
- **產品無存貨或供給不足** — 訂單狀態變更為 _已拒絕_，產品數量不會調整，會傳送一封電子郵件給客戶，其中包含問題的訂單詳細資料，而遭到拒絕的訂單詳細資料會顯示在 **訂購與退貨** 沒有可操作選項的清單。

使用指令行介面來啟用這些功能，或編輯 `app/etc/env.php` 檔案中定義的對應README檔案 [_模組參考指南_](https://developer.adobe.com/commerce/php/module-reference/).

**啟用AsyncOrder**：

您可以使用命令列介面啟用AsyncOrder：

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

另請參閱 [AsyncOrder](https://developer.adobe.com/commerce/php/module-reference/module-async-order/) 在 _模組參考指南_.

**停用AsyncOrder**：

>[!WARNING]
>
>在停用AsyncOrder模組之前，您必須確認 _全部_ 非同步訂購程式已完成。

您可以使用命令列介面停用AsyncOrder：

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

AsyncOrder支援有限的Adobe Commerce功能集。

| 類別 | 支援的功能 |
|------------------|--------------------------------------------------------------------------|
| 簽出型別 | OnePage簽出<br>標準簽出<br>B2B可轉讓報價 |
| 付款方法 | 支票/匯票<br>貨到付款<br>Braintree<br>PayPal PayFlow Pro |
| 送貨方法 | 支援所有送貨方法。 |

下列功能為 **非** AsyncOrder支援，但可繼續同步運作：

- 支援的功能清單中未包含付款方法
- 多位址簽出
- 管理訂單建立

#### Web API支援

啟用AsyncOrder模組後，下列REST端點和GraphQL變動會以非同步方式執行：

**REST：**

- [`POST /V1/carts/mine/payment-information`](https://adobe-commerce.redoc.ly/2.4.7-admin/tag/cartsminepayment-information#operation/PostV1CartsMinePaymentinformation)
- [`POST /V1/guest-carts/{cartId}/payment-information`](https://adobe-commerce.redoc.ly/2.4.7-admin/tag/guest-cartscartIdpayment-information#operation/PostV1GuestcartsCartIdPaymentinformation)
- [`POST /V1/negotiable-carts/{cartId}/payment-information`](https://adobe-commerce.redoc.ly/2.4.7-admin/tag/negotiable-cartscartIdpayment-information#operation/PostV1NegotiablecartsCartIdPaymentinformation)

**GraphQL：**

- [`placeOrder`](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/place-order/)
- [`setPaymentMethodAndPlaceOrder`](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/set-payment-place-order/)

>[!INFO]
>
>GraphQL不支援以非同步方式放置可轉讓的報價單。

#### 排除付款方法

開發人員可將某些付款方法新增至「 」，以明確將其從非同步下單中排除 `Magento\AsyncOrder\Model\OrderManagement::paymentMethods` 陣列。 使用已排除付款方法的訂單會同步處理。

### 可轉讓報價非同步訂單

此 _可轉讓報價非同步訂單_ B2B模組可讓您以非同步方式為 `NegotiableQuote` 功能。 您必須啟用AsyncOrder與NegotialQuote。

## 遞延總計計算

此 _遞延總計計算_ 模組會藉由將總計算推延至對購物車提出要求或在最後結帳步驟期間，來最佳化結帳程式。 啟用時，只有小計會在客戶新增產品至購物車時計算。

遞延總計計算為 **已停用** 依預設。 使用指令行介面來啟用這些功能，或編輯 `app/etc/env.php` 檔案中定義的對應README檔案 [_模組參考指南_](https://developer.adobe.com/commerce/php/module-reference/).

**啟用DeferredTotalCalculation**：

您可以使用命令列介面啟用DeferredTotalCalculation：

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

**若要停用DeferredTotalCalculation**：

您可以使用命令列介面停用DeferredTotalCalculation：

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

另請參閱 [DeferredTotalCalculating](https://developer.adobe.com/commerce/php/module-reference/module-deferred-total-calculating/) 在 _模組參考指南_.

### 固定產品稅金

啟用遞延總計計算時，將產品新增至購物車後，固定產品稅(FPT)不會納入迷你購物車的產品價格與購物車小計中。 將產品新增至迷你購物車時，FPT計算會延遲。 繼續進行最終結帳之後，FPT會在購物車中正確顯示。

## 停用詳細目錄檢查

此 _在購物車載入時啟用詳細目錄_ 全域設定決定在購物車中載入產品時是否執行庫存檢查。 停用庫存檢查程式可改善所有結帳步驟的效能，尤其是處理購物車中的大量產品時。

停用時，將產品新增到購物車時不會進行詳細目錄檢查。 如果跳過此庫存檢查，則某些缺貨情況可能會擲回其他型別的錯誤。 詳細目錄檢查 _一直_ 在訂購步驟中發生，即使停用亦然。

**在購物車載入時啟用詳細目錄檢查** 預設為啟用（設定為「是」）。 若要在載入購物車時停用詳細目錄檢查，請設定 **[!UICONTROL Enable Inventory Check On Cart Load]** 至 `No` 在Admin UI中 **商店** > **設定** > **目錄** > **詳細目錄** > **股票期權** 區段。 另請參閱 [設定全域選項](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/configuration/global-options) 和 [目錄詳細目錄](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/guide-overview) 在 _使用手冊_.

## 負載平衡

您可以啟用MySQL資料庫和Redis執行個體的次要連線，協助平衡不同節點的負載。

Adobe Commerce可以非同步方式讀取多個資料庫或Redis執行個體。 如果您在雲端基礎結構上使用Commerce，您可以透過編輯 [MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#mysql_use_slave_connection) 和 [REDIS_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#redis_use_slave_connection) 中的值 `.magento.env.yaml` 檔案。 只有一個節點需要處理讀寫流量，因此將變數設定為 `true` 會導致建立唯讀流量的次要連線。 將值設為 `false` 以從移除任何現有的唯讀連線陣列 `env.php` 檔案。

範例 `.magento.env.yaml` 檔案：

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true
```
