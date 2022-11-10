---
title: 防止和響應安全事件
description: 了解在雲端基礎架構專案上避免和回應Adobe Commerce安全性事件的最佳實務。
role: Admin, Developer, Leader, User
feature-set: Commerce
feature: Best Practices
source-git-commit: bb9b8cc9993a70ea50667f08c8260759ab0f91dc
workflow-type: tm+mt
source-wordcount: '1073'
ht-degree: 0%

---


# 幫助預防和應對安全事件的最佳做法

Adobe Commerce安全機構 [分擔責任](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-shared-responsibility-guide.pdf) 模型。 了解哪些Adobe和您的技術團隊應負責是關鍵所在。 以下簡要說明 [安全性最佳實務](https://www.adobe.com/content/dam/cc/en/security/pdfs/Adobe-Magento-Commerce-Best-Practices-Guide.pdf) 以確保您的項目具有最佳的安全控制，以及如何對安全事件作出最佳響應。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 共：

- Adobe Commerce雲基礎架構

## 對事件作出回應

您在回應安全事件時有許多考量。 如果您懷疑在雲基礎架構項目上遇到了Adobe Commerce的最近安全事件，則必須審核所有管理員用戶帳戶訪問權、啟用高級多因素身份驗證(MFA)控制、保留重要日誌，並審核Adobe Commerce版本的安全升級。

更多建議於下文詳細說明。 它們有助於防止未經授權的訪問，並開始進一步的事件分析過程。

## 如何防止安全事件

請遵循下列安全性最佳實務，主動預防會影響您Adobe Commerce網站和店面的安全事件：

- [啟用2FA以進行管理員存取](https://docs.magento.com/user-guide/stores/security-two-factor-authentication.html).
雙因素驗證被廣泛使用，通常為同一應用程式上的不同網站產生存取代碼。 這可確保只有您才能登入您的使用者帳戶。 如果您丟失了密碼，或者機器人猜出了密碼，雙因素驗證將增加一層保護。
- [啟用MSH訪問的MFA](https://devdocs.magento.com/cloud/project/project-enable-mfa-enforcement.html).
在項目上啟用MFA時，具有SSH訪問的雲基礎架構帳戶上的所有Adobe Commerce都必須遵循身份驗證工作流，該工作流需要雙重身份驗證(2FA)代碼，或API令牌和SSH證書才能訪問該環境。
- 升級至最新版Adobe Commerce。
Adobe為每個支援的版本發行安全性和功能修補程式Adobe Commerce。
- 設定及使用 [非預設管理URL](https://docs.magento.com/user-guide/stores/store-urls-custom-admin.html).
Adobe建議您使用不重複的自訂管理URL，而非預設URL `admin` 或常見詞語，例如 *後端*. 雖然此配置更改不會直接保護您的站點免受已確定的錯誤操作者的侵害，但它可以減少嘗試獲得未經授權訪問的指令碼的暴露。
- 使用  [`bin/magento config:set` CLI命令 `lock env` 組態選項](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configuration-management/set-configuration-values.html#set-configuration-values-that-cannot-be-edited-in-the-admin). 此選項會鎖定設定值，使其無法在「管理員」中編輯，或防止對已鎖定的設定進行變更。 使用此選項時，配置變更會寫入 `<Commerce base dir>/app/etc/env.php` 檔案。
- 設定並執行 [Adobe Commerce安全掃描工具](https://docs.magento.com/user-guide/magento/security-scan.html).
增強的安全掃描允許您監視每個Adobe Commerce站點(包括PWA)，以了解已知的安全風險和惡意軟體，並接收補丁程式更新和安全通知。
- [檢閱和更新管理員使用者存取權](https://docs.magento.com/user-guide/system/permissions-users-all.html) 和 [安全設定](https://docs.magento.com/user-guide/stores/security-admin.html).
   - 建議您移除任何舊帳戶、未使用帳戶或可疑帳戶，並為所有管理員使用者輪換密碼。
   - 檢閱並更新專案的進階安全設定&lt;。 管理安全設定可讓您將機密金鑰新增至URL、要求密碼區分大小寫，以及限制管理員工作階段的長度，包括密碼的存留期和在鎖定管理員使用者帳戶前可進行的登入嘗試次數。 為了提高安全性，您可以在當前會話過期之前配置鍵盤未活動的時間長度，並要求用戶名和密碼區分大小寫。
- 審計Adobe Commerce [雲端專案使用者](https://devdocs.magento.com/cloud/project/user-admin.html).
建議刪除任何舊帳戶、未使用帳戶或可疑帳戶，並請用戶更改其密碼。
- 稽核 [SSH金鑰](https://devdocs.magento.com/cloud/before/before-workspace-ssh.html) 適用於雲端基礎架構上的Adobe Commerce。
建議您檢閱、刪除和旋轉SSH金鑰。
- 為管理員實作存取控制清單(ACL)。
您可以結合自訂功能，使用Abmey Edge ACL清單 [VCL程式碼片段](https://devdocs.magento.com/cloud/cdn/fastly-vcl-allowlist.html#vcl) 以篩選傳入的請求，並允許管理員依IP位址存取。

## 分析事件

事件分析的第一步是盡可能快地收集盡可能多的事實。 收集事件相關資訊有助於確定事件的潛在原因。 Adobe Commerce提供下列工具，協助您進行事件分析。

- [稽核管理員動作記錄](https://docs.magento.com/user-guide/system/action-log-report.html).
「動作記錄報表」會顯示所有已啟用記錄功能之管理動作的詳細記錄。 每個記錄都加上時間戳記，並註冊使用者的IP位址和名稱。 記錄詳細資料包含管理員使用者資料和動作期間所做的相關變更。
- 使用 [Adobe Commerce工具觀察](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html?lang=en).
「Adobe Commerce觀察」工具可讓您分析複雜問題，協助找出根本原因。 與其跟蹤不同的資料，您可以花時間關聯事件和錯誤，以便更深入地了解效能瓶頸的原因。
此工具旨在清楚了解某些潛在網站問題，協助您找出根本原因，並讓網站以最佳方式運作。 按一下上方Adobe Commerce工具檔案的觀察連結，以存取工具檔案。 說明檔案中有一個區段，詳細說明可在 **安全性** 標籤。
- 使用分析日誌 [新舊日誌](https://devdocs.magento.com/cloud/project/new-relic.html#new-relic-logs). Adobe Commerce on cloud infrastructure Pro專案包括 [新舊日誌](https://docs.newrelic.com/docs/logs/new-relic-logs/get-started/introduction-new-relic-logs) 服務。 服務已預先設定，可匯總您的測試和生產環境中的所有記錄資料，以在集中的記錄管理控制面板中顯示。
您可以使用New Relic Logs服務完成下列工作：
   - 使用 [新的Relic查詢](https://docs.newrelic.com/docs/logs/new-relic-logs/ui-data/query-syntax-logs) 搜索聚合日誌資料。
   - 透過New Relic Logs應用程式視覺化記錄資料。

## 其他資訊

- [根本原因分析框架](https://sansec.io/kb/incident-response/magento-root-cause-analysis).
