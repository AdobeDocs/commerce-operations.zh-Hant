---
title: 共擔責任
description: 瞭解在雲端基礎結構專案中，Adobe Commerce中涉及的每一方的安全性責任。
source-git-commit: d216418c69cb972e93c04b5d5cc0a8ab0495653d
workflow-type: tm+mt
source-wordcount: '1562'
ht-degree: 0%

---


# 共擔責任安全性模型

雲端基礎結構上的Adobe Commerce是一項平台即服務(PaaS)產品，其仰賴共同責任安全性模式。 Adobe、商家、雲端服務提供者和內容傳遞網路(CDN)提供者各自都有責任維護Adobe Commerce在雲端基礎結構應用程式和商家專用程式碼和擴充功能上的安全性。

此方法可讓商戶設計和實作高度彈性、可自訂且可擴充的解決方案，以最符合其業務需求，同時儘量減少營運責任和成本。

一般來說，Adobe負責開發及維護安全的核心應用程式程式碼、維護平台的安全性、確保平台的SOC 2和PCI相容性及其與PCI相容技術元件（例如PHP、Redis）的相容性，以及回應核心平台的安全問題。 Adobe也負責與雲端服務供應商和CDN合作夥伴合作，以解決可能出現的問題。

商戶負責維護安全的自訂程式碼以及與協力廠商應用程式的整合、確保安全應用程式開發、若商戶的付款處理器提出要求即取得PCI認證，以及回應和回應安全性事件。

## Adobe責任

Adobe負責雲端基礎結構環境上的Adobe Commerce以及雲端基礎結構解決方案程式碼上的核心Adobe Commerce的安全性和可用性。 此外，Adobe還負責維護雲端基礎結構解決方案上Adobe Commerce安全性的必要活動和機制，包括：

- 在雲端基礎結構上為Adobe Commerce支援的應用程式套用伺服器層級安全性和修補程式，例如雲端資料儲存和搜尋功能
- 在雲端基礎結構程式碼上執行核心Adobe Commerce的滲透測試和掃描
- 對公共雲端服務提供者的身分與存取管理(IAM)解決方案和許可權管理（PCI法規遵循要求）進行半年一度的審查/稽核
- 對授權的使用者進行半年度審查/稽核，包括Adobe員工和承包商（PCI法規遵循要求）
- 進行備份和還原功能的年度測試和檔案記錄
- 設定伺服器和周邊防火牆
- 在雲端基礎結構存放庫上連線和設定Adobe Commerce
- 為Adobe職責範圍內的領域定義、測試、實施和記錄災難回覆(DR)計畫
- 定義全球平台網頁應用程式防火牆(WAF)規則
- 強化作業系統(OS)
- 在雲端基礎結構上實作並維護內容發佈網路(CDN)和應用程式效能管理(APM)解決方案與Adobe Commerce的整合
- 在雲端基礎結構程式碼上發佈核心Adobe Commerce的定期安全性和其他更新（套用修補程式是商家的責任）
- 管理商家支援和支援存取控制（例如Zendesk）
- 監控、記錄及修正雲端基礎結構上Adobe Commerce的安全事件
- 監控平台作業，並在雲端基礎結構商家上提供Adobe Commerce的全天候支援
- 布建生產和中繼環境
- 評估平台作業與基礎建設的潛在安全性威脅
- 根據與商戶的服務等級協定(SLA)的描述，擴充運算、儲存、網格和其他資源
- 設定DNS (僅限雲端基礎結構平台基礎結構上的Adobe Commerce)
- 測試平台是否有安全漏洞

雖然Adobe會維護雲端基礎結構解決方案上Adobe Commerce運作中所使用之基礎結構和服務的PCI認證，但商家須負責遵守自訂程式碼、系統和網路程式以及組織。

Adobe還可確保商家基礎架構的可用性，如適用的SLA中商定。

## 商戶責任

該商戶負責針對雲端基礎結構解決方案上其特定的Adobe Commerce自訂執行個體並執行下列安全性最佳實務：

