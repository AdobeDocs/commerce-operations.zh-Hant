---
title: Beta版本
description: 瞭解Adobe Commerce測試版以及如何參與。
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# Adobe Commerce測試版

從2023年6月開始，Adobe將持續發行修補程式版本的公開Beta （以下稱「Beta版本」）。 正式發行前(GA)的所有Adobe Commerce客戶和合作夥伴皆可取得Beta版，內容包括安全性、法規遵循、效能，以及高優先順序的品質修正。

>[!IMPORTANT]
>
>Beta版可能包含瑕疵，並依「原狀」提供，不含任何保固。 Adobe沒有義務維護、更正、更新、變更、修改或以其他方式支援(透過Adobe支援服務或其他方式)Beta版。 建議客戶謹慎使用，切勿依賴測試版和/或任何隨附檔案或資料的正確運作或效能。 因此，使用測試版完全由客戶自行承擔風險。

## 發行內容

每個Adobe Commerce測試版包含排程發行日期前提供給Adobe Commerce核心程式碼的所有變更，包括但不限於下列功能區域：

- 最新的安全性修正
- 效能改良
- GraphQL改良功能
- 一般品質錯誤修正
- 社群貢獻
- 支援與的相容性所需的變更 [Adobe Commerce服務](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/home.html)

## 命名慣例和排程

Adobe將每年發佈兩次測試版修補程式。 第一個Beta版修補程式通常會在新核心應用程式修補程式正式發行三個月後發行。

測試版套件具有 `-betaX` 尾碼。 例如，Adobe Commerce 2.4.7 Beta版套件會使用以下命名慣例：

- `2.4.7-beta1`
- `2.4.7-beta2`

請參閱 [發行排程](schedule.md) 以取得即將推出的公開測試版發行日期清單。

## 參與的優點

越早看到我們正在開發的程式碼，您就能越早準備好您的技術和商家來因應即將到來的升級。

雖然情況可能改變，但與Beta版互動可讓您開始瞭解程式碼基底變更的發生位置，並開始在GA發行日期之前進行準備。

## Beta版存取權

Adobe Commerce Beta版的發佈方式與任何其他Adobe Commerce修補程式版本相同： `https://repo.magento.com`. 原始程式碼位於 [GitHub](https://github.com/magento/magento2).

另請參閱 [撰寫器安裝快速入門](../installation/composer.md) 以取得更多詳細資料。

## 問題報告

Adobe不提供Beta版的標準Adobe支援服務。

若要提交與測試版相關的意見回饋，請遵循我們的 [一般問題報告流程](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) 於 [GitHub](https://github.com/magento/magento2).

我們的內部團隊將監控針對最新測試版報告的所有嚴重問題，並排定在GA發行日期之前要解決的優先順序。
