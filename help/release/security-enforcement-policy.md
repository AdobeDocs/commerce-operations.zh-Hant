---
title: 安全性原則：必要的動作和截止日期
description: 瞭解雲端版本和軟體相依性不支援的Adobe Commerce的安全性強制執行，包括截止日期、所需行動和風險。
TQID: 'https://experienceleague.adobe.com/0JX-Z-dRjsiQk5jO-LLRi-J4GWdylTh4pOfXRPOabxs'
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
badgePaas: label="僅限雲端上的Adobe Commerce" type="Informative" url="https://experienceleague.adobe.com/zh-hant/docs/commerce/user-guides/product-solutions" tooltip="僅適用於Adobe Commerce on Cloud 2.4.4版 — 2.4.9"
nudge: true
source-git-commit: 7512d5cd3fa1917c87b53e25ca69a3dc3c813727
workflow-type: tm+mt
source-wordcount: 1985
ht-degree: 0%

---

# 安全性原則：必要的動作和截止日期

Adobe在雲端環境中實施Adobe Commerce的安全性要求，包括支援的軟體相依性版本和支援的Adobe Commerce版本。 此頁面說明需求、執行日期，以及若不符合需求會發生什麼情況。

## 發生什麼事了？

Adobe企業安全性原則要求雲端上Adobe Commerce的所有Adobe代管環境都必須在安全且相容的軟體上執行，其中包括：

1. 所有協力廠商軟體相依專案(PHP、MariaDB、Elasticsearch/OpenSearch、Redis、RabbitMQ)的支援版本

1. 雲端上的Adobe Commerce的安全且相容版本（版本2.4.8、2.4.9或最新版本）

