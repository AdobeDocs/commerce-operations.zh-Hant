---
source-git-commit: b63fa9a8b2b59f6e8dfd7003e75c66caf99d5e81
workflow-type: tm+mt
source-wordcount: '81'
ht-degree: 0%

---
# 10月安全性修補程式中包含的Hotfix （2.4.4除外）

此版本包含解決Braintree付款閘道問題的Hotfix。

使用Braintree作為付款閘道時，系統現在包含必要欄位，以履行3DS VISA授權需求。 這可確保所有交易都符合VISA所設定的最新安全性標準。 先前，這些額外欄位未包含在傳送的付款資訊中，這可能會導致不遵守新的VISA要求。

<!--
BUNDLE-3360
-->