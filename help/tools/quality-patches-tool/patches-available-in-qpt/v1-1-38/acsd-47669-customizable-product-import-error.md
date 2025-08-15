---
title: ACSD-47669：匯入具有可自訂選項的產品時出現內部伺服器錯誤
description: 套用ACSD-47669修補程式，修正在匯入具有可自訂選項的產品期間發生內部伺服器錯誤的Adobe Commerce問題。
feature: Products
role: Admin, Developer
exl-id: e1a3b3b4-0392-4325-9766-a83276c1a593
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# ACSD-47669：匯入具有可自訂選項的產品時出現內部伺服器錯誤

ACSD-47669修補程式修正了在使用可自訂選項匯入產品期間發生內部伺服器錯誤的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.38時，即可使用此修補程式。 修補程式ID為ACSD-47669。 請注意，Adobe Commerce 2.4.6已修正此問題。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 - 2.4.5-p4

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

匯入具有可自訂選項的產品時發生內部伺服器錯誤。

<u>要再現的步驟</u>：

1. 建立其他商店檢視。 確定您有2個商店檢視，例如en、UK。
1. 建立兩個簡單的產品，例如prod1和prod2。
1. 準備一個csv檔案，該檔案會為每個存放區檢視中的產品以及&#x200B;**所有存放區檢視**&#x200B;範圍新增自訂選項。 匯入此csv檔案。
1. 準備另一個包含兩個記錄的csv檔案。 第一個記錄應更新專用於英國存放區檢視範圍的&#39;prod1&#39;自訂選項，第二個記錄應更新&#x200B;**所有存放區檢視**&#x200B;範圍的&#39;prod2&#39;自訂選項。 匯入第二個csv檔案。

<u>預期結果</u>：

您應該能夠自訂選項，不會發生任何錯誤。

<u>實際結果</u>：

發生完整性限制違規錯誤。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)：搜尋修補程式[!DNL Quality Patches Tool]。
