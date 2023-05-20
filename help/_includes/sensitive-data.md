---
source-git-commit: 475dbc056ac3e6a00c8f794259bb0fbf04143687
workflow-type: tm+mt
source-wordcount: '72'
ht-degree: 0%

---
# 敏感資料

Adobe Commerce和Magento Open Source使用您的加密密鑰加密以下內容：

* 信用卡資訊
* 在管理配置中指定的用戶名和密碼（例如，登錄到付款網關）
* 通過網路發送的驗證碼值

Adobe Commerce和Magento Open Source *不* 加密：

* 管理和客戶用戶名和密碼（這些密碼已散列）
* 地址
* 電話號碼
* 除信用卡號外的其他個人身份資訊類型
