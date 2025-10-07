---
title: '[!UICONTROL Redis]索引標籤'
description: 瞭解[!UICONTROL Redis]的 [!DNL Observation for Adobe Commerce]標籤。
exl-id: 9c52350d-45a7-4afe-9dd7-c3968bd84d71
feature: Configuration, Observability
source-git-commit: 4caabd1578e56b74600441c9c779b7b2dfd06987
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# [!DNL Redis]索引標籤

## [!UICONTROL Redis Node summary]

![Redis節點摘要](../../assets/tools/observation-for-adobe-commerce/redis-tab-1.jpg)

**[!UICONTROL Redis Node summary]**&#x200B;包含環境中的所有節點。 上述範例包含共用中繼的節點。 生產環境有一個主要和兩個次要環境，而中繼環境也有一個主要和兩個次要環境。

## [!UICONTROL Redis node detail]

![Redis伺服器效能度量和節點組態詳細資料](../../assets/tools/observation-for-adobe-commerce/redis-tab-2.jpg)

**[!UICONTROL Redis node detail]**&#x200B;框架表示環境、[!DNL Redis]角色、軟體版本和節點大小。

## [!UICONTROL Redis node roles timeline]

![Redis節點角色時間表](../../assets/tools/observation-for-adobe-commerce/redis-tab-3.jpg)

**[!UICONTROL Redis node roles timeline]**&#x200B;框架表示特定角色中遺失[!DNL Redis]服務。 如果折線下降，則表示折線所代表的特定角色已失去一或多個節點。

## [!UICONTROL Connection to Redis]

![連線到Redis](../../assets/tools/observation-for-adobe-commerce/redis-tab-4.jpg)

**[!UICONTROL Connection to Redis]**&#x200B;框架顯示[!DNL New Relic Redis]範例資料中的net.connectedClients值。 它顯示[!DNL New Relic]應用程式（環境）和節點的連線計數。

## [!UICONTROL Commands per second by node]

節點![每秒的](../../assets/tools/observation-for-adobe-commerce/redis-tab-5.jpg)個命令

**[!UICONTROL Commands per second by node]**&#x200B;影格會在選取的時間範圍內每秒依節點顯示[!DNL Redis]命令。

## [!UICONTROL Redis % of memory used]

已使用記憶體的![Redis %](../../assets/tools/observation-for-adobe-commerce/redis-tab-6.jpg)

**[!UICONTROL Redis % of memory used]**&#x200B;框架顯示[!DNL Redis]伺服器使用的最大記憶體百分比。

## [!UICONTROL Redis used memory]

![Redis已使用的記憶體](../../assets/tools/observation-for-adobe-commerce/redis-tab-7.jpg)

**[!UICONTROL Redis used memory]**&#x200B;框架顯示記憶體的節點使用量(GB/MB)。

## [!UICONTROL Redis changes since last db save]

![自上次db儲存後的Redis變更](../../assets/tools/observation-for-adobe-commerce/redis-tab-8.jpg)

[!DNL Redis]是記憶體駐留，並將資訊儲存到儲存空間。 **[!UICONTROL Redis changes since last db save]**&#x200B;框架表示自上次資料庫儲存至儲存體後發生的記憶體變更次數。 如需[持續性的詳細解釋，請參閱](https://redis.io/docs/latest/operate/oss_and_stack/management/persistence/)Redis持續性[!DNL Redis's]。

## [!UICONTROL Redis synchronization from Log]

![記錄檔的Redis同步處理](../../assets/tools/observation-for-adobe-commerce/redis-tab-9.jpg)

**[!UICONTROL Redis synchronization from Log]**&#x200B;框架著重於在[!DNL Redis]同步處理期間遇到的錯誤，或因同步處理問題而發生的錯誤。 如需[!DNL Redis]的詳細資訊，請參閱[[!DNL Redis] 檔案](https://redis.io/docs/)。
