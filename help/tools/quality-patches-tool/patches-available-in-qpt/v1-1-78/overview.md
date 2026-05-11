---
title: 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.78
description: 此小節提供 [!DNL Quality Patches Tool] (QPT) v1.1.78中可用修補程式所修正問題的詳細說明。
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: 24a6d3e2da8666278b0f491e3caaf6b2509c31d8
workflow-type: tm+mt
source-wordcount: '971'
ht-degree: 0%

---

# 概觀： [!DNL Quality Patches Tool] (QPT) v1.1.78

此小節提供[!DNL Quality Patches Tool] (QPT) v1.1.78中可用修補程式所修正問題的詳細說明。

QPT v1.1.78包含下列修補程式：
1. **ACP2E-4416**：修正在Admin中建立客戶獎勵點時未初始化的問題。
1. **ACP2E-4419**：修正成功在店面進行reCAPTCHA v2 （「我不是機器人」）驗證後，禮品卡在結帳時未正確套用的問題。
1. **ACP2E-4431**：修正重新索引程式期間刪除符合目標規則之相關產品的問題。
1. **ACP2E-4448**：修正Redis復原後，Redis中斷期間所做的設定變更未反映出來，而造成儲存過時值的問題。
1. **[ACP2E-4456](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4456.md)**：修正使用GraphQL突變取消訂單時，無法將完全使用禮品卡支付的訂單轉換成「已結」狀態的問題。
1. **[ACP2E-4452](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4452.md)**：修正[!UICONTROL Quick Order]頁面上的產品價格包含稅捐（無論稅捐顯示組態為何）的問題。
1. **ACP2E-4507**：修正透過GraphQL變動提出的客戶密碼重設請求未套用密碼選項組態的問題。
1. **ACP2E-4513**：修正系統未刪除過期驗證碼影像的問題。
1. **ACP2E-4522**：修正同時執行多個購物車合併或報價儲存請求時，quote_coupons表格發生間歇性重複金鑰錯誤的問題。
1. **[ACP2E-4448](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4448.md)**：修正Redis復原後，Redis中斷期間所做的設定變更未反映出來，而造成儲存過時值的問題。
1. **[ACP2E-4416](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4416.md)**：修正在Admin中建立客戶獎勵點時未初始化的問題。
1. **[ACP2E-4431](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4431.md)**：修正重新索引程式期間刪除與目標規則相符的[!UICONTROL Related Products]的問題。
1. **[ACP2E-4419](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4419.md)**：修正成功在店面進行reCAPTCHA v2 （「我不是機器人」）驗證後，禮品卡在結帳時未正確套用的問題。
1. **ACP2E-4448**：修正Redis復原後，Redis中斷期間所做的設定變更未反映出來，而造成儲存過時值的問題。
1. **ACP2E-4452**：修正「快速訂購」頁面上的產品價格包含稅捐（無論稅捐顯示組態為何）的問題。
1. **ACP2E-4456**：修正使用GraphQL突變取消訂單時，無法將完全使用禮品卡支付的訂單轉換成「已結」狀態的問題。
1. **[ACP2E-4507](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4507.md)**：修正透過GraphQL變動提出的客戶密碼重設請求未套用[!UICONTROL Password Options]設定的問題。
1. **ACP2E-4513**：修正系統未刪除過期驗證碼影像的問題。
1. **[ACP2E-4522](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4522.md)**：修正同時執行多個購物車合併或報價儲存請求時，quote_coupons表格發生間歇性重複金鑰錯誤的問題。
1. **ACP2E-4528**：修正客戶地址中的城市驗證問題，該問題現在允許正斜線(/)字元，並拒絕無效字元，例如！、&#39;、#和？。
1. **[ACP2E-4535](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4535.md)**：修正送出忘記密碼表單導致工作階段損毀或重新產生（PHPSESSID變更），且訪客購物車已清除的問題。
1. **ACP2E-4540**：修正Fotorama程式庫未正確載入的問題，此問題會導致系統只顯示第一個附加的影像。
1. **ACP2E-4555**：修正包含「。」的現代電話號碼的問題。 或「/」未正確驗證。
1. **ACP2E-4565**：修正使用X-Adobe-Company標頭時，GraphQL公司查詢傳回「目前客戶未獲授權」的問題。
1. **[ACP2E-4591](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4591.md)**：修正透過REST API下訂單時，根據訂單數的客戶區段（例如「首次購買者」）未更新的問題。
1. **[ACP2E-4540](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4540.md)**：修正Fotorama程式庫未正確載入的問題，此問題會導致系統只顯示第一個附加的影像。
1. **[ACP2E-4555](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4555.md)**：修正包含「。」的現代電話號碼的問題。 或「/」未正確驗證。
1. **[ACP2E-4565](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4565.md)**：修正使用X-Adobe-Company標頭時，GraphQL公司查詢傳回「目前客戶未獲授權」的問題。
1. **[ACP2E-4609](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4609.md)**：修正部分引號包含已刪除產品時，我的引號頁面未顯示引號的問題。
1. **ACP2E-4609**：修正部分引號包含已刪除產品時，我的引號頁面未顯示引號的問題。
1. **[ACP2E-4613](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4613.md)**：修正大型媒體目錄結構導致gettree回應緩慢，導致&#x200B;**[!UICONTROL Media Gallery]**&#x200B;目錄樹狀結構載入時間延長的問題。
1. **ACP2E-4628**：修正當「帳戶共用」設定為「全域」時，匯入具有大寫電子郵件地址的客戶會導致未定義陣列金鑰錯誤的問題。
1. **ACP2E-4665**：修正透過REST API提出要求時，產品相簿中含有視訊之可設定產品的子產品未列出的問題。
1. **ACP2E-4732**：修正當changelog表格中的version_id欄達到最大值時，具有大量更新的客戶停止部分索引的問題。
1. **[ACP2E-4763](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4763.md)**：修正當「型錄價格」設定為「包含稅捐」時，由於套用兩次稅捐，GraphQL customerOrders查詢會傳回膨脹的original_price_include_tax和original_row_total_include_tax值的問題。
1. **[ACP2E-4732](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4732.md)**：修正當changelog表格中的version_id欄達到最大值時，具有大量更新的客戶停止部分索引的問題。
1. **[ACP2E-4665](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4665.md)**：修正透過REST API提出要求時，產品相簿中含有視訊之可設定產品的子產品未列出的問題。
1. **ACP2E-4665**：修正透過REST API提出要求時，產品相簿中含有視訊之可設定產品的子產品未列出的問題。
1. **ACP2E-4763**：修正當「型錄價格」設定為「包含稅捐」時，由於套用兩次稅捐，GraphQL customerOrders查詢會傳回膨脹的original_price_include_tax和original_row_total_include_tax值的問題。
1. **ACSD-60989**：修正透過宣告式結構描述以外部索引鍵修改資料行而導致MariaDB發生錯誤的問題。

使用左側的功能表，導覽至特定的修補程式頁面。
