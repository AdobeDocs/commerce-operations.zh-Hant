---
title: 服務級別協定
description: 了解服務層級合約，以及如何使用這些合約來支援您的Adobe商務實作。
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 1%

---


# 服務級別協定(SLA)

服務級別協定(SLA)定義了客戶從服務提供商那裡期望的服務級別，其中包含衡量該服務的簡單指標，以及在達不到協定服務級別時的補救措施或處罰（如果有的話）。

可以收縮、維護和衡量不同類型事件關鍵性的SLA。 此外，回應類型可根據客戶所需的服務水準，有多種標準（金級、白金級）。

下表描述了具有多個服務級別的典型SLA度量劃分：

<table>
<thead>
  <tr>
    <th>問題類型</th>
    <th>影響</th>
    <th>範例</th>
    <th colspan="2">在支援的工作時間內的響應/恢復時間</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td colspan="3"></td>
    <td>金</td>
    <td>白金</td>
  </tr>
  <tr>
    <td>P1</td>
    <td>關鍵影響</td>
    <td>服務中斷或不可用</td>
    <td>1小時/4小時</td>
    <td>1小時/4小時</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>服務不可用</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>服務在最終用戶群中不可用</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>P2</td>
    <td>高影響</td>
    <td>服務嚴重受損</td>
    <td>2小時/12小時</td>
    <td>2小時/8小時</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>服務效能已降低</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>服務可用，但會產生顯著錯誤訊息</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>P3</td>
    <td>中等影響</td>
    <td>服務部分減值</td>
    <td>8小時/16小時</td>
    <td>8小時/12小時</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>生成錯誤消息，對最終用戶沒有明顯的影響</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>客戶啟動中使用功能的相關問題</td>
    <td></td>
    <td></td>
  </tr>
</tbody>
</table>

## 覆蓋範圍選項

承諾的SLA的覆蓋選項因不同的服務類型而異。 金級和白金級支援服務的範圍通常如下所示：

![顯示SLA覆蓋選項的資訊圖](../../assets/playbooks/sla-coverage-options.svg)
