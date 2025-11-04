---
title: 共擔責任安全性與營運模式
description: 瞭解在雲端基礎結構專案中，Adobe Commerce中涉及的每一方的安全性責任。
exl-id: f3cc1685-e469-4e30-b18e-55ce10dd69ce
source-git-commit: aac78fc95b86951f352a636eef33e0b79b22a183
workflow-type: tm+mt
source-wordcount: '2939'
ht-degree: 0%

---

# 共擔責任安全性與營運模式

雲端基礎結構上的Adobe Commerce是一項平台即服務(PaaS)產品，仰賴共同責任的安全性和營運模式。 這些責任由Adobe、商家、雲端服務提供者和內容傳遞網路(CDN)提供者共用。 各方都有責任保護及營運Adobe Commerce應用程式，以及雲端基礎結構上部署之商家專用程式碼和擴充功能。

此共用模式可讓商戶設計和實作高度彈性、可自訂且可擴充的解決方案，以符合其業務需求，同時將營運責任和成本降至最低。

>[!VIDEO](https://video.tv.adobe.com/v/3458392/?learn=on&enablevpops)

一般而言，Adobe的職責如下：

- 開發及維護安全的核心應用程式程式碼
- 維護平台的安全性
- 確保平台符合SOC 2和PCI標準，並與PCI標準的技術元件（例如PHP、Redis）相容
- 回應核心平台的安全問題
- 與雲端服務供應商和CDN合作夥伴合作，解決發生的任何問題

商家需負責下列事項：

- 維護自訂程式碼的安全性以及與協力廠商應用程式的整合
- 確保安全的應用程式開發
- 如果商戶的付款處理程式要求，請取得PCI認證
- 回應和回應安全性事件

## Adobe責任

Adobe負責雲端基礎結構環境及核心解決方案程式碼上的Adobe Commerce安全性和可用性。 此外，Adobe還負責必要的活動和機制，以維護Adobe Commerce在雲端基礎結構解決方案上的安全性，包括：

- 在雲端基礎結構上為Adobe Commerce支援的應用程式套用伺服器層級安全性和修補程式，例如雲端資料儲存和搜尋功能
- 在雲端基礎結構程式碼上執行核心Adobe Commerce的滲透測試和掃描
- 對公共雲端服務提供者的身分與存取管理(IAM)解決方案和許可權管理（PCI法規遵循要求）進行半年一度的審查和稽核
- 對授權的使用者進行半年一度的審查和稽核，包括Adobe員工和承包商（PCI法規遵循要求）
- 進行備份和還原功能的年度測試和檔案記錄
- 設定伺服器和周邊防火牆
- 在雲端基礎結構存放庫上連線和設定Adobe Commerce
- 為Adobe職責範圍內的區域定義、測試、實施和記錄災難回覆(DR)計畫
- 定義全域平台網頁應用程式防火牆(WAF)規則
- 強化作業系統(OS)
- 在雲端基礎結構上實作並維護內容發佈網路(CDN)和應用程式效能管理(APM)解決方案與Adobe Commerce的整合
- 在雲端基礎結構程式碼上發佈核心Adobe Commerce的定期安全性和其他更新（套用修補程式是商家的責任）
- 管理商家支援和支援存取控制（例如Zendesk）
- 監控、記錄及修正雲端基礎結構上Adobe Commerce的安全事件
- 監控平台作業，並在雲端基礎結構商家上提供Adobe Commerce的全天候支援
- 布建生產和中繼環境
- 評估平台作業與基礎建設的潛在安全性威脅
- 根據服務等級協定(SLA)和商家之間的說明，擴充運算、儲存、網格和其他資源
- 設定DNS (僅限雲端基礎結構平台基礎結構上的Adobe Commerce)
- 測試平台是否有安全漏洞

Adobe維護Adobe Commerce解決方案使用之基礎結構和服務的PCI認證。  商戶需負責自訂程式碼、系統和網路程式的合規性，以及組織。

Adobe也會確保商家基礎建設的可用性，如適用的SLA中所商定。

## 商戶責任

該商戶負責針對雲端基礎結構解決方案上其特定的Adobe Commerce自訂執行個體，遵循下列安全性最佳實務：

- 將雲端基礎結構設定檔案上的必要Adobe Commerce新增到存放庫
- 在Adobe發佈雲端基礎結構解決方案的自訂Adobe Commerce後，立即套用安全性和其他修補程式至其自訂
- 在廠商發佈所有自訂擴充功能和程式碼後，立即套用安全性和其他修補程式
- 建立、部署和測試自訂Vcl檔案
- 在雲端基礎結構解決方案上設計、設定主題、安裝、整合及保護自訂Adobe Commerce，包括所有自訂擴充功能和程式碼
- 授予和撤銷使用者對雲端基礎結構設定、應用程式和平台上Adobe Commerce商家例項的存取權
- 處理與商戶的內部網路、伺服器、基礎結構和任何在雲端基礎建設平台上的Adobe Commerce上建置的自訂應用程式相關的安全性問題
- 在雲端基礎結構上安裝Adobe Commerce命令列整合(CLI)工具
- 根據PCI-DSS准則的定義，維持自訂應用程式和其他內部程式所需的PCI相容性等級

  >[!NOTE]
  >
  >為了將必須檢視的領域降到最低，商家的PCI法規遵循建立在Adobe Commerce和雲端主機供應商的PCI認證上。

- 在雲端基礎結構程式碼和平台執行PCI ASV掃描並修正核心Adobe Commerce中的問題
- 監控所有可能顯示潛在安全威脅的應用程式活動，包括滲透測試、弱點掃描和記錄
- 監控及回應安全性事件，包括與商家Adobe Commerce相關的法證、補救及報告，用於雲端基礎結構解決方案和使用者帳戶
- 取得DNS提供者，以及設定和維護任何商家特定的DNS記錄
- 在自訂應用程式上執行效能測試
- 保護對平台帳戶的存取權、執行個體存取權和應用程式
- 自訂應用程式的測試和QA
- 維護商戶在雲端基礎結構應用程式上連線至Adobe Commerce的任何系統或網路的安全性

## Cloud Service提供者責任

Adobe仰賴成熟雲端服務提供者，在雲端基礎結構上為Adobe Commerce託管雲端伺服器基礎結構。 這些提供者負責網路安全，包括路由、交換及周邊網路安全，透過防火牆系統和入侵偵測系統(IDS)。 雲端服務供應商也負責在雲端基礎結構解決方案上託管Adobe Commerce的資料中心的實體安全性，以及資料中心的環境安全性。

雲端服務供應商也負責：

- 維護其雲端服務的PCI DSS、SOC 2和ISO 27001認證
- 保護Hypervisor
- 保護資料中心的安全，包括實體及網路存取

## CDN提供者責任

雲端基礎結構解決方案的Adobe Commerce使用CDN提供者來加速頁面載入時間、快取內容，並立即清除過時的內容。 這些提供者也負責與其CDN直接相關或影響其安全性的問題，以及定義和維護CDN WAF規則。

## 安全性責任摘要

>[!BEGINSHADEBOX]

下列摘要表使用RACI模型來顯示Adobe、商家和雲端服務提供者之間共用的安全性責任：

**R** — 負責
**A** — 負責
**C** — 已諮詢
**I** — 已通知

>[!ENDSHADEBOX]

<table>
<thead>
  <tr>
    <th>任務</th>
    <th>Adobe</th>
    <th>商家</th>
    <th>雲端服務提供者</th>
    <th>CDN供應商</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>在雲端基礎結構修補程式上套用Adobe Commerce</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>正在將修補程式套用至支援服務<br> （例如Nginx或MySQL。）</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>定義原始WAF規則</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>定義CDN WAF規則</td>
    <td>A</td>
    <td></td>
    <td></td>
    <td>R</td>
  </tr>
  <tr>
    <td>部署platform WAF規則</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>部署CDN WAF規則</td>
    <td>A</td>
    <td>I</td>
    <td></td>
    <td>R</td>
  </tr>
  <tr>
    <td>修正Adobe Commerce中雲端基礎結構程式碼的核心錯誤</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>在雲端基礎結構修補程式上發行Adobe Commerce</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>擴充能力（運算與儲存）</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>縮放（PaaS和格線）</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>確保原始碼的存取權，包括repo.magento.com</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>在雲端基礎結構CLI工具上安裝Adobe Commerce</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>在雲端基礎結構設定檔案中新增Adobe Commerce至存放庫</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>為商家建立專案（上線UI）</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>在雲端基礎結構上將存放庫連線至Adobe Commerce</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>正在設定來源存放庫<sup>1</sup></td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>為發行管理員建立使用者（入門UI）</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>將程式碼部署到生產環境</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>將程式碼部署到暫存環境</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>整合外部應用程式和擴充功能</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>安裝擴充功能</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>在雲端基礎結構上自訂Adobe Commerce</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>在雲端基礎結構上測試自訂Adobe Commerce的效能</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>測試自訂應用程式</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>自訂應用程式的主題設定和設計</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
    <tr>
    <td>建立、部署和測試自訂光漆VCL</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>設定DNS （僅限平台基礎結構）</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>開發CDN擴充功能並修正錯誤</td>
    <td>A</td>
    <td>C</td>
    <td></td>
    <td>R</td>
  </tr>
  <tr>
    <td>開始使用CDN</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>支援CDN<sup>2</sup></td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td>C</td>
  </tr>
  <tr>
    <td>設定New Relic APM和基礎結構應用程式</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>安裝New Relic APM和基礎建設應用程式</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>支援New Relic APM和基礎建設應用程式</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>正在設定Nginx<sup>3</sup></td>
    <td>R</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>取得DNS提供者（僅限Pro）</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>強化作業系統</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>布建生產和中繼環境</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>在雲端基礎結構上存取Adobe Commerce的Zendesk</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>解決商家安全性問題</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td>C</td>
  </tr>
  <tr>
    <td>解決雲端基礎結構安全性上的Adobe Commerce</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>解決CDN安全性問題</td>
    <td>A</td>
    <td></td>
    <td></td>
    <td>R</td>
  </tr>
  <tr>
    <td>解決APM安全問題</td>
    <td>A</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>協助Adobe進行安全性研究（軟體）</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>協助Adobe進行安全性研究（掃描/稽核）</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>執行PCI ASV掃描</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>正在修復雲端基礎結構上的Adobe Commerce PCI掃描<sup>4</sup></td>
    <td>R</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>正在修復PaaS PCI掃描</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>管理作業系統和平台機密</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>在雲端基礎結構加密金鑰上管理Adobe Commerce</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>在雲端基礎結構執行個體上掃描自訂的Adobe Commerce</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>監控安全性記錄檔</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>在雲端基礎結構上管理Adobe Commerce的IAMand許可權</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>管理支援存取控制(Transport)</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>控制商戶支援與存取</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Adobe DR計畫及備份與還原的年度測試和檔案</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>災難回覆計畫的年度測試與檔案</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</tbody>
<tfoot>
  <tr>
    <td colspan="5">
      <p><sup><strong>1</strong></sup>僅限將雲端基礎結構存放庫上的Adobe Commerce作為主要存放庫時。 商家全權負責使用其他外部存放庫。</p>
      <p><sup><strong>2</strong></sup> Adobe針對CDN提供者的問題提供第1級支援。</p>
      <p><sup><strong>3</strong></sup>商家必須負責為其應用程式設定的任何Ngnix控制項。</p>
      <p><sup><strong>4</strong></sup>針對PCI，滲透測試需求會在Adobe與商家之間共用。</p>
    </td>
  </tr>
</tfoot>
</table>

## 作業責任摘要

>[!BEGINSHADEBOX]

下列摘要表格說明在雲端基礎結構上開發、部署、維護及保護Adobe時，Adobe Commerce和商家的營運責任。

>[!ENDSHADEBOX]

### 編碼與開發

#### 核心Adobe Commerce程式碼

|     | Adobe | 商家 |
| --- | --- | --- |
| 將更新和修補程式發佈至Adobe Commerce核心 | R |     |
| 檔案系統的可用性與修正 | R |  |
| 將更新和修補程式發佈至ECE-Tools | R |     |
| 核心Adobe Commerce應用程式品質 | R |     |

{style="table-layout:auto"}

#### 程式碼存放庫

|     | Adobe | 商家 |
| --- | --- | --- |
| repo.magento.com的可用性 | R |     |
| 雲端Git伺服器上Adobe Commerce的可用性 | R |     |
| 其他商家選取的程式碼存放庫（GitHub、Bitbucket、託管的Git伺服器） |     | R |

{style="table-layout:auto"}

#### Cloud Docker

|     | Adobe | 商家 |
| --- | --- | --- |
| 使Cloud Docker容器可供下載 | R |   |
| Cloud Docker的部署和設定（可選） |     | R |
| 任何其他本機開發設定 |     | R |

{style="table-layout:auto"}

#### COMMERCE CLOUD CLI

|     | Adobe | 商家 |
| --- | --- | --- |
| ECE工具的持續品質和更新 | R |   |
| 安裝最新ECE工具版本 |     | R |

{style="table-layout:auto"}

#### 自訂

|  | Adobe | 商家 |
| --- | --- | --- |
| 自訂Adobe Commerce模組和程式碼 |     | R |
| 擴充功能 |     | R |
| 自訂整合 |     | R |

{style="table-layout:auto"}

#### 部署

|     | Adobe | 商家 |
| --- | --- | --- |
| 建置和部署程式碼的基礎架構可用性 | R |   |
| 持續品質的基礎架構建置和部署設定管道 | R |   |
| 組建和靜態內容部署的設定 |     | R |
| 建置並執行部署治理程式：條件與變更管理 |     | R |
| 部署到中繼環境 |     | R |
| 部署到生產環境 |     | R |
| 生產復原 |     | R |

{style="table-layout:auto"}

#### 同步環境

商家負責同步環境之間的資料。

#### 修補

|     | Adobe | 商家 |
| --- | --- | --- |
| 安裝ECE-Tools的更新和修補程式 |     | R |
| 安裝Adobe Commerce核心的更新和修補程式 |     | R |

#### 網站可用性

|  | Adobe | 商家 |
| --- | --- | --- |
| 自訂的Adobe Commerce應用程式和相關網站 |     | R |

#### 效能

|     | Adobe | 商家 |
| --- | --- | --- |
| 核心應用程式調整和最佳化 | R |   |
| 自訂程式碼調整和最佳化 |     | R |
| 自訂Adobe Commerce程式碼 |     | R |
| 載入測試 |     | R |
| 效能測試 |     | R |

{style="table-layout:auto"}


#### 記錄檔和監視

|     | Adobe | 商家 |
| --- | --- | --- |
| 旋轉記錄檔 | R |   |
| 自訂Adobe Commerce應用程式 | | R |
| New Relic服務的可用性：<br>APM應用程式與代理程式整合、基礎結構應用程式、<br>記錄與整合 | R |   |
| 設定New Relic警報 |     | R |
| 在PaaS伺服器上部署New Relic代理程式 | R |  |

{style="table-layout:auto"}

#### 偵錯和問題隔離

|     | Adobe | 商家 |
| --- | --- | --- |
| 偵錯和問題隔離 | R | R |
| 及時支援偵錯和問題隔離流程 |     | R |

{style="table-layout:auto"}

### 應用程式和服務設定

#### Commerce應用程式

|     | Adobe | 商家 |
| --- | --- | --- |
| 應用程式設定 |     | R |
| 將網域新增至Adobe Commerce應用程式（基本URL） |     | R |
| 設定PaaS以使用已部署的Adobe Commerce版本<br><br>所支援的服務版本。例如，不同的Commerce版本與特定的PHP、Redis等版本相容。 |     | R |

{style="table-layout:auto"}

#### 使用cron工作排程任務

|     | Adobe | 商家 |
| --- | --- | --- |
| 預設cron工作的可用性 | R | |
| 持續品質的自訂cron工作 |  | R |

{style="table-layout:auto"}

#### 訊息佇列架構的訊息代理人

|     | Adobe | 商家 |
| --- | --- | --- |
| RabbitMQ服務的可用性 | R |   |
| 預設RabbitMQ設定的組態 | R |   |
| RabbitMQ的持續品質和修補 | R |   |
| 提交服務請求以安裝與已安裝Adobe Commerce版本相容的RabbitMQ版本 |   | R |

{style="table-layout:auto"}

#### PHP服務

|     | Adobe | 商家 |
| --- | --- | --- |
| PHP的可用性 | R |   |
| 預設PHP設定的組態 | R |     |
| 自訂PHP設定的組態 |     | R |
| YAML檔案的設定，以調整與已安裝的Adobe Commerce版本相容的PHP版本 |    | R |

{style="table-layout:auto"}

#### 資料庫服務

|     | Adobe | 商家 |
| --- | --- | --- |
| Galera和MariaDB服務的可用性 | R | |
| 持續維護預設資料庫設定<br><br> （索引和最佳化核心表格，最佳化預設sys-admin設定） | R |   |
| 持續維護商家資料及修改設定<br><br> （設定正規化與一般資料表、索引及最佳化自訂與協力廠商資料表、封存或移除資料、設定系統管理設定） |     | R |
| Galera和MySQL的設定 | R |   |
| Galera和MariaDB的持續品質與修補 | R |   |
| 持續性基礎架構最佳化 | R |   |
| 識別並修正緩慢查詢 |     | R |
| 提交服務要求以安裝與已安裝Adobe Commerce版本相容的MariaDB版本 |     | R |
| 設定及維護商家特定的資料保留原則(Adobe的資料保留原則會在商家合約中定義) |     | R |

{style="table-layout:auto"}

#### CDN服務

|     | Adobe | 商家 |
| --- | --- | --- |
| CDN的可用性和品質 | R |   |
| Fastly服務設定（透過擴充功能/API） |     | R |
| Fastly擴充品質 | R |   |
| Fastly整合VCL程式碼片段（與Fastly擴充功能整合）品質 | R |   |
| 頁面快取最佳化 |     | R |
| 將網域新增至服務、CDN和基礎架構 | R |   |
| 自訂VCL程式碼片段 |     | R |
| WAF和WAF規則 | R |   |

{style="table-layout:auto"}

#### 快取服務

|     | Adobe | 商家 |
| --- | --- | --- |
| Redis服務的可用性 | R |   |
| 預設Redis設定的設定 | R |   |
| Redis的持續品質與修補 | R |   |
| 提交服務要求以安裝與已安裝Adobe Commerce版本相容的Redis版本 |     | R |

{style="table-layout:auto"}

#### 搜尋服務

|     | Adobe | 商家 |
| --- | --- | --- |
| Elasticsearch或OpenSearch的可用性 | R |   |
| 預設Elasticsearch或OpenSearch設定的組態 | R |   |
| 提交服務要求以安裝與已安裝的Elasticsearch版本相容的Adobe Commerce或OpenSearch版本 |  | R |

{style="table-layout:auto"}

#### 電子郵件服務

|     | Adobe | 商家 |
| --- | --- | --- |
| SendGrid電子郵件服務的可用性及其整合 | R |   |
| 監視商家的SendGrid使用量是否超過限制 | R |   |
| 商家只負責將服務用於外寄異動電子郵件<br>服務不支援行銷電子郵件的傳送。 |     | R |
| 設定選用的協力廠商電子郵件服務 |     | R |

{style="table-layout:auto"}

#### 協力廠商服務

|     | Adobe | 商家 |
| --- | --- | --- |
| 協力廠商服務的可用性與品質 |     | R |

{style="table-layout:auto"}

### Commerce服務擴充功能

#### 進階報告服務

|     | Adobe | 商家 |
| --- | --- | --- |
| 進階報告服務的可用性 | R |   |
| 進階報告的設定符合進階報告的條款與條件 |     | R |

{style="table-layout:auto"}

#### Commerce Intelligence

|     | Adobe | 商家 |
| --- | --- | --- |
| Adobe Commerce Business Intelligence服務的可用性 | R |   |
| MBI資料同步程式 | R |   |
| 偵測MBI同步問題 | R |   |
| 設定MBI資料同步處理至Adobe Commerce Cloud Pro、Starter、內部部署或非Adobe Commerce<br>（API、資料品質和格式、商家網路、<br>Adobe Commerce Cloud DB內外的DB連線，超過資料臨界值） |     | R |
| 正在設定MBI資料同步處理至Adobe Commerce Cloud Pro<br>（Adobe Commerce Cloud資料庫設定） | R |   |

{style="table-layout:auto"}

>
>商戶必須使用最新版的即時搜尋、產品建議和支付服務，以確保最高的穩定性、功能和支援資格。
>Adobe不支援過時的版本，而升級可確保您受益於最新的增強功能和錯誤修正。
>如需支援版本的詳細資訊，請參閱[Commerce服務的產品可用性矩陣](https://experienceleague.adobe.com/en/docs/commerce-operations/release/product-availability#commerce-services)。

#### 產品推薦

|     | Adobe | 商家 |
| --- | --- | --- |
| Product Recommendations服務的可用性 | R |   |
| 升級Product Recommendations模組 |   | R |

{style="table-layout:auto"}

#### 即時搜尋

|     | Adobe | 商家 |
| --- | --- | --- |
| 即時搜尋服務的可用性 | R |   |
| 升級即時搜尋模組 |   | R |

{style="table-layout:auto"}

#### 店面活動（資料收集）的品質，可支援產品建議和即時搜尋輸出

|     | Adobe | 商家 |
| --- | --- | --- |
| 核心主題(Luma) | R |   |
| 自訂主題 |  | R |
| 核心PWA實施 | R |   |
| 自訂PWA實施 |  | R |
| 核心AEM EDS實作(Commerce樣板) | R |   |
| 自訂AEM EDS實施 |  | R |
| 任何其他自訂店面實作 |  | R |

{style="table-layout:auto"}

#### 付款服務

|     | Adobe | 商家 |
| --- | --- | --- |
| 付款服務的可用性 | R |   |
| 升級付款模組 |   | R |

{style="table-layout:auto"}

### 網路服務

#### 影像最佳化

|     | Adobe | 商家 |
| --- | --- | --- |
| 影像最佳化的可用性和品質 | R |  |
| 影像最佳化的設定 |     | R |

{style="table-layout:auto"}

#### SSL憑證

|     | Adobe | 商家 |
| --- | --- | --- |
| SSL專用憑證 — 到期 | R |  |
| 布建SSL憑證 | R |  |
| 購買及維護EV/特定SSL憑證（提供的預設值除外）並提供給Adobe |     | R |

{style="table-layout:auto"}

#### Web應用程式防火牆(WAF)

|     | Adobe | 商家 |
| --- | --- | --- |
| WAF的可用性和設定 | R |  |
| 處理WAF規則的誤判 | R | |
| 報告WAF規則誤判 |     | R |
| WAF規則調整（不支援） |     |     |
| WAF/CDN記錄檔 |     | R |

{style="table-layout:auto"}

#### DDOS

|     | Adobe | 商家 |
| --- | --- | --- |
| 主動IP封鎖 |     | R |
| 機器人保護 |     | R |
| DDOS偵測 — 第3-4層 | R |   |
| DDOS偵測 — 第7層 |     | R |
| DDOS回應 | R |   |

{style="table-layout:auto"}

#### 私人連結

|     | Adobe | 商家 |
| --- | --- | --- |
| 使用Adobe擁有的VPC設定並維護PrivateLink連線（如果使用） | R |   |
| 使用商家擁有的VPC設定及維護PrivateLink連線（若已使用） |     | R |
| SSH （非私人連結）的可用性 | R |   |
| PrivateLink傳入至Adobe Commerce雲端服務端點的設定 | R |   |
| 接受傳入至Adobe Commerce雲端服務端點的PrivateLink |     | R |
| 傳入至商家VPC服務端點的PrivateLink設定 |     | R |
| 接受傳入至商家VPC服務端點的PrivateLink | R |   |
| PrivateLink整合（端點對帳戶）的設定 |     | R |
| PrivateLink端點<br><br>之商家擁有的VPC的設定（包括任何VPN連線） |     | R |

{style="table-layout:auto"}

### 系統和基礎結構

#### 應用程式伺服器

|     | Adobe | 商家 |
| --- | --- | --- |
| Nginx的可用性 | R |   |
| Nginx的設定 | R |   |
| Nginx的持續品質與修補 | R |   |

{style="table-layout:auto"}

#### 作業系統

|     | Adobe | 商家 |
| --- | --- | --- |
| 作業系統的可用性 | R |   |
| 作業系統的持續品質與修補 | R |   |

{style="table-layout:auto"}

#### 備份、高可用性和容錯移轉

|     | Adobe | 商家 |
| --- | --- | --- |
| 快照和備份程式的可用性 | R |   |
| 為Cloud Pro測試和生產環境排程備份 | R |   |
| 為Cloud Starter和Pro整合環境排程備份 |     | R |
| 高可用性/容錯移轉 | R |   |

{style="table-layout:auto"}

#### 雲端伺服器和擴展

|     | Adobe | 商家 |
| --- | --- | --- |
| CPU資源、資料中心、磁碟空間的可用性 | R |   |
| 提供並執行突增容量或緊急規模調整 | R |   |
| 請求突增容量 |     | R |
| 根據限制監視vCPU使用量 | R |   |

{style="table-layout:auto"}
