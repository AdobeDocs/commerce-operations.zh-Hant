---
title: Adobe Commerce生命週期原則
description: 瞭解Adobe Commerce支援期間、支援終止和雲端執行日期、過渡性規定，以及支援版本的路徑。
exl-id: 9ee4ecc8-d893-412a-a605-5a8606a1b9a9
source-git-commit: 620523021580a9dba44e0e2041d8100761b8bce1
workflow-type: tm+mt
source-wordcount: '1526'
ht-degree: 0%

---


# Adobe Commerce生命週期原則

Adobe Commerce會遵循已定義的軟體生命週期原則，以確保客戶可在安全、支援的版本上執行。 如果您處於較舊的發行路線，瞭解您在此生命週期中的哪個階段以及在執行截止日期前採取行動，至關重要。 此主題涵蓋支援層級定義、支援終止和執行日期、接近生命週期結束的版本的轉換規定，以及支援版本要保留的路徑。

>[!IMPORTANT]
>
>Adobe正推出適用於Adobe Commerce on Cloud (PaaS)的強製版本升級政策。 自&#x200B;**2027年6月1日**&#x200B;起，Adobe將停止維護執行不支援Commerce版本的雲端環境，並保留停用這些版本的權利。 如果您在Cloud (PaaS)上執行，則必須移至支援的Adobe Commerce版本，或移轉至[!DNL Adobe Commerce as a Cloud Service]，才能在您已發佈的發行專案的[延長支援結束](lifecycle-policy.md#end-of-support-dates)日期之前完成。 請參閱[雲端版本升級執行原則](version-upgrade-enforcement-policy.md)，以取得執行日期、受影響的版本，以及您在不支援的版本上所發生的情況。

## 瞭解支援階層

Adobe Commerce為發行版本定義了三個支援層級。 以下各節說明每個階層。

### 定期支援

一般可用性(GA)日期的標準三年支援期間。 定期支援包括品質修正、安全性修補程式，以及完整的Adobe Commerce電話支援。

