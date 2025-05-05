---
title: 上市後支援與維護
description: 使用我們完整的啟動後支援和維護最佳實務，確保Adobe Commerce商店的最佳效能和安全性。
role: Admin, User, Developer
feature: Best Practices
source-git-commit: bcb45d53aba4a73a5730989e9bf29ccba6e9bf35
workflow-type: tm+mt
source-wordcount: '2116'
ht-degree: 0%

---


# Adobe Commerce的啟動後支援與維護

上市後支援和維護是確保Adobe Commerce商店順暢運作、執行良好、安全無虞，並繼續達成業務目標的關鍵。 此階段涉及持續監控、最佳化、錯誤修正、更新和使用者支援。 下列章節將&#x200B;**啟動後支援**&#x200B;劃分為主要類別：

## 定期的網站監控與效能最佳化

### 效能監視

- **網站速度和負載測試**： Adobe Commerce需要大量資源，因此定期的效能監視至關重要。

   - **使用工具**：雲端基礎結構專案上的所有Adobe Commerce都包含對New Relic的存取權，這有助於在Commerce應用程式和雲端基礎結構中監視效能和調查事件。 其他工具包括Google PageSpeed Insights和GTMetrix。

   - **要監視的專案**：以下是雲端基礎結構上Adobe Commerce要監視的主要專案：

      - **健康狀態通知**：磁碟空間和環境健康狀態警示。

      - **觀察**：綜合監視結合來自多個來源的記錄檔資料，以進行有效的網站管理。

      - **New Relic服務**：以關鍵量度為焦點，監視中繼及生產環境的效能。

      - **受管理的警示原則**：追蹤具有預先定義臨界值的測量結果，以觸發影響效能之基礎結構或應用程式問題的通知。

  >[!TIP]
  >
  >請參閱&#x200B;_雲端指南_&#x200B;中的[效能監視](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/monitor/performance)。


- **資料庫效能最佳化**：若要在Adobe Commerce Cloud中最佳化資料庫效能，請實作下列專案：

   - **監視和最佳化MySQL查詢**：識別並解決執行緩慢的查詢，這可以使用MySQL的SHOW FULL PROCESSLIST和EXPLAIN命令完成。 對於更複雜的設定，Pro架構使用者可利用Percona Toolkit來分析查詢記錄檔中的效能問題。

   - **索引管理**：確定每個資料表都有主索引鍵並移除任何重複的索引，因為這樣會降低效率，並在同時寫入時導致衝突。

   - **Cron工作最佳化**： Cron工作應排程在非尖峰時段，以將對效能的影響降至最低，尤其是在索引等背景工作頻繁的情況下。

  >[!TIP]
  >
  >請參閱[解決資料庫效能問題的最佳實務](resolve-database-performance-issues.md)。

- **監視CDN**：若要在Adobe Commerce Cloud中監視Fastly CDN效能，您可以執行下列動作：

   - **利用New Relic進行監視**： Adobe Commerce提供New Relic來監視中繼和生產環境上的Fastly效能和其他量度。 此工具可深入分析伺服器健康狀態、CDN快取和網路要求隨時間的變化，有助於識別模式並最佳化CDN設定。

   - **Fastly記錄分析**：對於Adobe Commerce Cloud Pro專案，您可以使用New Relic記錄檔來檢閱和分析Fastly CDN和WAF記錄檔資料，以追蹤效能趨勢、安全性事件，並診斷錯誤或延遲問題。

   - **使用cURL命令**：執行具有Fastly特定標頭的cURL命令以檢查網站的快取狀態。 金鑰回應標頭包含`X-Cache` (HIT/MISS)、`Fastly-Module-Enabled`、`Fastly-Magento-VCL-Uploaded`和`Cache-Control`，以驗證快取和模組狀態。 Adobe為中繼和生產環境提供範例cURL命令。

   - **檢查標頭資訊**： Inspect標頭（例如`Cache-Control`、`Pragma`和`X-Magento-Tags`）以確認是否對快取的內容有適當的快取行為和標籤處理。 適當的標頭值可指出快取設定是否有效地套用在整個CDN。

   - **Fastly偵錯和測試**：使用Fastly的偵錯功能來識別和疑難排解快取HIT和MISS率、快取邏輯或不正確的標頭回應等問題，這些問題可能指向設定問題或與預期的快取規則不符。

