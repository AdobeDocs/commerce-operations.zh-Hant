---
title: 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.71
description: 此小節提供 [!DNL Quality Patches Tool] (QPT) v1.1.71中可用修補程式所修正問題的詳細說明。
feature: Tools and External Services
role: Admin, Developer
source-git-commit: 57fea42c0c893166c3489f6b95e09ccba787b9f1
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 0%

---

# 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.71

此小節提供[!DNL Quality Patches Tool] (QPT) v1.1.71中可用修補程式所修正問題的詳細說明。

QPT v1.1.71包含下列修補程式：


* **ACSD-60624**： **[!UICONTROL Upload Image]**&#x200B;無法用於[!UICONTROL Image]中[!UICONTROL Banner]、[!UICONTROL Slider]和[!DNL Page Builder]區段中的空白內容。
* **ACSD-67089**： `inventory/export-stock-salable-qty` API中的分頁問題，這會將`total_count`錯誤地限製為頁面大小。
* **ACSD-67093**：使用日期範圍篩選器透過[!DNL GraphQL]擷取訂單時，傳回不正確的結果。
* **ACSD-67459**：無法匯入描述超過65,536個字元的產品。
* **ACSD-67603**：啟用影像包含之產品的網站地圖產生處理時間過長
* **ACSD-67643**：在含有大量巢狀類別的環境中進行排程更新時，會建立重複的專案。
* **ACSD-67652**：在[!DNL GraphQL]呼叫中，即使子產品和父產品有庫存，套件組合產品狀態也會傳回為無庫存。
* **ACSD-67904**：如果城市名稱包含數字(0-9)、&amp;符號(&amp;)、句點(.)或括弧()，則無法下訂單。

使用左側的功能表，導覽至特定的修補程式頁面。
