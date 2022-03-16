---
title: 服務級別協定
description: 瞭解服務級別協定以及如何使用它們支援您的Adobe Commerce實施。
exl-id: 5da42dfa-e165-4142-a863-6f3ce7689478
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 1%

---

# 服務級別協定(SLA)

服務級別協定(SLA)定義了客戶從服務提供商期望的服務級別，使用衡量該服務的簡單標準，以及在達不到商定的服務級別時的補救措施或處罰（如果有）。

可以收縮、維護和測量不同類型事件關鍵性的SLA。 此外，響應類型可以根據客戶要求的服務級別而具有多個標準（金、白金）。

下表描述了具有多個服務級別的典型SLA度量細分：

<table>
<thead>
  <tr>
    <th>問題類型</th>
    <th>影響</th>
    <th>示例</th>
    <th colspan="2">支援的工作時間內的響應/恢復時間</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td colspan="3"></td>
    <td>黃金</td>
    <td>白金</td>
  </tr>
  <tr>
    <td>P1</td>
    <td>關鍵影響</td>
    <td>服務關閉或無法使用</td>
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
    <td>服務效能降低</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>服務可用，但會生成大量錯誤消息</td>
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
    <td>生成錯誤消息，對最終用戶沒有明顯影響</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>有關客戶啟動中使用的功能的問題</td>
    <td></td>
    <td></td>
  </tr>
</tbody>
</table>

## 覆蓋範圍選項

承諾的SLA的覆蓋範圍選項因不同的產品類型而異。 通常，黃金和白金支援服務的範圍如下所示：

![顯示SLA覆蓋選項的資訊圖](../../assets/playbooks/sla-coverage-options.svg)
