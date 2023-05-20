---
title: 自主托管Adobe Commerce效能提示
description: 瞭解自主承載效能提示思想、概念和要考慮的最佳做法。
landing-page-description: 瞭解一些在您自己主持Adobe Commerce時需要考慮的效能提示概念和內容。
short-description: 瞭解自己主持Adobe Commerce的策略和效能提示概念。
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: 95ff0c79-21d0-4514-991c-d88f616db68f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1304'
ht-degree: 0%

---

# 自主托管Adobe Commerce效能提示

使用靈活而強大的電子商務平台並不意味著您必須犧牲效能。 自Adobe Commerce成立以來，核心應用程式已有許多改進。 在2.5.4版中，Adobe Commerce工程團隊執行了一個集test來對應用程式進行基準測試。 test結果表明，Adobe Commerce能夠處理超過2.4億個SKU的大目錄，API請求時間超常，平均為300毫秒，而每小時的頁面瀏覽量和訂單數量以200萬頁和208,000條/小時的速度驚人。

通過標題到 [Experience League-Adobe Commerce — 實施行動手冊 — 基準](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/infrastructure/performance/benchmarks.html){target="_blank"}。

要盡可能保持最佳狀態，請在項目中添加自定義項和附加複雜性時遵循這些標準。

以下各節介紹了要考慮的主題，以及有關如何優化自主托管實施的建議。

## 清漆

清漆是帶快取的HTTP反向代理。 儘管這看起來很複雜，但結果是快速響應，以幫助確保返回請求的速度快於從源中提取項目的速度。 如果運行Adobe Commerce站點而不使用某個版本的清漆，則會導致頁面載入速度減慢和其他關鍵度量。 清漆可能很難設定和管理自己，但我們在Experience League中確實有這個主題 [配置清漆](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/varnish/config-varnish.html){target="_blank"} 以便更好地理解它和Adobe Commerce的用途。 另一種選擇是使用基於雲的解決方案。 儘管有很多需要考慮的問題，但是Appisty被選為雲上Adobe Commerce的解決方案。 它是基於雲的Rebisty的一個版本，它使用VCLs和很多清漆面。

很難找到最適合您的應用程式、配置、預算和技術能力的解決方案。 使用基於雲的選項，所有硬體部件都會消失，只要考慮管理、配置、伺服器和其他基礎架構元件。 由於其效能、可擴充性、吞吐量以及許多其他關鍵指標，Adobe Commerce雲團隊選擇它作為其解決方案。

通過為您的項目選擇關於清漆的好解決方案，您可以為客戶創造最佳效能，並避免商業應用程式比必須的工作更加努力。

## CDN

除清漆外，清漆還是您的Adobe Commerce項目的寶貴資產，接下來是CDN。 除了清漆，CDN還可以為您的CSS提供快取實例、頁面資產（如影像），以幫助減少傳入您的Adobe Commerce應用程式的頻寬。 它可以快取GraphQL的回應，進一步推進無頭Adobe Commerce網站的好處。 一些CDN提供了映像優化、Web應用程式防火牆等功能。

Adobe Commerce在雲端選擇使用Abriest作為其清漆快取，也作為其CDN。 此單一解決方案提供多種功能，為Adobe Commerce雲客戶提供絕佳體驗。 您可以在Experience League中閱讀Axpeistservices概述 [Affeist服務概述](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html){target="_blank"}

CDN為Adobe Commerce項目提供優化和安全的交付內容。 如果這可能不是您項目的必需元件，則應當視為您的站點成熟，訪問者數量增加。 通過提供CDN，您可以延遲向基礎架構添加附加硬體或擴展現有基礎架構，因為從每個請求中卸除了負載。

## 禁用模組

應考慮禁用未使用的模組，但不應輕視。 這種技術確實減少了一些請求的開銷和處理時間，但也有一些副作用需要考慮。 有時，開發人員在建立功能時假定模組可用。 這通常是安全的，除非他們選擇使用在已禁用的模組中找到的某些類。

禁用模組（如本機「新聞簡訊」）是相當常見的事件。 尤其是當店主擁有第三方公司來管理其新聞稿時，情況就更是如此。 這可能是一個問題，即安裝第三方模組時，出於某種原因，他們決定使用新聞簡報中的類。 在初始安裝和測試時，可能會發現此意外依賴關係，但是您必須決定是否要保留此第三方模組，啟用新聞簡報，然後回歸test站點，以查找引入的任何奇特行為。 或者，您是否找到了第三方模組的替代產品。 這兩個決定都伴隨著風險、時間，可能還有錯誤。

在禁用未使用的模組之前，請確保沒有任何test，如設備， [MFTF](https://developer.adobe.com/commerce/cloud-tools/docker/test/application-testing/){target="_blank"}, [Codeception testing](https://developer.adobe.com/commerce/cloud-tools/docker/test/code-testing/){targe="_blank"} 載入test或可能受影響的API請求。

## 要求每個拉入請求都遵循Adobe Commerce和PHP編碼標準

Adobe Commerce [編碼標準](https://developer.adobe.com/commerce/php/coding-standards/){target="_blank"}。 這些幫助確保無論軟體開發類型如何，都遵循類似的模式、樣式和預期設計。 在為Adobe Commerce基礎庫作貢獻時，這是一個要求。 但是，如果您選擇採用此方法進行自定義開發，則將為所有開發人員奠定堅實的基礎，無論是當前還是未來。 當要求所有拉取請求都通過代碼標準時，有助於確保每個人都能理解並期望得到相同的一致開發模式。

為配合Adobe Commerce編碼標準，採用的另一個基礎是PHP基本編碼標準。 應在開發人員指南中明確定義它，以指導您需要遵循哪些標準以及任何可接受的偏差。 但是，應回退到以下位置的公開維護指南 [PHP-FIG](https://www.php-fig.org){target="_blank"}。

對遵守PSR-1和PSR-12的立場是堅定的。 確保為項目作出貢獻的開發人員遵守這些規則有助於確保不存在結構異常的檔案和模式。 這還有助於確保未來的開發人員能夠快速閱讀和理解他們正在審閱的代碼。 遵循這些模式和編碼標準越近，意味著未來的開發工作應該更容易被閱讀，執行得也更快。

## 在每個部署後運行負載test

在每次部署後執行載入test可能過多。 但是，如果遵循此方法，則可以跟蹤並減少新引入的導致效能下降的功能的機會。

除了檢測新代碼導致的效能降級外，從站點中參考關鍵指標還有助於深入瞭解何時啟用新工具或更改基礎架構。 例如，在向托管公司支付費用以調整您的環境規模並希望您獲得預期的效能提升之前，您可以設定具有新配置的登台環境並運行載入test，以查看實際結果。

這些test可以自動化，並且是CI/CD管道的一部分。 因此，您還可以設定規則來獲取結果，如果與范數的偏離過多，則可能會阻止特徵的合併。 此資料的使用案例數量是無限的，但如果不啟動此過程，您可能永遠無法實現其潛力。

Adobe Commerce在Experience League中對此主題有很好的寫作 [效能測試提示](https://experienceleague.adobe.com/docs/commerce-operations/deliver-commerce-at-scale/launch.html){target="_blank"} and in [Testing guidance](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/guidance.html){target="_blank"}。

{{$include /help/_includes/hosting-related-links.md}}
