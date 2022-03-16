---
title: 質量控制
description: 瞭解與實施項目相關的Adobe Commerce質量控制流程。
exl-id: 0eb62b24-21f6-4cec-8ef9-eeaa1ee6ae52
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 0%

---

# 質量控制過程和工具

![質量控制流程圖](../../assets/playbooks/quality-control-diagram.svg)

前圖中的質量控制過程可簡要描述如下。

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
    <td>審查並參與test計畫</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td>建立test規格(test案例/test方案)</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td>準備和獲取test資料</td>
  </tr>
  <tr>
    <td></td>
    <td>Test分析和設計</td>
    <td>審查並參與test計畫</td>
    <td>開始準備，規範</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>建立test規格(test案例/test方案)</td>
    <td>編寫或審閱項目的Test策略</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>準備和獲取test資料</td>
    <td> 指導、指導和監測分析、設計</td>
  </tr>
  <tr>
    <td>內部測試</td>
    <td>Test實施和執行</td>
    <td>實施test、執行和記錄test</td>
    <td>監測各項test的執行</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>檢查效能和掃描安全性 — 評估結果和與預期結果的偏差</td>
    <td>確保test對test的可跟蹤性，並跟蹤Bug跟蹤系統上的Bug</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>將Bug發佈到Bug跟蹤系統(Jira/Redmine/Trello)</td>
    <td>排定test的優先順序/計畫順序，以與PM定義的項目計畫保持一致</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>修復錯誤後重新測試（確認測試）</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>評估和報告</td>
    <td>向QC線索和PM報告test進度</td>
    <td>評估test結果和進度</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td>根據在test期間收集的資訊編寫test摘要報告</td>
  </tr>
  <tr>
    <td>UAT</td>
    <td>UAT</td>
    <td>驗證客戶反饋或更改請求(CR)</td>
    <td>後續行動</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>更改原始碼後執行重新測試和回歸測試</td>
    <td>控制</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>更新test規範</td>
    <td></td>
  </tr>
  <tr>
    <td>維護</td>
    <td>維護</td>
    <td>審查和協助任務</td>
    <td>查看和估計任務的時間</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>建立/更新test規範</td>
    <td>後續test進展</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>執行這些任務的test</td>
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

與 [工具](project-management-tools.md) 我們為開發過程確定了一些選項，我們選擇了一些我們經常用於質量控制測試的解決方案和平台。

| 目的 | 工具 |
|---------------------------|---------------------------------------------------|
| 網站效能索引 | GooglePageSpeed、Webpagetest、JMeter |
| 安全 | Adobe Commerce安全掃描工具、聲納庫比、ZAP |
| 問題管理系統 | 吉拉 |
| UI測試 | 完美像素，瀏覽器棧 |
| API測試 | 郵遞員，SoapUI |
| 自動化測試 | 硒 |


## 網站效能索引

GooglePageSpeed報告移動和案頭設備上某頁的效能，並提供如何改進該頁的建議。

WebPageTest是一種Web效能工具，它使用真正的瀏覽器訪問網頁並收集計時度量。

JMeter是一個Apache項目，可用作分析和測量各種服務效能的負載測試工具，其重點是Web應用程式。

## 安全

SonarQube和ZAP在開發過程中被引入，但我們也在這裡介紹它，並詳細介紹它如何參與QC過程。

SonarQube還用於持續檢查代碼質量，通過靜態分析代碼來檢測錯誤、代碼氣味和安全漏洞來執行自動檢查。

OWASPZAP(Zed Attack Proxy)旨在同時由應用程式安全性的新用戶和專業的滲透測試人員使用。 某些內置功能包括攔截代理伺服器、傳統和AJAXWeb爬網程式、自動掃描程式、被動掃描程式、強制瀏覽、Fuzzier、WebSocket支援、指令碼語言和Plug-n-Hack支援。

## UI測試

Perfect Pixel允許開發人員和標籤設計人員在開發HTML的頂部放置半透明影像覆蓋，並在它們之間執行像素完美比較。

BrowserStack是一個雲網路和移動測試平台，使開發人員能夠跨按需瀏覽器、作業系統和真正的移動設備test其網站和移動應用程式。

## API測試

郵遞員是API開發的協作平台。 郵遞員簡化了構建API的每一步，並優化了協作，以便您可以建立更好的API。

SoapUI是用於簡單對象訪問協定(SOAP)和表示狀態傳輸(REST)的開源Web服務測試應用程式。 其功能包括Web服務檢查；調用、開發、模擬和嘲弄；功能測試；負載和合規性測試。

## 自動化測試

Selenium由幾個元件(Selenium client API, Selenium WebDriver)組成，每個元件在幫助Web應用test自動化的開發中都起著特定的作用。
