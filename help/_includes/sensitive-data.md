---
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '64'
ht-degree: 1%

---
# 敏感資料

Adobe Commerce會使用您的加密金鑰來加密下列專案：

* 信用卡資訊
* 在管理員設定中指定的使用者名稱和密碼（例如，登入付款閘道）
* 透過網路傳送的驗證碼值

Adobe Commerce do *非* 加密：

* 管理和客戶使用者名稱及密碼（這些密碼會經過雜湊處理）
* 地址
* 電話號碼
* 除信用卡號碼以外的其他個人識別資訊
