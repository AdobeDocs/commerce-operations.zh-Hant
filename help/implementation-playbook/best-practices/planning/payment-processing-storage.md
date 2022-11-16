---
title: 支付處理和儲存的最佳做法
description: 了解如何安全地處理和儲存付款詳細資訊
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: 124eaf6e7b465b320d3d7e6a3694130edb93f187
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 0%

---


# 支付處理和儲存的最佳做法

維護 [PCI合規性](https://nam04.safelinks.protection.outlook.com/GetUrlReputation) 正在制定適當處理和儲存信用卡支付的策略。

在Adobe Commerce中儲存持卡人資料 **嚴禁** 而且，這樣做可能違反您作為支付卡行業資料安全標準(PCI-DSS)下的商家所承擔的義務。 有關我們的商家義務共用責任模式和准則的更多資訊，請參閱 [共用Adobe Commerce責任指南](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-shared-responsibility-guide.pdf) Adobe信任中心。

建議您遵循下列最佳實務，以協助您妥善處理電子商務網站上的付款資訊。 有關整體安全性最佳實務的其他指引，請參閱 [Adobe Commerce的安全性最佳實務指南](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-best-practices-guide.pdf) 在Adobe信任中心

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 共：

* Adobe Commerce雲基礎架構
* Adobe Commerce內部

## 保護持卡人資料

如果需要儲存持卡人資料，持卡人資料應儲存在Adobe Commerce以外，並提供儲存保障。 為支付詳細資訊（如信用持卡人資料）設定儲存保護，有助於防止欺詐和其他潛在安全問題。 根據其他PCI標準，有保護是第一道防線。 一些增強對儲存資料的保護的優選方法包括加密、截斷、標籤化、單向散列和掩碼。

對加密密鑰的保護對於資料保護策略至關重要。 擁有技術熟練且值得信賴的托管機構來監督這些密鑰至關重要。

最後，主要帳號(PAN)在儲存期間必須不可讀（例如，如XXX被遮罩）。 這包括可攜式儲存和備份介質，如快閃記憶體驅動器、USB和外部硬碟，甚至審核日誌。

## 持卡人資料的加密傳輸

在傳輸過程中保護資料是保護支付資訊的關鍵，如持卡人資料。 當通過開放網路傳輸此資訊時，它可能會更容易受到安全問題的影響。

### 使用安全傳輸協定

使用安全傳輸協定和實踐傳輸持卡人資料，包括：

* 受信任的密鑰和證書
* TLS、SSH或VPN等安全傳輸協定
* 加密中的非對稱算法
* 透射和顯示PAN的Tokenization、掩蔽和穿透測試
* 限制對持卡人資料的訪問
* 對敏感資訊的訪問應根據知情需要加以限制，並僅提供給那些有業務需要的授權人員

處理持卡人資料的建議方法是不儲存主要帳號(PAN)，而是使用特定支付處理提供者來標籤卡片，並儲存代號、卡片類型和加密的到期日。 您可以將代號用作檔案上的憑據，以備將來使用，因為它僅對每個商家是唯一的。 由於代號是唯一的，如果有安全性問題，則中的代號會失效，有助於防止欺詐活動

## 其他資訊

如果您正在按Adobe查找建議的支付解決方案，請考慮 [Adobe支付服務](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html).
