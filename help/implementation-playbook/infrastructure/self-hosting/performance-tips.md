---
title: 自行托管Adobe Commerce效能秘訣
description: 了解自行托管效能秘訣的想法、概念及最佳實務，以供參考。
landing-page-description: 了解自行托管Adobe Commerce時需考慮的效能秘訣概念和事項。
short-description: 了解自行托管Adobe Commerce的策略和效能秘訣概念。
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
source-git-commit: ab099b2a8a353c2462424831cf8100e7e281b1be
workflow-type: tm+mt
source-wordcount: '1304'
ht-degree: 0%

---


# 自行托管Adobe Commerce效能秘訣

使用靈活而強大的電子商務平台並不意味著您必須犧牲效能。 自Adobe Commerce成立以來，核心應用程式已有諸多改善。 在2.5.4版中，Adobe Commerce工程團隊執行了一組測試，以便對應用程式進行基準測試。 測試結果顯示，Adobe Commerce可處理超過2.4億個SKU的大型目錄，API請求時間平均為300毫秒，而每小時的頁面檢視次數和訂購次數則是驚人的，每小時可處理200萬個頁面檢視和208,000個訂單。

查看最新基準結果，前往 [Experience League- Adobe Commerce — 實作行動手冊 — 基準](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/infrastructure/performance/benchmarks.html){target="_blank"}.

若要盡可能讓項目保持最佳狀態，請在專案中新增自訂項目和額外的複雜度時，遵循這些標準。

以下小節涵蓋需要考慮的主題，以及如何最佳化自行托管實作的建議。

## 清漆

清漆是帶快取的HTTP反向代理。 雖然這看起來可能很複雜，但結果是快速回應，可協助確保傳回請求的速度比從來源擷取項目來得快。 若不使用某些版本的清漆，執行Adobe Commerce網站將會導致頁面載入速度變慢，並導致其他關鍵量度。 清漆可能很難自行設定和管理，不過我們在Experience League中確實有這個主題 [配置清漆](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/varnish/config-varnish.html){target="_blank"} 以便更清楚地了解其與Adobe Commerce的用途。 另一種選擇是使用雲端式解決方案。 雖然有很多需要考慮的問題，但是Ampley被選為雲上Adobe Commerce的解決方案。 它是一種基於雲的Ampley版本，它使用了VCL和清漆的許多方面。

很難找到最適合您的應用程式、配置、預算和技術能力的解決方案。 使用基於雲的選項，只要考慮管理、配置、伺服器和其他基礎架構元件，所有硬體部件都會消失。 由於效能、延展性、吞吐量以及許多其他關鍵指標，雲端團隊的Adobe Commerce將其選為解決方案。

通過為您的項目選擇關於清漆的良好解決方案，您可以為客戶設定最佳效能，並避免商務應用程式比必須更努力地工作。

## CDN

除了清漆是您Adobe Commerce專案的寶貴資產外，接下來還有CDN。 除了清漆外，CDN還可為CSS、頁面資產（例如影像）提供快取的例項，以協助減少傳至Adobe Commerce應用程式的頻寬。 它可快取GraphQL回應，進一步發揮無頭式Adobe Commerce網站的優點。 有些CDN提供影像最佳化、Web應用程式防火牆和其他功能。

Adobe Commerce on cloud選擇將Abmet用於其清漆快取，也用作其CDN。 此單一解決方案提供多種功能，可為雲端客戶提供絕佳的Adobe Commerce體驗。 您可以閱讀「Ambey服務」概述的Experience League [快速服務概述](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html){target="_blank"}

CDN為Adobe Commerce專案提供最佳化且安全的傳遞內容。 如果這可能不是專案的必要元件，當網站成熟且訪客數量增加時，應將其視為必要元件。 提供CDN後，您就會因為從每個請求移除的負載，而延遲將其他硬體新增至基礎架構，或調整現有基礎架構的規模。

## 禁用模組

應考慮停用未使用的模組，但不應輕視。 此技術確實會減少某些請求的額外負荷和處理時間，但有些副作用應予考慮。 開發人員在建立功能時，經常會假設模組可供使用。 這通常是安全的，除非他們選擇使用在已禁用的模組中找到的某些類。

停用模組（例如原生「電子報」）是相當常見的事件。 當商店擁有者有第三方公司管理其電子報時，尤其如此。 這可能是安裝協力廠商模組時，且出於某些原因，他們決定使用電子報中的類別。 在某些初始安裝和測試期間，可能會捕獲到此意外相依性，但之後您將被迫決定是否要保留此協力廠商模組、啟用電子報，然後回歸測試網站，以尋找所引入的任何奇怪行為。 還是找到該協力廠商模組的替代項目？ 這兩項決定都伴有風險、時間，可能還有錯誤。

在禁用未使用的模組之前，請確保您沒有任何測試，如設備、 [MFTF](https://developer.adobe.com/commerce/cloud-tools/docker/test/application-testing/){target="_blank"}, [Codeception testing](https://developer.adobe.com/commerce/cloud-tools/docker/test/code-testing/){targe="_blank"} 載入測試或可能受影響的API要求。

## 要求每次提取請求都遵循Adobe Commerce和PHP編碼標準

Adobe Commerce [編碼標準](https://developer.adobe.com/commerce/php/coding-standards/){target="_blank"}. 這些有助於確保無論軟體開發類型如何，都能遵循類似的模式、樣式和預期設計。 協助撰寫Adobe Commerce程式碼基底時，此為必要條件。 不過，如果您選擇遵循此自訂開發方法，可為所有開發人員（包括目前和未來）奠定堅實的基礎。 若要求所有提取請求都傳遞程式碼標準，有助於確保每個人都能了解並期待相同的一致開發模式。

為配合Adobe Commerce編碼標準，採用的另一個基礎是PHP基本編碼標準。 開發人員指南中應清楚定義您必須遵循哪些標準，以及任何可接受的偏差。 不過，回復應該是公開維護的指南，請參閱 [PHP-FIG](https://www.php-fig.org){target="_blank"}.

對PSR-1和PSR-12的堅定立場。 確保為項目做出貢獻的開發人員遵循這些規則，有助於確保不存在結構怪異的檔案和模式。 這也有助於確保未來的開發人員快速閱讀及了解所檢閱的程式碼。 您越接近這些模式和編碼標準，就意味著未來開發工作應該更容易閱讀，實施速度也更快。

## 在每個部署後運行負載測試

在每個部署後執行負載測試可能看起來過多。 但是，如果遵循此方法，則可追蹤並緩解新引入功能導致效能下降的機會。

除了檢測新代碼的效能下降外，從您的網站參考關鍵量度的歷史資料有助於深入了解新工具或變更基礎架構的啟用時間。 例如，在向托管公司付款以增加您的環境規模並希望您獲得預期的效能提升之前，您可以使用新的設定來設定預備環境，並執行負載測試以查看實際結果。

這些測試可以自動執行，且屬於您的CI/CD管道。 因此，您也可以制定規則，以取得結果，並且如果發生過多偏離基準的情況，可能會阻止特徵合併。 此資料的使用案例數量無限，但若不啟動此程式，您可能永遠無法發揮其潛力。

Adobe Commerce對此主題的註解良好，請參閱Experience League [效能測試提示](https://experienceleague.adobe.com/docs/commerce-operations/deliver-commerce-at-scale/launch.html){target="_blank"} and in [Testing guidance](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/guidance.html){target="_blank"}.

{{$include /help/_includes/hosting-related-links.md}}