這些監控步驟有助於維持最佳的CDN效能，並解決影響網站速度和可靠性的問題。

>[!TIP]
>
>請參閱&#x200B;_雲端指南_&#x200B;中的[Fastly服務總覽](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/cdn/fastly)。

#### 定期安全性監控

為了在Adobe Commerce Cloud中維持定期的安全性監控，Adobe建議採用多層面的方法，包括持續掃描、記錄和主動式安全性做法。 以下是確保持續安全性的幾個核心動作：

- **安全性掃描**：使用Adobe的安全性掃描工具來監視您Commerce網站上的已知漏洞和惡意軟體。 此工具會針對潛在安全性風險和法規遵循問題提供警示。

- **定期修補程式和更新維護**：套用Adobe的安全性修補程式和更新程式。 升級至最新的Adobe Commerce版本，可確保擁有最新的威脅防禦能力。

- **稽核與記錄監控**：運用New Relic記錄檔（適用於Pro專案）等工具，集中及分析中繼與生產環境的安全記錄，提高潛在安全性問題與破壞的能見度。

- **帳戶與存取管理**：定期稽核使用者與管理員帳戶，以移除任何未經授權或過時的帳戶。 透過針對管理員使用者的多重驗證(MFA)來加強存取控制。

- **Web應用程式防火牆(WAF)**：使用整合的Fastly WAF偵測並減輕惡意流量模式的威脅，例如未經授權的資料擷取嘗試。

- **自訂程式碼和擴充功能安全性**：執行一般程式碼稽核，並將擴充功能限製為經Adobe驗證的擴充功能，以保護任何自訂程式碼或協力廠商擴充功能的安全。

>[!TIP]
>
>請參閱&#x200B;_系統管理系統指南_&#x200B;中的[安全性](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/systems/security/security)。

#### 錯誤記錄與監視

為了在Adobe Commerce Cloud中監控錯誤記錄，Adobe提供了數種工具和實務，以便有效進行疑難排解和效能管理：

- **使用New Relic的記錄彙總**： New Relic會收集並集中來自Adobe Commerce應用程式的記錄檔，包括與基礎架構、CDN和WAF相關的記錄檔。 此設定可簡化錯誤追蹤、建立控制面板和查詢記錄，以深入瞭解應用程式效能和問題。 存取New Relic記錄檔可依各種屬性搜尋和篩選記錄檔，以便快速診斷問題。

- **錯誤記錄型別**： Adobe Commerce Cloud中的金鑰錯誤記錄包含`cloud.log`和`cloud.error.log`，其中含有部署回饋，並記錄部署警告和錯誤。 其他用於偵錯的特定記錄檔包括`debug.log`、`system.log`和`exception.log`，每個記錄檔都會在整個Commerce平台的錯誤和事件追蹤中提供不同的角色。

- **使用Monolog的自訂記錄**： Adobe Commerce支援透過Monolog的自訂記錄，如此可讓開發人員將記錄訊息導向各種目的地，例如檔案、資料庫，甚至警示。 此彈性對於建置進階記錄策略非常有用，可因應開發和生產環境的不同監控需求。

- **使用全網站分析工具監控例外狀況**：全網站分析工具可協助監控及管理例外狀況記錄檔，識別部署和應用程式事件間的週期性問題。 此工具會強調常見問題，讓您更輕鬆地排定優先順序並處理影響效能的關鍵問題。

>[!TIP]
>
>如需Adobe Commerce Cloud中記錄與錯誤追蹤實務的詳細資訊，請參閱[New Relic記錄管理](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/monitor/new-relic/log-management)與[例外狀況監視](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/site-wide-analysis-tool/exceptions)。

### 安全性與更新

#### 安全性修補程式與更新

為了持續更新並確保Adobe Commerce Cloud系統的安全性，以下提供監控安全性修補程式和更新的一些主要作法：

- **訂閱Adobe Commerce安全性警示**：透過[註冊來自Adobe](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/systems/security/security)的通知，隨時掌握安全性弱點的最新資訊。

- **檢查發行說明**：定期檢閱[安全性修補程式發行說明](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/release/notes/security-patches/overview)，這些發行說明在版本（例如2.3.5-p1）上標示「 — pN」，並包含關鍵修正和改良。

