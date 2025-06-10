---
title: 軟體生命週期原則
description: 了解 Adobe Commerce 版本軟體支援終止的關鍵日期。
exl-id: 9ee4ecc8-d893-412a-a605-5a8606a1b9a9
source-git-commit: 5a45f2b0ad2485014abd3b807a5797f9fc82388b
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 3%

---


# Adobe Commerce生命週期原則

對於Adobe Commerce 2.4.4和後續版本：

- 為了簡化Adobe Commerce生命週期政策及支援客戶的關鍵任務需求，Adobe將支援期間從Adobe Commerce 2.4.4和更新版本的「一般可用性」(GA)日期延長至三年。 Adobe提供2.4.4及更新版本的品質修正，支援期為三年。 客戶可以聯絡[Adobe Commerce支援](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide)或自助服務[[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)來存取品質修正（若其版本仍符合品質支援資格）。 下表說明Adobe Commerce發行版本的軟體支援終止日期。

- Adobe透過安全性修補程式版本，在三年支援期間提供安全性修正。

- 針對關鍵安全性問題，例如零日漏洞，Adobe會為使用支援版本的所有客戶提供[修補程式](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-)，即使他們未使用最新修補程式或安全性修補程式版本。 請注意，Hotfix並不完整，且無法解決升級至最新版本時可解決的所有安全性問題。

- Adobe並未針對客戶處於Adobe Commerce的三年支援期期間，而可能到期的協力廠商服務和軟體相依性（例如PHP和MySQL）提供安全性和品質修正。 請參閱[系統需求](../installation/system-requirements.md)，以取得測試及支援的協力廠商技術的完整清單。

- 對於使用版本2.4.4和2.4.5的雲端上的Adobe Commerce客戶，Adobe會自動將PHP 8.1期限安全性修正套用至基礎結構，因此這些客戶不會受到PHP 8.1支援終止的影響。 若內部部署客戶使用Adobe Commerce 2.4.4和2.4.5，則必須聯絡Adobe支援，要求PHP 8.1期限安全性修補程式（如有需要）。

- Adobe提供與第三方服務和軟體相依性的相容性，而客戶在僅限安全性的修補程式發行範圍內享有Adobe Commerce的三年支援期，但前提是客戶可以在不引進回溯不相容變更的情況下提供支援。

## 延伸支援

Adobe鼓勵客戶儘快升級。 不過，為了提供更大的彈性以符合升級計畫和業務需求，Adobe針對2.4.4和2.4.5版免費為Adobe Commerce客戶提供一年期的支援延長服務。支援擴充功能包括核心應用程式的品質與安全性修補程式，有效期最長為一年。

>[!NOTE]
>
>延長支援僅適用於Adobe Commerce客戶。 它不適用於Magento Open Source程式碼基底。

## 終止軟體支援

| 版本 | 全面發佈 | 結束一般支援<sup>1</sup> | 終止延伸支援 | 相依PHP版本 | 相依MariaDB版本 |
|----------------------|----------------------|------------------------------------|-------------------------|-----------------------|---------------------------|
| Adobe Commerce 2.4.8 | 2025年4月8日 | 2028年4月11日 | 不適用 | 8.3和8.4 | 11.4 |
| Adobe Commerce 2.4.7 | 2024年4月9日 | 2027年4月9日 | 不適用 | 8.2和8.3 | 10.11<sup>3</sup> |
| Adobe Commerce 2.4.6 | 2023年3月14日 | 2026年8月11日<sup>2</sup> | 不適用 | 8.1和8.2 | 10.11<sup>4</sup> |
| Adobe Commerce 2.4.5 | 2022年8月9日 | 2025年8月9日 | 2026年8月11日 | 8.1 | 10.6<sup>5</sup> |
| Adobe Commerce 2.4.4 | 2022年4月12日 | 2025年4月12日 | 2026年4月14日 | 8.1 | 10.6<sup>6</sup> |

{style="table-layout:auto"}

>[!NOTE]
>
>- <sup>1</sup>軟體支援終止包括品質修正終止和安全性修正結束。
>- <sup>2</sup>已更新以符合2.4.5的延伸支援結尾。
>- <sup>3</sup>從2.4.7-p6安全性修補程式開始。
>- <sup>4</sup>從2.4.6-p11安全性修補程式開始。
>- <sup>5</sup>從2.4.5-p11安全性修補程式開始。
>- <sup>6</sup>從2.4.4-p12安全性修補程式開始。
>- 請參閱[軟體生命週期原則](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)。

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
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2.4.5</td>
    <td colspan="2"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="9"></td>
  </tr>
  <tr>
    <td>2.4.6</td>
    <td colspan="4"></td>
    <td colspan="15" style="background-color:#67ac68;"></td>
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
 </tbody>
</table>
