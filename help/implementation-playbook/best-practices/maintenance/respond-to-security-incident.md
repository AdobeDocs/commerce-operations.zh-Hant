---
title: 回應安全性事件
description: 依照最佳實務處理安全性事件，以回應及修正影響網站可用性與效能的安全性問題。
feature: Best Practices
exl-id: 77275d37-4f1d-462d-ba11-29432791da6a
source-git-commit: e63f68dd469564e70269154810cbfbd95d2b2e57
workflow-type: tm+mt
source-wordcount: '1172'
ht-degree: 0%

---

# 回應安全性事件的最佳實務

以下文章總結了回應安全性事件和修正影響Adobe Commerce網站可用性、可靠性和效能之問題的最佳實務。

遵循這些最佳實務有助於防止未經授權的存取和惡意程式碼攻擊。 如果確實發生安全性事件，這些最佳實務可協助您準備立即回應、進行根本原因分析，並管理修復程式以恢復正常作業。

>[!TIP]
>
>Adobe發現，大部分安全事件都發生在威脅行動者利用Commerce應用程式和基礎架構設定中現有的未修補漏洞、不良密碼以及弱所有權和許可權設定時。 在設定、設定和更新Adobe Commerce安裝時，檢閱並遵循Adobe安全性最佳實務，將安全性事件的發生降至最低。 請參閱[保護您的Commerce網站和基礎結構](../launch/security-best-practices.md)。


## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md)：

- 雲端基礎結構上的Adobe Commerce
- Adobe Commerce內部部署

## 回應事件

如果您懷疑雲端基礎結構專案上的Adobe Commerce受到安全性事件的影響，重要的首要步驟為：

- 稽核所有管理員使用者帳戶存取權
- 啟用進階多重驗證(MFA)控制項
- 保留重要記錄
- 檢閱您的Adobe Commerce版本的安全性升級。

更多建議詳見下文。

## 發生攻擊時立即採取行動

萬一發生網站損毀的不幸事件，請遵循以下重要建議：

- 請您的系統整合商和適當的安全人員參與調查和補救工作。

- 判斷攻擊的範圍：
   - 是否存取過信用卡資訊？
   - 哪些資訊遭竊？
   - 妥協後已經過了多少時間？
   - 資訊是否已加密？

- 請檢閱伺服器記錄檔和檔案變更，嘗試尋找攻擊向量，以判斷網站何時及如何遭到破壞。

   - 在特定情況下，建議清除並重新安裝所有專案，或在虛擬託管的情況下，建立全新的執行個體。 惡意程式碼可能隱藏在不受懷疑的位置，只是等待自我還原。

   - 移除所有不必要的檔案。 然後，從已知乾淨的來源重新安裝所需的檔案。 例如，您可以使用版本控制系統中的檔案，或從Adobe的原始散發檔案來重新安裝。

   - 重設所有認證，包括資料庫、檔案存取、付款和運送整合、網站服務以及管理員登入。 同時重設所有可能用來攻擊系統的整合及API金鑰和帳戶。

## 分析事件

事件分析的第一個步驟是儘可能快速地收集儘可能多的事實。 收集事件相關資訊有助於判斷事件的可能原因。 Adobe Commerce提供下列工具，協助您進行事件分析。

