---
title: 部署的先決條件
description: 請參閱將商務部署至開發、建置或生產系統的必要條件清單。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---


# 開發、建置和生產系統的必要條件

檔案權限和所有權必須在開發、構建和生產系統之間保持一致。 若要讓此功能發揮作用，您必須：

- 以下所有事項：

   - 在所有系統上設定相同的檔案系統所有者用戶名
   - 確保Web伺服器在所有系統上以同一用戶身份運行
   - 確保檔案系統所有者位於所有系統上的Web伺服器組中

- 根據需要，使用以下准則更改每個系統的商務檔案系統權限和所有權：

   - 開發與建置： [設定安裝前的所有權和權限（兩個用戶）](file-system-permissions.md#set-up-two-owners-for-default-or-developer-mode)
   - 生產： [開發和生產中的商務所有權和權限](file-system-permissions.md)

>[!INFO]
>
>如果您選擇此方法，則每次從構建系統提取代碼時（如果構建系統上的檔案系統所有者或Web伺服器用戶不同），必須設定檔案系統權限和所有權。
