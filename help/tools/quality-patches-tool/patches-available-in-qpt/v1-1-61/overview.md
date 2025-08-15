---
title: 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.61
description: 此小節提供 [!DNL Quality Patches Tool] (QPT) v1.1.61中可用修補程式所修正問題的詳細說明。
feature: Tools and External Services
role: Admin, Developer
exl-id: 065235fb-12e3-448b-bc37-51efdf95393a
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 0%

---

# 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.61

此小節提供[!DNL Quality Patches Tool] (QPT) v1.1.61中可用修補程式所修正問題的詳細說明。

QPT v1.1.61包含下列修補程式：

1. **ACP2E-3689**：修正類別樹狀結構在較深層級顯示並反映錨點/非錨點關係的多個問題。
1. **ACP2E-3705**：修正設定`indexer_update_all_views`時`MAGE_INDEXER_THREADS_COUNT` cron執行失敗的問題。
1. **ACSD-63883**：修正[!UICONTROL Requisition List]回應中`items_count`傳回不正確[!DNL GraphQL]的問題。
1. **ACSD-63974**：修正當專案過多時，[!UICONTROL Requisition List]頁面載入時間過長的問題，方法是在店面的[!UICONTROL Requisition List]格線新增分頁功能，只顯示限製為每頁記錄數的記錄部分，而非一次顯示所有記錄。
1. **ACSD-64178**：修正數千個產品屬性時，[!UICONTROL Attribute Set]編輯頁面載入緩慢的問題。
1. **ACSD-64209**：修正cron排程器擷取所有可協商的引號，但不排除狀態為&#x200B;**[!UICONTROL ordered]**&#x200B;的引號，進而觸發電子郵件或電子郵件的問題。
1. **ACSD-64431**：要求中包含優惠券代碼資訊的`placeOrder`變異不再擲回內部錯誤，而是顯示已成功下訂單。
1. **ACSD-64467**：修正儲存商店檢視層級的類別說明後，WYSIWYG編輯器顯示為空白的問題。
1. **ACSD-64546**：修正UI中發生一般錯誤訊息，且UPS傳送標籤建立期間，在記錄中儲存&#x200B;*陣列到字串轉換*&#x200B;例外狀況的問題，確保UI中顯示實際錯誤，並在記錄中儲存正確的錯誤訊息。
1. **ACSD-64684**：修正因數字&#x200B;*一千(1,000)*&#x200B;中的逗號（千位分隔符號）而編輯及儲存值大於&#x200B;*999*&#x200B;的禮品卡時發生驗證錯誤的問題。

使用左側的功能表，導覽至特定的修補程式頁面。
