---
title: 軟體生命週期原則
description: 了解 Adobe Commerce 版本軟體支援終止的關鍵日期。
exl-id: 9ee4ecc8-d893-412a-a605-5a8606a1b9a9
source-git-commit: 7df5edf2acba706fb01f58cc3749c4a2bf136fc5
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 5%

---


# Adobe Commerce生命週期原則

對於Adobe Commerce 2.4.4和後續版本：

- 為了簡化Adobe Commerce生命週期政策及支援客戶的關鍵任務需求，Adobe將支援期間從Adobe Commerce 2.4.4和更新版本的「一般可用性」(GA)日期延長至三年。 Adobe提供2.4.4及更新版本的品質修正，支援期為三年。 客戶可以聯絡[Adobe Commerce支援](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html)或自助服務[[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)來存取品質修正（若其版本仍符合品質支援資格）。 有關Adobe Commerce發行版本的軟體支援結束日期，請參閱下表。

- Adobe透過安全性修補程式版本，在三年支援期間提供安全性修正。

- 針對關鍵安全性問題，例如零日漏洞，Adobe會為支援版本的所有客戶提供[修補程式](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-)，即使他們不在最新修補程式或安全性修補程式發行版本中。 請務必注意，Hotfix並非包羅萬象，也不會解決升級至最新版本後會修正的所有安全性問題。

- Adobe不針對客戶處於Adobe Commerce的三年支援期期間，而可能到期的第三方服務和軟體相依性（例如PHP和MySQL）提供安全性和品質修正。 請參閱[系統需求](../installation/system-requirements.md)，以取得測試及支援的協力廠商技術的完整清單。

- 在僅限安全性的修補程式發行範圍內，當客戶處於Adobe Commerce的三年支援期時，Adobe可提供與協力廠商服務和軟體相依性的相容性，但前提是客戶可以在不引入回溯不相容變更的情況下這樣做。

## 終止軟體支援

| 版本 | 全面發佈 | 終止軟體支援<sup>1</sup> | 相依PHP版本 | 相依MariaDB版本 |
|----------------------|----------------------|-------------------------------------|-----------------------|------------------------------|
| Adobe Commerce 2.4.7 | 2024年4月9日 | 2027年4月9日 | 8.2和8.3 | 10.6 |
| Adobe Commerce 2.4.6 | 2023年3月14日 | 2026年3月14日 | 8.1和8.2 | 10.6 |
| Adobe Commerce 2.4.5 | 2022年8月9日 | 2025年8月9日 | 8.1 | 10.5<sup>2</sup> |
| Adobe Commerce 2.4.4 | 2022年4月12日 | 2025年4月24日 | 8.1 | 10.5<sup>3</sup> |

{style="table-layout:auto"}

>[!NOTE]
>
>- <sup>1</sup>軟體支援終止包括品質修正終止和安全性修正結束。
>- <sup>2</sup>從2.4.5-p8安全性修補程式開始。
>- <sup>3</sup>從2.4.4-p9安全性修補程式開始。
>- 請參閱[軟體生命週期原則](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)。

<table style="table-layout:auto">
<thead>
  <tr>
    <th colspan="2"></th>
    <th colspan="4">2022</th>
    <th colspan="4">2023</th>
    <th colspan="4">2024</th>
    <th colspan="4">2025</th>
    <th colspan="4">2026</th>
    <th colspan="4">2027</th>
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
  </tr>
  <tr>
    <td>2.4.4</td>
    <td></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2.4.5</td>
    <td colspan="2"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="9"></td>
  </tr>
  <tr>
    <td>2.4.6</td>
    <td colspan="4"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="8"></td>
  </tr>
  <tr>
    <td>2.4.7</td>
    <td colspan="9"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="2"></td>
  </tr>
</tbody>
</table>

**索引鍵**

<table style="table-layout:auto">
 <tbody>
  <tr>
   <td style="background-color:#67ac68;">支援</td>
   <td>Adobe Commerce的安全性與品質修補程式</td>
  </tr>
  <!-- <tr>
   <td style="background-color:#cd3c3c;">End of software support</td>
   <td>Version that has reached end of software support.</td>
  </tr>
 </tbody> -->
</table>
