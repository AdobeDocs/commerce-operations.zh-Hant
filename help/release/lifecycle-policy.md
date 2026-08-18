---
title: 軟體生命週期原則
description: 了解 Adobe Commerce 版本軟體支援終止的關鍵日期。
exl-id: 9ee4ecc8-d893-412a-a605-5a8606a1b9a9
nudge: true
last-update: 2026-08-17T00:00:00Z
source-git-commit: 7ba189685721799de047bc8d0e7108fa512f7120
workflow-type: tm+mt
source-wordcount: '1350'
ht-degree: 1%

---


# Adobe Commerce生命週期原則

為了簡化Adobe Commerce生命週期政策及支援客戶的關鍵任務需求，Adobe提供三年標準支援期間，從一般可用性(GA)日期開始算起，針對每個版本並在該期間發佈品質修正。 如需每個版本的軟體支援結束的日期和詳細資訊，請參閱[支援結束日期](#end-of-support-dates)表格。

Adobe並未針對客戶處於Adobe Commerce三年或延長支援期間期間，可能到期的第三方服務與軟體相依性（例如PHP與MySQL）提供安全性與品質修正。 請參閱[系統需求](../installation/system-requirements.md)，以取得測試及支援的協力廠商技術的完整清單。

## 標準支援

一般可用性(GA)日期的標準三年支援期間。 標準支援包括品質修正、安全性修補程式，以及完整的Adobe Commerce電話支援。

- **品質修正** — 客戶可以連絡[Adobe Commerce支援](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide)或自助服務[[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)來存取品質修正。

- **安全性修正** - Adobe透過累積安全性修補程式和非累積[隔離安全性修補程式檔案](versioning-policy.md#isolated-security-patch-file)，在三年支援期間提供安全性修正。

- **Hotfix** — 針對嚴重安全性問題（例如零日漏洞），Adobe會為使用支援版本的所有客戶提供[Hotfix](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-)，即使他們未使用最新修補程式或安全性修補程式版本。 請注意，Hotfix並不完整，且無法解決升級至最新版本時可解決的所有安全性問題。

## 延伸支援

Adobe鼓勵客戶儘快升級。 但是，為了提供更大的彈性以符合升級計畫和業務需求，Adobe針對2.4.6和2.4.7版為Adobe Commerce客戶提供一年的額外支援，而不需額外付費。 支援擴充功能包含核心應用程式的品質和安全性修補程式。 Adobe Commerce 2.4.4和2.4.5版本的延伸支援如期於2026年4月和8月結束。

>[!NOTE]
>
>Adobe正推出適用於Adobe Commerce on Cloud的強製版本升級政策，協助每位客戶維持在安全、支援的平台上。 自&#x200B;**2027年6月1日**&#x200B;起，Adobe將不再維護執行不支援Commerce版本的雲端環境，並將強制採取適當的動作來保證Adobe Commerce平台及其客戶的安全性。 這包括暫停流向受影響基礎結構的流量。 因此，您的電子商務店面將會離線。 如果您在Cloud上執行，則必須移至支援的Adobe Commerce版本，或在您發行版本的已發佈[終止延伸支援](lifecycle-policy.md#end-of-support-dates)日期之前移轉至[!DNL Adobe Commerce as a Cloud Service]。 如果您使用2.4.4版到2.4.9版，請參閱[安全性與合規性通知](security-enforcement-policy.md)，以瞭解適用於您環境的特定動作和截止日期。

## 僅限安全性的過渡期

僅限於2.4.4、2.4.5和2.4.6版（其延伸支援將於2025或2026年結束）的一次性有限過渡期。 僅限安全性的過渡期僅提供有限的隔離安全性修正（無品質修正）。

>[!IMPORTANT]
>
>僅限安全性的過渡期間是一次性例外。 不會超過發佈日期。 將僅限安全性時段視為移轉時間，而非長期支援階層。 如果您想協助建立移轉計畫，請聯絡您的客戶團隊。

## 支援結束日期

下表顯示每個Adobe Commerce版本的完整生命週期，包括雲端環境上Adobe Commerce的新版本升級執行日期。

{{$include /help/_includes/templated/release/end-of-support-dates.md}}

## 支援時間表

支援時間表會對應每個Adobe Commerce發行版本的每季支援期間。 使用本主題前面提供的表格來取得確切的結束日期。

<table style="table-layout:auto">
<thead>
  <tr>
    <th colspan="1"></th>
    <th colspan="4">2022</th>
    <th colspan="4">2023</th>
    <th colspan="4">2024</th>
    <th colspan="4">2025</th>
    <th colspan="4">2026</th>
    <th colspan="4">2027</th>
    <th colspan="4">2028</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Commerce</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
  </tr>
  <tr>
    <td>2.4.4</td>
    <td></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="5" style="background-color:#FFBF00"></td>
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2.4.5</td>
    <td colspan="2"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="4" style="background-color:#FFBF00"></td>
    <td colspan="9"></td>
  </tr>
  <tr>
    <td>2.4.6</td>
    <td colspan="4"></td>
    <td colspan="15" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2.4.7</td>
    <td colspan="9"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="2"></td>
  </tr>
  <tr>
    <td>2.4.8</td>
    <td colspan="13"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="2"></td>
  </tr>
</tbody>
</table>

**索引鍵**

<table style="table-layout:auto">
 <tbody>
  <tr>
   <td style="background-color:#67ac68;"></td>
   <td>標準支援</td>
  </tr>
  <tr>
   <td style="background-color:#ffd700;"></td>
   <td>延伸支援</td>
  </tr>
    <tr>
   <td style="background-color:#FFBF00;"> </td>
   <td>延伸安全性修正</td>
  </tr>
 </tbody>
</table>

## 平台相依性

若要繼續使用支援的Commerce版本，還需要有支援的平台相依性。 Adobe不針對您可能在Adobe Commerce三年或延長支援期期間終止的第三方服務和軟體相依性（例如MariaDB、OpenSearch、Redis、Valkey、RabbitMQ等）提供安全性和品質修正。 如需詳細資訊，請參閱[共用職責安全性與運作模型](../security-and-compliance/shared-responsibility.md)。

您負責維護主動支援版本上的所有協力廠商相依性和平台服務。 請參閱[系統需求](../installation/system-requirements.md)，以取得測試及支援的協力廠商技術的完整清單。

>[!IMPORTANT]
>
>執行不受支援的相依性版本可能會導致Adobe無法解析的雲端例項出現安全性弱點。 在這種情況下，Adobe將被迫採取適當的行動來維護Adobe Commerce平台及其客戶的安全。 這包括暫停流向受影響基礎結構的流量。 因此，您的電子商務店面將會離線。
>
>如果環境在流量暫停後繼續不相容，Adobe可以終止雲端服務，啟動解除委任程式。 退役後，託管電子商務環境中的所有資料和資產（包括所有例項、環境和分支）將會永久刪除且無法還原。 請參閱[保護Commerce環境所需的動作和截止日期](security-enforcement-policy.md)，以瞭解這些升級的排程方式以及在整個過程中可供您使用的支援。

## PHP生命週期結束與PCI法規遵循

您負責監視環境中使用的PHP版本的支援狀態。

舊版Commerce發行版本系列使用的下列PHP版本已到期或即將到期，這對PCI法規遵循有直接影響。

| PHP版本 | 生命週期結束日期 | 受影響的Commerce版本 | PCI法規遵循影響 |
| ------------- | ------------------ | ---------------------------- | ------------------------ |
| PHP 8.1 | 2025年12月31日 | 2.4.4、2.4.5和2.4.6 （其中使用PHP 8.1） | PCI法規遵循存在風險 — PHP 8.1的生命週期結束日期已過，這意味著PHP中的安全性弱點可能無法得到修正，導致PCI法規遵循面臨風險。 評估規範遵循狀態並排定升級的優先順序。 |
| PHP 8.2 | 2026年12月31日 | 2.4.6 （其中使用PHP 8.2） | 從2026年底開始，PCI法規遵循面臨風險 — 在2026年底之前規劃升級或遷移，以維持PCI法規遵循。 |

{style="table-layout:auto"}

>[!IMPORTANT]
>
>**PCI法規遵循通知：** PCI法規遵循是商家的評估責任。 Adobe強烈建議使用受影響版本的商家諮詢其合格的安全性評估師，並儘快優先使用支援的Commerce版本和支援的PHP版本。 如需PHP支援時間表，請參閱[PHP支援的版本](https://www.php.net/supported-versions.php)和[PHP生命週期結束](https://www.php.net/eol.php)。

## 升級和移轉選項

如果您使用的版本接近或超過支援結束日期，請立即採取行動。 若保留不受支援的版本，您的商店將面臨安全性漏洞、法規遵循問題以及失去支援的風險。 Adobe提供以下路徑來轉換至支援的版本。

### 建議的路徑：移轉至Adobe Commerce as a Cloud Service

[!DNL Adobe Commerce as a Cloud Service]是Adobe的新一代託管商務平台，也是Adobe建議所有Adobe Commerce雲端客戶長期使用的目的地。

- Adobe會自動管理所有基礎架構、修補和升級。
- 您一律使用受支援、符合規範的基礎架構，不會發生生命週期結束的情況。
- 您可以存取Adobe的最新功能：AI支援的銷售、可撰寫的店面架構，以及原生Adobe Experience Cloud整合。
- 您可消除週期性升級週期。

請連絡您的Adobe客戶團隊，以開始移轉評估。 如需產品概述，請參閱[Adobe Commerce as a Cloud Service](https://experienceleague.adobe.com/zh-hant/docs/commerce/cloud-service/overview)。

### 替代路徑：在雲端或內部部署版本上升級至支援的Adobe Commerce

如果您無法立即移轉至[!DNL Adobe Commerce as a Cloud Service]，可以在雲端版本上升級至目前支援的最新Adobe Commerce。 這會將您移至完全支援的現代化基礎架構棧疊，同時保留雲端部署模式上的現有Commerce。

請注意，此路徑無法免除未來的升級義務。 在雲端部署上使用Adobe Commerce的客戶必須在發行行達到其版本升級強制執行日期時繼續升級。
