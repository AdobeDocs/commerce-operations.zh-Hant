---
title: 雲基礎架構安全
description: 瞭解我們如何保護Adobe Commerce雲基礎架構的安全。
exl-id: cd5d1106-c8db-4b70-b1c7-12378d7d77a7
source-git-commit: 6509c939c7abc5462bffbe104466b2ff9e6fadc9
workflow-type: tm+mt
source-wordcount: '1639'
ht-degree: 0%

---

# 安全

Adobe Commerce專業計畫體系結構旨在提供高度安全的環境。 每個客戶都被部署到他們自己孤立的伺服器環境中，與其他客戶分開。 生產環境的安全詳細資訊如下所述。

## Web瀏覽器

進出雲環境的流量大部分來自消費者的Web瀏覽器。 對於網站上的所有頁面，可使用HTTPS保護用戶通信（使用共用SSL證書或客戶自己的SSL證書，但需額外付費）。 總是使用HTTPS為簽出和帳戶頁提供服務。 最佳做法是使用HTTPS服務所有頁面。

## 內容分發網路(CDN)

Reblish提供CDN和分佈式拒絕服務(DDoS)保護。 Apphise CDN可幫助隔離對源伺服器的直接訪問。 公共DNS只指向Affestible Network。 Reblished DDoS解決方案可防止高破壞性的第3層和第4層攻擊，以及更複雜的第7層攻擊。 可以使用基於整個HTTP/HTTPS請求的自定義規則並根據客戶端和請求標準（包括報頭、cookie、請求路徑和客戶端IP）或像地理位置這樣的指示符來阻止第7層攻擊。

## Web應用程式防火牆(WAF)

Application Firewall(WAF)用於提供附加保護。 基於雲的WAF使用來自商業和開源源的第三方規則，如OWASP核心規則集。 此外，還採用了針對Adobe Commerce的規則。 保護客戶免受關鍵應用程式層攻擊，包括注入攻擊和惡意輸入、跨站點指令碼、資料過濾、HTTP協定違規和其他OWASP Top 10威脅。

如果檢測到新的漏洞，Adobe Commerce會更新WAF規則，使Managed Services能夠在軟體補丁之前「虛擬地修補」安全問題。 Reblished WAF不提供速率限制或bot檢測服務。 如果需要，客戶可以許可與Rebish相容的第三方bot-detection服務。

## 虛擬專用雲(VPC)

Adobe CommercePro計畫生產環境配置為虛擬專用雲(VPC)，因此生產伺服器是隔離的，並且連接到雲環境和連接到雲環境外的能力有限。 只允許安全連接到雲伺服器。 SFTP或rsync等安全協定可用於檔案傳輸。

客戶可以使用SSH隧道來確保與應用程式的通信安全。 客人可以額外付費使用AWS私人連結。 所有到這些伺服器的連接都使用AWS安全組進行控制，該虛擬防火牆限制到環境的連接。 客戶的技術資源可以使用SSH訪問這些伺服器。

## 加密

Amazon彈性塊儲存(EBS)用於儲存。 所有EBS卷都使用AES-265算法進行加密。 這意味著資料將在靜止時被加密。 系統還加密在CDN和源伺服器之間以及源伺服器之間傳輸的資料。 客戶密碼儲存為散列。 敏感憑據（包括用於支付網關的憑據）使用SHA-256算法進行加密。

當資料不在靜止或未在伺服器之間傳輸時，Adobe Commerce應用程式不支援列級或行級加密或加密。 客戶可以從應用程式內管理加密密鑰。 系統使用的密鑰儲存在AWS密鑰管理系統中，必須由Managed Services管理才能提供部分服務。

## 穿透試驗

Managed Services利用開箱應用對Adobe Commerce雲系統進行定期滲透test。 客戶負責對其定制應用程式進行任何滲透測試。

## 付款網關

Adobe Commerce要求支付網關整合，信用卡資料直接從消費者瀏覽器傳送到支付網關。 在任何Adobe Commerce專業計畫Managed Services環境中，卡資料都不可用。 使用來自網關的對事務的引用來完成由電子商務應用程式對事務的操作。

## Adobe Commerce應用

Adobe定期test安全漏洞的核心應用程式碼。 為客戶提供了缺陷和安全問題的修補程式。 產品安全團隊按照OWASP應用程式安全准則驗證Adobe Commerce產品。 幾個安全漏洞評估工具和外部供應商用於test和驗證合規性。 安全工具包括：

- Veracode靜態和動態掃描
- RIPS原始碼掃描
- Trustwave和Alert Logic的漏洞掃描服務
- 伯普套房Pro
- 奧瓦斯帕普
- 和SqlMap

