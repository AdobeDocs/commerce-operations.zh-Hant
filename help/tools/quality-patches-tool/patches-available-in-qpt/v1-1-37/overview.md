---
title: 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.37
description: 此小節提供 [!DNL Quality Patches Tool] (QPT) v1.1.37中可用修補程式所修正問題的詳細說明。
feature: Tools and External Services
role: Admin, Developer
exl-id: 92338019-d71c-4fe8-984f-879d551b418f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.37

此小節提供[!DNL Quality Patches Tool] (QPT) v1.1.37中可用修補程式所修正問題的詳細說明。

QPT v1.1.37包含下列修補程式：

1. **ACSD-52613**：修正即使未透過rest API更新`Inventory_source`個專案，快取和索引仍會重新整理的問題。
1. **ACSD-51884**：修正執行調整大小命令後，產品影像快取路徑不正確的問題。
1. **ACSD-53628**：修正CSV銷售訂單報告顯示不正確的特殊字元的問題。
1. **ACSD-49843**：修正啟用&#x200B;*[!UICONTROL Payment Action]* = *[!UICONTROL Sale]*&#x200B;設定的線上付款方式自動開立訂購專案的發票後，無法使用產品下載連結的問題。
1. **ACSD-53148**：修正GraphQL中新增相同可設定產品至購物車的兩個平行請求，在購物車上產生兩個具有相同產品SKU的個別專案的問題。
1. **ACSD-47054**：修正預覽重新索引為所有存放區執行重新索引，導致速度變慢的問題。
1. **ACSD-52606**：修正使用者按一下&#x200B;*時，顯示錯誤訊息*&#x200B;您的訂單未準備好取貨&#x200B;**[!UICONTROL Notify Order is Ready for Pickup]**&#x200B;的問題。
1. **ACSD-51574**：修正將影像取代為具有相同名稱的另一個影像後，未在前端更新影像的問題。
1. **ACSD-53728**：修正產品EAV索引器完成時間較長的問題。
1. **ACSD-53979**：若歡迎訊息包含單引號，修正首頁上發生的JS問題。
1. **ACSD-52143**：修正產品匯入後移除自訂選項的問題。
1. **ACSD-53750**：修正多重執行緒&#x200B;*重新索引期間的*&#x200B;中斷的管道或關閉的連線`catalog_product_price`錯誤。

使用左側的功能表，導覽至特定的修補程式頁面。