- [稽核管理員動作記錄檔](https://experienceleague.adobe.com/docs/commerce-admin/systems/action-logs/action-log-report.html?lang=zh-Hant)。

  「動作記錄報表」會顯示所有已啟用記錄功能的管理員動作的詳細記錄。 每個記錄都加蓋時間戳記，並註冊使用者的IP位址和名稱。 記錄詳細資訊包括管理員使用者資料以及在動作期間完成的相關變更。

- 使用Adobe Commerce工具[&#128279;](../../../tools/observation-for-adobe-commerce/intro.md)的觀察分析事件。

  Adobe Commerce觀察工具可讓您分析複雜的問題，協助找出根本原因。 與其追蹤不同的資料，您可以花時間將事件和錯誤建立關聯，以更深入地瞭解效能瓶頸的成因。

  使用工具中的&#x200B;**安全性**&#x200B;索引標籤，以清楚檢視潛在的安全性問題，協助找出根本原因，讓網站維持最佳效能。

- 分析包含[New Relic記錄檔](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic/new-relic-service.html?lang=zh-Hant)的記錄檔

  雲端基礎結構上的Adobe Commerce Pro專案包含[New Relic記錄檔](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic/log-management.html?lang=zh-Hant)服務。 此服務已預先設定為彙總來自測試和生產環境的所有記錄資料，以便在集中式記錄管理控制面板中顯示，您可在此搜尋和視覺化彙總的資料。

  對於其他Commerce專案，您可以設定並使用[New Relic記錄檔](https://docs.newrelic.com/docs/logs/get-started/get-started-log-management/)服務來完成下列工作：
   - 使用[New Relic查詢](https://docs.newrelic.com/docs/logs/new-relic-logs/ui-data/query-syntax-logs)來搜尋彙總記錄檔資料。
   - 透過New Relic記錄檔應用程式以視覺效果呈現記錄檔資料。

## 稽核帳戶、程式碼和資料庫

請檢閱Commerce管理員和使用者帳戶、應用程式程式碼以及資料庫設定和記錄檔，以識別並清除可疑的程式碼，確保帳戶、網站和資料庫存取的安全性。 接著，視需要重新部署。

發生事件後，請繼續密切監視網站，因為許多網站在數小時內會再次受到危害。 確保持續進行記錄檢閱和檔案完整性監控，以快速偵測任何新的危害跡象。

### 稽核管理員使用者帳戶

- [檢閱管理員使用者存取權](https://experienceleague.adobe.com/docs/commerce-admin/systems/user-accounts/permissions-users-all.html?lang=zh-Hant) — 移除舊的、未使用的或可疑的帳號，並為所有管理員使用者輪換密碼。

- [檢閱管理員安全性設定](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-admin.html?lang=zh-Hant) — 確認管理員安全性設定遵循安全性最佳實務。

- [在雲端基礎結構專案上檢閱Adobe Commerce的使用者帳戶](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=zh-Hant) — 移除舊的、未使用的或可疑的帳戶，並為所有雲端專案管理員使用者輪換密碼。 請確定已正確設定帳戶安全性設定。

- 在雲端基礎結構上[稽核Adobe Commerce的SSH金鑰](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=zh-Hant) — 檢閱、刪除和輪換SSH金鑰。

### 稽核代碼

- 從Admin檢閱所有範圍層級（包括`website`和`store view`）中的[HTML頁首與頁尾設定](https://experienceleague.adobe.com/docs/commerce-admin/content-design/design/page-setup.html?lang=zh-Hant)。 從指令碼和樣式表中移除任何未知的JavaScript程式碼，以及其他HTML設定。 僅保留可辨識的程式碼，例如追蹤代碼片段。

- 將目前的生產程式碼庫與儲存在版本控制系統(VCS)中的程式碼庫進行比較。

- 隔離任何可疑的代碼。

- 將程式碼基底重新部署至生產環境，確保沒有可疑程式碼殘留。

### 稽核資料庫設定和記錄

- 檢閱任何預存程式以進行修改。

- 確認只有Commerce執行個體才能存取資料庫。

- 使用公開可用的惡意程式碼掃描工具掃描網站，以確認惡意程式碼已不存在。

- 變更Admin面板的名稱，並確認網站`app/etc/local.xml`和`var` URL無法公開存取，以保護該面板。

- 發生事件後，請繼續密切監視網站，因為許多網站在數小時內會再次受到危害。 確保持續進行記錄檢閱和檔案完整性監控，以快速偵測任何新的危害跡象。

## 移除Google警告

如果Google將網站標示為包含惡意程式碼，請在清除網站後要求檢閱。 檢閱受惡意程式碼感染的網站需要幾天時間。 Google判斷網站乾淨後，搜尋結果和瀏覽器的警告應該會在72小時內消失。 請參閱[要求檢閱](https://web.dev/articles/request-a-review)。

## 檢閱惡意程式碼結果檢查清單

如果公開可用的惡意程式碼掃描工具確認惡意程式碼攻擊，請調查事件。 與解決方案整合商合作，清理網站並遵循建議的補救流程。

## 進行其他審查

處理複雜的攻擊時，最好的辦法是與經驗豐富的開發人員、第三方專家或解決方案整合商合作，全面修復網站並審查安全性實務。 與經驗豐富的安全專家合作，可確保採取全面而進階的措施，確保您的企業及其客戶的安全。

## 其他資訊

- [根本原因分析架構](https://sansec.io/kb/incident-response/magento-root-cause-analysis)。
