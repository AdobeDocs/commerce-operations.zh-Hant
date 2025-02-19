---
title: 程式碼管理最佳作法
description: 瞭解Adobe Commerce專案開發階段的程式碼管理最佳實務。
feature: Best Practices
role: Developer
exl-id: 0bff4c7a-1082-4b3e-b19c-bc8ad529b131
source-git-commit: ee7551374aa6d4ad462dd64ee3d05b934b43ce45
workflow-type: tm+mt
source-wordcount: '659'
ht-degree: 0%

---

# Adobe Commerce的程式碼管理最佳作法

此主題旨在協助您決定是否使用Git或Composer來發佈自訂程式碼，並考量發行管理、程式碼複雜性和相依性管理。

>[!NOTE]
>
>這些最佳實務最適合移轉和實作，但適用於單一模組開發則否。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md)：

- 雲端基礎結構上的Adobe Commerce
- Adobe Commerce內部部署

## 定義

{{$include /help/_includes/gra-definitions.md}}

## 何時使用Git或Composer

<table>
<thead>
  <tr>
    <th></th>
    <th>主要透過Git管理的程式碼</th>
    <th>主要透過撰寫器管理的程式碼</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>何時用於單一執行個體設定</td>
    <td>
      <ul>
        <li><strong>用於管理單一執行個體設定的程式碼的標準方法</strong></li>
        <li>當程式碼庫未來不再屬於多品牌GRA的一部分時</li>
        <li>當所有品牌作為網站在單一執行個體上執行時</li>
      </ul>
    </td>
    <td>
      <ul>
        <li>當程式碼基底未來可以或將成為多執行個體設定的一部分時</li>
      </ul>
    </td>
  </tr>
  <tr>
    <td>何時用於多執行個體設定</td>
    <td>
      <ul>
        <li>當幾乎所有模組都相互連結時（不建議）</li>
        <li>當計畫碼由不熟悉撰寫器的團隊維護時</li>
      </ul>
    </td>
    <td>
      <ul>
        <li><strong>管理多執行個體設定的程式碼的標準方法</strong></li>
        <li>當Adobe維護程式碼庫或維護團隊熟悉撰寫器時</li>
      </ul>
    </td>
  </tr>
</tbody>
</table>

## 功能矩陣

| 功能 | Git | 作曲者 |
|------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------|
| 主要程式碼存放庫 | 所有程式碼都位在單一或數個Git存放庫中 | 所有程式碼都在Composer存放庫中的套件中<br>每個單一Composer套件都由Git存放庫表示 |
| 程式碼位置 | 開發發生在`app/`目錄中 | 開發發生在`vendor/`目錄中 |
| 核心升級管理 | 使用Composer安裝及升級Adobe Commerce核心，結果會在Git中認可 | Adobe Commerce核心已使用Composer安裝和升級；結果會提交到Git中 |
| 協力廠商模組管理 | 協力廠商模組若是透過Marketplace或packagist.org安裝，則會安裝在`vendor/`中。 否則會安裝在`app/`中 | 所有協力廠商模組都安裝在`vendor/`目錄中 |
| 發行版本 | 釋放的特徵為`git merge`和`git pull`或`git checkout`命令 | 釋放的特徵為`composer update`和`git pull`或`git checkout`命令 |
| Git存放庫數量 | 少數 | 許多 |
| 開發複雜性 | 簡單 | 複雜 |
| 提取請求複雜性 | 簡單 | 複雜 |
| 程式碼檢閱複雜性 | 簡單 | 簡單 |
| 開發/QA/UAT環境更新複雜性 | 簡單 | 複雜 |
| GRA支援 | ![是圖示](../../../assets/yes.svg) | ![是圖示](../../../assets/yes.svg) |
| 模組可以自動安裝外部程式庫 | ![沒有圖示](../../../assets/no.svg) | ![是圖示](../../../assets/yes.svg) |
| GRA組合中的彈性 | ![沒有圖示](../../../assets/no.svg) | ![是圖示](../../../assets/yes.svg) |
| 模組相依性管理 | ![是圖示](../../../assets/yes.svg)僅透過`module.xml`，功能有限 | ![是圖示](../../../assets/yes.svg)透過`composer.json`進行完整相依性管理 |
| 模組版本設定 | ![是圖示](../../../assets/yes.svg)您可以定義版本，但無法安裝特定版本 | ![是圖示](../../../assets/yes.svg)完整版本支援 |
| 需要付費服務 | Git存放庫 | Git存放庫、私人封裝商(每年600±元) |
| 可能與Jira整合Bitbucket | ![是圖示](../../../assets/yes.svg) | ![是圖示](../../../assets/yes.svg) |
| 可立即安裝的程式碼變更 | ![是圖示](../../../assets/yes.svg) | ![是圖示](../../../assets/yes.svg) |

## 要避免的解決方案

1. **為您的模組**&#x200B;組合撰寫器和`app/code`

   導致這兩個程式碼管理樣式在您的專案中結合的所有缺點。 這增加了不必要的複雜性、不穩定和缺乏彈性。

   例如：
   - 向開發團隊說明Git和撰寫器工作流程（而非只有一個）。
   - 在`app/code`中安裝不相容的模組，因為沒有可以阻止其發生的專案。
   - 將模組從`app/code`移至Composer （或反之）很麻煩，尤其是在進行中的開發中。

1. **Satis封裝管理員**

   私人包裝商每年±費600歐元。 此成本適用於整個GRA組合，而非個別品牌。 請勿使用免費解決方案Satis來避免這些成本。 每當您推送認可給Git時，Satis都不會自動更新您的套件。 此外，Satis沒有內建授權。 您必須維護網頁伺服器才能執行Satis。 您最後會花費大量的Private Packagist訂閱費用來維護Satis。

1. **從Git開始，然後移至撰寫器**

   在專案開始時選擇程式碼管理方法。 從Git切換到Composer或反之，進行中的開發很麻煩，並可能導致程式碼遺失和修訂記錄遺失。
