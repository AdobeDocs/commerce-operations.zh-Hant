---
title: 付款處理和儲存的最佳做法
description: 瞭解如何安全地處理和儲存付款詳細資訊
role: Developer
feature-set: Commerce
feature: Best Practices
exl-id: 635f38d3-0199-4d96-ba75-9edd0cb94b5c
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 0%

---

# 付款處理和儲存的最佳做法

維護 [PCI合規性](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/payments/compliance-pci.html) 正在制定妥善處理和儲存信用卡付款的策略。

在Adobe Commerce儲存持卡人資料 **嚴禁** 而這樣做可能違反了您作為支付卡行業資料安全標準(PCI-DSS)下的商戶的義務。 有關我們的共同責任模式和商家義務指南的詳細資訊，請參閱 [共同責任指南Adobe Commerce](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-shared-responsibility-guide.pdf) Adobe信託中心。

我們建議遵循以下最佳實踐，以幫助您確保正確處理電子商務網站上的付款資訊。 有關總體安全最佳做法的其他指導，請參見 [安全最佳做法指南Adobe Commerce](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-best-practices-guide.pdf) Adobe信託中心

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md) 共：

* Adobe Commerce在雲基礎架構上
* Adobe Commerce內部

## 保護持卡人資料

如果需要儲存持卡人資料，持卡人資料應在Adobe Commerce境外儲存，並提供儲存保護。 為支付詳細資訊設定儲存保護，有助於防止欺詐和其他潛在安全問題。 按照其他PCI標準，有保護是第一道防線。 一些增強儲存資料保護的優選方法包括加密、截斷、標籤化、單向散列和掩蔽。

對加密密鑰的保護對於資料保護策略至關重要。 擁有熟練且值得信賴的保管員來監督這些密鑰至關重要。

最後，主帳號(PAN)在儲存期間必須不可讀（例如，屏蔽如XXX）。 這包括可移植的儲存和備份介質，如快閃記憶體驅動器、USB和外置硬碟，甚至包括審核日誌。

## 持卡人資料的加密傳輸

在傳輸過程中保護資料是保護支付資訊的關鍵，如持卡人資料。 當這些資訊通過開放網路傳輸時，它會更容易受到安全問題的影響。

### 使用安全傳輸協定

使用安全傳輸協定和做法傳輸持卡人資料，包括：

* 受信任的密鑰和證書
* 安全傳輸協定，如TLS、SSH或VPN
* 加密中的非對稱算法
* 具有發射和顯示PAN的標籤、掩蔽和穿透測試
* 限制對持卡人資料的訪問
* 對敏感資訊的訪問應根據知情需要加以限制，並僅給予那些有業務需要的授權人員

建議處理持卡人資料的方法是不儲存主要帳號(PAN)，而是使用特定付款處理提供商將卡標籤化，並儲存令牌、卡類型和加密的到期日期。 您可以將令牌用作檔案上的憑據，以備將來使用，因為它僅對每個商家是唯一的。 由於令牌是唯一的，如果存在安全問題，則其中的令牌無效，有助於防止欺詐活動

## 其他資訊

如果您正在按Adobe尋求建議的付款解決方案，請考慮 [Adobe支付服務](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html)。
