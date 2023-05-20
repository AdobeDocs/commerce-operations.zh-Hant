---
title: 防止和響應安全事件
description: 瞭解在雲基礎架構項目中避免和應對Adobe Commerce安全事件的最佳實踐。
role: Admin, Developer, Leader, User
feature-set: Commerce
feature: Best Practices
exl-id: 77275d37-4f1d-462d-ba11-29432791da6a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1073'
ht-degree: 0%

---

# 幫助防止和響應安全事件的最佳做法

Adobe Commerce的安保機構 [共擔責任](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-shared-responsibility-guide.pdf) 模型。 瞭解Adobe和您的技術團隊負責什麼是關鍵。 下面我們總結 [安全最佳做法](https://www.adobe.com/content/dam/cc/en/security/pdfs/Adobe-Magento-Commerce-Best-Practices-Guide.pdf) 確保您的項目擁有最佳的安全控制，以及如何對安全事件作出最佳響應。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 共：

- Adobe Commerce在雲基礎架構上

## 響應事件

在對安全事件作出響應時，有許多考慮。 如果您懷疑您在雲基礎架構項目上遇到了Adobe Commerce最近的安全事件，則必須審核所有管理員用戶帳戶訪問、啟用高級多重身份驗證(MFA)控制、保留關鍵日誌，並查看Adobe Commerce版本的安全升級。

下文詳述了更多建議。 它們可以幫助防止未經授權的訪問並開始進一步分析事件的過程。

## 如何防止安全事件

遵循這些安全最佳實踐，主動預防影響您的Adobe Commerce站點和店面的安全事件：

- [啟用2FA以進行管理員訪問](https://docs.magento.com/user-guide/stores/security-two-factor-authentication.html)。
雙因素認證是應用最廣泛的，在同一應用上為不同的網站生成訪問代碼是常見的。 這確保只有您才能登錄到用戶帳戶。 如果您丟失了密碼或機器人猜測了密碼，二元身份驗證將增加一層保護。
- [為SSH訪問啟用MFA](https://devdocs.magento.com/cloud/project/project-enable-mfa-enforcement.html)。
在項目上啟用MFA時，具有SSH訪問權的雲基礎架構帳戶上的所有Adobe Commerce都必須遵循一個身份驗證工作流，該工作流要求雙重身份驗證(2FA)代碼，或API令牌和SSH證書才能訪問環境。
- 升級到最新版本的Adobe Commerce。
Adobe為每個受支援版本的Adobe Commerce發佈安全和功能修補程式。
- 設定和使用 [非預設管理URL](https://docs.magento.com/user-guide/stores/store-urls-custom-admin.html)。
Adobe建議您使用唯一的自定義管理URL，而不是預設URL `admin` 或常用術語，例如 *後端*。 儘管此配置更改不會直接保護您的站點免受已確定的壞角色的侵害，但它可以減少嘗試獲得未經授權訪問權限的指令碼的暴露。
- 使用  [`bin/magento config:set` CLI命令 `lock env` 配置選項](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configuration-management/set-configuration-values.html#set-configuration-values-that-cannot-be-edited-in-the-admin)。 此選項可以鎖定配置值，使其無法在Admin中編輯，也可以阻止對已鎖定的設定的更改。 使用此選項時，配置更改將寫入 `<Commerce base dir>/app/etc/env.php` 的子菜單。
- 設定並運行 [Adobe Commerce安全掃描工具](https://docs.magento.com/user-guide/magento/security-scan.html)。
增強的安全掃描允許您監視每個Adobe Commerce站點(包括PWA)，以發現已知的安全風險和惡意軟體，並接收補丁程式更新和安全通知。
- [查看和更新管理員用戶訪問權限](https://docs.magento.com/user-guide/system/permissions-users-all.html) 和 [安全設定](https://docs.magento.com/user-guide/stores/security-admin.html)。
   - 我們建議刪除任何舊帳戶、未使用帳戶或可疑帳戶，並為所有管理員用戶輪替密碼。
   - 查看並更新項目的「高級安全設定」&lt;。 管理員安全配置使您能夠向URL添加密鑰、要求密碼區分大小寫以及限制管理員會話的長度，包括密碼的生存期以及在管理員用戶帳戶被鎖定之前可以進行的登錄嘗試次數。 為了提高安全性，您可以配置當前會話過期之前鍵盤不活動的長度，並要求用戶名和密碼區分大小寫。
- 審核Adobe Commerce [雲項目用戶](https://devdocs.magento.com/cloud/project/user-admin.html)。
我們建議刪除任何舊帳戶、未使用帳戶或可疑帳戶，並請用戶更改其密碼。
- 審計 [SSH密鑰](https://devdocs.magento.com/cloud/before/before-workspace-ssh.html) 為Adobe Commerce提供雲基礎設施。
我們建議查看、刪除和旋轉SSH密鑰。
- 為管理員實施訪問控制清單(ACL)。
您可以將Reblished Edge ACL清單與自定義 [VCL代碼段](https://devdocs.magento.com/cloud/cdn/fastly-vcl-allowlist.html#vcl) 過濾傳入請求並允許通過IP地址訪問管理員。

## 分析事件

事件分析的第一步是盡可能快地收集盡可能多的事實。 收集有關事件的資訊可能有助於確定事件的潛在原因。 Adobe Commerce提供以下工具來幫助您進行事件分析。

- [審核管理操作日誌](https://docs.magento.com/user-guide/system/action-log-report.html)。
「Action Logs Report（操作日誌報告）」顯示為日誌啟用的所有管理操作的詳細記錄。 每個記錄都加上時間標籤並註冊用戶的IP地址和名稱。 日誌詳細資訊包括管理員用戶資料和在操作過程中所做的相關更改。
- 使用 [Adobe Commerce工具觀察](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html?lang=en)。
「Adobe Commerce觀察」工具允許您分析複雜問題，以幫助確定根源。 您可以花時間關聯事件和錯誤，而不是跟蹤不同的資料，以便更深入地瞭解效能瓶頸的原因。
該工具旨在清楚地瞭解一些潛在的站點問題，以幫助您確定根本原因並保持站點的最佳運行。 按一下上面「Adobe Commerce觀察」工具文檔的連結以訪問工具文檔。 文檔中有一個部分，詳細列出了 **安全** 頁籤。
- 分析日誌 [New Relic日誌](https://devdocs.magento.com/cloud/project/new-relic.html#new-relic-logs)。 Adobe Commerce在雲基礎架構Pro項目包括 [New Relic日誌](https://docs.newrelic.com/docs/logs/new-relic-logs/get-started/introduction-new-relic-logs) 服務。 該服務已預配置為聚合登台和生產環境中的所有日誌資料，以在集中的日誌管理儀表板中顯示。
您可以使用New Relic日誌服務完成以下任務：
   - 使用 [New Relic查詢](https://docs.newrelic.com/docs/logs/new-relic-logs/ui-data/query-syntax-logs) 搜索聚合日誌資料。
   - 通過New Relic日誌應用程式可視化日誌資料。

## 其他資訊

- [根本原因分析框架](https://sansec.io/kb/incident-response/magento-root-cause-analysis)。
