---
title: 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.33
description: 此小節提供 [!DNL Quality Patches Tool] (QPT) v1.1.33中可用修補程式所修正問題的詳細說明。
feature: Tools and External Services
role: Admin
exl-id: 31812668-1d24-4da6-992f-981c259e00da
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.33

此小節提供[!DNL Quality Patches Tool] (QPT) v1.1.33中可用修補程式所修正問題的詳細說明。

QPT v1.1.33包含下列修補程式：

1. **ACSD-50478**：修正資料庫傾印包含觸發程式和分隔符號SQL命令時的資料庫復原命令。
1. **ACSD-50512**：修正錯誤： *可下載的連結與產品無關。 請驗證連結，然後再試一次。更新可下載產品臨時更新的開始日期時會發生的*。
1. **ACSD-50949**：修正搭配SKU篩選器使用時，[!UICONTROL Advanced Search]中的價格篩選器無法傳回正確結果的問題。
1. **ACSD-51645**：修正擴充功能`Magento_OfflineShipping`停用時儲存新[!UICONTROL Cart Price Rule]時擲回的錯誤。
1. **ACSD-50895**：修正未設定[!DNL Google Analytics] 4 GTM時未引發[!DNL Google Analytics] 3 GTM標籤的問題。
1. **ACSD-51102**：修正排程更新啟用規則時，套用至大量產品的目錄規則未正確編制索引的問題。
1. **ACSD-50368**：修正透過Async REST API或Async Bulk REST API建立客戶時，客戶的`group_id`遭忽略的問題。
1. **ACSD-51497**：修正客戶無法依下拉式清單型別[!UICONTROL Custom Attribute]排序目錄頁面的問題。
1. **ACSD-51408**：修正訂單專案狀態未正確設定為[!UICONTROL Backordered]的問題。
1. **ACSD-51735**：修正當產品庫存為&#x200B;*0*&#x200B;時，訂單專案狀態未正確設定為[!UICONTROL Ordered]的問題。
1. **ACSD-51792**：修正啟用[!DNL Google Tag Manager] 4時頁面沒有曝光事件的問題。
1. **ACSD-51471**：修正管理員使用者無法針對使用簡單產品的套件組合產品儲存已排程更新的問題，此套件組合產品本身已有排程更新。
1. **ACSD-51700**：修正在admin的可下載產品編輯頁面上切換商店檢視時發生的錯誤。
1. **ACSD-51120**：修正包含透過中繼更新更新的GraphQL區塊的CMS頁面未清除CMSGET快取的問題。
1. **ACSD-51240**：修正透過公司登錄檔完成註冊時，所上傳檔案遺失的問題。
1. **ACSD-51907**：修正受限管理員使用者無法以離線退款建立銷退折讓單的問題。
1. **ACSD-52148**：修正[!UICONTROL Google V3 reCAPTCHA Admin]登入偶爾失敗的問題。
1. **ACSD-51431**：修正即使變更記錄檔中沒有新專案，索引器狀態仍正常運作的問題。
1. **ACSD-51892**：修正部署期間設定檔案載入多次的效能問題。

使用左側的功能表，導覽至特定的修補程式頁面。
