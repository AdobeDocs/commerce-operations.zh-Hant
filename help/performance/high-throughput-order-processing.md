---
title: 結帳效能最佳實務
description: 瞭解如何最佳化Adobe Commerce網站上結帳體驗的效能。
feature: Best Practices, Orders
exl-id: dc2d0399-0d7f-42d8-a6cf-ce126e0b052d
source-git-commit: ee7551374aa6d4ad462dd64ee3d05b934b43ce45
workflow-type: tm+mt
source-wordcount: '1121'
ht-degree: 0%

---


# 結帳效能最佳實務

Adobe Commerce中的[結帳](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/point-of-purchase/checkout/checkout-process)程式是店面體驗的關鍵層面。 它仰賴內建的[購物車](https://experienceleague.adobe.com/en/docs/commerce-admin/start/storefront/storefront#shopping-cart)和[結帳](https://experienceleague.adobe.com/en/docs/commerce-admin/start/storefront/storefront#checkout-page)功能。

效能是維持良好使用者體驗的關鍵。 您可以為&#x200B;**高輸送量訂單處理**&#x200B;設定下列選項，以最佳化結帳效能：

- [AsyncOrder](#asynchronous-order-placement) — 使用佇列以非同步方式處理訂單。
- [延後總計計算](#deferred-total-calculation) — 延後訂單總計計算，直到結帳開始。
- [購物車載入時的詳細目錄檢查](#disable-inventory-check) — 選擇略過購物車專案的詳細目錄驗證。
- [負載平衡](#load-balancing) — 啟用MySQL資料庫和Redis執行個體的次要連線。

AsyncOrder、延遲總計計算及購物車載入庫存檢查組態選項都可獨立運作。 您可以同時使用全部三個功能，或以任何組合來啟用和停用功能。

>[!NOTE]
>
>請勿使用自訂PHP程式碼來自訂內建購物車和出庫功能。 除了潛在的效能問題之外，使用自訂PHP程式碼還可能導致複雜的升級和維護挑戰。 這些問題會增加您的總擁有成本。 如果無法避免PHP購物車和結帳自訂，則僅使用[Adobe Commerce Marketplace](https://commercemarketplace.adobe.com/)核准的擴充功能。 所有Marketplace擴充功能都需經過[廣泛檢閱](https://developer.adobe.com/commerce/marketplace/guides/sellers/extension-quality-program/)，才能確認其符合Adobe Commerce程式碼標準和最佳實務。

## 非同步下單

_非同步訂單_&#x200B;模組啟用非同步訂單放置，這會將訂單標示為`received`，將訂單置於佇列中，並以先進先出原則處理佇列中的訂單。 AsyncOrder預設為&#x200B;**已停用**。

例如，客戶新增產品至購物車並選取&#x200B;**[!UICONTROL Proceed to Checkout]**。 他們填寫&#x200B;**[!UICONTROL Shipping Address]**&#x200B;表單、選擇他們偏好的&#x200B;**[!UICONTROL Shipping Method]**、選擇付款方式並下訂單。 購物車已結清，訂單已標示為&#x200B;**[!UICONTROL Received]**，但產品數量尚未調整，也不會傳送銷售電子郵件給客戶。 已收到訂單，但由於訂單尚未完全處理，因此尚未提供訂單詳細資料。 它會保留在佇列中，直到`placeOrderProcess`取用者開始，使用[庫存檢查](#disable-inventory-check)功能驗證訂單（預設為啟用），並更新訂單，如下所示：

- **可用的產品** — 訂單狀態變更為&#x200B;_擱置中_、產品數量已調整、含訂單詳細資料的電子郵件已傳送給客戶，而且成功的訂單詳細資料可在&#x200B;**訂單與退貨**&#x200B;清單中檢視，並包含可操作的選項，例如重新訂購。
- **產品無存貨或供給不足** — 訂單狀態變更為&#x200B;_已拒絕_，未調整產品數量，已傳送一封包含訂單詳細資訊的電子郵件給客戶，且在&#x200B;**訂單與退貨**&#x200B;清單中可以使用已拒絕的訂單詳細資訊，且沒有可操作的選項。

使用命令列介面來啟用這些功能，或根據&#x200B;[_模組參考指南_](https://developer.adobe.com/commerce/php/module-reference/)中定義的對應README檔案來編輯`app/etc/env.php`檔案。

**若要啟用AsyncOrder**：

您可以使用命令列介面啟用AsyncOrder：

```bash
bin/magento setup:config:set --checkout-async 1
```

`set`命令會將下列內容寫入`app/etc/env.php`檔案：

```conf
...
   'checkout' => [
       'async' => 1
   ]
```

請參閱&#x200B;_模組參考指南_&#x200B;中的[非同步訂單](https://developer.adobe.com/commerce/php/module-reference/module-async-order/)。

**停用AsyncOrder**：

>[!WARNING]
>
>在停用AsyncOrder模組之前，您必須確認&#x200B;_所有_&#x200B;非同步訂購程式已完成。

您可以使用命令列介面停用AsyncOrder：

```bash
bin/magento setup:config:set --checkout-async 0
```

`set`命令會將下列內容寫入`app/etc/env.php`檔案：

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
| 付款方法 | 支票/現金訂單<br>交貨付款<br>Braintree<br>PayPal PayFlow Pro |
| 送貨方法 | 支援所有送貨方法。 |

下列功能&#x200B;**不受AsyncOrder支援**，但可繼續同步運作：

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

開發人員可以透過將某些付款方法新增至`Magento\AsyncOrder\Model\OrderManagement::paymentMethods`陣列，將其從非同步訂購中明確排除。 使用已排除付款方法的訂單會同步處理。

### 可轉讓報價非同步訂單

_可轉讓報價非同步訂單_ B2B模組可讓您非同步儲存`NegotiableQuote`功能的訂單專案。 您必須啟用AsyncOrder與NegotialQuote。

## 遞延總計計算

_遞延總計計算_&#x200B;模組會藉由遞延總計計算來最佳化結帳程式，直到購物車要求總計計算或在最終結帳步驟期間為止。 啟用時，只有小計會在客戶新增產品至購物車時計算。

遞延總計計算預設為&#x200B;**停用**。 使用命令列介面來啟用這些功能，或根據&#x200B;[_模組參考指南_](https://developer.adobe.com/commerce/php/module-reference/)中定義的對應README檔案來編輯`app/etc/env.php`檔案。

**若要啟用DeferredTotalCalculation**：

您可以使用命令列介面啟用DeferredTotalCalculation：

```bash
bin/magento setup:config:set --deferred-total-calculating 1
```

`set`命令會將下列內容寫入`app/etc/env.php`檔案：

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

`set`命令會將下列內容寫入`app/etc/env.php`檔案：

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 0
   ]
```

請參閱&#x200B;_模組參考指南_&#x200B;中的[DeferredTotalCalculating](https://developer.adobe.com/commerce/php/module-reference/module-deferred-total-calculating/)。

### 固定產品稅金

啟用遞延總計計算時，將產品新增至購物車後，固定產品稅(FPT)不會納入迷你購物車的產品價格與購物車小計中。 將產品新增至迷你購物車時，FPT計算會延遲。 繼續進行最終結帳之後，FPT會在購物車中正確顯示。

## 停用詳細目錄檢查

_在購物車載入時啟用詳細目錄_&#x200B;全域設定決定在購物車載入產品時是否執行詳細目錄檢查。 停用庫存檢查程式可改善所有結帳步驟的效能，尤其是處理購物車中的大量產品時。

停用時，將產品新增到購物車時不會進行詳細目錄檢查。 如果跳過此庫存檢查，則某些缺貨情況可能會擲回其他型別的錯誤。 庫存檢查&#x200B;_一律_&#x200B;會發生在訂單放置步驟，即使停用也一樣。

**購物車載入時啟用存貨檢查**&#x200B;預設為啟用（設定為「是」）。 若要在載入購物車時停用詳細目錄檢查，請在管理UI **商店** > **設定** > **目錄** > **詳細目錄** > **庫存選項**&#x200B;區段中，將&#x200B;**[!UICONTROL Enable Inventory Check On Cart Load]**&#x200B;設定為`No`。 請參閱&#x200B;_使用手冊_&#x200B;中的[設定全域選項](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/configuration/global-options)和[目錄詳細目錄](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/guide-overview)。

## 負載平衡

您可以啟用MySQL資料庫和Redis執行個體的次要連線，協助平衡不同節點的負載。

Adobe Commerce可以非同步方式讀取多個資料庫或Redis執行個體。 如果您在雲端基礎結構上使用Commerce，您可以編輯`.magento.env.yaml`檔案中的[MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#mysql_use_slave_connection)和[REDIS_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#redis_use_slave_connection)值來設定次要連線。 只有一個節點需要處理讀寫流量，因此將變數設定為`true`會導致建立唯讀流量的次要連線。 將值設定為`false`以從`env.php`檔案中移除任何現有的唯讀連線陣列。

`.magento.env.yaml`檔案的範例：

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true
```
