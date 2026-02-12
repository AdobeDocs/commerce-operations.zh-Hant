---
title: 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.76
description: 此小節提供 [!DNL Quality Patches Tool] (QPT) v1.1.76中可用修補程式所修正問題的詳細說明。
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: aeda6ddd9bac7e5f81329d9bd05ab8957ef2fb76
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 0%

---

# 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.76

此小節提供[!DNL Quality Patches Tool] (QPT) v1.1.76中可用修補程式所修正問題的詳細說明。

QPT v1.1.76包含下列修補程式：
1. **ACSD-67091**：修正寫入集大小上限錯誤，以根據資料磁碟區實作兩種刪除策略，確保目錄規則產品索引清理。
1. **ACSD-67370**：修正PDP/PLP上套件組合產品的價格不正確，以及多貨幣商店購物車頁面的多個問題。
1. **ACSD-68410**：修正針對可轉讓報價下訂單時，錯誤地將其他購物車明細新增或合併至報價的問題。 離開可協商報價結帳的最後一步後，產品現在可以正確新增到購物車中。
1. **ACSD-69086**：修正cron工作無法清除changelog表格，在處理大量資料時導致[!DNL Galera Cluster]當機的問題。
1. **ACSD-69115**：修正為指派給非預設網站的客戶管理購物車時，未向管理員使用者顯示購物車錯誤的問題。
1. **ACSD-69129**：修正當嘗試透過[!DNL REST] API更新次要網站的層級價格時，刪除預設基本網站並使用次要網站作為預設網站會導致錯誤的問題。
1. **ACSD-69203**：修正當類別條件中列出多個類別時，**[!UICONTROL Products List]** Widget傳回錯誤結果的問題。
1. **ACSD-69261**：修正因部分發票中`times_used`屬性的處理不正確及剩餘數量取消情況，而多次重複使用針對每位客戶設定為單次使用的購物車價格規則優惠券的問題。
1. **ACSD-69308**：修正僅於網站層級（非`special_price`）設定&#x200B;**[!UICONTROL All Store Views]**&#x200B;時，目錄價格規則不適用的問題。 修正後，請先檢查網站的預設商店，正確套用目錄價格規則。
1. **ACSD-69319**：修正子產品在自訂來源下有存貨時，套件價格未正確編制索引的問題。
1. **ACSD-69325**：修正修改SKU案例導致產品在店面無存貨的問題。
1. **ACSD-69331**：修正媒體集中的內容建立者無法僅以`create_folder`許可權建立資料夾的問題。 完成修正後，他們就能如預期建立資料夾。
1. **ACSD-69333**：修正具有作用中排程更新的產品允許SKU變更的問題。 修正後，SKU變更在作用中更新期間被禁止；儲存失敗並出現明確錯誤，管理SKU欄位被停用。 這可防止MSI。
1. **ACSD-69541**：修正管理員中的產品數量減少至低於購物車中已有產品數量時，無法透過GraphQL編輯該購物車中產品數量的問題。

使用左側的功能表，導覽至特定的修補程式頁面。
