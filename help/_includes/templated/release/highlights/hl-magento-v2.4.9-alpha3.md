---
source-git-commit: 233ff6d5de2f4da3d477e70d066dd5cd46c771ee
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---
# Magento Open Source發行說明(v2.4.9-alpha3)

## v2.4.9-alpha3中的醒目提示

下列重點適用於Magento Open Source 2.4.9-alpha3版本。

### Braintree

#### 透過帳戶區域儲存Google Pay

在Magento 2.4.9-alpha3中，當在Braintree中啟用Google Pay Vault時，客戶現在可以透過帳戶區域儲存其Google Pay卡片。 儲存的卡片會顯示在已儲存的付款方式下，可用於結帳時未來的購買，並可由客戶刪除。 這將儲存庫支援擴展到卡片和PayPal之外，擴展到Google Pay。

_BUNDLE-3459_

#### 將Magento訂單連結至Braintree入口網站訂單

在Magento 2.4.9-alpha3中，Braintree入口網站連結現在已新增到Magento管理員中的訂單詳細資料。 按一下連結，使用Magento訂單中的貿易商ID和交易ID，在Braintree入口網站（在新標籤中）中開啟相關交易。 如此一來，不需分別登入兩個系統，即可直接交叉參照。

_BUNDLE-3461_

#### 即時帳戶更新程式(RTAU)

適用於Braintree的Magento 2.4.9-alpha3中的即時帳戶更新程式(RTAU)功能可確保當卡到期或被取代時，儲存的Visa、萬事達卡和Discover卡詳細資料會自動更新。 這樣可將失敗的付款減至最少，使Magento Vault保持最新狀態，並跳過不支援的型別(預付、Apple支付、Google支付)，而不會發生錯誤。

_BUNDLE-3462_

#### Braintree卡付款的ELO卡型別支援

在Magento 2.4.9-alpha3中，Braintree支付已新增對ELO卡型別的支援。 管理員現在可以在信用卡設定中啟用ELO，客戶可以在結帳時使用ELO卡成功下訂單，確保透過Braintree進行順暢的交易。

_BUNDLE-3464_

### 框架

#### 從RabbitMQ移轉至Apache ActiveMQ

_AC-14558_

#### 將chart.js相依性升級至最新版本

chart.js相依性已升級至最新版本4.5.0

_AC-15133 - [GitHub程式碼貢獻](https://github.com/magento/magento2/commit/657f983e)_

#### 從Laminas MVC移轉

Adobe Commerce已引進原生MVC實作，取代舊有的Laminas MVC，以確保超越PHP 8.5的長期相容性和穩定性。此變更可增強效能、減少外部相依性，並為Commerce提供更符合未來需求的基礎

_AC-15160_