使用這些工具每兩週掃描一次完整代碼庫。 通過直接電子郵件、應用程式中的通知和 [安全中心](https://magento.com/security)。

客戶必須確保這些修補程式在發佈後的30天內按照PCI指南應用於其定製的應用程式。 Adobe還提供 [安全掃描工具](https://docs.magento.com/user-guide/magento/security-scan.html) 使商家能夠定期監控其站點並接收有關已知安全風險、惡意軟體和未經授權的訪問的更新。 安全掃描工具是免費服務，可在任何版本的Adobe Commerce上運行。

為了鼓勵安全研究人員識別和報告漏洞，Adobe Commerce [賞蟲計畫](https://hackerone.com/magento) 除了內部測試。 此外，如果需要，向客戶提供應用程式的完整原始碼以供其自己審閱。

## 只讀檔案系統

所有可執行代碼都部署到只讀檔案系統映像中，這大大減少了可用於攻擊的表面。 部署過程建立Squash-FS映像。 此方法大大減少了將PHP或JavaScript代碼注入系統或修改Adobe Commerce應用程式檔案的機會。

## 遠程部署

將可執行代碼導入Managed Services生產環境的唯一方法是通過設定過程運行它。 這涉及將原始碼從源儲存庫推送到遠程儲存庫，以啟動部署過程。 對該部署目標的訪問受控制，因此您可以完全控制誰可以訪問該部署目標。 應用程式碼到非生產環境的所有部署都由客戶控制。

## 記錄

所有AWS活動都登錄到AWSCloudTrail。 Linux 、應用程式伺服器和資料庫日誌儲存在生產伺服器上並儲存在備份中。 所有原始碼更改都記錄在Git儲存庫中。 部署歷史記錄在Adobe Commerce [Project Web介面](https://devdocs.magento.com/cloud/project/projects.html#login)。 記錄所有支援訪問並記錄支援會話。

## 敏感資料

敏感資料可以涵蓋來自消費者的個人資訊或來自Managed Services客戶的機密資料。 保護敏感客戶和消費者資料是Adobe CommerceManaged Services的一項重要義務。 Managed Services和我們的客戶都對個人身份資訊負有法律義務。 除了體系結構的安全功能外，還有其他控制來限制對敏感資料的分發和訪問。

客戶擁有其資料，並控制該資料的位置。 客戶指定其生產和開發實例所在的位置。 它們還指定將與Commerce一起用於Magento Business Intelligence(MBI)環境的位置，以及該MBI應用程式是否有權訪問個人識別資訊。 生產實例可以位於AWS的大多數地區，而開發和MBI環境可以在美國或歐盟境內找到。

敏感資料可能會通過Abmestify CDN伺服器網路，但不會儲存在Abmestify網路中。 Adobe CommerceManaged Services項目中包括的所有夥伴都有確保保護敏感資料的合同義務。 Managed Services不會將敏感客戶或消費者資料從客戶指定的位置移走。

作為提供Adobe CommerceManaged Services服務的一部分，Managed Services工作人員需要使用包含敏感資料的生產系統。 這些員工接受了有關保護敏感客戶和消費者資料的義務培訓。 對這些系統的訪問僅限於需要訪問的員工。 這些員工只能在提供這些服務所需的時間內進行訪問。

## 一般資料保護法規(GDPR)

GDPR是一個法律框架，為歐盟(EU)的個人收集和處理個人資訊制定了指導方針。 這些規定適用於任何地點，而歐盟訪問者也可以訪問。

實際上，網站從訪問者那裡收集的資料必須通知訪問者，並明確同意收集資訊。 如果站點保存的個人資料被洩露，站點必須通知訪問者。

運營該站點的商家或公司還必須有一個專門的資料保護官員，負責監督該站點的資料安全性，如果訪問者要求擦除其資料，此個人（或網站管理團隊）應可以聯繫。

GDPR還要求收集到的任何個人身份資訊（如姓名、種族和出生日期）要麼匿名，要麼假名。

>[!NOTE]
>
> 本頁僅是GDPR要考慮的一般概述。 有關詳細資訊，請咨詢您的法律顧問或參閱[正式文本](https://eur-lex.europa.eu/eli/reg/2016/679/oj)。

## 備份

在過去24小時的操作中，每小時執行一次備份。 在24小時後，使用AWSEBS快照服務按以下時間表保留備份：

| 期間 | 備份保留策略 |
|----------------|-------------------------|
| 第1至3天 | 每個備份 |
| 第4至6天 | 每天一次備份 |
| 第2至6週 | 每週一次備份 |
| 第8至12週 | 每週一次備份 |
| 第12至22週 | 每月一次備份 |

這將在冗餘儲存上建立獨立備份。 由於EBS卷是加密的，因此備份也是加密的。 此外，Managed Services還根據客戶要求執行按需備份。

您的Adobe CommerceManaged Services備份和恢複方法使用高可用性體系結構和完整系統備份。 每個項目都跨三個獨立的AWS可用區複製 — 所有資料、代碼和資產；每個區域都有一個獨立的資料中心。
