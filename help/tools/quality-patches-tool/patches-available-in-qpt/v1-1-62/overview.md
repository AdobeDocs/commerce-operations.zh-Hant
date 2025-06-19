---
title: 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.62
description: 此小節提供 [!DNL Quality Patches Tool] (QPT) v1.1.62中可用修補程式所修正問題的詳細說明。
feature: Tools and External Services
role: Admin, Developer
exl-id: be8ffedc-b589-4a30-ba9a-eed705696825
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.62

此小節提供[!DNL Quality Patches Tool] (QPT) v1.1.62中可用修補程式所修正問題的詳細說明。

QPT v1.1.62包含下列修補程式：

1. **ACSD-63406**：修正`persistent_clear_expired` cron工作執行時，任何cron工作都無法清除過期的永久性引號的問題。
1. **ACSD-63520**：修正透過&#x200B;**[!UICONTROL Configurations]**&#x200B;在管理面板中新增的影像未遵守上傳大小上限的問題。
1. **ACSD-64523**：修正可能透過匯入程式（透過admin或API）建立不含名稱的新產品，導致管理員介面中斷並導致產品無效的問題。
1. **ACSD-64532**：修正設定為&#x200B;*false*&#x200B;的ENV變數被視為字串&#x200B;*false*&#x200B;而非布林值false的問題。
1. **ACSD-64592**：修正非預設商店中禮品卡的電子郵件宣告連結一律將禮品卡宣告重新導向至預設網站的問題。
1. **ACSD-65164**：修正錯誤訊息&#x200B;*某些選取的專案選專案前無法使用*&#x200B;的問題，當使用單一選取的核取方塊自訂選項重新排序可設定的產品時。
1. **ACSD-64732**：修正協力廠商控制器未正確隨客戶區段快取的問題。

使用左側的功能表，導覽至特定的修補程式頁面。
