---
title: 付款處理與儲存的最佳作法
description: 瞭解如何安全地處理和儲存付款詳細資料
role: Developer
feature: Best Practices
exl-id: 635f38d3-0199-4d96-ba75-9edd0cb94b5c
source-git-commit: db0fce79b22d409e8d639b959dc5a04693e72659
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# 付款處理與儲存的最佳作法

維護[PCI法規遵循](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/payments/compliance-pci.html)的重要原則之一，是擁有適當處理和儲存信用卡付款的策略。

在Adobe Commerce中儲存持卡人資料是&#x200B;**嚴格禁止的**，這麼做可能會違反您身為商家應盡的支付卡產業資料安全標準(PCI-DSS)義務。 在Adobe信任中心的[Adobe Commerce分擔責任模式指南](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-shared-responsibilities-guide.pdf)中，可取得有關商戶責任的分擔責任模式和指引的詳細資訊。

請遵循下列最佳實務，以確保您在電子商務網站上正確處理付款資訊。 如需安全性最佳實務的其他指引，請參閱[保護您的網站和基礎結構](../launch/security-best-practices.md)。

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md)：

* 雲端基礎結構上的Adobe Commerce
* Adobe Commerce內部部署

## 保護持卡人資料

如果需要儲存持卡人資料，則持卡人資料應儲存於Adobe Commerce外部並提供儲存保障。 針對信用卡持卡人資料等付款詳細資料建立儲存保障，有助於防止欺詐和其他潛在的安全問題。 與其他PCI標準一樣，保護措施是第一道防線。 增強儲存資料保護的一些慣用方法包括加密、截斷、代碼化、單向雜湊和遮罩。

密碼編譯金鑰的保護對資料保護策略至關重要。 由技術高超且值得信賴的保管人來監管這些金鑰非常重要。

最後，主要帳號(PAN)在儲存期間必須無法讀取，例如以`XXX`遮罩。 這包括可攜式儲存和備份媒體，例如快閃磁碟機、USB和外部硬碟，甚至稽核記錄。

## 加密持卡人資料的傳輸

在傳輸期間保護資料是保護付款資訊（例如持卡人資料）的關鍵。 當這些資訊透過開放網路傳輸時，可能會更容易受到安全性問題的攻擊。

### 使用安全傳輸通訊協定

使用安全的傳輸通訊協定和實務來傳輸持卡人資料，包括：

* 信任的金鑰和憑證
* TLS、SSH或VPN等安全傳輸通訊協定
* 加密中的非對稱演演算法
* 透過傳輸和顯示PAN來進行代碼化、遮罩和滲透測試
* 限制對持卡人資料的存取
* 機密資訊的存取權應該視需要而加以限制，並且僅提供給有業務需要的授權人員

處理持卡人資料的建議方法是將資料代碼化，而非加以儲存。 將信用卡與特定的付款處理提供者記號，並儲存代號、信用卡型別和加密的到期日。 您可將代號作為檔案上的認證來使用，因為代號僅供每個商家使用。 由於代號是唯一的，因此如果有安全性問題，中的代號就會失效，有助於防止詐騙活動。

## 其他資訊

如果您正在尋找依Adobe建議的付款解決方案，請考慮[Adobe付款服務](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html)。
