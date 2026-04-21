---
title: 軟體生命週期原則
description: 了解 Adobe Commerce 版本軟體支援終止的關鍵日期。
exl-id: 9ee4ecc8-d893-412a-a605-5a8606a1b9a9
source-git-commit: 3e7cef954a2be506c6f72e704710d16ed1d9b7a3
workflow-type: tm+mt
source-wordcount: '807'
ht-degree: 2%

---


# Adobe Commerce生命週期原則

為了簡化Adobe Commerce生命週期政策及支援客戶的關鍵任務需求，Adobe從一般可用性(GA)日期開始提供三年支援期間，每個版本在此期間會發佈品質修正。 如需每個版本的軟體支援結束的日期和詳細資訊，請參閱[軟體支援結束](#end-of-software-support)表格。

在三年支援期間，客戶可以存取：

- **品質修正** — 客戶可以連絡[Adobe Commerce支援](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide)或自助服務[[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)來存取品質修正。 下表說明Adobe Commerce發行版本的軟體支援終止日期。

- **安全性修正**-Adobe透過累積安全性修正程式和非累積[隔離安全性修正程式檔案](versioning-policy.md#isolated-security-fixes)，在三年支援期間提供安全性修正。

- **Hotfix** — 針對重大安全性問題，例如零日漏洞，Adobe會為使用支援版本的所有客戶提供[Hotfix](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-)，即使他們未使用最新修補程式或安全性修補程式版本。 請注意，Hotfix並不完整，且無法解決升級至最新版本時可解決的所有安全性問題。

Adobe並未針對客戶處於Adobe Commerce三年或延長支援期間期間，可能到期的第三方服務與軟體相依性（例如PHP與MySQL）提供安全性與品質修正。 請參閱[系統需求](../installation/system-requirements.md)，以取得測試及支援的協力廠商技術的完整清單。

## 延伸支援

Adobe鼓勵客戶儘快升級。 但是，為了提供更大的彈性以符合升級計畫和業務需求，Adobe為Adobe Commerce客戶2.4.6版免費提供一年的支援延長期。支援擴充功能包括核心應用程式的品質與安全性修補程式，有效期最長為一年。 Adobe Commerce 2.4.4和2.4.5版本的延伸支援如期於2026年4月和8月結束。

>[!NOTE]
>
>延長支援僅適用於Adobe Commerce客戶。 它不適用於Magento Open Source程式碼基底。

## 終止軟體支援

| 版本 | 全面發佈 | 結束一般支援<sup>1</sup> | 終止延伸支援 |
|----------------------|----------------------|------------------------------------|-------------------------|
| Adobe Commerce 2.4.8 | 2025年4月8日 | 2028年5月31日 | 待定 |
| Adobe Commerce 2.4.7 | 2024年4月9日 | 2027年5月31日 | 待定 |
| Adobe Commerce 2.4.6 | 2023年3月14日 | 2026年8月11日 | 2027年8月30日 |
| Adobe Commerce 2.4.5 | 2022年8月9日 | 2025年8月12日 | 2026年8月11日 |
| Adobe Commerce 2.4.4 | 2022年4月12日 | 2025年4月12日 | 2026年4月14日 |

{style="table-layout:auto"}

>[!NOTE]
>
>- <sup>1</sup>如果您是Adobe Commerce客戶，在延長的支援期間，可以繼續獲得額外一年的安全性與品質修正。
>- 請參閱[軟體生命週期原則](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)。

## Adobe Commerce 2.4.4和2.4.5布建的其他安全性修正

作為一次性例外情況，Adobe針對Adobe Commerce版本2.4.4和2.4.5提供更長的安全性修正布建期間，讓客戶有更多時間移轉至Adobe Commerce as a Cloud Service或升級至支援的發行系列。

在此安全性修正布建期間，請注意下列事項：

- **僅隔離安全性修補檔** — 將依照發行排程發行這些版本的隔離安全性修補檔。 在此期間不會提供安全性修補程式發行版本（無新的 — p版本）。

  若要套用隔離的安全性修補程式檔案，客戶必須在其支援的發行版本行上使用最新的僅限安全性的修補程式發行版本（最新的 — p版本），因為隔離的安全性修補程式是專門針對該版本進行測試的。

- **在此期間不會針對2.4.4或2.4.5版提供品質修正或工程協助** — 無錯誤修正、品質更新（[品質修補工具](../tools/quality-patches-tool/usage.md)）或工程協助（[Adobe Commerce支援](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide)）。

- **不保證PCI相容性：** — 因為2.4.4和2.4.5使用生命週期已結束的PHP版本，所以無法保證這些發行版本的商戶符合PCI相容性。 繼續執行這些版本可能會使您的PCI相容性面臨風險。

若要維持完整的安全性涵蓋範圍並確保PCI法規遵循，客戶必須儘快升級至目前支援的Adobe Commerce版本，或移轉至[Adobe Commerce as a Cloud Service](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/overview)。

| 版本 | 全面發佈 | 終止延伸支援 | 結束安全性修正布建 |
|----------------------|----------------------|-------------------------|------------------------------------|
| Adobe Commerce 2.4.5 | 2022年8月9日 | 2026年8月11日 | 2027年5月 |
| Adobe Commerce 2.4.4 | 2022年4月12日 | 2026年4月14日 | 2027年5月 |

{style="table-layout:auto"}

>[!NOTE]
>
>其他安全性修正僅適用於Adobe Commerce客戶，不適用於Magento Open Source程式碼基底。


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
    <td colspan="6"></td>
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
   <td>定期支援</td>
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
