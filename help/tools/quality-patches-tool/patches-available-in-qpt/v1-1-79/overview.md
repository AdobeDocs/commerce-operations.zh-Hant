---
title: 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.79
description: 此小節提供 [!DNL Quality Patches Tool] (QPT) v1.1.79中可用修補程式所修正問題的詳細說明。
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: a8666ceccfe78536a624c67227692c98a521f555
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.79

此小節提供[!DNL Quality Patches Tool] (QPT) v1.1.79中可用修補程式所修正問題的詳細說明。

QPT v1.1.79包含下列修補程式：
1. **ACP2E-4402**：修正啟用後，建立為停用的產品未新增回相關[!UICONTROL Target Rule]結果的問題。
1. **ACP2E-4505**：修正從重複的瀏覽器分頁儲存過時資料類別的問題，建立循環相依性。
1. **ACP2E-4531**：修正變更CMS頁面的URL金鑰未更新頁面階層式URL的問題。
1. **ACP2E-4601**：修正付款交易處理在某些情況下可能表現無效的問題。
1. **ACP2E-4603**：修正執行[!UICONTROL Catalog Permissions]產品重新索引時，現有許可權索引列未變更，導致更新的類別許可權授予無法可靠地反映在產品上的問題。
1. **ACP2E-4706**：修正[!UICONTROL Target Rule]索引器略過[!UICONTROL Admin]範圍中未啟用的產品的問題。
1. **ACP2E-4720**：修正搭售方案產品未正確套用或移除免運費的問題，以及購物車折扣規則。
1. **ACP2E-4411**：修正購物車頁面及多貨幣商店迷你購物車中，套件產品價格顯示不正確的問題。
1. **ACP2E-4475**：修正啟用&#x200B;**[!UICONTROL Display Out of Stock Products]**&#x200B;選項時，產品清單頁面錯誤篩選及依價格排序無存貨搭售產品的問題。
1. **ACP2E-4110**：修正非預設貨幣的PDP與PLP上，以特殊價格捆綁產品的數量顯示不正確的問題。
1. **AC-10698**：修正系統在所有訂單層級傳送貨幣，而非將其與個別訂單產生關聯的問題。 現在，每個訂單的交易價格和總計都會傳送到[!DNL Google Tag]，提高電子商務資料追蹤的準確性。
1. **AC-10737**：修正`bin/magento setup:db:status`命令無法辨識JSON資料型別的問題。

使用左側的功能表，導覽至特定的修補程式頁面。
