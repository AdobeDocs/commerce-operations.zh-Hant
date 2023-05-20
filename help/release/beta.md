---
title: Beta版本
description: 瞭解Adobe CommerceBeta版本及如何參與。
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# Adobe Commerceβ釋放

從2023年6月開始，今後，Adobe將發佈修補程式版本（「beta版本」）的公開貝塔。 Beta版本在正式上市(GA)之前可供所有Adobe Commerce客戶和合作夥伴使用，包括安全性、合規性、效能和高優先順序質量修復。

>[!IMPORTANT]
>
>Beta版本可能包含缺陷，並提供「原樣」，不提供任何保證。 Adobe將沒有義務維護、更正、更新、更改、修改或以其他方式支援(通過Adobe支援服務或其他方式)測試版。 建議客戶謹慎，不要以任何方式依賴測試版和/或任何隨附文檔或資料的正確功能或效能。 因此，任何使用測試版都完全有客戶的風險。

## 發佈內容

每個Adobe Commerce測試版都包括在預定發佈日期之前交付給Adobe Commerce核心代碼的所有更改，包括但不限於以下功能領域：

- 最新安全修復
- 效能改進
- GraphQL改進
- 常規質量錯誤修復
- 社區捐款
- 支援與 [Adobe Commerce服務](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/home.html)

## 命名約定和計畫

Adobe將每年發佈兩次Beta修補程式。 第一個測試版修補程式通常在新核心應用程式修補程式發佈後三個月發佈。

Beta版軟體包 `-betaX` 尾碼。 例如，Adobe Commerce2.4.7測試版軟體包使用以下命名約定：

- `2.4.7-beta1`
- `2.4.7-beta2`

查看 [發佈計畫](schedule.md) 即將發佈的公開測試版日期清單。

## 參與的好處

您越早看到我們正在開發的代碼，您就越能為即將進行的升級做好準備。

儘管情況可能會改變，但使用Beta版本將使您能夠開始瞭解在代碼庫更改發生的位置，並在GA發佈日期之前開始準備。

## Beta版本訪問

Adobe Commerce的beta版本與任何其他Adobe Commerce修補程式版本的分發方式相同：作為作曲家的隱喻 `https://repo.magento.com`。 原始碼可在 [GitHub](https://github.com/magento/magento2)。

請參閱 [作曲家安裝快速入門](../installation/composer.md) 的子菜單。

## 問題報告

Adobe未提供標準的測試版Adobe支援服務。

要提交與測試版相關的反饋，請遵循我們的 [定期發佈報告流程](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) 上 [GitHub](https://github.com/magento/magento2)。

我們的內部團隊將監控根據最新測試版報告的所有關鍵問題，並確定在正式發佈日期之前要解決的問題的優先順序。
