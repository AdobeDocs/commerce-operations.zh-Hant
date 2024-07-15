---
title: 自行託管Adobe Commerce效能秘訣
description: 瞭解自行託管效能秘訣概念以及要考慮的最佳實務。
landing-page-description: 瞭解自行託管Adobe Commerce時的一些效能秘訣概念和考量事項。
short-description: 瞭解自行託管Adobe Commerce的策略和效能提示概念。
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: bfce5c35-66c3-4d5c-a7b0-58f6d54febf8
feature: Install
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '1271'
ht-degree: 0%

---

# 自行託管Adobe Commerce效能秘訣

使用彈性且功能強大的電子商務平台，並不表示您不得不犧牲效能。 自Adobe Commerce創立以來，核心應用程式已獲得許多改良。 在2.5.4版中，Adobe Commerce工程團隊執行了設定測試，以評估應用程式的基準。 測試結果證明Adobe Commerce有能力處理超過2.4億個SKU的大型目錄，API請求時間平均為300毫秒異常，且每小時的頁面檢視次數和訂單數非常驚人，達到200萬次頁面檢視和208,000次訂單/小時。

若要檢視最新的效能標竿結果，請前往[Experience League- Adobe Commerce — 實作行動手冊 — 效能標竿](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/infrastructure/performance/benchmarks.html){target="_blank"}。

若要讓一切儘可能保持最佳狀態，請在為專案新增自訂專案和其他複雜性時，遵循這些標準。

以下小節涵蓋如何最佳化自行託管實作時應考量的主題和建議。

## 亮漆

清漆是含有快取的HTTP反向Proxy。 雖然看起來很複雜，但結果會產生快速的回應，以確保傳回請求的速度比從來源擷取專案的速度更快。 在沒有某些版本Varnish的情況下執行Adobe Commerce網站將會導致頁面載入和其他關鍵量度變慢。 光澤漆可能有點難以自行設定和管理，但我們在Experience League[設定光澤漆](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/varnish/config-varnish.html){target="_blank"}中已有此主題，以便更清楚瞭解它與Adobe Commerce搭配使用。 另一種選擇是使用雲端型解決方案。 雖然要考慮的因素很多，但最終還是選擇了Fastly作為Adobe Commerce雲端運算的解決方案。 它是以Fastly雲端為基礎的，使用VCL和許多光澤的彩繪版本。

尋找最適合您的應用程式、組態、預算及技術能力的解決方案，是一項困難的工作。 使用雲端式選項，可讓所有硬體零件消失，如管理、組態、伺服器和其他基礎架構元件。 由於其效能、擴充性、輸送量和許多其他關鍵量度，雲端團隊的Adobe Commerce將其選為解決方案。

透過為您的專案選擇有關Varnish的良好解決方案，您將自己設定為最佳客戶效能，並節省商務應用程式的工作量。

## CDN

除了光澤是您Adobe Commerce專案的寶貴資產外，下一個順理成章的是CDN。 除了您的塗漆，CDN還可以為您的CSS和頁面資產（例如影像）提供快取例項，以協助減少進入Adobe Commerce應用程式的頻寬。 它可以快取GraphQL回應，進一步發揮Headless Adobe Commerce網站的優點。 有些CDN提供影像最佳化、Web應用程式防火牆和其他功能。

雲端上的Adobe Commerce選擇使用Fastly做為其Varnish快取，但也作為其CDN。 此單一解決方案提供多種功能，可為Adobe Commerce在雲端上的客戶提供絕佳體驗。 您可以閱讀Experience League[Fastly服務總覽](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html){target="_blank"}中的Fastly服務總覽

CDN可為Adobe Commerce專案提供最佳化且安全的傳遞內容。 如果這不是您專案的必要元件，應視為您的網站日趨成熟且訪客數量增加。 藉由提供CDN，您可以延遲將額外硬體新增至基礎架構，或因每個要求移除的負載而擴充現有基礎架構。

## 停用模組

停用未使用的模組應予以考慮，但不應輕易進行。 此技術的確可減少部分要求的部分開銷和處理時間，但也有副作用，應加以考慮。 開發人員有時會在建立功能時假設模組可用。 這通常是安全的，除非他們選擇使用某些在已停用的模組中找到的類別。

停用模組（例如原生「電子報」）是相當常見的事件。 當商店擁有管理其電子報的第三方公司時，尤其如此。 這可能是個問題，因為已安裝協力廠商模組，且基於某些原因，他們決定使用電子報中的類別。 在某些初始安裝和測試期間可能會發現這種意外相依性，但隨後您將不得不決定是否要保留此協力廠商模組、啟用Newsletter，然後回歸測試網站，尋找引入的任何怪異行為。 或者，您是否找到替代該協力廠商模組的專案。 這兩個決定都伴隨著風險、時間和可能的錯誤。

在停用未使用的模組之前，請確定您沒有任何測試，例如單元、[MFTF](https://developer.adobe.com/commerce/cloud-tools/docker/test/application-testing/){target="_blank"}、[欺騙偵測測試](https://developer.adobe.com/commerce/cloud-tools/docker/test/code-testing/){targe=&quot;_blank&quot;}載入測試，或可能受影響的API要求。

## 要求每個提取請求都必須遵循Adobe Commerce和PHP編碼標準

Adobe Commerce有一組[編碼標準](https://developer.adobe.com/commerce/php/coding-standards/){target="_blank"}。 這些有助於確保遵循類似的模式、樣式和預期設計，無論軟體開發型別為何。 貢獻至Adobe Commerce程式碼基底時，這是必要專案。 不過，如果您選擇遵循此自訂開發方法，可為所有開發人員（包括目前和未來）奠定堅實的基礎。 在要求所有提取請求都必須通過程式碼標準時，請確定每個人都能瞭解並期待相同的一致開發模式。

為了配合Adobe Commerce編碼標準，使用的另一個基礎是PHP基本編碼標準。 開發人員指南應清楚定義您需遵循的標準，以及任何可接受的偏差。 不過，應該針對在[PHP-FIG](https://www.php-fig.org){target="_blank"}找到的公開維護指南進行遞補。

對遵循PSR-1和PSR-12的堅定立場。 確保為專案貢獻內容的開發人員遵循這些規則，有助於確保沒有奇怪的結構化檔案和模式。 這也有助於確保未來的開發人員能快速閱讀並瞭解他們檢閱的程式碼。 您越是遵循這些模式和編碼標準，未來開發的努力應該就越容易閱讀且實施得更快。

## 在每次部署後執行負載測試

在每次部署後執行負載測試可能會顯得過多。 但是，如果遵循此方法，則可以追蹤和緩解新推出功能導致效能降低的機會。

除了偵測新程式碼效能的下降，擁有網站關鍵量度的歷史參考資料也有助於深入瞭解何時啟用新工具或變更基礎架構。 例如，在付費給託管公司以增加您的環境規模並希望您可獲得您期望的效能提升之前，您可以使用新的設定來設定中繼環境，並執行負載測試以檢視實際結果。

這些測試可以自動化，且是CI/CD管道的一部分。 因此，您也可以制定規則來取得結果，如果發生過多偏離基準的情況，則可能會阻礙特徵合併。 此資料的使用案例數量是無限的，但如果不開始此程式，您可能會永遠無法實現其潛力。

在Experience League[效能測試秘訣](https://experienceleague.adobe.com/docs/commerce-operations/deliver-commerce-at-scale/launch.html){target="_blank"}和[測試指南](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/guidance.html){target="_blank"}中，Adobe Commerce對此主題有良好的記錄。

{{$include /help/_includes/hosting-related-links.md}}
