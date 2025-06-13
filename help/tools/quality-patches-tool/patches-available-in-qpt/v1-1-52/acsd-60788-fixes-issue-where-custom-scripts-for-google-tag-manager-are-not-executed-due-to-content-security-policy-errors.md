---
title: ACSD-60788：由於CSP錯誤， [!DNL Google Tag Manager] 的自訂指令碼未執行
description: 套用ACSD-60788修補程式以修正Adobe Commerce問題，該問題導致 [!DNL Google Tag Manager] 的自訂指令碼因內容安全性原則(CSP)錯誤而無法執行。
feature: Security
role: Admin, Developer
exl-id: 3392da76-86cb-4357-8658-c95d914a5829
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# ACSD-60788：由於內容安全性原則錯誤，[!DNL Google Tag Manager]的自訂指令碼未執行

ACSD-60788修補程式修正因內容安全性原則錯誤而無法執行[!DNL Google Tag Manager]的自訂指令碼的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.52時，即可使用此修補程式。 修補程式ID為ACSD-60788。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.4.7-p1

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

由於內容安全性原則(CSP)錯誤，[!DNL Google Tag Manager]的自訂指令碼未執行。

<u>要再現的步驟</u>：

1. 設定&#x200B;*[!DNL Google Tag Manager]*&#x200B;變數。
1. 設定&#x200B;*[!DNL Google Tag Manager]*&#x200B;自訂HTML標籤。
1. 將下列JavaScript程式碼放入第一個標籤中：

   ```
   <script nonce="{{gtmNonce}}">
   console.log("Nonce from simple JS {{gtmNonce}}");
   </script>
   ```

1. 設定&#x200B;*GTM*&#x200B;後排清快取。
1. 在瀏覽器中開啟開發人員主控台。
1. 開啟首頁。

<u>預期結果</u>：

瀏覽器開發主控台顯示來自簡單JS （隨機字元）*的* Nonce。

<u>實際結果</u>：

瀏覽器開發主控台會顯示&#x200B;*未定義簡易JS的* Nonce。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