- **立即套用安全性修補程式**：一旦有可用的安全性修補程式，立即套用。 這包括更新至最新版本或套用特定修補程式檔案。

- **使用雲端修補程式**：若為Adobe Commerce Cloud，可在Cloud Tools Suite中整合安全性修補程式。 請務必升級套裝或Commerce版本，以接收這些修正。

- **自動修補管理**：請考慮使用集中式修補程式之類的工具，自動[管理和套用多個存放區的修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/implementation-playbook/best-practices/maintenance/patching-at-scale)。

>[!TIP]
>
>如需套用修補程式和維護安全性的詳細資訊和逐步指示，請參閱[安全性修補程式發行說明](../../../release/release-notes/security/overview.md)和[如何套用安全性修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/how-to/how-to-obtain-and-apply-security-patches)。 您也應該檢閱[全網站分析工具](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/site-wide-analysis-tool/access)報告。

#### PCI法規遵循

若要確保Adobe Commerce Cloud符合PCI規範，請遵循下列主要作法：

- **Protect持卡人資料**：請勿在Adobe Commerce中儲存持卡人資料。 如果需要儲存，請使用加密和代碼化方法來保護儲存。

- **使用安全傳輸通訊協定**：一律透過TLS等安全通訊協定傳輸付款資料，並具備加密和適當的金鑰管理。

- **利用Web應用程式防火牆(WAF)**： Fastly支援的WAF服務可在惡意流量到達您的網站之前，封鎖惡意流量，協助您符合PCI DSS 6.6需求，並防止常見漏洞。 在[這裡](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/implementation-playbook/best-practices/planning/payment-processing-storage)和[這裡](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/cdn/fastly-waf-service)檢視更多資訊。

- **限制存取**：確保只有授權人員才能存取敏感的付款資料，並[套用存取控制以降低暴露風險](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/implementation-playbook/best-practices/planning/payment-processing-storage)。

- **一般安全性掃描**：執行一般PCI ASV掃描和[監視您的環境](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/security-and-compliance/shared-responsibility)，以解決潛在的漏洞。

>[!TIP]
>
>如需維護Adobe Commerce PCI相容性的詳細准則，請參閱[付款處理與儲存的最佳實務](../planning/payment-processing-storage.md)。

### 使用者和客戶支援

#### 設定

- **支援管道**：實作客戶支援管道，例如：

   - **即時交談**：提供即時聊天支援，以立即取得協助。 熱門解決方案包括Zendesk、Intercom和Tidio。

   - **電子郵件支援**：使用Freshdesk或Zoho Desk等支援票證系統，有效管理客戶查詢。

   - **電話支援**：如果您有大量客戶群，請考慮在工作時間提供電話支援。

#### 管理員使用者培訓

- **內部訓練**：訓練您的員工如何使用Adobe Commerce管理員、處理訂單、管理產品及處理客戶服務問題。

- **檔案**：維護內部知識庫或使用者手冊，以取得常見問題(FAQ)、疑難排解及一般工作的相關資訊。

#### 客戶體驗最佳化

- **調查和意見反應**：使用調查來收集客戶意見反應並最佳化客戶體驗。 Adobe Commerce支援與SurveyMonkey或Google Forms等工具的整合。

- **檢閱管理**：管理客戶對您產品的檢閱和評等。 鼓勵快樂的客戶離開評論，同時適當地回應負面評論。

- **Personalization**：實作個人化功能，例如個人化產品推薦或鎖定目標的促銷活動。

### 持續性商店維護和最佳化

#### 搜尋引擎最佳化(SEO)

- **內容最佳化**：定期更新產品說明、部落格和類別頁面，讓內容保持最新狀態並與搜尋引擎相關。

- **SEO稽核**：使用Google Search Console或Screaming Frog之類的工具，執行一般SEO稽核以識別SEO問題（例如，連結損毀、遺失中繼資料、重複內容）。

- **URL結構**：保持簡潔的邏輯URL結構，並確定沒有中斷的連結或重新導向。

#### 轉換率最佳化(CRO)

- **A/B測試**：針對不同的頁面元素（例如產品頁面或結帳程式）執行A/B測試，以提高轉換率。