- **品質修正** — 客戶可以連絡[Adobe Commerce支援](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide)或自助服務[[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)來存取品質修正。

- **安全性修正** - Adobe透過累積安全性修補程式和非累積[隔離安全性修補程式檔案](versioning-policy.md#isolated-security-patch-file)，在三年支援期間提供安全性修正。

- **Hotfix** — 針對嚴重安全性問題（例如零日漏洞），Adobe會為使用支援版本的所有客戶提供[Hotfix](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-)，即使他們未使用最新修補程式或安全性修補程式版本。 請注意，Hotfix並不完整，且無法解決升級至最新版本時可解決的所有安全性問題。

### 延伸支援

除一般支援外，特定發行行還提供一年支援延長服務。 包括品質和安全性修補程式。 僅適用於Adobe Commerce客戶 — 不適用於Magento Open Source。

### 僅限安全性的過渡期

特定版本的延伸支援於2025或2026年結束的一次性有限過渡期。 僅限安全性的過渡期僅提供有限的隔離安全性修正。 不包括Adobe Commerce電話支援。 此期間不等於一般或延長支援，且不會進一步延長。 將其視為移轉期間，而非長期支援層級。 請參閱[僅限安全性轉換規定](#security-only-transitional-provisions)。

## 支援結束日期

下表顯示每個Adobe Commerce版本的完整生命週期，包括雲端環境中的Adobe Commerce (PaaS)新版本升級強制執行日期。

| 版本 | 全面發佈 | 終止定期支援 | 終止延伸支援 | 僅限安全性期間的結尾 | [版本升級強制日期（僅限雲端）](version-upgrade-enforcement-policy.md) |
|---------|----------------------|------------------------|-------------------------|-----------------------------|-----------------------------------------------|
| Adobe Commerce 2.4.9 | 2026年5月12日 | 2029年5月31日 | 待定 | 不適用 | 待定 |
| Adobe Commerce 2.4.8 | 2025年4月8日 | 2028年5月31日 | 待定 | 不適用 | 待定 |
| Adobe Commerce 2.4.7 | 2024年4月9日 | 2027年5月31日 | 2028年5月31日 | 不適用 | 2028年6月1日 |
| Adobe Commerce 2.4.6 | 2023年3月14日 | 2026年8月11日 | 2027年8月30日 | 2028年5月31日 | 2028年6月1日 |
| Adobe Commerce 2.4.5 | 2022年8月9日 | 2025年8月12日 | 2026年8月12日 | 2027年5月31日 | 2027年6月1日 |
| Adobe Commerce 2.4.4 | 2022年4月12日 | 2025年4月12日 | 2026年4月14日 | 2027年5月31日 | 2027年6月1日 |

{style="table-layout:auto"}

如果您的版本行接近或超過這些日期，請參閱[升級和移轉選項](#upgrade-and-migration-options)。 如需雲端強制實行詳細資訊，請參閱[雲端版本升級強制實行原則](version-upgrade-enforcement-policy.md)。

### 按季度支援時間表

使用此圖表可檢視跨發行線重疊的支援視窗。 如需確切的結束日期，請參閱上表。 2.4.8和2.4.9的延伸支援為待定，未顯示。

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
    <th colspan="4">2029</th>
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
    <td colspan="4" style="background-color:#FFBF00;"></td>
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2.4.5</td>
    <td colspan="2"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="3" style="background-color:#FFBF00;"></td>
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2.4.6</td>
    <td colspan="4"></td>
    <td colspan="15" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="3" style="background-color:#FFBF00;"></td>
    <td colspan="6"></td>
  </tr>
  <tr>
    <td>2.4.7</td>
    <td colspan="9"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="6"></td>
  </tr>
  <tr>
    <td>2.4.8</td>
    <td colspan="13"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="6"></td>
  </tr>
  <tr>
    <td>2.4.9</td>
    <td colspan="17"></td>
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
   <td>定期支援</td>
  </tr>
  <tr>
   <td style="background-color:#ffd700;"></td>
   <td>延伸支援</td>
  </tr>
    <tr>
   <td style="background-color:#FFBF00;"> </td>
   <td>僅限安全性的過渡期</td>
  </tr>
 </tbody>
</table>

## 僅限安全性的過渡性規定 {#security-only-transitional-provisions}

Adobe針對2.4.4、2.4.5和2.4.6版提供延伸支援（已於2025年和2026年結束），作為單次測量，提供下列過渡性條文，讓您有更多時間規劃及執行移轉或升級。 這些布建不會取代PaaS環境的[雲端版本升級強制執行](version-upgrade-enforcement-policy.md)。 您仍然必須在發佈的執行日期之前升級或移轉。

| 版本 | 過渡性規定 | 期間 | 包含的內容 | 未包含的內容 |
|---------|------------------------|--------|------------------|----------------------|
| 2.4.4和2.4.5 | 僅限安全性的過渡期 | 至2027年5月31日 | 針對個別案例進行有限的隔離安全性修正 | Adobe Commerce電話支援、品質修正、平台相依性更新 |
| 2.4.6 | 延長支援+僅限安全性的過渡期 | 延長支援至2027年8月30日。 僅限安全性期間至2028年5月31日。 | 延長支援期間：品質和安全修補程式。 僅限安全性期間：有限的隔離安全性修正。 | 僅限安全性期間：Adobe Commerce電話支援、品質修正、平台相依性更新 |

{style="table-layout:auto"}

>[!IMPORTANT]
>
>僅限安全性的過渡期間是一次性例外。 不會超過發佈日期。 將僅限安全性時段視為移轉時間，而非長期支援階層。

## 平台相依性

若要繼續使用支援的Commerce版本，還需要有支援的平台相依性。 對於您處於Adobe Commerce的三年或延長支援期間時可能會終止的第三方服務和軟體相依性（例如PHP、MariaDB、OpenSearch、Redis、Valkey、RabbitMQ等），Adobe不提供安全性和品質修正。

您負責維護主動支援版本上的所有協力廠商相依性和平台服務。 請參閱[系統需求](../installation/system-requirements.md)，以取得測試及支援的協力廠商技術的完整清單。

Adobe不針對執行不支援之相依性版本的部署提供安全性支援或協助。 如需詳細資訊，請參閱[共用職責安全性與運作模型](../security-and-compliance/shared-responsibility.md)。

>[!IMPORTANT]
>
>執行不受支援的相依性版本可能會導致Adobe無法解析的雲端例項出現安全性弱點。 在這種情況下，無論您的Adobe版本支援狀態為何，Adobe Commerce都會保留強制升級受影響的軟體相依性，或在不可能升級時停用服務的權利。

## PHP生命週期結束與PCI法規遵循

您負責監視環境中使用的PHP版本的支援狀態。

舊版Commerce發行版本系列使用的下列PHP版本已到期或即將到期，這對PCI法規遵循有直接影響。

| PHP版本 | 生命週期結束日期 | 受影響的Commerce版本 | PCI法規遵循影響 |
|-------------|------------------|----------------------------|------------------------|
| PHP 8.1 | 2025年12月31日 | 2.4.4、2.4.5和2.4.6 （其中使用PHP 8.1） | PCI法規遵循存在風險 — PHP 8.1的生命週期結束日期已過，這意味著PHP中的安全性弱點可能無法得到修正，導致PCI法規遵循面臨風險。 評估規範遵循狀態並排定升級的優先順序。 |
| PHP 8.2 | 2026年12月31日 | 2.4.6 （其中使用PHP 8.2） | 從2026年底開始，PCI法規遵循面臨風險 — 在2026年底之前規劃升級或遷移，以維持PCI法規遵循。 |

{style="table-layout:auto"}

### PCI法規遵循通知

PCI法規遵循是商家的評估責任。 Adobe強烈建議使用受影響版本的商家諮詢其合格的安全性評估師，並儘快優先使用支援的Commerce版本和支援的PHP版本。 如需PHP支援時間表，請參閱[PHP支援的版本](https://www.php.net/supported-versions.php)和[PHP生命週期結束](https://www.php.net/eol.php)。

## 升級和移轉選項

如果您使用的版本接近或超過支援結束日期，請立即採取行動。 若保留不受支援的版本，您的商店將面臨安全性漏洞、法規遵循問題以及失去支援的風險。 Adobe提供以下路徑來轉換至支援的版本。

### 建議的路徑：移轉至Adobe Commerce as a Cloud Service (ACCS)

[!DNL Adobe Commerce as a Cloud Service]是Adobe的新一代託管商務平台，也是Adobe建議所有Adobe Commerce雲端客戶長期使用的目的地。

- Adobe會自動管理所有基礎架構、修補和升級。
- 您一律使用受支援、符合規範的基礎架構，不會發生生命週期結束的情況。
- 您可以存取Adobe的最新功能：AI支援的銷售、可撰寫的店面架構，以及原生Adobe Experience Cloud整合。
- 您可消除週期性升級週期。

請連絡您的Adobe客戶團隊，以開始移轉評估。 如需產品概述，請參閱[Adobe Commerce as a Cloud Service](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/overview)。

### 替代路徑：在雲端或內部部署版本上升級至支援的Adobe Commerce

如果您無法立即移轉至[!DNL Adobe Commerce as a Cloud Service]，您可以升級至目前支援的最新內部Adobe Commerce或雲端版本。 這會將您移至完全支援的現代化基礎建設棧疊，同時保留您現有的PaaS部署模式。

請注意，此路徑無法免除未來的升級義務。 PaaS的客戶必須繼續升級，因為發行版本線已達版本升級強制執行日期。
