---
title: 「 [!UICONTROL Redis] 標籤」
description: 了解 [!UICONTROL Redis] 標籤 [!DNL Observation for Adobe Commerce].
source-git-commit: f4379d0b89a6ea6d2f2a5a02c505581d4d54708f
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%

---

# 此 [!DNL Redis] 標籤

## [!UICONTROL Redis Node summary]

![Redis節點摘要](../../assets/tools/observation-for-adobe-commerce/redis-tab-1.jpg)

此 **[!UICONTROL Redis Node summary]** 包含環境中的所有節點。 上述範例包含共用中繼的節點。 生產環境中有一個主節點和兩個輔助節點，在測試環境中有一個主節點和兩個輔助節點。

## [!UICONTROL Redis node detail]

![密文節點詳細資訊](../../assets/tools/observation-for-adobe-commerce/redis-tab-2.jpg)

此 **[!UICONTROL Redis node detail]** 框指示環境， [!DNL Redis] 角色、軟體版本和節點大小。

## [!UICONTROL Redis node roles timeline]

![密文節點角色時間軸](../../assets/tools/observation-for-adobe-commerce/redis-tab-3.jpg)

此 **[!UICONTROL Redis node roles timeline]** frame表示 [!DNL Redis] 服務。 如果線條下降，表示該線所代表的特定角色已失去節點或節點。

## [!UICONTROL Connection to Redis]

![與Redis的連接](../../assets/tools/observation-for-adobe-commerce/redis-tab-4.jpg)

此 **[!UICONTROL Connection to Redis]** frame顯示net.connectedClients值，來自 [!DNL New Relic Redis] 範例資料。 它顯示連接計數 [!DNL New Relic] 應用程式（環境）和節點。

## [!UICONTROL Commands per second by node]

![每秒按節點顯示的命令數](../../assets/tools/observation-for-adobe-commerce/redis-tab-5.jpg)

此 **[!UICONTROL Commands per second by node]** 框顯示 [!DNL Redis] 按節點在所選時間範圍內每秒的命令。

## [!UICONTROL Redis % of memory used]

![已用記憶體的密文%](../../assets/tools/observation-for-adobe-commerce/redis-tab-6.jpg)

此 **[!UICONTROL Redis % of memory used]** frame顯示 [!DNL Redis] 伺服器。

## [!UICONTROL Redis used memory]

![Redis已用記憶體](../../assets/tools/observation-for-adobe-commerce/redis-tab-7.jpg)

此 **[!UICONTROL Redis used memory]** frame顯示節點記憶體的使用（以GB/MB為單位）。

## [!UICONTROL Redis changes since last db save]

![自上次儲存資料庫後進行的更改](../../assets/tools/observation-for-adobe-commerce/redis-tab-8.jpg)

[!DNL Redis] 是記憶體駐留器，並將資訊保存到儲存器。 此 **[!UICONTROL Redis changes since last db save]** frame指示自上次將資料庫保存到儲存器後發生的記憶體更改的數量。 請參閱 [Redis持續性](https://redis.io/docs/manual/persistence/) 以取得更多說明 [!DNL Redis's] 持續性。

## [!UICONTROL Redis synchronization from Log]

![從日誌中編輯同步](../../assets/tools/observation-for-adobe-commerce/redis-tab-9.jpg)

此 **[!UICONTROL Redis synchronization from Log]** 框架著重於 [!DNL Redis] 由於同步問題而發生的同步或錯誤。 如需 [!DNL Redis]，請參閱 [[!DNL Redis] 檔案](https://redis.io/docs/).
