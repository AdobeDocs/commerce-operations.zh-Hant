---
title: 「 [!DNL Infra] 標籤」
description: 此 [!DNL Infra] tab可隔離基礎架構問題和原因。
source-git-commit: 38467ebd2ec29f9e1679182fb1ee7076d738664b
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---


# 此 [!DNL Infra] 標籤

此 **[!DNL Infra]** tab可隔離基礎架構問題和原因。 進一步說明可在索引標籤上看到的框架。

## [!UICONTROL Service Alerts – Infrastructure Alerts by Application name]

![服務警報](../../assets/tools/observation-for-adobe-commerce/service-alerts.jpg)

此 **[!UICONTROL Service Alerts – Infrastructure Alerts by Application name]** 圖表顯示 [!DNL New Relic] 基礎設施代理。 這將顯示服務重新啟動，其中許多與部署相關。

## [!UICONTROL Inode usage by mount]

![按裝載使用Inode](../../assets/tools/observation-for-adobe-commerce/inode-usage-mount.jpg)

此 **[!UICONTROL Inode usage by mount]** 影格播放 [!DNL inode] 在所選時間範圍內裝載使用。 即使儲存空間可能足夠，如果節點用完 [!DNL inodes]，則會顯示缺少可用的儲存。 移除檔案（尤其是小檔案）將可釋放兩個空間，並 [!DNL inodes] 可用。

## [!UICONTROL vCPU tier view over timeline GREATER 2 weeks]

![跨時間軸的vCPU層查看時間更長2週](../../assets/tools/observation-for-adobe-commerce/vCPU-tier.jpg)

此 **[!UICONTROL vCPU tier view over timeline GREATER 2 weeks]** frame會顯示在超過兩週的選定時間範圍內的vCPU層視圖。 此幀會查看分配給 [!DNL New Relic] 顯示的應用程式名稱。

## [!UICONTROL vCPU tier view over timeline]

![跨時間軸的vCPU層視圖](../../assets/tools/observation-for-adobe-commerce/vcpu-tier-24.jpg)

此 **[!UICONTROL vCPU tier view over timeline]** frame會顯示在24小時以上的選定時間範圍內的vCPU層視圖。 此幀會查看分配給 [!DNL New Relic] 顯示的應用程式名稱。 它將顯示群集的更大和縮減大小。

## [!UICONTROL vCPU tier view over timeline BY NODE]

![按NODE跨時間表的vCPU層視圖](../../assets/tools/observation-for-adobe-commerce/infra_by_node.png)

此 **[!UICONTROL vCPU tier view over timeline BY NODE]** frame會依節點顯示所選時間範圍內的vCPU層視圖。 此幀有助於檢測節點丟失或節點過大或過小時。 通過時間軸（按節點）查看的vCPU層次，應查看不到24小時的時間軸。

## [!UICONTROL Instance details]

![執行個體詳細資訊](../../assets/tools/observation-for-adobe-commerce/instance-details.jpg)

此 **[!UICONTROL Instance details]** 表格顯示每個 [!DNL New Relic] 應用程式。

## [!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]

![非回應式節點](../../assets/tools/observation-for-adobe-commerce/non-responsive-node.jpg)

此 **[!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]** frame會顯示一個時段內的非回應式節點。
