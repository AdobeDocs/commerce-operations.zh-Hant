---
source-git-commit: e625670e741c0669050ab758d4f87c5ca06fe3df
workflow-type: tm+mt
source-wordcount: '724'
ht-degree: 0%

---
# 代碼片段

## 僅限Commerce {#commerce-only}

>[!NOTE]
>
>[!DNL Upgrade Compatibility Tool]僅適用於Adobe Commerce執行個體。

<!-- Configuration guide snippets -->

## 檔案系統擁有者 {#file-system-owner}

>[!WARNING]
>
>所有Magento CLI命令都必須由[檔案系統擁有者](/help/configuration/cli/config-cli.md#prerequisites)執行。

## 備份命令 {#tip-backup-command}

>[!TIP]
>
>`support:backup`命令是&#x200B;_不是_&#x200B;由`setup:backup`命令執行的相同程式碼備份。 `support:backup`命令是用來備份程式碼，以供Adobe Commerce支援人員檢查。

## B2B修補程式 {#b2b-patches}

>[!NOTE]
>
>安裝此安全性修補程式後，Adobe Commerce B2B商家也必須更新至最新相容的B2B安全性修補程式版本。 請參閱[B2B發行說明](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/release-notes)。

## 僅限Adobe Commerce {#ee-only}

>[!NOTE]
>
>此功能僅適用於Adobe Commerce執行個體。

## 已棄用分割資料庫 {#deprecate-split-db}

>[!IMPORTANT]
>
>Adobe Commerce 2.4.2版中的分割資料庫功能已[棄用](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187?_ga=2.128934671.2024864496.1657558157-1596100530.1657558157)。 請參閱[從分割資料庫還原至單一資料庫](/help/configuration/storage/revert-split-database.md)。

<!-- End of Configuration guide snippets -->

## 與舊版不相容的變更 {#bics}

>[!NOTE]
>
>Adobe Commerce版本可能包含與舊版不相容的變更(BIC)。 若要檢閱回溯不相容的變更，請參閱[BIC參考](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/reference/)。 在[BIC重點專案](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/)中說明嚴重的回溯不相容問題。 並非所有發行版本都會推出主要BIC。

## Alpha免責宣告 {#alpha}

>[!IMPORTANT]
>
>[Alpha](/help/release/versioning-policy.md#alpha-patch-release)發行版本可能不完整，且可能包含瑕疵。 產品依原樣提供，不含任何保固。 Adobe沒有義務維護、更正、更新、變更、修改或以其他方式支援(透過Adobe支援服務或其他方式) Alpha版本。 客戶不應依賴Alpha發行版本或任何隨附檔案或資料的正確運作或效能。 使用Alpha版本須完全由客戶自行承擔風險。

## Beta免責宣告 {#beta}

>[!IMPORTANT]
>
>Beta發行版本可能包含瑕疵，並依「現況」提供，並無任何保固。 Adobe沒有義務維護、更正、更新、變更、修改或以其他方式支援(來自Adobe支援服務或任何其他服務)Beta版。 客戶應謹慎使用，切勿依賴測試版和/或任何隨附檔案或資料的正確運作或效能。 因此，使用測試版完全由客戶自行承擔風險。

## CVE通知 {#cve-notice}

>[!NOTE]
>
>從2.3.2版開始，我們將指派並發佈索引式常見漏洞和暴露(CVE)編號，其中會包含外部各方回報給我們的每個安全性錯誤。 這可讓使用者更輕鬆地識別其部署中未解決的漏洞。 您可以在[CVE](https://cve.mitre.org/)進一步瞭解CVE識別碼。

## 其他發行資訊 {#other-release-info}

>[!NOTE]
>
>雖然這些發行說明中所述的增強功能和錯誤修正程式碼與Adobe Commerce捆綁在一起，但其中幾個專案(例如B2B、頁面產生器和Progressive Web Applications (PWA) Studio)也獨立發行。 這些專案的錯誤修正記錄在每個專案檔案中提供的個別專案特定發行資訊中。 請參閱[產品版本總覽](/help/release/release-notes/overview.md)。

## PHP程式控制 {#php-process-control}

您必須先在PHP中啟用「程式控制」支援(`pcntl`)，才能以平行模式執行索引器。 請參閱PHP檔案中的[安裝](https://www.php.net/manual/en/pcntl.installation.php)。

## 自訂修補程式 {#custom-patches-disclaimer}

>[!IMPORTANT]
>
>Adobe不支援使用此方法套用Adobe提供的官方修補程式。 請自行承擔下列方法的風險。 若要套用正式修補程式，請使用[[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}。 在部署任何自訂修補程式之前，請務必執行完整的測試。

## 2025年10月安全性修補程式反向移植 {#oct-2025-backports}

<!--These fixes were backported to 2.4.8-pe, 2.4.7-p8, and 2.4.6-p13-->

* **從TinyMCE移轉至Hugerte.org**

  由於TinyMCE 5和6的支援終止以及TinyMCE 7的授權不相容問題，Adobe Commerce WYSIWYG編輯器的目前實作從TinyMCE移轉到開放原始碼[GreatRTE編輯器](https://hugerte.org/)。

  此移轉確保Adobe Commerce仍符合開放原始碼授權，避免已知的TinyMCE 6漏洞，並為商家和開發人員提供現代且受支援的編輯體驗。

* **已新增對Apache ActiveMQ Artemis STOMP通訊協定的支援**

  透過Simple Text Oriented Messaging Protocol (STOMP)新增對ActiveMQ Artemis開放原始碼訊息代理程式的支援。 它提供可靠且可擴充的傳訊系統，提供彈性的STOMP式整合。 請參閱[Commerce設定指南](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/message-queues/message-queue-framework#apache-activemq-artemis-stomp)中的&#x200B;*Apache ActiveMQ Artemis*。

## 簽出頁面無法載入static.min.js和mixins.min.js {#checkout-page-fails-to-load-static-min-js-and-mixins-min-js}

最近CSP/SRI變更後，當JavaScript套件組合和縮制都在生產模式中啟用時，簽出頁面不會載入static.min.js和mixins.min.js。 因此，RequireJS mixin無法執行，且出庫去底版範本無法解析（例如，`"Failed to load the 'Magento_Checkout/shipping' template requested by 'checkout.steps.shipping-step.shippingAddress'"`）。

**因應措施**：

* 停用JavaScript套件組合；或
* 如果您持續啟用JavaScript套件組合，請停用JavaScript縮制。

>[!IMPORTANT]
>
>請勿在生產環境中停用CSP或移除SRI保護。 任何外掛程式層級的略過，都只能當作Hotfix的最後手段，且必須由安全性團隊檢閱。

**Hotfix**：

將儘快發行解決此問題的Hotfix。 請監視此發行說明頁面以瞭解更新內容。
