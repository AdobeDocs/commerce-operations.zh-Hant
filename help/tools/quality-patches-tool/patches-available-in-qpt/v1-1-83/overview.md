---
title: 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.83
description: 此小節提供[!DNL Quality Patches Tool] (QPT) v1.1.83中可用修補程式所修正問題的詳細說明。
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: 6fedf98a6936fe842230003e0c2d52598bcf999d
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 0%
---
# 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.83

此小節提供[!DNL Quality Patches Tool] (QPT) v1.1.83中可用修補程式所修正問題的詳細說明。

QPT v1.1.83包含下列修補程式：

1. **AC-17975**：修正某些PHP環境中影響Admin工作流程、簽出驗證、驗證碼處理、類別管理、設定頁面和命令列作業的多個PHP 8.5相容性問題。
1. **AC-18128**：修正GraphQL傳回的訂單日期與訂單註解時間戳記在非英文地區設定中顯示錯誤行事曆日期的問題。
1. **AC-18096**：將日期格式從斜線分隔(`/`)還原為破折號(`-`)，修正Sales GraphQL日期欄位傳回與舊版不同格式日期的問題。
1. **ACP2E-4639**：修正GraphQL結構描述中請購單清單專案型別拼字錯誤的問題，而較舊的專案欄位和`RequistionListItems`型別仍可使用，但已過時。
1. **ACP2E-4838**：修正具有受限制許可權的管理員使用者無法從客戶格線中刪除客戶的問題。
1. **ACP2E-4877**：修正在&#x200B;*擱置中*&#x200B;狀態中，使用&#x200B;**[!UICONTROL Payment on Account]**&#x200B;下達的訂單無法在Admin中編輯的問題。
1. **ACP2E-4908**：修正大型目錄導致Redis或Valkey中記憶體使用過量的問題，因為每個商店檢視中的每項產品都有個別的版面配置快取專案。
1. **AC-12854**：修正在Admin中重新排序訂單時，會建立尾碼為&#x200B;*-1*&#x200B;的新訂單編號而非指派下一個順序編號的問題。
1. **ACP2E-4977**：修正可設定產品發票與銷退折讓單總計不包含&#x200B;**[!UICONTROL Fixed Product Tax]** (FPT)的問題，導致總計低於訂單總計。
1. **AC-16530**：修正購物車未一致反映目錄價格規則之排程更新的問題。
1. **AC-11389**：修正某些四捨五入案例中折扣、稅金和訂單總計計算錯誤的問題。
1. **ACP2E-4998**：修正裝載中有一個SKU不存在時，整個請求的`POST /V1/products/tier-prices` REST API請求失敗的問題，以防止更新有效的SKU。
1. **ACP2E-5015**：修正當需要的目錄資料無法使用時，將共用目錄儲存在「管理員」中可能會無意中移除指派的產品和定價的問題。
1. **AC-14940**：修正某些商店相關案例中，在管理員中按一下客戶帳戶的「**[!UICONTROL Reset Password]**」時，未傳送密碼重設電子郵件的問題。
1. **ACP2E-5101**：修正當索引子設為&#x200B;**[!UICONTROL Update on Schedule]**&#x200B;時，安裝B2B模組失敗的問題。
1. **ACP2E-5205**：修正當類別載入需要相當長的時間，或當涉及大量類別和產品時造成逾時的問題。 此外，每個類別分葉的產品計數現在都會正確顯示。
1. **ACP2E-3211**：修正將相同產品同時新增到店面的購物車中，會在購物車中建立相同SKU的個別專案，而非將它們合併為單一專案的問題。
1. **ACP2E-5223**：修正目錄許可權索引包含從客戶群組排除的網站的問題。

使用左側的功能表，導覽至特定的修補程式頁面。
