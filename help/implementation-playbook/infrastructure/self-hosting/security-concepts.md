---
title: 自行托管Adobe Commerce安全性概念
description: 了解自行托管的安全性構想、概念及最佳實務，以供考慮。 了解唯讀檔案系統、惡意軟體掃描等概念，以及托管adobe商務時需考慮的許多其他主題。
landing-page-description: 了解自行托管Adobe Commerce時應考量的安全性概念和事項。
short-description: 了解自行托管Adobe Commerce的策略和安全性概念。
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
source-git-commit: 0d5c2d3ae44008142797c7ac91530a9df98ae004
workflow-type: tm+mt
source-wordcount: '1571'
ht-degree: 0%

---


# 安全性概念

對於任何與電子商務項目相關的項目，安全性應始終是一個強有力的考慮因素。 如果沒有強有力的安全姿態，可攻擊的表面面積將呈指數級增長。 所呈現的概念和構想提供經證實可減少一般所利用之常見弱點的方法。

下列概念不依特定順序排列。 它們旨在提供一些想法和概念以供考慮。 許多設備是免費的，或需要最少的設定和配置以及後續的監控。 在本教學課程之外研究這些主題，以確保您對此處呈現的概念有足夠深入的了解。

## 只讀檔案系統

只讀檔案系統概念借用自 [Adobe Commerce在雲基礎設施方面](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"}. 這完全消除了一個壞演員使用的主要區域。 許多漏洞利用更改了Commerce應用程式中預期的檔案以避免檢測。 壞操作程式不會建立，而是會更改現有檔案的內容以執行意外操作。 使檔案系統為只讀，可顯著減少此攻擊向量。

## 使用TWO Factor身份驗證和密碼管理器

永遠不要共用密碼。 每位管理員使用者都應有各自的帳戶，並有正確的ACL。 確保永不禁用或刪除兩個因素標識。 如果您提供第三方的管理員存取權，請確保密碼由密碼管理員產生，且絕不重複使用。

## 惡意軟體掃描

通常從嘗試專門處理Adobe Commerce的托管提供者找到惡意軟體掃描。 隨著新威脅的發現、檢測和診斷，這個已知惡意軟體和漏洞庫的數量不斷增加。 查詢托管提供商是否具有此類服務，以及這些服務是否可以自動運行，或僅在請求時運行。 您也可以訂閱一些服務，這些服務可以使用其自己的已知木馬程式庫，不斷檢查您的商務應用程式中是否有木馬程式。 其中有些僅為外部，有些可添加到基礎架構中，以提供所有資料夾、檔案甚至資料庫的內部深層掃描。 從Sansec.io到Sucuri，當然還有MageReport，在此領域有多年經驗的提供商。 有些是免費的，有些則需支付相關費用。 了解這項功能後，您就能與Adobe Commerce架構師和DevOps團隊進行周到的對話，將能確保您找到合適的解決方案。

## 適用於商務的全網站分析工具

此 [全網站分析工具](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/intro.html){target="_blank"} 是主動式自助服務工具和中央存放庫，包含詳細的系統分析和建議，以確保Adobe Commerce安裝的安全性和可操作性。 它提供24/7即時效能監控、報告和建議，以識別潛在問題，並更清楚地了解站點運行狀況、安全性和應用程式配置。 它有助於縮短解析時間，並改善網站的穩定性和效能。

## 啟用並驗證管理動作記錄的設定

登入Adobe Commerce管理員並導覽至「商店>設定>進階>管理員>管理動作記錄」後，即可找到此項目。 這會提供監控和記錄的事件清單。 如果懷疑是他們取得商務管理員的存取權，則在已利用之網站上進行法證分析時，此功能很有用。 此記錄和報告有助於查看壞演員執行的事件。 如果任何管理員動作記錄遭到停用，表示某人可能已停用這些動作以涵蓋執行特定動作時移除記錄。

## 用於SSH訪問的Bastion Server

這更難說明「安全性概念」教學課程中的大部分主題。 其基本思想是提供可作為ssh存取中間商的伺服器。 如此一來，您的生產伺服器就不會允許外部ssh連線。 您可以建立此堡壘伺服器，並使用本地IP掩碼來確保只允許指定的伺服器向它們SSH。

## 查看ACL角色和權限

Adobe Commerce的每位管理員使用者都獲派ACL角色。 應建立此角色，僅提供必須執行作業的功能。 應經常評估ACL角色，以確保它們不會提供超出必要的權限。 如有需要，請建立許多具有責任的ACL角色。 如果因故授予第三方存取權，應盡快停用。 詢問在建立管理員使用者時，他們絕對需要存取權並設定自動到期日的時間。

## 經常審核管理員用戶和SSH用戶訪問

若要偵測建立的管理員使用者不想要或未經授權，應經常稽核管理員使用者清單。 有一個理想的經驗法則是每月檢查誰擁有Adobe Commerce應用程式的SSH和管理員存取權。 如果檢測到任何新用戶，請禁用其帳戶，並遵循此類事件的任何公司策略和過程。 恢復用戶訪問比從利用漏洞中恢復更容易。

## 資料庫清理

限制對生產資料的存取。 這些指定的團隊成員應該能夠下拉生產資料庫，並清除他們的真實資料。 如果您可以移除資料，請截斷適當的表格，例如訂單、引號和客戶。 不過，有時候您會想要完整的資料集，但您可以對值進行匿名處理。 在測試環境中，這通常是正確的。 在升級之前，它也很有用。 具有真實的資料量，但匿名處理可確保您測試並驗證執行部署以正確升級的時間。 如果資料集有限，則可能會低估升級過程和時間。

+++隨機化客戶資訊範例以下是如何以隨機字串以及Adobe Commerce儲存資料之某些標準表格中所有名字和姓氏欄位來變更客戶電子郵件地址的範例。 **請記得檢查所有表中是否有敏感資料，此清單並不包括可能儲存客戶資料的表**

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


+++您也可以截斷表格，而不是嘗試匿名

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

[!BADGE Adobe Commerce僅在雲端上]{type=Informative}

使用環境變數有助於您設定可針對每個環境變更和應變更的特定值。 例如，您可能想要有適用於每個環境的不同管理URL。 將此值設為環境變數後，您就可以設定此值，並在必要時從雲端UI快速參考此值。

您可以閱讀更多有關此主題的Experience League [雲基礎架構環境變數上的商務](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html){target="_blank"}

## 軟體漏洞掃描工具

CI/CD管道是功能強大的工具，可協助自動執行部分工作。 尤其是，開發人員提交可能被利用的代碼的機會始終是實實在在的可能。 同行代碼審查通常會抓住這類內容，但因為它是人類，所以會出錯。 自動程式碼掃描有助於減少新推出功能中出現意外弱點的機會。 這些工具甚至可阻止程式碼合併至即時程式碼基底。 提供自動化程式碼安全性和品質掃描的方式和工具有很多。 有強大的自訂開發工具，但需要不斷更新和調整。 另一種方法是應用主動更新的工具，如synk.io和Amazon的代碼檢查器。

## Web應用程式防火牆

與DevOps或托管提供者對話時經常使用的Web應用程式防火牆或WAF。

Web應用程式防火牆(WAF)通過根據一組安全規則過濾流量來防止惡意流量進入站點和網路。 觸發任何規則的流量在可能損壞您的網站或網路之前即被阻止。

Adobe Commerce的雲WAF提供WAF策略，該策略包含旨在保護您的Adobe Commerce Web應用程式免受範圍廣泛的攻擊的規則集。 如果您選擇自行托管選項，請尋找WAF並設定規則即為您的責任。 有些托管提供者和WAF提供者有一組通用規則，這是個好開端，不過，您希望有些工作能讓項目運作正常。

WAF會檢查網路和管理員流量，以識別任何可疑活動。 它會評估GET和POST流量（HTTP API呼叫），並套用規則集以判斷要封鎖的流量。 WAF可以阻止各種攻擊，包括SQL注入攻擊、跨站點指令碼攻擊、資料過濾攻擊和HTTP協定違規。

作為基於雲的服務，WAF無需安裝或維護硬體或軟體。 Amply是現有的技術合作夥伴，提供軟體和專業知識。 它們的高效能、永遠開啟的WAF駐留在Ampley的全球交付網路中的每個快取節點中。

如需Apply提供之Adobe Commerce上WAF的詳細資訊，請參閱 [Adobe Commerce知識庫常見問題集](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/web-application-firewall-waf-powered-by-fastly-the-faq.html){target="_blank"}.

{{$include /help/_includes/hosting-related-links.md}}
