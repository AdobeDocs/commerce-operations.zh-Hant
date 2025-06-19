---
title: 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.50
description: 此小節提供 [!DNL Quality Patches Tool] (QPT) v1.1.50中可用修補程式所修正問題的詳細說明。
feature: Tools and External Services
role: Admin, Developer
exl-id: 4e136531-6bd4-4294-9a5a-66d19eb136db
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.50

此小節提供[!DNL Quality Patches Tool] (QPT) v1.1.50中可用修補程式所修正問題的詳細說明。

QPT v1.1.50包含下列修補程式：

1. **ACSD-59280**：修正安裝2.4.4-pX版本時發生錯誤&#x200B;*呼叫未定義的方法ReflectionUnionType：：getName()*&#x200B;的問題。
1. **ACSD-45049**：修正客戶&#x200B;*[!UICONTROL Is required]*&#x200B;屬性設定無法按照Admin中的網站範圍正確運作的問題。
1. **ACSD-46938**：修正`setup:upgrade`期間DB觸發器重新建立的效能問題。
1. **ACSD-48210**：修正特定存放區檢視中更新&#x200B;*[!UICONTROL website scope]*&#x200B;屬性會覆寫全域範圍中屬性值的問題。
1. **ACSD-54887**：修正啟用&#x200B;*[!UICONTROL Persistent Shopping Cart]*&#x200B;的客戶工作階段過期後，客戶購物車被清空的問題。
1. **ACSD-58141**：修正`PHPSESSID`在已登入客戶的店面區域重新產生POST要求的問題（如果[!UICONTROL L2 Redis cache]已啟用，且客戶已從Admin更新）。
1. **ACSD-58352**：修正要求標頭中指定非預設存放區檢視時，透過GraphQL API傳回預設存放區檢視之傳回屬性標籤的問題。
1. **ACSD-58442**：修正寬度&#x200B;*768px*&#x200B;的裝置被視為行動裝置的問題，造成功能表和標題載入行動檢視而非案頭。
1. **ACSD-58790**：修正[!DNL Chrome]上行動檢視中產品詳細資料頁面影像的&#x200B;*縮放夾控*&#x200B;功能。
1. **ACSD-59036**：修正載入上下限均等於&#x200B;*$0*&#x200B;的產品價格時發生的例外狀況。
1. **ACSD-59229**：修正客戶群組相關資訊因請求中[!UICONTROL X-Magento-Vary]的舊值而儲存在錯誤區段的問題。
1. **ACSD-59378**：修正匯入期間未正確更新存放區層級URL重寫的問題。
1. **ACSD-59514**：修正具有[!DNL Page Builder]之管理區域中的表單擲回&#x200B;*[!DNL Page Builder]且呈現5秒而未釋放鎖定的問題。提交表單後，瀏覽器主控台發生*&#x200B;錯誤，變更無法儲存。
1. **ACSD-60303**：修正啟用HTML縮制後，無法發出管理員訂單的問題。
1. **ACSD-60441**：修正使用後端產生的整合存取權杖時，透過`V1/customers REST API`端點更新客戶的問題。

使用左側的功能表，導覽至特定的修補程式頁面。
