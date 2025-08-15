---
title: ' [!DNL Infra] 標籤'
description: ' [!DNL Infra] 索引標籤可隔離基礎架構問題的問題和原因。'
exl-id: 45f24177-3264-4848-99bc-951be32c1f7b
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 0%

---

# [!DNL Infra]索引標籤

**[!DNL Infra]**&#x200B;索引標籤可隔離基礎架構問題的問題和原因。 進一步說明您可以在標籤上看到的框架。

## [!UICONTROL Service Alerts – Infrastructure Alerts by Application name]

![服務警示](../../assets/tools/observation-for-adobe-commerce/service-alerts.jpg)

**[!UICONTROL Service Alerts – Infrastructure Alerts by Application name]**&#x200B;圖表顯示[!DNL New Relic]基礎結構代理程式所收集的服務警示。 這會顯示服務重新啟動，其中許多與部署有關。

## [!UICONTROL Inode usage by mount]

![依掛載的Inode使用量](../../assets/tools/observation-for-adobe-commerce/inode-usage-mount.jpg)

**[!UICONTROL Inode usage by mount]**&#x200B;框架顯示所選時間範圍內掛載的[!DNL inode]使用量。 即使可能有足夠的可用儲存空間，如果節點用完[!DNL inodes]，會顯示缺少可用的儲存空間。 移除檔案（尤其是小型檔案）將釋放兩個空間，並使[!DNL inodes]可用。

## [!UICONTROL vCPU tier view over timeline GREATER 2 weeks]

![vCPU層檢視超過時間表2週](../../assets/tools/observation-for-adobe-commerce/vCPU-tier.jpg)

**[!UICONTROL vCPU tier view over timeline GREATER 2 weeks]**&#x200B;框架會在超過兩週的選定時間範圍內顯示vCPU層檢視。 此框架會檢視指派給所顯示[!DNL New Relic]應用程式名稱的vCPU數量。

## [!UICONTROL vCPU tier view over timeline]

![vCPU層檢視超過時間表](../../assets/tools/observation-for-adobe-commerce/vcpu-tier-24.jpg)

**[!UICONTROL vCPU tier view over timeline]**&#x200B;框架會在超過24小時的所選時間範圍內顯示vCPU層檢視。 此框架會檢視指派給所顯示[!DNL New Relic]應用程式名稱的vCPU數量。 它會顯示叢集向上和向下移動。

## [!UICONTROL vCPU tier view over timeline BY NODE]

依節點![在時間線上檢視](../../assets/tools/observation-for-adobe-commerce/infra_by_node.png)vCPU層

**[!UICONTROL vCPU tier view over timeline BY NODE]**&#x200B;框架會依節點顯示所選時間範圍內的vCPU層檢視。 此框架有助於偵測節點遺失，或節點已放大或縮小時。 依節點依時間表的vCPU層檢視，應檢視少於24小時的時間表。

## [!UICONTROL Instance details]

![執行個體詳細資料](../../assets/tools/observation-for-adobe-commerce/instance-details.jpg)

**[!UICONTROL Instance details]**&#x200B;表格顯示每個[!DNL New Relic]應用程式的執行個體詳細資料。

## [!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]

![無回應式節點](../../assets/tools/observation-for-adobe-commerce/non-responsive-node.jpg)

**[!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]**&#x200B;框架顯示一段時間內無回應的節點。
