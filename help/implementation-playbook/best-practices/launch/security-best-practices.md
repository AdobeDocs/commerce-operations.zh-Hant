---
title: 保護您的Commerce網站與基礎架構
description: 在設定、設定和更新Adobe Commerce安裝時，透過實作安全性最佳實務來維護安全性。
feature: Best Practices
exl-id: 50d8a464-6496-4e9a-b642-0c6d0eb51ba0
source-git-commit: ee7551374aa6d4ad462dd64ee3d05b934b43ce45
workflow-type: tm+mt
source-wordcount: '2000'
ht-degree: 0%

---

# 保護您的Commerce網站與基礎架構

為部署在雲端基礎結構上的Adobe Commerce專案建立和維護安全的環境，是Adobe Commerce客戶、解決方案合作夥伴和Adobe共同的責任。 本指南旨在為方程式中的客戶提供最佳實務。

雖然您無法消除所有安全性風險，但套用這些最佳實務會強化Commerce安裝的安全性狀態。 安全的網站和基礎建設會降低惡意攻擊的吸引力，確保解決方案和客戶敏感資訊的安全性，並有助於將可能導致網站中斷和昂貴調查的安全相關事件降至最低。

>[!NOTE]
>
>如需在雲端基礎結構上保護和維護Adobe Commerce專案的角色和責任的詳細資訊，請參閱&#x200B;_Adobe Commerce安全性與合規性指南_&#x200B;中的[共用責任模式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/security-and-compliance/shared-responsibility#security-responsibilities-chart)。

[所有支援的版本](../../../release/versions.md)：

- 雲端基礎結構上的Adobe Commerce
- Adobe Commerce內部部署

## 優先順序建議

Adobe認為下列建議為所有客戶的最高優先順序。 在所有Commerce部署中實作這些重要的安全性最佳實務：

