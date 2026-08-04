---
title: 安全性與法規遵循：必要的動作與截止日期
description: 瞭解雲端版本和軟體相依性不支援的Adobe Commerce的安全性強制執行，包括截止日期、所需行動和風險。
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
feature_v2:
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
  - id: c32adafa-ed01-4b31-997e-2413013911b0
  - id: cc250cf1-34eb-4863-80d0-d170d45ea067
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
subfeature_v2:
  - id: f2261633-201d-46c5-8a66-999e70527a83
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
badgePaas: label="僅限雲端上的Adobe Commerce" type="Informative" url="https://experienceleague.adobe.com/zh-hant/docs/commerce/user-guides/product-solutions" tooltip="僅適用於Adobe Commerce on Cloud 2.4.4到2.4.9版"
color: blue
source-git-commit: 79afa4fa95c425dfd4bc0fd894abc24db2d1b33b
workflow-type: tm+mt
source-wordcount: 2040
ht-degree: 0%

---


# 安全性與法規遵循通知：必要的動作與截止日期

>[!NOTE]
>
> **套用至：**&#x200B;執行Adobe Commerce 2.4.4到2.4.9版的雲端(PaaS)環境上的Adobe Commerce。
>
> 此指引不適用於[!DNL Adobe Commerce as a Cloud Service] (SaaS)環境或Adobe Commerce內部部署。

網路安全的格局正在發生根本性的改變，企業已具備的防禦機制需要快速演化。 安全性對電子商務企業至關重要，因為線上交易需要他們處理敏感的個人和業務資料，在違規事件中使他們面臨財務和身分風險。 PaaS電子商務環境在Adobe和我們的客戶之間具有共同的安全責任模式，客戶負責維護應用程式層相依性、與第三方軟體的整合以及部署管道。

Adobe會主動處理不斷演變的風險，並確保我們在雲端上設定Adobe Commerce的客戶，以達到最高的安全性標準。 其中包括：

* 每月和隔離的安全性修正，針對關鍵弱點提供更快速且可預測的保護
* 提供長期支援的年度修補程式發行
* 透過3年的支援期間，簡化每個版本的生命週期原則

雖然Adobe會採取必要步驟來保護客戶的安全，但Adobe Commerce on Cloud的[共用責任模式](../security-and-compliance/shared-responsibility.md)要求我們的客戶一律使用Adobe Commerce on Cloud的支援版本和協力廠商軟體、套用應用程式修補程式、稽核協力廠商擴充功能，以及安全自訂程式碼。 已超過廠商支援期限的軟體不再接收安全性修補程式，因此軟體中的安全性問題無法解決。 繼續在不支援的軟體上執行您的電子商務店面，會產生真實且不斷增加的安全性風險。

本頁面概述雲端Adobe Commerce （版本2.4.4到2.4.9）上所有客戶為確保其電子商務環境安全所需採取的行動、強制執行日期，以及未符合安全需求時的期望。

## 維護安全、合規的環境所需的動作

為了確保您的電子商務環境安全且相容，Adobe Commerce on Cloud的所有客戶都必須使用：

1. 所有協力廠商軟體相依性的支援版本：PHP、MariaDB、Elasticsearch/OpenSearch、Redis和RabbitMQ

1. 雲端上的Adobe Commerce的安全且支援版本

