---
title: MDVA-37725：透過非預設網站傳送的電子郵件包含預設網站的標誌URL
description: MDVA-37725修補程式修正了透過包含預設網站之標誌URL的非預設網站傳送非同步訂購電子郵件的問題。
feature: Communications, Orders
role: Admin
exl-id: 6e72897c-7652-4b5a-8575-090e94188daf
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# MDVA-37725：透過非預設網站傳送的電子郵件包含預設網站的標誌URL

>[!WARNING]
>
> MDVA-37725修補程式已過時。

MDVA-37725修補程式修正了透過包含預設網站之標誌URL的非預設網站傳送非同步訂購電子郵件的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.4時，即可使用此修補程式。 修補程式ID為MDVA-37725。 請注意，此問題已排程在Adobe Commerce 2.4.4中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.4.2

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.3.0 - 2.4.3

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

非同步訂購電子郵件會透過包含預設網站標誌URL的非預設網站傳送。

<u>必要條件</u>：

1. 第二個網站/商店/商店檢視必須已建立。
1. **非同步傳送**&#x200B;設定必須從&#x200B;**商店** > **設定** > **設定** > **銷售** > **銷售電子郵件** > **一般設定**&#x200B;啟用。
1. **已開啟將商店代碼新增至URL的設定**，以便從&#x200B;**商店** > **設定** > **設定** > **URL選項**&#x200B;存取次要網站。

<u>要再現的步驟</u>：

1. 從第一家和第二家商店下訂單。
1. 執行cron以傳送銷售電子郵件。
1. 檢查來自第二個網站的電子郵件。

<u>預期結果</u>：

電子郵件的標誌URL包含第二個網站的URL。

<u>實際結果</u>：

電子郵件的標誌URL包含預設網站的URL。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)中可用的[修補程式區段。
