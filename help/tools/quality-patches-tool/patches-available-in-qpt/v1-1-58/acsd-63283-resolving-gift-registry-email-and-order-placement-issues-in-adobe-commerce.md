---
title: ACSD-63283：解決Adobe Commerce中的[!UICONTROL Gift Registry]個電子郵件和訂購問題
description: 套用ACSD-63283修補程式以修正Adobe Commerce的問題，即從[!UICONTROL Gift Registry]訂購專案會導致例外狀況，並確保[!UICONTROL Gift Registry Updates]僅包含正確專案。
feature: Gift, Shopping Cart
role: Admin, Developer
source-git-commit: a9dd031ba004954074a0551315e80a2bd733f690
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# ACSD-63283：解決Adobe Commerce中的[!UICONTROL Gift Registry]個電子郵件和訂購問題

ACSD-63283修補程式修正了從[!UICONTROL Gift Registry]訂購專案會導致例外狀況的問題，並確保[!UICONTROL Gift Registry Updates]僅包含正確的專案。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58時，即可使用此修補程式。 修補程式ID為ACSD-63283。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

>[!NOTE]
>此修補程式會取代並擴充[ACSD-56280](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-44/acsd-56280-gift-registry-purchases-are-not-completed) QPT修補程式。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.4.6-p3

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

Adobe Commerce中的[!UICONTROL Gift Registry]功能受兩個重大問題影響：

* 當客戶從其[!UICONTROL Gift Registry]下達專案訂單時，由於已觸發例外狀況，流程會失敗。
* 此外，傳送給登入擁有者的[!UICONTROL Gift Registry Updates]電子郵件錯誤地包含來自所有禮品登入的專案，而不是將更新限制在要更新的特定登入中的專案。

<u>要再現的步驟</u>：

1. 建立兩個產品：產品A和產品B。
1. 建立兩個客戶：客戶A和客戶B。
1. 以客戶A身分登入並建立新的[!UICONTROL Gift Registry]。
1. 導覽至產品A的產品頁面，並將其新增至[!UICONTROL Wishlist]。 開啟[!UICONTROL Wishlist Page]並使用[!UICONTROL Add to Gift Registry]將產品A移至[!UICONTROL Gift Registry]。
1. 以客戶B身分登入，建立新的[!UICONTROL Gift Registry]，並將產品B新增至其中。
1. 身為客戶B，透過電子郵件共用[!UICONTROL Gift Registry]： **[!UICONTROL My Account]> [!UICONTROL Gift Registry] >[!UICONTROL Share]**。
1. 登出為客戶B。
1. 按一下電子郵件中收到的連結。 將產品B新增至[!UICONTROL Cart]並下訂單。

<u>預期結果</u>：

客戶B只會從他們的贈品註冊處收到包含更新專案的電子郵件。

<u>實際結果</u>：

客戶B會收到包含所有禮品註冊處之專案的電子郵件。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。


## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
