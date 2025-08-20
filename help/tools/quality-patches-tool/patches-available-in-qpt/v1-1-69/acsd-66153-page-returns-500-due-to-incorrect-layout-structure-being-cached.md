---
title: ACSD-66153：由於快取的不正確配置結構，頁面傳回500錯誤
description: 套用ACSD-66153修補程式來修正Adobe Commerce問題，該問題導致頁面因快取的不正確佈局結構而傳回500錯誤代碼。
feature: Catalog Management
role: Admin, Developer
type: Troubleshooting
source-git-commit: 70c7255e369ef366407d539488f0d815eb93f48a
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---


# ACSD-66153：由於快取的不正確配置結構，頁面傳回500錯誤

ACSD-66153修補程式修正了頁面因快取的不正確佈局結構而傳回500錯誤碼的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69時，即可使用此修補程式。 修補程式ID為ACSD-66153。 請注意，此問題已排程在Adobe Commerce 2.4.9中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p10

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

由於快取的不正確配置結構，頁面傳回500錯誤。

<u>要再現的步驟</u>：

1. 安裝`2.4-develop`。
1. 建立及安裝自訂模組：
1.1新增自訂區塊至`catalog_category_view`配置。
1.1透過其建構函式將`Magento\Framework\View\Result\Layout`插入自訂區塊。
1. 建立類別&#x200B;**[!UICONTROL shop]**。
1. 開啟&#x200B;**[!UICONTROL two terminal windows]**：
   1. **終端機1**：持續清除配置快取：

      ```
      for i in {1..200}; do
        bin/magento cache:clean layout
      done
      ```

   1. **終端機2**：模擬類別頁面的同時要求：

      ```
      for i in {1..200}; do
        curl -s -o /dev/null -w "Request $i: HTTP %{http_code}\n""http://your_magento_base_url/shop.html?req=$i"
      done
      ```

1. 有些要求會隨機失敗並產生500狀態碼，`var/log/support_report.log`會顯示下列錯誤：

   ```
   report.CRITICAL: The element with the "root" ID wasn't found. Verify the ID and try again. [] []
   ```

<u>預期結果</u>：

所有要求都會傳回200 OK。

<u>實際結果</u>：

有些要求會斷斷續續傳回500內部伺服器錯誤。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
