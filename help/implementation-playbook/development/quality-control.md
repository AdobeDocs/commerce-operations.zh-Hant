---
title: 質量控制
description: 了解與實作專案相關的Adobe商務品質控制流程。
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 0%

---


# 質量控制過程和工具

![質量控制流程圖](../../assets/playbooks/quality-control-diagram.svg)

上圖中的質量控制過程可以簡要描述如下。

<table>
<thead>
  <tr>
    <th>軟體開發過程</th>
    <th>QC工作流</th>
    <th>QC</th>
    <th>QC領導</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>開發</td>
    <td>規劃</td>
    <td></td>
    <td>審核並協助測試計畫</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td>建立測試規格（測試案例/測試案例）</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td>準備和獲取測試資料</td>
  </tr>
  <tr>
    <td></td>
    <td>測試分析與設計</td>
    <td>審核並協助測試計畫</td>
    <td>開始準備，規範</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>建立測試規格（測試案例/測試案例）</td>
    <td>編寫或審核項目的測試策略</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>準備和獲取測試資料</td>
    <td> 領導、指導和監測分析、設計</td>
  </tr>
  <tr>
    <td>內部測試</td>
    <td>測試實作與執行</td>
    <td>實作測試、執行和記錄測試</td>
    <td>監控測試的實作和執行</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>檢查效能和掃描安全性 — 評估結果和與預期結果的偏差</td>
    <td>確保測試的可跟蹤性，使其達到測試的基礎，並跟蹤Bug跟蹤系統中的錯誤</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>發佈錯誤至錯誤追蹤系統(Jira/Redmine/Trello)</td>
    <td>排定測試的優先順序/排程，以與PM定義的項目計劃一致</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>修正錯誤後重新測試（確認測試）</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>評估和報告</td>
    <td>向QC領導和PM報告測試進度</td>
    <td>評估測試結果和進度</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td>根據測試期間收集的資訊編寫測試摘要報告</td>
  </tr>
  <tr>
    <td>UAT</td>
    <td>UAT</td>
    <td>驗證客戶回饋或變更請求(CR)</td>
    <td>後續</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>在更改原始碼後執行重新測試和回歸測試</td>
    <td>控制</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>更新測試規範</td>
    <td></td>
  </tr>
  <tr>
    <td>維護</td>
    <td>維護</td>
    <td>審核並協助執行任務</td>
    <td>審查和估計任務時間</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>建立/更新測試規範</td>
    <td>後續測試進度</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>執行這些任務的測試</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>執行回歸測試</td>
    <td></td>
  </tr>
</tbody>
</table>

與我們為開發流程確定的[tools](project-management-tools.md)類似，我們選擇了幾個我們經常用於質量控制測試的選擇解決方案和平台。

| 用途 | 工具 |
|---------------------------|---------------------------------------------------|
| 網站效能索引 | Google PageSpeed, Webpagetest, JMeter |
| 安全性 | Adobe商務安全掃描工具、SonarQube、ZAP |
| 問題管理系統 | 吉拉 |
| UI測試 | 完美像素，瀏覽器堆疊 |
| API測試 | Postman, SoapUI |
| 自動化測試 | 硒 |


## 網站效能索引

GooglePageSpeed會報告行動裝置和案頭裝置上頁面的效能，並提供如何改善該頁面的建議。

WebPageTest是使用實際瀏覽器來存取網頁和收集計時量度的網頁效能工具。

JMeter是Apache專案，可作為負載測試工具，用於分析和測量各種服務的效能，並將重點放在Web應用程式上。

## 安全性

SonarQube和ZAP在開發過程中被引入，但我們也將其包括在這裡，詳細介紹了它如何參與QC過程。

SonarQube還用於持續檢查代碼質量，以執行自動審查，對代碼進行靜態分析，以檢測錯誤、代碼氣味和安全漏洞。

OWASPZAP(Zed Attack Proxy)旨在讓應用程式安全的新用戶以及專業的滲透測試者都能使用。 部分內置功能包括攔截代理伺服器、傳統和AJAX Web爬蟲程式、自動掃描器、被動掃描器、強制瀏覽、模糊器、WebSocket支援、指令碼語言和插件 — n-Hack支援。

## UI測試

Perfect Pixel可讓開發人員和標籤設計人員將半透明影像覆蓋放在開發的HTML上方，並在兩者之間執行像素完美比較。

BrowserStack是雲端網頁和行動測試平台，可讓開發人員在隨選瀏覽器、作業系統和實際行動裝置上測試其網站和行動應用程式。

## API測試

Postman是API開發的共同作業平台。 Postman可簡化建立API的每個步驟，並簡化共同作業，讓您能建立更好的API。

SoapUI是用於簡單對象訪問協定(SOAP)和表示狀態傳輸(REST)的開源Web服務測試應用程式。 其功能包括Web服務檢查；叫用、開發、模擬和模仿；功能測試；負載和合規性測試。

## 自動化測試

Selenium由多個元件(Selenium client API, Selenium WebDriver)組成，每個元件都在幫助開發Web應用測試自動化方面發揮特定作用。
