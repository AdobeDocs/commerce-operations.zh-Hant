---
source-git-commit: 475dbc056ac3e6a00c8f794259bb0fbf04143687
workflow-type: tm+mt
source-wordcount: '72'
ht-degree: 0%

---
# 敏感資料

Adobe Commerce和Magento Open Source會使用您的加密金鑰加密下列項目：

* 信用卡資訊
* 在管理配置中指定的用戶名和密碼（例如，登錄支付網關）
* 透過網路傳送的驗證碼值

Adobe Commerce和Magento Open Sourcedo *not* 加密：

* 管理用戶名和客戶用戶名和密碼（這些密碼為雜湊）
* 地址
* 電話號碼
* 除信用卡號外的其他個人識別資訊類型