![檢查清單](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **為您的管理員和所有SSH連線啟用雙因素驗證**

- [Commerce管理員的安全性](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication.html?lang=zh-Hant)

- [安全SSH連線](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/multi-factor-authentication.html?lang=zh-Hant) （雲端基礎結構）

在專案上啟用MFA時，具有SSH存取權的雲端基礎結構帳戶上的所有Adobe Commerce都必須遵循驗證工作流程。 此工作流程需要雙因素驗證(2FA)代碼，或API權杖和SSH憑證才能存取環境。

![檢查清單](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **保護管理員**

- [設定非預設管理員URL](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/store-urls.html?lang=zh-Hant#use-a-custom-admin-url)，而不使用預設`admin`或常用辭彙（例如`backend`）。 此設定可減少嘗試取得未經授權存取您網站的指令碼暴露情形。

- [設定進階安全性設定](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-admin.html?lang=zh-Hant) — 將機密金鑰新增至URL、要求密碼必須區分大小寫，並限制管理員工作階段長度、密碼存留時間間隔，以及在鎖定管理員使用者帳戶之前允許的登入嘗試次數。 為了提高安全性，請設定目前工作階段到期前鍵盤閒置的時間長度，並要求使用者名稱和密碼區分大小寫。

- [啟用ReCAPTCHA](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/captcha/security-google-recaptcha.html?lang=zh-Hant)以保護管理員不受自動暴力攻擊。

- 將[管理員許可權](https://experienceleague.adobe.com/docs/commerce-admin/systems/user-accounts/permissions.html?lang=zh-Hant)指派給角色和角色指派給管理員使用者帳戶時，請遵循最低許可權原則。

![檢查清單](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **升級至Adobe Commerce的最新版本**

透過[將您的Commerce專案升級至Adobe Commerce、Commerce服務和擴充功能的最新版本](#upgrade-to-the-latest-release) (包括安全性修補程式、Hotfix和Adobe提供的其他修補程式)，保持您的程式碼更新。

![檢查清單](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **安全敏感設定值**

使用[組態管理](../../../configuration/cli/set-configuration-values.md)來鎖定重要的組態值。

`lock config`和`lock env` CLI命令會設定環境變數，以防止它們從管理員更新。 命令會將值寫入`<Commerce base dir>/app/etc/env.php`檔案。 (若為雲端基礎結構專案上的Commerce，請參閱[存放區組態管理](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html?lang=zh-Hant#sensitive-data)。)

![檢查清單](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **執行安全性掃描**

使用[Commerce安全性掃描服務](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html?lang=zh-Hant)來監視所有Adobe Commerce網站是否有已知的安全性風險和惡意軟體，並註冊接收修補程式更新和安全通知。

## 確保擴充功能和自訂程式碼的安全性

當您從Adobe Commerce Marketplace新增協力廠商擴充功能或新增自訂程式碼來擴充Adobe Commerce時，請套用下列最佳實務來確保這些自訂的安全性：

![檢查清單](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **選擇精通安全性的合作夥伴或解決方案整合商(SI)** — 選取遵循安全開發實務並具有防止和解決安全性問題的可靠記錄的組織，以確保安全整合及自訂程式碼的安全傳遞。

![檢查清單](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **使用安全擴充功能** — 請諮詢您的解決方案整合商或開發人員，並遵循[Adobe擴充功能最佳實務](../planning/extensions.md)，以識別Commerce部署最適當且安全的擴充功能。

- 僅限來自Adobe Commerce Marketplace或透過解決方案整合商的來源擴充功能。 如果擴充功能是透過整合器取得，請確保擴充功能授權的所有權可轉移，以防整合器變更。

- 限制擴充功能和廠商的數量，降低風險暴露。

- 如果可行，在與Commerce應用程式整合之前，請先檢閱擴充功能程式碼的安全性資訊。

- 確保PHP擴充功能開發人員遵循Adobe Commerce開發指導方針、流程和安全性最佳實務。 具體來說，開發人員必須避免使用可能導致遠端程式碼執行或弱加密的PHP功能。 請參閱&#x200B;*擴充功能開發人員最佳實務指南*&#x200B;中的[安全性](https://developer.adobe.com/commerce/php/best-practices/security/)。

![檢查清單](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **稽核程式碼** — 檢閱您的伺服器和原始程式碼存放庫中的開發剩餘專案。 確保沒有可存取的記錄檔、公開可見的.git目錄、執行SQL敘述句的通道、資料庫傾印、php資訊檔案，或任何其他不需要而且可能在攻擊中使用的未受保護檔案。

## 升級至最新版本

Adobe會持續發行更新的解決方案元件，以提升安全性並更能保護客戶，避免可能的危害。 升級至最新版的Adobe Commerce應用程式、已安裝的服務和擴充功能，並套用最新的修補程式，是防範安全威脅的首要和最佳防線。

Commerce通常會每季發佈安全性更新，但保留根據優先順序和其他因素針對主要安全性威脅發佈Hotfix的權利。

請參閱下列資源，以取得可用Adobe Commerce版本、發行週期以及升級和修補程式的資訊：

- [發行版本](../../../release/versions.md)
- [產品可用性](../../../release/product-availability.md) (Adobe Commerce服務和Adobe編寫的擴充功能)
- [Adobe Commerce生命週期原則](../../../release/lifecycle-policy.md)
- [升級指南](../../../upgrade/overview.md)
- [如何套用修補程式](../../../upgrade/patches/overview.md)

>[!TIP]
>
>訂閱[Adobe安全性通知服務](https://www.adobe.com/subscription/adbeSecurityNotifications.html)，以取得最新的安全性資訊，並減輕已知安全性問題的困擾。

## 制定災難回覆計畫

如果您的Commerce網站遭到破壞，請開發並實作完整的災難回覆計畫，快速控制損壞並恢復正常的業務運作。

如果客戶因災難而需要還原Commerce執行個體，Adobe可為客戶提供備份檔案。 如果適用，客戶和解決方案整合商可以執行還原。

在災難回覆計畫中，Adobe強烈建議客戶[匯出其Adobe Commerce應用程式組態](../../../configuration/cli/export-configuration.md)，以便在因業務持續性目的而需要時，輕鬆重新部署。 將組態匯出至檔案系統的主要原因是系統組態優先於資料庫組態。 在唯讀檔案系統中，必須重新部署應用程式以變更敏感的組態設定，以提供額外的保護層。

### 其他資訊

**已在雲端基礎結構上部署Adobe Commerce**

- [備份與災難回覆](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html?lang=zh-Hant#backup-and-disaster-recovery)

- [在雲端基礎結構上為Adobe Commerce儲存配置管理](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html?lang=zh-Hant)

**內部部署Adobe Commerce**

- [匯出組態設定](../../../configuration/cli/export-configuration.md)

   - [匯入組態設定](../../../configuration/cli/import-configuration.md)

   - [備份及回覆檔案系統、媒體及資料庫](../../../installation/tutorials/backup.md)

## 維護安全的站台與基礎建設

本節概述維護Adobe Commerce安裝的網站與基礎架構安全性的最佳實務。 這些最佳實務大多著重於保護電腦基礎建設的安全，因此其中有些建議可能已經實施。

![檢查清單](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **封鎖未經授權的存取** — 請與您的代管合作夥伴合作設定VPN通道，以封鎖對Commerce網站和客戶資料的未經授權存取。 設定SSH通道以封鎖對Commerce應用程式的未授權存取。

![檢查清單](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **使用Web應用程式防火牆** — 分析流量並發現可疑模式，例如使用Web應用程式防火牆傳送至未知IP位址的信用卡資訊。

部署在雲端基礎結構上的Adobe Commerce安裝可以使用內建的WAF服務，並與[Fastly服務整合](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html?lang=zh-Hant)搭配使用

![檢查清單](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **設定進階密碼安全性設定** — 設定強式密碼，並按照PCI資料安全性標準在8.2.4節中的建議，至少每90天變更一次。請參閱[設定管理員安全性設定](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-admin.html?lang=zh-Hant)。

![檢查清單](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **使用HTTPS** — 如果Commerce網站是新實作，請使用HTTPS啟動整個網站。 Google不僅使用HTTPS作為排名因素，而且許多使用者甚至不會考慮從網站購買，除非網站受到HTTPS的保護。

## 針對惡意程式碼的Protect

以電子商務網站為目標的惡意程式碼攻擊非常普遍，威脅行為主體不斷開發從交易中獲取信用卡和個人資訊的新方法。

不過，Adobe發現，大多數網站上的妥協並非源自於創新的駭客。 相反地，威脅行動者通常會利用檔案系統中現存的未修補漏洞、不良的密碼，以及薄弱的擁有權和許可權設定。

在最常見的攻擊中，惡意程式碼會插入客戶存放區的絕對頁首或絕對頁尾中。 在那裡，程式碼會收集客戶在店面中輸入的表單資料，包括客戶登入憑證和結帳表單資料。 然後，這些資料會出於惡意目的傳送到另一個位置，而不是傳送到Commerce後端。 此外，惡意程式碼可能會危及管理員執行代碼，以假表單取代原始付款表單，並覆寫付款提供者所設定的任何保護。

使用者端信用卡掠奪者是一種將程式碼嵌入商家網站內容的惡意軟體，可在使用者的瀏覽器中執行，如下圖所示。

![以電子商務網站為目標的惡意程式碼攻擊資料流程](../../../assets/playbooks/malware-data-flow.svg)

在某些動作（例如使用者提交表單或修改欄位值）發生後，Skimmer會將資料序列化並傳送至第三方端點。 這些端點通常是其他受到侵害的網站，會作為轉送資料到其最終目的地的轉送。


>[!TIP]
>
>如果Commerce網站受到惡意程式碼攻擊的影響，請依照Adobe Commerce最佳作法[回應安全性事件](../maintenance/respond-to-security-incident.md)。

### 瞭解最常見的攻擊

以下是常見型別的攻擊，Adobe建議所有Commerce客戶注意並採取措施防止這些攻擊：

- **網站損毀** — 攻擊者透過變更網站的視覺外觀或新增自己的訊息來損害網站。 雖然對網站和使用者帳戶的存取權已受到危害，但付款資訊通常仍會保持安全。

- **殭屍網路** — 客戶的Commerce伺服器會成為傳送垃圾電子郵件之殭屍網路的一部分。 雖然使用者資料通常不會受到危害，但客戶的網域名稱可能會被垃圾郵件篩選器列入封鎖名單，以防止從網域傳送任何電子郵件。 或者，客戶的網站會成為殭屍網路的一部分，導致其他網站上的分散式阻斷服務(DDoS)攻擊。殭屍網路可能會封鎖傳入Commerce伺服器的IP流量，導致客戶無法購物。

- **直接伺服器攻擊** — 資料遭到破壞、後門和惡意程式碼已安裝，且網站作業受到影響。 未儲存在伺服器上的付款資訊不太可能因這些攻擊而受到危害。

- **無訊息卡擷取** — 在這個最災難性的攻擊中，入侵者會安裝隱藏的惡意程式碼或卡擷取軟體，或更糟的是，會修改結帳程式以收集信用卡資料。 然後，資料會傳送到另一個網站，以供在黑暗網站上出售。 這類攻擊可能會在較長的一段時間內不被發現，並可能導致客戶帳戶和財務資訊的重大危害。

- **無訊息金鑰記錄** — 威脅執行者會在客戶伺服器上安裝金鑰記錄程式碼，以收集管理員使用者認證，讓他們可以登入並啟動其他攻擊，而不會被偵測到。

### Protect抵禦密碼猜測攻擊

暴力密碼猜測攻擊可能導致未經授權的管理員存取。 依照下列最佳作法，從這些攻擊Protect您的網站：

- 識別並保護可從外部存取Commerce安裝的所有接觸點。

  設定Commerce專案時，您可以依照Adobe的[優先順序建議](#priority-recommendations)，確保對管理員的存取權（通常需要最嚴格的保護）。

- 設定存取控制清單，只允許來自指定IP位址或網路的使用者存取，藉此控制對Commerce網站的存取。

  您可以使用Fastly Edge ACL搭配自訂VCL程式碼片段，篩選傳入的請求並允許IP位址存取。 檢視[允許要求](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-allowlist.html?lang=zh-Hant)的自訂VCL。


  >[!TIP]
  >
  >如果您僱用遠端員工，請確保將遠端員工的IP位址包含在有權存取Commerce網站的位址清單中。

### 避免點選劫持利用漏洞

Adobe會提供`X-Frame-Options` HTTP要求標頭，供您加入對店面的要求中，以保護您的店面免受點選劫持攻擊。 請參閱&#x200B;*Adobe Commerce設定指南*&#x200B;中的[避免點選劫持](../../../configuration/security/xframe-options.md)。