- 將雲端基礎結構設定檔案上的必要Adobe Commerce新增到存放庫
- 在依Adobe發行雲端基礎結構解決方案的自訂Adobe Commerce中立即套用安全性和其他修補程式
- 在廠商發佈所有自訂擴充功能和程式碼後，立即套用安全性和其他修補程式
- 建立、部署和測試自訂Vcl檔案
- 在雲端基礎結構解決方案上設計、設定主題、安裝、整合及保護自訂Adobe Commerce，包括所有自訂擴充功能和程式碼
- 授予和撤銷使用者對雲端基礎結構設定、應用程式和平台上Adobe Commerce商家例項的存取權
- 處理與商戶的內部網路、伺服器、基礎結構和任何在雲端基礎建設平台上的Adobe Commerce上建置的自訂應用程式相關的安全性問題
- 在雲端基礎結構上安裝Adobe Commerce命令列整合(CLI)工具
- 根據PCI-DSS准則的定義，維持自訂應用程式和其他內部程式所需的PCI相容性等級

  >[!NOTE]
  >
  >商戶的PCI法規遵循以雲端基礎結構和雲端託管提供者的Adobe Commerce PCI認證為基礎，將必須檢視的領域降至最低。

- 在雲端基礎結構程式碼和平台執行PCI ASV掃描並修正核心Adobe Commerce中的問題
- 監控所有可能顯示潛在安全威脅的應用程式活動，包括滲透測試、弱點掃描和記錄
- 監控及回應安全性事件，包括與商家Adobe Commerce相關的法證、補救及報告，用於雲端基礎結構解決方案和使用者帳戶
- 取得DNS提供者，以及設定和維護任何商家特定的DNS記錄
- 在自訂應用程式上執行效能測試
- 保護對平台帳戶的存取權、執行個體存取權和應用程式
- 自訂應用程式的測試和QA
- 維護商戶在雲端基礎結構應用程式上連線至Adobe Commerce的任何系統或網路的安全性

## 雲端服務提供者的責任

Adobe仰賴成熟雲端服務提供者，在雲端基礎結構上為Adobe Commerce託管雲端伺服器基礎結構。 這些提供者負責網路安全，包括路由、交換及周邊網路安全，透過防火牆系統和入侵偵測系統(IDS)。 雲端服務供應商也負責在雲端基礎結構解決方案上託管Adobe Commerce的資料中心的實體安全性，以及資料中心的環境安全性。

雲端服務供應商也負責：

- 維護其雲端服務的PCI DSS、SOC 2和ISO 27001認證
- 保護Hypervisor
- 保護資料中心的安全，包括實體及網路存取

## CDN提供者責任

雲端基礎結構解決方案的Adobe Commerce使用CDN提供者來加速頁面載入時間、快取內容，並立即清除過時的內容。 這些提供者也負責與其CDN直接相關或影響其安全性的問題，以及定義和維護CDN WAF規則。

## 安全性責任圖

下列圖表使用RACI模型（R — 負責，A — 負責，C — 已諮詢，I — 已告知），以視覺化方式描繪生態系統中與Adobe Commerce雲端基礎結構共用責任模型有關的安全性責任各方：

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
    <td>將修補程式套用至支援服務<br>（例如Nginx、MySQL）</td>
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
    <td>部署平台WAF規則</td>
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
    <td>縮放（PaaS/格線）</td>
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
    <td>設定來源存放庫<sup>1</sup></td>
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
    <td>設定New Relic APM/基礎架構</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>安裝New Relic APM/基礎架構</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>支援New Relic APM/基礎架構</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>設定Nginx<sup>3</sup></td>
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
    <td>在雲端基礎結構上修復Adobe Commerce PCI掃描<sup>4</sup></td>
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
    <td>AdobeDR計畫及備份與還原的年度測試與檔案</td>
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
      <p><sup><strong>1</strong></sup> 僅限將雲端基礎結構存放庫上的Adobe Commerce作為主要存放庫時。 商家全權負責使用其他外部存放庫。</p>
      <p><sup><strong>2</strong></sup> Adobe針對CDN提供者的問題提供第1級支援。</p>
      <p><sup><strong>3</strong></sup> 有些Ngnix控制項是由商家為其應用程式設定，並由其負責。</p>
      <p><sup><strong>4</strong></sup> 對於PCI，滲透測試需求在Adobe和商家之間共用。</p>
    </td>
  </tr>
</tfoot>
</table>
