---
title: 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.67
description: 此小節提供 [!DNL Quality Patches Tool] (QPT) v1.1.67中可用修補程式所修正問題的詳細說明。
feature: Tools and External Services
role: Admin, Developer
exl-id: 47f6b57d-b945-4e77-8630-2df709a3469e
source-git-commit: 7fd88da04ca147829aa5aa7f90d05d8760ff0f3d
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---

# 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.67

此小節提供[!DNL Quality Patches Tool] (QPT) v1.1.67中可用修補程式所修正問題的詳細說明。

QPT v1.1.67包含下列修補程式：
1. **AC-14985**：與TLS一併傳送的SMTP郵件傳回錯誤。
1. **AC-14984**： php-amqplib/php-amqplib ^3.2.0的SSL連線問題。
1. **ACSD-65935**： `customerOrders` GraphQL查詢在刪除產品時傳回內部伺服器錯誤。
1. **ACSD-66049**：非英文店面因為ICU的資料庫版本而顯示不正確的價格。
1. **ACSD-66084**： `row_total_incl_tax`針對訂單API回應中的完全折扣專案，傳回接近零的殘值，而非0.00。
1. **ACSD-66118**：若未重新整理組態快取，更新存放區檢視程式碼會清除設計組態設定。
1. **ACSD-66139**： GraphQL在訂購期間傳回不存在的或非使用中購物車的UNDEFINED錯誤。
1. **ACSD-66301**：將產品從訂單移回Admin中的購物車導致數量不符。
1. **[ACSD-66434](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-67/acsd-66434-customer-id-missing-from-company-graphql-queries.md)**：公司GraphQL查詢中缺少客戶ID。
1. **ACSD-66441**：多存放區設定中可設定產品的階層式導覽索引資料不正確。

使用左側的功能表，導覽至特定的修補程式頁面。
