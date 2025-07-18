---
title: ACSD-58141：為已啟用L2 Redis快取的登入客戶在POST請求上重新產生PHPSESSID
description: 套用ACSD-58141修補程式以修正Adobe Commerce問題，其中針對已啟用L2 Redis快取的登入客戶，在店面區域上重新產生POST請求的「PHPSESSID」，且客戶會從Admin更新。
feature: Customers, Cache
role: Admin, Developer
exl-id: c188c215-204c-489f-8703-4c81ca8703b7
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# ACSD-58141：如果L2 Redis快取已啟用，PHPSESSID會在登入客戶的[!DNL POST]個要求上重新產生

ACSD-58141修補程式修正了在啟用L2 Redis快取且客戶從Admin更新時，針對已登入客戶的[!DNL POST]個請求重新產生`PHPSESSID`的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50時，即可使用此修補程式。 修補程式ID為ACSD-58141。 請注意，問題已在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6

**與Adobe Commerce和Magento Open Source版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

針對已啟用L2 Redis快取的登入客戶，在[!DNL POST]個要求上重新產生`PHPSESSID`。

<u>必要條件</u>

環境必須設定為至少具有3個節點的Redis。

<u>要再現的步驟</u>：

1. 建立簡單的產品。
1. 建立客戶並登入店面。
1. 檢查`PHPSESSID`的值。
1. 傳送一些[!DNL POST]請求（例如，將產品加入購物車），並檢視`PHPSESSID`是否維持不變。
1. 登入&#x200B;**[!UICONTROL Admin]**&#x200B;面板並變更客戶的中間名稱。
1. 儲存中間名時，請變更它並再儲存幾次。
1. 在店面，傳送[!DNL POST]要求。 `PHPSESSID`應該已更新。
1. 在店面，傳送另一個[!DNL POST]要求並檢查`PHPSESSID`。
1. 重複上一步幾次。

<u>預期結果</u>

變更客戶資料後，`PHPSESSID`只會重新產生一次。

<u>實際結果</u>：

每次傳送[!DNL POST]要求時，`PHPSESSID`都會重新產生。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
