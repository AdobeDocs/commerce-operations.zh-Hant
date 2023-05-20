---
title: 自辦Adobe Commerce安全概念
description: 瞭解要考慮的自我托管安全理念和概念以及最佳做法。 瞭解只讀檔案系統、惡意軟體掃描等概念，以及許多其他主題，以便在托管Adobe Commerce時加以考慮。
landing-page-description: 瞭解一些安全概念和需要考慮的事項，以便您自己主持Adobe Commerce。
short-description: 瞭解自己托管Adobe Commerce的戰略和安全概念。
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: c4912f02-0411-466f-8c77-d610de9eb35d
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1571'
ht-degree: 0%

---

# 安全概念

對於任何與電子商務項目相關的項目，安全應始終是一個強大考慮因素。 如果沒有強的安全姿態，可攻擊的表面面積將呈指數級增長。 提出的概念和思想提供了經驗證的方法，以減少通常被利用的常見漏洞。

以下概念不按任何特定順序排列。 它們旨在提供一些想法和概念供考慮。 許多設備是免費的，或需要最少的設定和配置以及後續的監控。 在本教程之外研究這些主題，以確保您對此處介紹的概念有足夠深入的瞭解。

## 只讀檔案系統

只讀檔案系統概念是從 [Adobe Commerce在雲基礎架構上](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"}。 這完全消除了壞演員使用的一個主要區域。 許多漏洞利用更改Commerce應用程式中預期的檔案來避免檢測。 壞執行者不會建立一個，而是會更改現有檔案的內容以執行意外操作。 使檔案系統為只讀，會顯著降低此攻擊向量。

## 使用TWO Factor身份驗證和密碼管理器

從不共用密碼。 每個管理員用戶應擁有自己的帳戶，並有正確的ACL。 確保從不禁用或刪除兩個因素標識。 如果您提供對第三方的管理員訪問權限，請確保密碼由密碼管理器生成，且永遠不要重用。

## 惡意軟體掃描

惡意軟體掃描通常從試圖在Adobe Commerce專門化的托管提供程式中找到。 隨著新威脅的發現、篩選和診斷，此已知惡意軟體和漏洞庫成為不斷增加的清單。 查詢托管提供方是否具有此類服務，以及是否可以自動或僅在請求時運行這些服務。 您還可以訂閱一些服務，這些服務可以使用自己已知漏洞的庫來不斷檢查您的商業應用程式是否存在漏洞。 其中有些只是外部的，有些可以添加到基礎架構中，以便對所有資料夾、檔案甚至資料庫進行內部深度掃描。 從Sansec.io到Sucuri，當然還有MageReport，在這個領域有多年經驗的一些供應商。 有些免費，有些則附帶相關費用。 知道這一點可用，並與您的Adobe Commerce架構師和DevOps團隊進行深思熟慮的對話將確保您找到正確的解決方案。

## 面向商業的站點分析工具

的 [站點範圍分析工具](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/intro.html){target="_blank"} 是一種主動式自助服務工具和中央儲存庫，包括詳細的系統見解和建議，以確保您的Adobe Commerce安裝的安全性和可操作性。 它提供全天候即時效能監控、報告和建議，以確定潛在問題並更好地瞭解站點運行狀況、安全和應用程式配置。 它有助於縮短解析時間，並提高站點穩定性和效能。

## 啟用並驗證管理操作日誌記錄的設定

登錄到Adobe Commerce管理員並導航到「儲存」>「配置」>「高級」>「管理」>「管理員操作日誌」後，即可找到此資訊。 這提供了監視和記錄的事件清單。 在被利用的站點上進行法證分析時，如果懷疑他們獲得了對Commerce管理員的訪問權限，則此功能非常有用。 此日誌記錄和報告有助於查看壞角色執行的事件。 如果禁用了任何管理員操作日誌記錄，表明在執行某些操作時有人可能已禁用它們以覆蓋刪除日誌記錄。

## 用於SSH訪問的Bastion伺服器

這更難解釋「安全概念」教程中的大多數主題。 其基本思想是提供充當ssh訪問中間人的伺服器。 這樣，生產伺服器就永遠不允許外部ssh連接。 您可以建立此堡壘伺服器並使用本地IP掩碼來確保只允許指定的伺服器SSH到這些伺服器中。

## 查看ACL角色和權限

每個Adobe Commerce的管理員用戶都分配了ACL角色。 應建立此角色以僅提供必須執行作業的功能。 應經常評估ACL角色，以確保它們不會提供超出必要的權限。 如果需要，請建立許多具有責任的ACL角色。 如果出於某種原因授予第三方訪問權，則應盡快取消其訪問權。 詢問他們在建立管理員用戶時完全需要訪問和設定自動過期日期的時間。

## 審核管理員用戶和SSH用戶訪問頻繁

要檢測不需要或未經授權的管理員用戶建立，應經常審核管理員用戶清單。 一個很好的經驗法則是每月檢查誰擁有對Adobe Commerce應用程式的SSH和管理員訪問權限。 如果檢測到任何新用戶，請禁用其帳戶並遵循此類事件的任何公司策略和過程。 恢復用戶訪問比從利用漏洞中恢復更容易。

## 資料庫清理

限制對生產資料的訪問。 這些指定的團隊成員應該能夠拉下生產資料庫，並清除其實際資料。 如果刪除資料是一個選項，則截斷相應的表，如訂單、報價和客戶。 但是，有時你想要完整的資料集，但是這些值是匿名的。 在轉移環境中通常是這樣。 在升級之前，它還非常有用。 通過擁有真實的資料量，但匿名化可確保您測試和驗證執行部署以正確升級的時間。 如果資料集有限，則可能會低估升級過程和時間。

+++隨機化客戶資訊示例以下是一個示例，說明如何使用隨機字串以及Adobe Commerce儲存資料的某些標準表中的所有名字和姓氏欄位更改客戶電子郵件地址。 **切記檢查所有表中是否有敏感資料，此清單並不包括可能儲存客戶資料的表**

```SQL
SET FOREIGN_KEY_CHECKS=0;
UPDATE customer_entity SET email = REPLACE(email, SUBSTRING(email, LOCATE('@', email) +1), CONCAT(UUID(), '.com'));
UPDATE email_contact SET email = REPLACE(email, SUBSTRING(email, LOCATE('@', email) +1), CONCAT(UUID(), '.com'));
UPDATE sales_invoice_grid SET customer_email = 'customer@example.com', customer_name  = 'Jack Smith';
UPDATE sales_order SET customer_email = 'customer@example.com', customer_firstname = 'Sally', customer_lastname = 'Smith', remote_ip = '127.0.0.1';
UPDATE sales_order_address SET region = 'Ohio', postcode = '12345-1234', lastname = 'Smith', street = '123 Main street', region_id = 44, city = 'Phoenix', telephone = NULL, firstname = 'Jane', company = NULL;
UPDATE sales_order_grid SET customer_email = 'customer@example.com', shipping_name = 'Jack', billing_name = 'Jack Smith', billing_address = '123 Main Street', shipping_address = '321 Pine Street', customer_name = 'Jane Smith';
UPDATE sales_shipment_grid SET customer_email = 'customer@example.com', customer_name = 'Jane Smith', billing_address = '123 Main street', billing_name = 'Jack Doe', shipping_name = 'Susie Smith';
UPDATE quote SET customer_email = 'customer@example.com', customer_firstname = 'Sally', customer_lastname = 'Jones', customer_dob = NULL, remote_ip = '127.0.0.1';
UPDATE quote_address SET email = 'customer@example.com', firstname = 'Jack', lastname = 'Smith', company = NULL, street = '123 Main st', city = 'AnyCity', region = 'Some State', region_id = 44, postcode = '12345-1234', telephone = NULL;
UPDATE magento_rma SET customer_custom_email = 'customer@example.com' WHERE customer_custom_email IS NOT NULL;
UPDATE customer_address_entity SET firstname = 'Jack', lastname = 'Smith', telephone = '909-555-1212', postcode = NULL,  region = NULL, street = '123 Main street', city = 'Anycity', company = NULL;
UPDATE customer_grid_flat SET name = 'Jane Doe', email = 'customer@example.com', dob = NULL, gender = NULL, taxvat = NULL, shipping_full = '', billing_full = '', billing_firstname = 'Jack', billing_lastname = 'Smith', billing_telephone = NULL, billing_postcode = NULL, billing_country_id = NULL, billing_region = NULL, billing_street = '123 Main street', billing_city = 'Anycity', billing_fax = NULL, billing_vat_id = NULL, billing_company = NULL;
UPDATE sales_creditmemo_grid SET billing_name = 'Sally', billing_address = '123 Main Street', customer_name = 'Jack Smith', customer_email = 'customer@example.com';
    
UPDATE magento_rma_grid SET customer_name = 'Jack Smith';
SET FOREIGN_KEY_CHECKS=1;
```

+++


+++您還可以截斷表，而不是嘗試匿名化

```SQL
SET FOREIGN_KEY_CHECKS=0;
TRUNCATE customer_log;  
TRUNCATE customer_visitor;  
TRUNCATE magento_logging_event;
TRUNCATE oauth_consumer;
TRUNCATE oauth_nonce;
TRUNCATE oauth_token;
TRUNCATE password_reset_request_event;
TRUNCATE acknowledgement;
TRUNCATE acknowledgement_report;
TRUNCATE avatax_log;
TRUNCATE avatax_queue;
TRUNCATE cron_schedule;
SET FOREIGN_KEY_CHECKS=1;
```

+++

+++完全刪除資訊示例以下是在啟動之前或較低開發環境之前刪除所有訂單、報價、貸項通知單等內容的示例

```SQL
DELETE FROM `gift_message`;
DELETE FROM `inventory_reservation`;
DELETE FROM `quote`;
DELETE FROM `quote_address`;
DELETE FROM `quote_address_item`;
DELETE FROM `quote_id_mask`;
DELETE FROM `quote_item`;
DELETE FROM `quote_item_option`;
DELETE FROM `quote_payment`;
DELETE FROM `quote_shipping_rate`;
DELETE FROM `reporting_orders`;
DELETE FROM `sales_bestsellers_aggregated_daily`;
DELETE FROM `sales_bestsellers_aggregated_monthly`;
DELETE FROM `sales_bestsellers_aggregated_yearly`;
DELETE FROM `sales_creditmemo`;
DELETE FROM `sales_creditmemo_comment`;
DELETE FROM `sales_creditmemo_grid`;
DELETE FROM `sales_creditmemo_item`;
DELETE FROM `sales_invoice`;
DELETE FROM `sales_invoiced_aggregated`;
DELETE FROM `sales_invoiced_aggregated_order`;
DELETE FROM `sales_invoice_comment`;
DELETE FROM `sales_invoice_grid`;
DELETE FROM `sales_invoice_item`;
DELETE FROM `sales_order`;
DELETE FROM `sales_order_address`;
DELETE FROM `sales_order_aggregated_created`;
DELETE FROM `sales_order_aggregated_updated`;
DELETE FROM `sales_order_grid`;
DELETE FROM `sales_order_item`;
DELETE FROM `sales_order_payment`;
DELETE FROM `sales_order_status_history`;
DELETE FROM `sales_order_tax`;
DELETE FROM `sales_order_tax_item`;
DELETE FROM `sales_payment_transaction`;
DELETE FROM `sales_refunded_aggregated`;
DELETE FROM `sales_refunded_aggregated_order`;
DELETE FROM `sales_shipment`;
DELETE FROM `sales_shipment_comment`;
DELETE FROM `sales_shipment_grid`;
DELETE FROM `sales_shipment_item`;
DELETE FROM `sales_shipment_track`;
DELETE FROM `sales_shipping_aggregated`;
DELETE FROM `sales_shipping_aggregated_order`;
DELETE FROM `tax_order_aggregated_created`;
DELETE FROM `tax_order_aggregated_updated`;
DELETE FROM `magento_rma`;
DELETE FROM `magento_rma_grid`;
DELETE FROM `magento_rma_item_entity`;
DELETE FROM `magento_rma_status_history`;
DELETE FROM `magento_sales_creditmemo_grid_archive`;
DELETE FROM `magento_sales_invoice_grid_archive`;
DELETE FROM `magento_sales_order_grid_archive`;
DELETE FROM `magento_sales_shipment_grid_archive`;
DELETE FROM `sequence_creditmemo_0`;
DELETE FROM `sequence_creditmemo_1`;
DELETE FROM `sequence_creditmemo_2`;
DELETE FROM `sequence_creditmemo_7`;
DELETE FROM `sequence_invoice_0`;
DELETE FROM `sequence_invoice_1`;
DELETE FROM `sequence_invoice_2`;
DELETE FROM `sequence_invoice_7`;
DELETE FROM `sequence_order_0`;
DELETE FROM `sequence_order_1`;
DELETE FROM `sequence_order_2`;
DELETE FROM `sequence_order_7`;
DELETE FROM `sequence_rma_item_0`;
DELETE FROM `sequence_rma_item_1`;
DELETE FROM `sequence_rma_item_2`;
DELETE FROM `sequence_rma_item_7`;
DELETE FROM `sequence_shipment_0`;
DELETE FROM `sequence_shipment_1`;
DELETE FROM `sequence_shipment_2`;
DELETE FROM `sequence_shipment_7`;

## USE THE FOLLOWING WITH CAUTION - CAN CAUSE ISSUES WITH TAX/PAYMENT PROCESSORS IF YOU REUSE ORDER NUMBERS, ETC.

ALTER TABLE sequence_creditmemo_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_creditmemo_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_creditmemo_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_creditmemo_7 AUTO_INCREMENT=1;
ALTER TABLE sequence_invoice_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_invoice_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_invoice_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_invoice_7 AUTO_INCREMENT=1;
ALTER TABLE sequence_order_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_order_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_order_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_order_7 AUTO_INCREMENT=1;
ALTER TABLE sequence_rma_item_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_rma_item_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_rma_item_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_rma_item_7 AUTO_INCREMENT=1;
ALTER TABLE sequence_shipment_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_shipment_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_shipment_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_shipment_7 AUTO_INCREMENT=1;
```

+++

## 使用環境變數

[!BADGE Adobe Commerce僅雲]{type=Informative}

使用環境變數有助於您設定可以且應該為每個環境更改的某些值。 例如，您可能希望每個環境都有不同的管理URL。 通過將此值設定為環境變數，您可以配置此值，並在必要時從雲UI中快速引用此值。

您可以在Experience League中閱讀有關此主題的更多內容 [雲基礎架構環境變數的商務](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html){target="_blank"}

## 軟體漏洞掃描工具

CI/CD管道可以成為一種強大的工具，並有助於自動執行某些任務。 特別是，開發人員提交可能被利用的代碼的機會始終是實實在在的可能。 同行代碼評論通常會捕捉到這樣的內容，但因為它是人類，所以會出錯。 自動代碼掃描有助於減少新引入的功能中出現意外漏洞的機會。 這些工具甚至可以阻止代碼合併到即時代碼庫中。 提供自動代碼安全性和質量掃描的方法和工具很多。 可以有強大的自定義開發工具，但它們需要不斷的更新和調整。 另一種方法是應用主動更新的工具，如synk.io和Amazon的代碼檢查器。

## Web應用程式防火牆

在與DevOps或主機提供程式通話時，經常使用Web應用程式防火牆或WAF。

Web應用程式防火牆(WAF)通過根據一組安全規則過濾通信來防止惡意通信進入站點和網路。 觸發任何規則的通信在可能損壞您的站點或網路之前被阻止。

Adobe Commerce的雲WAF提供了WAF策略，其規則集旨在保護您的Adobe CommerceWeb應用程式免受各種攻擊。 如果選擇自主承載選項，則查找WAF並配置規則是您的責任。 一些托管提供商和WAF提供商擁有一組通用規則，這是一個良好的開端，但是，希望一些工作能夠讓項目的內容發揮作用。

WAF檢查Web和管理通信以識別任何可疑活動。 它評估GET和POST通信（HTTP API調用），並應用規則集來確定要阻止的通信。 WAF可以阻止各種攻擊，包括SQL注入攻擊、跨站指令碼攻擊、資料過濾攻擊和HTTP協定違規。

作為基於雲的服務，WAF不需要安裝或維護任何硬體或軟體。 而且，Robbist是一個現有的技術合作夥伴，它提供了軟體和專業知識。 它們的高效能、永久開啟的WAF駐留在Appriest的全球傳輸網路的每個快取節點中。

欲瞭解Amphist公司在Adobe Commerce雲上提供的WAF的更多資訊，請閱讀 [Adobe Commerce知識庫常見問題](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/web-application-firewall-waf-powered-by-fastly-the-faq.html){target="_blank"}。

{{$include /help/_includes/hosting-related-links.md}}
