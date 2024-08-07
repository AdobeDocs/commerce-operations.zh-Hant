---
title: 品質控制
description: 瞭解與實作專案相關的Adobe Commerce品質控制流程。
exl-id: 0eb62b24-21f6-4cec-8ef9-eeaa1ee6ae52
feature: Build
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 0%

---

# 品質控制流程與工具

![品質控制程式圖](../../assets/playbooks/quality-control-diagram.svg)

上圖中的品質控制流程可簡述如下。

<table>
<thead>
  <tr>
    <th>軟體開發程式</th>
    <th>QC工作流程</th>
    <th>QC</th>
    <th>QC負責人</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>開發</td>
    <td>規劃</td>
    <td></td>
    <td>檢閱並貢獻測試計畫</td>
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
    <td>準備和取得測試資料</td>
  </tr>
  <tr>
    <td></td>
    <td>測試分析和設計</td>
    <td>檢閱並貢獻測試計畫</td>
    <td>啟動準備作業、規格</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>建立測試規格（測試案例/測試案例）</td>
    <td>撰寫或檢閱專案的測試策略</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>準備和取得測試資料</td>
    <td> 領導、指導及監控分析、設計</td>
  </tr>
  <tr>
    <td>內部測試</td>
    <td>測試實作與執行</td>
    <td>實作測試、執行及記錄測試</td>
    <td>監控測試的實作與執行</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>檢查效能和掃描安全性 — 評估結果與預期結果的偏差</td>
    <td>確保測試可追蹤至測試基礎，並追蹤Bug追蹤系統上的錯誤</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Post錯誤至錯誤追蹤系統(Jira/Redmine/Trello)</td>
    <td>排定測試的優先順序/排程，以符合PM定義的專案計畫</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>修正錯誤後重新測試（確認測試）</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>評估與報告</td>
    <td>向QC銷售機會和PM報告測試進度</td>
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
    <td>驗證客戶反饋或變更請求(CR)</td>
    <td>後續追蹤</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>變更原始程式碼後，執行重新測試和回歸測試</td>
    <td>控制</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>更新測試規格</td>
    <td></td>
  </tr>
  <tr>
    <td>維護</td>
    <td>維護</td>
    <td>檢閱和貢獻任務</td>
    <td>檢閱和估計任務所需時間</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>建立/更新測試規格</td>
    <td>後續測試進度</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>執行這些工作的測試</td>
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

與我們針對開發程式所識別的[工具](project-management-tools.md)類似，我們選取了幾個我們經常用於品質控制測試的解決方案和平台。

| 用途 | 工具 |
|---------------------------|---------------------------------------------------|
| 網站績效指數 | Google PageSpeed， Webpagetest， JMeter |
| 安全性 | Adobe Commerce安全性掃描工具、SonarQube、ZAP |
| 問題管理系統 | JIRA |
| UI測試 | 完美畫素，BrowserStack |
| API測試 | Postman、SoapUI |
| 自動化測試 | Selenium |


## 網站績效指數

GooglePageSpeed會報告行動裝置和案頭裝置上頁面的效能，並提供如何改善該頁面的建議。

WebPageTest是一種網頁效能工具，使用真正的瀏覽器來存取網頁並收集計時測量結果。

JMeter是Apache專案，可作為負載測試工具，用於分析和測量各種服務的效能，其重心為Web應用程式。

## 安全性

SonarQube和ZAP已引進開發流程，但我們也在此處加入有關其如何參與QC流程的更多資訊。

SonarQube也用於持續檢查程式碼品質，透過程式碼的靜態分析執行自動審查，以偵測錯誤、程式碼異味和安全性漏洞。

OWASPZAP (Zed Attack Proxy)旨在供應用程式安全性新手以及專業滲透測試人員使用。 部分內建功能包括攔截代理伺服器、傳統和AJAX Web編目程式、自動化掃描器、被動式掃描器、強制瀏覽、Fuzzier、WebSocket支援、指令碼語言和隨插即用支援。

## UI測試

Perfect Pixel可讓開發人員和標籤設計人員將半透明影像覆蓋圖放置在開發HTML上方，並在兩者之間執行完美的畫素比較。

BrowserStack是雲端網頁和行動測試平台，可讓開發人員透過隨選瀏覽器、作業系統和真實行動裝置測試其網站和行動應用程式。

## API測試

Postman是API開發的共同作業平台。 Postman可簡化建立API的每個步驟，並簡化共同作業，讓您建立更好的API。

SoapUI是開放原始碼Web服務測試應用程式，適用於Simple Object Access Protocol (SOAP)和代表性狀態轉移(REST)。 其功能涵蓋網站服務檢查；叫用、開發、模擬和模擬；功能測試；載入和合規性測試。

## 自動化測試

Selenium由數個元件（Selenium使用者端API、Selenium WebDriver）組成，每個元件都承擔協助開發Web應用程式測試自動化的特定角色。
