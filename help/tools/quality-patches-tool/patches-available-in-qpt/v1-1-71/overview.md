---
title: 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.71
description: 此小節提供[!DNL Quality Patches Tool] (QPT) v1.1.71中可用修補程式所修正問題的詳細說明。
feature: Tools and External Services
role: Admin, Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: 618ab558-d6ad-5352-99d6-d5702c6fdf80
    internal-label: Tools and External Services
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%
---
# 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.71

此小節提供[!DNL Quality Patches Tool] (QPT) v1.1.71中可用修補程式所修正問題的詳細說明。

QPT v1.1.71包含下列修補程式：


* **ACSD-60624**： [!DNL Page Builder]中影像、橫幅和滑桿區段中的空白內容無法上傳影像
* **ACSD-67089**： `inventory/export-stock-salable-qty` API中的分頁問題，這會將`total_count`錯誤地限製為頁面大小。
* **ACSD-67093**：使用日期範圍篩選器透過[!DNL GraphQL]擷取訂單時，傳回不正確的結果。
* **ACSD-67459**：無法匯入描述超過65,536個字元的產品。
* **ACSD-67603**：啟用影像包含之產品的網站地圖產生處理時間過長
* **ACSD-67643**：在含有大量巢狀類別的環境中進行排程更新時，會建立重複的專案。
* **ACSD-67652**：在[!DNL GraphQL]呼叫中，即使子產品和父產品有庫存，套件組合產品狀態也會傳回為無庫存。
* **ACSD-67904**：如果城市名稱包含數字(0-9)、&amp;符號(&amp;)、句點(.)或括弧()，則無法下訂單。

使用左側的功能表，導覽至特定的修補程式頁面。
