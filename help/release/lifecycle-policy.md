---
title: 軟體生命週期策略
description: 了解Adobe Commerce版本軟體支援終止的主要日期。
source-git-commit: ffa8b957828833d2c3f9bc79c31dc3fa2c6035a5
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 5%

---


# Adobe Commerce生命週期政策

若為Adobe Commerce 2.4及後續版本：

- 為了更好地簡化我們的生命週期策略，Adobe為2.4版提供了質量修正，直到其所基於的PHP版本的支援日期結束。 客戶可以聯絡 [Adobe Commerce支援](https://developer.adobe.com/commerce/contributor/community/support/) 或通過自助服務 [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target=&quot;_blank&quot;}，如果其版本仍符合品質支援的資格。 請參閱下表，了解Adobe Commerce發行版本的軟體支援終止日期。

- Adobe僅透過最新修補程式或安全修補程式發行提供安全性修正，即使客戶的版本仍符合品質支援的資格。 與品質修正不同，安全性修正無法移植到先前的次要版本，也無法移植到支援的次要版本中的先前修補版本。

- 針對重大安全問題（例如零天漏洞）,Adobe提供 [hotfix](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) 對於支援版本的所有客戶，即使他們未使用最新補丁程式或安全補丁程式版本。 請務必注意，Hotfix並非全包，並未解決透過升級至最新版本而可修正的所有安全性問題。

## 軟體支援終止

| 發行 | 發行日期 | 軟體支援終止<sup>1</sup> | 相依PHP版本 |
| -------------------------------- | ----------------- | ----------------------------------- | --------------------------- |
| Adobe Commerce 2.3 | 2018年11月28日 | 2022年9月8日<sup>2</sup> | PHP 7.3和7.4<sup>3</sup> |
| Adobe Commerce 2.4.0-2.4.3 | 2020年7月28日 | 2022年11月28日 | PHP 7.4 |
| Adobe Commerce 2.4.4-2.4.6 | 2022年4月12日 | 2024年11月25日 | PHP 8.1 |

<sup>1軟體支援終止包括質量修復終止和安全修復終止。</sup><br>
<sup>2 2.3的軟體支援終止日期已延長至2022年9月8日，讓客戶有更多時間升級至2.4.4版，此版本將於2022年3月8日正式推出。</sup><br>
<sup>3 2.3.0-2.3.6取決於PHP 7.3;2.3.7取決於PHP 7.4。</sup>

>[!NOTE]
>
>請參閱 [軟體生命週期策略](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

<table>
<thead>
  <tr>
    <th colspan="2"></th>
    <th colspan="4">2022年</th>
    <th colspan="4">2023年</th>
    <th colspan="4">2024年</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>商務</td>
    <td>PHP</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>第3季度</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>第3季度</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>第3季度</td>
    <td>Q4</td>
  </tr>
  <tr>
    <td>2.4.0 - 2.4.3</td>
    <td style="text-align:center">7.4</td>
    <td colspan="3" style="background-color:#67ac68;"></td>
    <td style="background-color:#cd3c3c;">11月</td>
    <td colspan="8" ></td>
  </tr>
  <tr>
    <td>2.4.4</td>
    <td rowspan="2" style="text-align:center">8.1</td>
    <td></td>
    <td colspan="10" style="background-color:#67ac68;">3月</td>
    <td rowspan="2" style="background-color:#cd3c3c;">11月</td>
  </tr>
  <tr>
    <td>2.4.5</td>
    <td colspan="2"></td>
    <td colspan="9" style="background-color:#67ac68;">8月</td>
  </tr>
</tbody>
</table>

## 金鑰

<table>
  <thead>
   <tr>
    <th></th>
    <th></th>
   </tr>
  </thead>
 <tbody>
  <tr>
   <td style="background-color:#67ac68;">支援</td>
   <td>已由Adobe完全測試且受支援的版本。</td>
  </tr>
  <tr>
   <td style="background-color:#cd3c3c;">軟體支援終止</td>
   <td>已到軟體支援終止的版本。</td>
  </tr>
 </tbody>
</table>
