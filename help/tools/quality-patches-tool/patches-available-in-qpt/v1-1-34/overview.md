---
title: 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.34
description: 此小節提供 [!DNL Quality Patches Tool] (QPT) v1.1.34中可用修補程式所修正問題的詳細說明。
feature: Tools and External Services
role: Admin
exl-id: d6cc3161-802c-4a1a-95b1-1eb85715643b
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.34

此小節提供[!DNL Quality Patches Tool] (QPT) v1.1.34中可用修補程式所修正問題的詳細說明。

QPT v1.1.34包含下列修補程式：

1. **ACSD-52277**：修正了在管理員中建立新訂單時，選取商店檢視後，管理員使用者未正確重新導向的問題。
1. **ACSD-50813**：修正管理員無法在具有[!UICONTROL Add Products by SKU]功能的SKU中，新增包含斜線的套件產品至管理員訂單的問題。
1. **ACSD-51630**：修正大量系統訊息導致下載管理頁面變慢的問題。
1. **ACSD-51853**：修正使用[!DNL Page Builder]時未套用複製文字樣式的問題。
1. **ACSD-52160**：修正未根據規則條件&#x200B;*如果在購物車中找到/找不到專案，且所有條件皆為true*，正確評估購物車價格規則之產品驗證結果的問題。
1. **ACSD-51636**：修正管理員無法從客戶帳戶區段新增使用者（儘管擁有所有必要的角色和許可權）的問題。
1. **ACSD-51739**：修正在`CompanyTeam` GraphQL要求中要求`structure_id`時傳回錯誤的問題。
1. **ACSD-51857**：修正`aggregate_sales_report_bestsellers_data` cron報告效能緩慢影響大型`sales_order`和`sales_order_item`資料庫資料表的問題。
1. **ACSD-48448**：修正取消訂單期間發生競爭條件問題，而此問題會造成&#x200B;*inventory_reservation*&#x200B;表格中出現重複專案的問題。
1. **ACSD-52689**：修正無法使用REST API將影像上傳至[!DNL Amazon S3]儲存空間的問題。

使用左側的功能表，導覽至特定的修補程式頁面。
