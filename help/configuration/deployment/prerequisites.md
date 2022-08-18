---
title: 部署的先決條件
description: 請參閱將Commerce部署到開發、構建或生產系統的先決條件清單。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---


# 開發、構建和生產系統的先決條件

檔案權限和所有權必須在開發、構建和生產系統之間保持一致。 要使此功能有效，您必須執行以下任一操作：

- 以下所有事項：

   - 設定相同 [檔案系統所有者](https://glossary.magento.com/magento-file-system-owner) 所有系統的用戶名
   - 確保Web伺服器在所有系統上以同一用戶身份運行
   - 確保檔案系統所有者位於所有系統的Web伺服器組中

- 根據需要，使用以下准則更改Commerce檔案系統權限和每個系統的所有權：

   - 開發和構建： [設定預安裝所有權和權限（兩個用戶）](file-system-permissions.md#set-up-two-owners-for-default-or-developer-mode)
   - 生產： [商業所有權和開發和生產許可](file-system-permissions.md)

>[!INFO]
>
>如果選擇此方法，則每次從生成系統中提取代碼時，都必須設定檔案系統權限和所有權（如果生成系統上的檔案系統所有者或Web伺服器用戶不同）。