請依照下列准則檢查您是否需要採取動作來保護雲端環境上的Adobe Commerce。 不符合下表1所列截止日期之安全性需求的環境，將會暫停傳入流量，使店面離線。 若您對完成期限有任何顧慮，且需要短期的延長時間，請連絡您的客戶團隊或Adobe [支援](https://experienceleague.adobe.com/zh-hant/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#support-case)。

**表1：安全性需求與截止日期**

| 雲端上的Adobe Commerce版本 | 升級至支援的協力廠商軟體相依性 | 升級至雲端版本上的最新Adobe Commerce，或移轉至[!DNL Adobe Commerce as a Cloud Service] |
| --- | --- | --- |
| 2.4.4或2.4.5 | 2026年10月30日前必填。 | 2027年6月1日前必填 |
| 2.4.6或2.4.7 | 視軟體而定，需在2026年10月30日或2027年5月31日之前完成。 | 2028年6月1日前必填 |
| 2.4.8或2.4.9 | 視軟體而定，需在2026年10月30日或2027年5月31日之前完成。 | 目前不需要 |

## 保護環境的詳細步驟

### 動作1：驗證及升級協力廠商軟體相依性

檢查您的環境是否正在執行下列協力廠商軟體相依性的廠商支援版本：PHP、MariaDB、Elasticsearch/OpenSearch、Redis、RabbitMQ。 如果沒有，請將軟體相依性升級至支援的版本。

#### 步驟1：檢查您的協力廠商軟體相依性版本

1. 登入[雲端主控台](https://experienceleague.adobe.com/zh-hant/docs/commerce-on-cloud/start/cloud-console)。
2. 開啟相關專案，然後選取您要檢閱的環境。
3. 檢查`.magento/services.yaml`檔案中該環境的服務設定，其定義雲端上的Adobe Commerce所支援的服務名稱和版本。

如需詳細指示，請參閱[設定服務](https://experienceleague.adobe.com/zh-hant/docs/commerce-on-cloud/user-guide/configure/service/services-yaml)。

所有不支援的軟體相依性都必須升級至下表2中時間表所列的版本。

**表2：必要的相依性升級**

| 相依性 | 版本 | 必須升級至 | 期限 |
| --- | --- | --- | --- |
| PHP | 8.1及以下的版本 | 8.2或更新版本 | 2027年5月31日 |
| MariaDB/Galera | 10.5及以下 | 10.6或更新版本 | 2026年10月30日 |
| MariaDB/Galera | 高於10.5但低於10.11 | 10.11版或更新版本 | 2027年5月31日 |
| Elasticsearch | 任何版本 | OpenSearch：2.19版，適用於2.4.4和2.4.5客戶。 2.4.6及更高版本客戶的第3版。 | 2026年10月30日 |
| OpenSearch | 1.x | 2.19版（適用於2.4.4和2.4.5客戶）。 2.4.6及更高版本客戶的第3版。 | 2027年5月31日 |
| Redis | 5以下（含） | Valkey 8或更高版本 | 2027年5月31日 |
| RabbitMQ | 3.9及以下的版本 | 3.13版或更新版本 | 2026年10月30日 |
| RabbitMQ | 大於3.9但小於3.13 | 4.3或更新版本 | 2027年5月31日 |

#### 步驟2：準備進行協力廠商軟體相依性升級

Adobe將協助您直接升級這些軟體相依性。

* **開始：**&#x200B;開啟[支援票證](https://experienceleague.adobe.com/zh-hant/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#support-case)，其中列出您需要升級的環境和相關的相依性。 請在執行日期前至少30天開啟票證，讓Adobe可以排程工作。

* **停機時間：** Adobe會在排程時與您確認預期的視窗。

* **測試：**&#x200B;在生產之前升級並驗證非生產環境。 至少需驗證結帳、搜尋、購物車及任何自訂整合。 需求適用於您的所有環境，因此請規劃升級每個環境，而非僅憑生產環境。

* **相容性：**&#x200B;這些變更大多是相同軟體中的版本升級，而且風險很低。 下列變更值得密切關注：

  * **Elasticsearch到OpenSearch**&#x200B;和&#x200B;**Redis到Valkey**&#x200B;正在移轉至不同的軟體，而非版本升級。 參照原始服務的自訂程式碼、擴充功能或設定可能需要更新。
  * 從&#x200B;**PHP 8.1升級至8.2**&#x200B;時，可能會出現自訂程式碼和協力廠商擴充功能中的棄用警告。

如果您使用協力廠商擴充功能，請向您的廠商確認其最新版本支援您的目標軟體版本。 如果您與解決方案整合商合作，請讓他們及早參與升級規劃、測試和驗證。

### 動作2：檢查雲端上的Commerce版本，並升級至支援的版本

檢查您的環境執行雲端上的Adobe Commerce版本。 如果任何環境不在支援的版本上，您可以升級至2.4.9版或最新支援的版本，或移轉至[!DNL Adobe Commerce as a Cloud Service]。

#### 步驟1：檢查您的Adobe Commerce on Cloud版本和所需動作

1. 登入您的Adobe Commerce管理面板。

   目前版本會顯示在任何Admin頁面的右下角。

1. 如果版本在「管理員」面板中隱藏：

   * 連線到[遠端環境](https://experienceleague.adobe.com/zh-hant/docs/commerce-on-cloud/user-guide/develop/secure-connections#connect-to-a-remote-environment)。
   * 使用Adobe Commerce [命令列工具](../configuration/cli/config-cli.md)檢查版本。

     ```shell
     bin/magento --version
     ```

請檢視下表中您的Adobe Commerce版本所需的動作。

**表3：雲端上的Adobe Commerce版本升級需求**

| 雲端上的Adobe Commerce目前版本 | 必要動作 | 期限 |
|---|---|---|
| 版本2.4.4或2.4.5 | 在Cloud 2.4.9版（或最新版本）上升級至Adobe Commerce或移轉至[!DNL Adobe Commerce as a Cloud Service]。<br>原因： v2.4.4和2.4.5僅接收核心應用程式的限制、獨立安全性修正，直到2027年5月31日 — 這不包括品質修正、應用程式相依性的相容性支援（例如PHP）或平台相依性更新。 請參閱Adobe的[生命週期原則](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/release/planning/lifecycle-policy)。 | 2027年6月1日 |
| 版本2.4.6或2.4.7 | 在Cloud 2.4.9版（或最新版本）上升級至Adobe Commerce，或移轉至[!DNL Adobe Commerce as a Cloud Service]。<br>原因： 2.4.6版直到2027年8月30日為止仍可繼續支援，而且在2028年5月31日之前，僅會收到核心應用程式的有限且獨立的安全性修正。 2.4.7版於2027年5月31日前獲得標準支援，並於2028年5月31日前獲得延長支援。 請參閱Adobe的[生命週期原則](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/release/planning/lifecycle-policy)。 | 2028年6月1日 |
| 2.4.8或2.4.9版 | 不需要Adobe Commerce on Cloud版本升級動作。 動作1中的協力廠商軟體相依性截止日期仍適用。<br>原因：尚未設定截止日期。 | 目前不需要 |

#### 步驟2：決定升級或移轉路徑

如果您需要升級雲端上的Adobe Commerce版本，您有兩個選項：

1. 升級至雲端上支援的Adobe Commerce版本
1. 移轉至[!DNL Adobe Commerce as a Cloud Service] (SaaS)

若要協助您決定最佳路徑，請使用下表來比較您的選項：

**表格4：雲端上的Adobe Commerce與[!DNL Adobe Commerce as a Cloud Service]**&#x200B;的比較

| | 雲端上的Adobe Commerce 2.4.9版 | [!DNL Adobe Commerce as a Cloud Service] |
|---|---|---|
| **它是什麼** | 最新Adobe Commerce版本包含完整的安全性涵蓋範圍、品質修正和平台相依性更新。 | Adobe完全受管理的commerce平台，專為持續創新而打造，不需要升級額外負荷。 [了解更多](https://experienceleague.adobe.com/zh-hant/docs/commerce/cloud-service/overview)。 |
| **如果是**，則為您最好 | 您想要持續管理自己的基礎建設、升級和修補程式。 | 您想要永遠保留升級週期、降低總體擁有成本，並自動取得Adobe的最新功能，而不需額外付費。 |
| **主要優點** | 符合安全性需求，同時保留現有的設定。 | 快如閃電的邊緣交付店面、高度擴充的目錄、原生數位資產管理，以及內建的創作AI，全都由Adobe管理的基礎建設上。 |

## 如果在截止日期前沒有採取任何動作，會發生什麼情況？

Adobe會繼續致力協助您採取必要步驟，以升級到雲端和協力廠商軟體上的Adobe Commerce支援版本。

如果環境在上述共用強制執行日期前未符合安全性需求，Adobe將被強制採取適當的行動來保證較大安裝群的安全性。 這包括暫停流向受影響基礎結構的流量，因此，您的電子商務店面將會離線。

如果環境在流量暫停後繼續不相容，Adobe可以終止雲端服務，啟動解除委任程式。 退役後，託管電子商務環境中的所有資料和資產（包括所有例項、環境和分支）將會永久刪除且無法還原。

## 支援升級或移轉的資源

**如果您選擇升級至Cloud 2.4.9版的Adobe Commerce：**

* **升級相容性報告：** Adobe提供詳細報告，明確說明升級至Adobe Commerce 2.4.9版所需的專案，包括成本範圍。 [產生您的升級相容性報告](https://supportinsights.adobe.com/commerce/tab/main)。

* **軟體相依性升級：**&#x200B;由於您無法直接升級軟體相依性，請開啟Adobe的[支援票證](https://experienceleague.adobe.com/zh-hant/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#support-case)為您處理升級。 如需詳細資訊，請參閱[設定服務](https://experienceleague.adobe.com/zh-hant/docs/commerce-on-cloud/user-guide/configure/service/services-yaml)。

**如果您選擇移轉至[!DNL Adobe Commerce as a Cloud Service]：**

Adobe提供的工具可減少移轉至[!DNL Adobe Commerce as a Cloud Service]的成本和時間。 您可以免費取得這些軟體。 這些工具僅適用於移轉。 它們不用於Adobe Commerce on Cloud版本升級。 如需完整的移轉指南，包括移轉路徑和階段，請參閱[移轉概觀](https://experienceleague.adobe.com/zh-hant/docs/commerce/cloud-service/migration/overview)。

* **移轉評估：**&#x200B;評定自訂的移轉複雜性。 請參閱[移轉評估工具總覽](https://experienceleague.adobe.com/zh-hant/docs/commerce/cloud-service/migration/migration-tools/assessment)。

* **資料移轉：** [大量和增量資料移轉工具](https://experienceleague.adobe.com/zh-hant/docs/commerce/cloud-service/migration/migration-tools/bulk-data/migration-tool)會將您的資料移至新的[!DNL Adobe Commerce as a Cloud Service]環境。

* **AI輔助移轉和開發人員工具：**&#x200B;由Edge Delivery Services支援的Adobe Developer App Builder和Commerce店面，可加速店面現代化和擴充功能重新平台。

如有疑問，請連絡您的帳戶團隊或聯絡[支援服務](https://experienceleague.adobe.com/zh-hant/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide?lang=en#submit-ticket)。

>[!MORELIKETHIS]
>
>* [生命週期原則](lifecycle-policy.md)
>* 雲端上Adobe Commerce的[版本升級強制原則](version-upgrade-enforcement-policy.md)
>* [共用職責安全性與運作模式](../security-and-compliance/shared-responsibility.md)
