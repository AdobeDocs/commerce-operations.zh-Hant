---
title: 測試版
description: 了解Adobe Commerce測試版及參與方式。
source-git-commit: 1ce0ff87291c5c3f0fd130aa351bc975f42501e3
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---


# Adobe Commerce測試版

從2023年6月開始至今，Adobe將發行修補程式版本的公開測試版（「測試版」）。 在正式發行(GA)之前，所有Adobe Commerce客戶和合作夥伴都可使用測試版，其中包括安全性、合規性、效能和高優先順序品質修正。

>[!IMPORTANT]
>
>測試版可能包含缺陷，按「原樣」提供，不提供任何類型的保證。 Adobe沒有義務維護、更正、更新、更改、修改或以其他方式支援(通過Adobe支援服務或其他)測試版。 建議客戶小心，不要依賴測試版和/或任何隨附的檔案或資料的正確運作或效能。 因此，任何使用測試版本的風險完全由客戶自行承擔。

## 發行內容

每個Adobe Commerce測試版都包含排程發行日期前傳送至Adobe Commerce核心程式碼的所有變更，其中包含但不限於下列功能領域：

- 最新安全性修正
- 效能改善
- GraphQL改良
- 一般品質錯誤修正
- 社群投稿
- 支援與 [Adobe Commerce服務](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/home.html)

## 命名慣例和排程

Adobe每年發行兩次測試版修補程式。 第一個測試版修補程式通常會在新核心應用程式修補程式正式發行後三個月發行。

測試版發行套件具有 `-betaX` 尾碼。 例如，Adobe Commerce 2.4.7測試版套件會使用下列命名慣例：

- `2.4.7-beta1`
- `2.4.7-beta2`

請參閱 [發行排程](schedule.md) 以取得即將發行的公開測試版日期清單。

## 參與的好處

您越早看到我們正在開發的代碼，您就越早準備好您的技術和商戶，以迎接即將進行的升級。

雖然情況可能有所變更，但與測試版合作可讓您開始了解程式碼基底變更的發生位置，並在GA發行日期前開始準備。

## 測試版發行存取

Adobe Commerce測試版的發佈方式與任何其他Adobe Commerce修補程式版本相同：作為上的撰寫元集 `https://repo.magento.com`. 原始碼可在上使用 [GitHub](https://github.com/magento/magento2).

請參閱 [撰寫器安裝快速入門](../installation/composer.md) 以取得更多詳細資訊。

## 問題報告

Adobe未針對測試版提供標準Adobe支援服務。

若要提交與測試版相關的意見反應，請遵循我們的 [定期問題報告流程](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) on [GitHub](https://github.com/magento/magento2).

我們的內部團隊將監控針對最新測試版所回報的所有重大問題，並排定在正式發行日期前解決的優先順序。