- **購物車放棄**：實作購物車放棄電子郵件行銷活動或退出意圖快顯視窗，以復原損失的銷售。

- **簽出最佳化**：減少步驟數並提供來賓簽出功能以改善轉換，藉此簡化您的簽出程式。

#### 行銷整合

- **電子郵件行銷活動**：設定歡迎電子郵件、捨棄的購物車電子郵件和購買後追蹤的自動電子郵件行銷流程。 Adobe Marketo、Mailchimp或Klaviyo等平台可與Adobe Commerce妥善整合。

- **社群媒體和廣告整合**：與Facebook、Instagram和Google Ads等平台整合，以執行目標式行銷活動並追蹤成效。

#### 行動裝置最佳化

- **行動裝置回應能力**：定期測試您網站的行動裝置回應能力和可用性。 鑑於行動商務正在成長，行動優先對於持續成功至關重要。

- **行動裝置效能**：使用Google的行動裝置相容測試與效能工具，將您的行動裝置商店體驗最佳化。

### 縮放比例和新功能開發

- **自動縮放流量處理**：

   - Adobe Commerce Cloud支援自動調整規模，以根據即時流量需求動態調整伺服器資源（例如網頁節點），確保您的商店可以處理大量訪客，無需手動干預。 請參閱&#x200B;_雲端指南_&#x200B;中的[自動縮放](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/architecture/autoscaling)。

   - Web和服務層可以獨立擴展，新增更多的Web節點以增加流量，並擴展資料庫或服務節點以在尖峰期間提高後端效能。 請參閱&#x200B;_雲端指南_&#x200B;中的[縮放架構](https://experienceleague.adobe.com/zh-hant/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture)。

- **效能監視**：

   - 使用&#x200B;**New Relic**&#x200B;來監視即時效能測量結果（例如CPU使用率、流量等級），並視需要進行調整。

   - 在縮放之前在中繼環境中測試效能，以避免生產中的問題。

- **新功能的開發**：

   - 整合進階功能，例如&#x200B;**AI驅動的個人化**、**訂閱管理**&#x200B;和自訂解決方案。

   - 在部署到生產環境之前，持續在中繼環境中測試和調整功能，以將停機時間降至最低。

- **進行中的網站維護**：

   - 定期審查系統記錄和效能指標，以找出需要改進的領域。

   - 確保基礎架構保持可擴充，並可因應新業務需求與成長調整。

>[!TIP]
>
>如需詳細指引，請參閱[維護最佳實務](overview.md)、[個人化](https://business.adobe.com/blog/the-latest/adobe-commerce-continues-investment-in-composable-development-tools-and-ai-powered-personalization)和[功能開發](https://business.adobe.com/blog/the-latest/adobe-commerce-continues-investment-in-composable-development-tools-and-ai-powered-personalization)。

### 報告與分析

- **Adobe Commerce Intelligence：** Commerce Intelligence是Adobe Commerce的核心功能，可跨多個資料來源提供最佳實務深入分析，讓商家能夠做出科學資料導向式決策，並採取清楚且明智的動作。 請參閱&#x200B;[_Commerce Intelligence使用手冊_](https://experienceleague.adobe.com/zh-hant/docs/commerce-business-intelligence/mbi/getting-started)。

- **Adobe Analytics：** Adobe Analytics提供強大的解決方案，可追蹤、分析和最佳化您的線上商店效能。 Adobe Analytics可協助電子商務企業深入瞭解客戶行為、產品績效、轉換率和其他關鍵量度，進而制定資料導向式決策。

- **Google Analytics：**&#x200B;使用Google Analytics追蹤客戶行為、流量來源和轉換率。

- **其他Commerce Intelligence工具：** Adobe Commerce包含進階報告。 此功能可讓您存取一套以您的產品、訂單和客戶資料為根據的動態報表，以及根據您的業務需求量身打造的個人化儀表板。如需詳細資訊，請參閱&#x200B;_管理員使用指南_&#x200B;中的[進階報表](https://experienceleague.adobe.com/zh-hant/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting)。

### 結論

上市後支援和維護是持續性的工作，需要定期關注以確保您的Adobe Commerce商店持續執行良好、保持安全和適應您的業務需求。 實作結構化網站監控、客戶支援、最佳化和更新方法，對於長期的成功至關重要。
