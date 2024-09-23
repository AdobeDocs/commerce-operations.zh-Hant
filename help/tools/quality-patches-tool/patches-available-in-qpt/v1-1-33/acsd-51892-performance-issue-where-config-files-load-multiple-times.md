---
title: 'ACSD-51892：設定檔案載入多次的效能問題'
description: 套用ACSD-51892修補程式，修正部署期間設定檔案載入多次的Adobe Commerce效能問題。
feature: Observability
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-51892：設定檔案載入多次的效能問題

ACSD-51892修補程式修正每次在單一請求中存取部署組態值時載入`app/etc/env.php`和`app/etc/config.php`檔案所產生的效能問題。 過度讀取檔案會給系統帶來壓力，導致整體效能降低。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.33時，即可使用此修補程式。 修補程式ID為ACSD-51892。 請注意，Adobe Commerce 2.4.6-p2已修正問題。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

設定檔案載入多次時會發生效能問題。

<u>要再現的步驟</u>：

1. 執行部署或升級至Adobe Commerce 2.4.6或更新版本。
1. 在部署執行時，檢查檔案系統記錄檔以存取`app/etc/env.php`和`app/etc/config.php`個檔案。

<u>預期結果</u>：

部署在正常時間範圍內成功。

<u>實際結果</u>：

* 伺服器正疲於回應您輸入的任何命令。 存取網站時發生&#x200B;*錯誤503第一個位元組逾時*。
* 記錄檔中有多個專案可存取`app/etc/env.php`和`app/etc/config.php`個檔案。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