這是為了降低電子商務環境的安全風險。 未在[表1](#determine-your-required-actions)的截止日期前符合這些要求的環境將暫停輸入流量，使店面離線。 請將此通知視為包含執行日期的安全性和合規性要求。

您可能需要採取兩個動作。

1. 檢查是否支援協力廠商軟體相依性。 如果沒有，請升級至支援的版本。

1. 檢查您是否需將雲端上的Adobe Commerce版本升級至支援的版本。

在底下找到您的Adobe Commerce雲端版本，檢視您的需求，並檢視需求：

1. 協力廠商軟體相依性

1. 雲端上的Adobe Commerce版本

| 您的版本 | 升級協力廠商軟體相依性<br>(PHP、MariaDB、Elasticsearch/OpenSearch、Redis、RabbitMQ)<br>*請參閱[動作1：升級協力廠商軟體相依性](#action-1-upgrade-third-party-software-dependencies)以取得詳細資訊和後續步驟。* | 升級或移轉您的Adobe Commerce版本&#x200B;<br>*請參閱[動作2：如果您需要升級雲端上的Adobe Commerce &#x200B;](#action-2-if-you-need-to-upgrade-your-adobe-commerce-on-cloud-version)，請取得詳細資訊和後續步驟。* |
| --- | --- | --- |
| 2.4.4或2.4.5 | 2026年10月30日前必填。 | 2027年6月1日前必填 |
| 2.4.6或2.4.7 | 視軟體而定，需在2026年10月30日或2027年5月31日之前完成。 | 2028年6月1日前必填 |
| 2.4.8或2.4.9 | 視軟體而定，需在2026年10月30日或2027年5月31日之前完成。 | 目前不需要 |

**表1：版本**&#x200B;的必要動作和截止日期

## 不需要採取動作的使用者

本通知不適用於：

* 使用Adobe Commerce 2.4.8或2.4.9版雲端版，且其環境執行協力廠商軟體支援版本的客戶

* [!DNL Adobe Commerce as a Cloud Service]上的客戶

### 如何檢查您執行的版本

您需要電子商務管理員的協助，才能進行下列步驟以檢查您正在執行的版本。

**您的Adobe Commerce on Cloud版本**

1. 登入您的Adobe Commerce管理面板。

   目前版本應顯示在任何Admin頁面的右下角。

1. 如果版本未顯示在Admin中，請使用[Adobe Commerce命令列工具](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/configuration-guide/cli/config-cli){target="_blank"}執行版本命令：

   ```shell
   bin/magento --version
   ```

**您的軟體相依性版本**

1. 登入[雲端主控台](https://console.adobecommerce.com/)。
1. 開啟相關專案，然後選取您要檢閱的環境。
1. 檢查`.magento/services.yaml`檔案中該環境的服務設定，其定義雲端基礎結構上Adobe Commerce使用的支援服務名稱和版本。
如需詳細指示，請參閱[設定服務](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/services/config-services){target="_blank"}檔案。

## 為什麼此安全性授權很重要

已超過廠商支援終止的軟體不再接收安全性修補程式，這表示該軟體中的已知安全性問題無法修正。 此外，根據[Adobe生命週期原則](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/release/planning/lifecycle-policy)：

* **Adobe Commerce 2.4.4和2.4.5**&#x200B;版現在只接收核心應用程式的限制、獨立安全性修正，直到2027年5月31日為止。 這項有限支援不包括品質修正、應用程式相依性（例如PHP）的相容性支援，或平台相依性更新

* **Adobe Commerce 2.4.6**&#x200B;將持續支援2027年8月30日，並且在2028年5月31日之前僅會收到核心應用程式的有限且孤立的安全性修正

* **Adobe Commerce 2.4.7**&#x200B;版將於2027年5月31日前獲得標準支援，並於2028年5月31日前繼續獲得支援

* **Cloud 2.4.8和2.4.9**&#x200B;版上的Adobe Commerce仍受支援，目前不需要升級版本。

持續在不受支援的軟體上經營電子商務店面，會為貴企業帶來真實且不斷增加的安全性風險，包括維持PCI法規遵循及保護客戶資料的能力。

>[!IMPORTANT]
>
>如果您的環境未在[表格1](#determine-your-required-actions)詳述的截止日期前符合要求，Adobe將會暫停受影響環境的傳入流量。 您的電子商務店面將會離線，不會為購物者提供服務。 請參閱[如果未採取任何動作會發生什麼情況](#what-happens-if-no-action-is-taken)。

## 有關您需要採取的動作的詳細資訊

### 動作1：升級協力廠商軟體相依性

視軟體而定，所有不支援的軟體相依性都必須依照下表所共用的時間表進行升級。 您可以在[雲端主控台](https://console.adobecommerce.com/)中檢視環境，並使用這些[指示](#check-software-dependency-versions)檢查執行中的相依性版本。 軟體相依性升級適用於Cloud 2.4.4到2.4.9版的所有Adobe Commerce。

| 相依性 | 版本 | 必須升級至 | 執行日期 |
| --- | --- | --- | --- |
| PHP | 8.1及以下的版本 | 8.2或更新版本 | 2027年5月31日 |
| MariaDB/Galera | 10.5及以下 | 10.6或更新版本 | 2026年10月30日 |
| MariaDB/Galera | 高於10.5但低於10.11 | 10.11或更新版本 | 2027年5月31日 |
| Elasticsearch | 任何版本 | OpenSearch：<br><br>- 2.19版（適用於2.4.4和2.4.5客戶）<br>- 3 （適用於2.4.6及更高版本）客戶。 | 2026年10月30日 |
| OpenSearch | 1.x | 版本2.19 （適用於2.4.4和2.4.5客戶）。<br>版本3 （適用於2.4.6及更高版本）。 | 2027年5月31日 |
| Redis | 5以下（含） | Valkey 8或更新版本 | 2027年5月31日 |
| RabbitMQ | 3.9及以下的版本 | 3.13或更新版本 | 2026年10月30日 |
| RabbitMQ | 大於3.9但小於3.13 | 4.3或更新版本 | 2027年5月31日 |

**表2：軟體相依性升級需求**

#### 準備進行協力廠商軟體相依性升級

Adobe將協助您直接升級這些軟體相依性。

* **快速入門：**&#x200B;開啟[支援票證](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket)，其中列出您需要升級的環境和相關的相依性。 請在執法日期前至少30天開啟票證，以便我們的團隊能排程工作。

* **停機時間：** Adobe會在排程時與您確認預期的視窗。

* **測試：**&#x200B;在生產之前升級並驗證非生產環境。 至少需驗證結帳、搜尋、購物車及任何自訂整合。 需求適用於您的所有環境，因此請規劃升級每個環境，而非僅憑生產環境。

* **相容性：**&#x200B;這些變更大多是相同軟體中的版本升級，而且風險很低。 請進一步注意下列事項：

  * **Elasticsearch到OpenSearch**&#x200B;和&#x200B;**Redis到Valkey**&#x200B;正在移轉至不同的軟體，而非版本升級。 參照原始服務的自訂程式碼、擴充功能或設定可能需要更新。
  * **PHP 8.1到8.2**&#x200B;可以在自訂程式碼和協力廠商擴充功能中顯示棄用。

如果您使用協力廠商擴充功能，請向您的擴充功能廠商確認，他們目前的版本支援您的目標版本。 如果您與解決方案整合商合作，請讓他們參與規劃和驗證。

### 動作2：如果您需要在雲端版本上升級Adobe Commerce：

您可以選擇(i)升級至雲端版本上支援的Adobe Commerce，或(ii)移轉至Adobe Commerce as a Cloud Service （Adobe的完整受管商務平台）

無論您選擇哪個選項，目前版本的強制實施日期皆適用。

| 目前版本 | 動作 | 執行日期 |
| --- | --- | --- |
| 使用Adobe Commerce on Cloud 2.4.4或2.4.5版 | 升級至Cloud 2.4.9版（或最新版本）上的Adobe Commerce，或移轉至Adobe Commerce as a Cloud Service | 2027年6月1日 |
| 使用Adobe Commerce on Cloud 2.4.6或2.4.7版 | 升級至Cloud 2.4.9版（或最新版本）上的Adobe Commerce，或移轉至Adobe Commerce as a Cloud Service | 2028年6月1日 |
| 在Cloud 2.4.8或2.4.9版上使用Adobe Commerce | 目前不需要Adobe Commerce on Cloud版本升級動作。 動作1中的軟體相依性截止日期仍適用。 | 不適用 |

**表3：如果您必須在雲端版本**&#x200B;上升級目前的Adobe Commerce，則需遵循准則並完成期限

請參閱下列矩陣以取得有關Cloud 2.4.9版的Adobe Commerce和Adobe Commerce as a Cloud Service的更多詳細資料，讓您可以做出明智的決定。

**表4：升級至雲端上的Adobe Commerce與移轉至Adobe Commerce as a Cloud Service**

| | 雲端上的Adobe Commerce 2.4.9版 | Adobe Commerce as a Cloud Service |
| --- | --- | --- |
| 內容 | 最新Adobe Commerce版本包含完整的安全性涵蓋範圍、品質修正和平台相依性更新。 | Adobe完全受管理的commerce平台，專為持續創新而打造，不需要升級額外負荷。 [了解更多](https://experienceleague.adobe.com/zh-hant/docs/commerce/cloud-service/overview)。 |
| 最適合您的是 | 您現在想要持續管理自己的基礎建設、升級和修補程式。 您隨時都可以移轉至Adobe Commerce as a Cloud Service 。 | 您想要永遠保留升級週期、降低總體擁有成本，並自動取得Adobe的最新功能，而不需額外付費。 |
| 主要優點 | 立即符合安全性需求，同時保留現有的設定。 | 快如閃電的邊緣交付店面、高度擴充的目錄、原生數位資產管理，以及內建的創作AI，全都由Adobe管理的基礎建設上。 |

## 如果未採取任何動作會發生什麼事？

如果環境在[以上](#determine-your-required-actions)共用的執行日期之前尚未符合這些要求，Adobe將採取適當行動。 這包括暫停流向受影響基礎結構的流量，因此，您的電子商務店面將會離線。

如果環境在流量暫停後繼續不相容，Adobe可以終止雲端服務，啟動解除委任程式。 退役後，託管電子商務環境中的所有資料和資產（包括所有例項、環境和分支）將會永久刪除且無法還原。

## Adobe會如何協助您的摘要

無論您是升級還是移轉，Adobe都能提供工具和支援，讓轉換儘可能順暢。

**如果您選擇升級至Adobe Commerce on Cloud 2.4.9**

* **升級相容性報告：** Adobe提供詳細報告，明確說明升級至Adobe Commerce 2.4.9版所需的專案，包括時間和成本範圍。 [產生您的升級相容性報告](https://supportinsights.adobe.com/commerce/tab/main)。

* **軟體相依性升級：**&#x200B;由於您無法直接升級軟體相依性，請[開啟Adobe的支援票證](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket){target="_blank"}為您處理升級。 如需詳細資訊，請參閱[設定服務](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/configuration/overview){target="_blank"}。

**如果您選擇移轉至Adobe Commerce as a Cloud Service**

Adobe提供的工具可減少移轉至Adobe Commerce as a Cloud Service的成本和時間。 您無須為此付費。 這些工具僅適用於移轉，不用於雲端上的Adobe Commerce版本升級。 如需完整的移轉指南，包括移轉路徑和階段，請參閱[移轉概觀](https://experienceleague.adobe.com/zh-hant/docs/commerce/cloud-service/migration/overview)。

* **移轉評估：**&#x200B;評定自訂的移轉複雜性。 請參閱[移轉評估工具總覽](https://experienceleague.adobe.com/zh-hant/docs/commerce/cloud-service/migration/migration-tools/assessment)。

* **資料移轉：** [大量與增量資料移轉工具](https://experienceleague.adobe.com/zh-hant/docs/commerce/cloud-service/migration/migration-tools/bulk-data/migration-tool)會將您的資料移至新的Adobe Commerce as a Cloud Service環境。

* Adobe的[AI輔助移轉和開發人員工具](https://developer.adobe.com/commerce/extensibility/developer-agent/) （包括&#x200B;**[!DNL Adobe Developer App Builder]**&#x200B;和&#x200B;**[!DNL Commerce Storefront powered by Edge Delivery Services]**）可協助加速店面現代化及擴充功能重新平台。

如果您有任何問題，請連絡您的客戶團隊、解決方案客戶經理、續約專家，或聯絡[支援服務](https://experienceleague.adobe.com/zh-hant/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide?lang=en#submit-ticket)。
