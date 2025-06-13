---
title: MDVA-39605： Redis快取TTL （到期日）的值錯誤
description: MDVA-39605修補程式解決了Redis快取TTL （到期日）的值錯誤的問題。 安裝[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13後，即可使用此修補程式。 修補程式ID為MDVA-39605。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。
feature: Cache, Console, Services
role: Admin
exl-id: 65f5d50a-e49e-4155-9d1a-3758f0c723a8
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 0%

---

# MDVA-39605： Redis快取TTL （到期日）的值錯誤

MDVA-39605修補程式解決了Redis快取TTL （到期日）的值錯誤的問題。 安裝[品質修補工具(QPT)](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13時，即可使用此修補程式。 修補程式ID為MDVA-39605。 請注意，此問題已排程在Adobe Commerce 2.4.5中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.3.4 - 2.4.4

>[!NOTE]
>
>此修補程式可能適用於其他發行了「品質修補程式」工具的版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

Redis快取TTL （到期日）的值錯誤。

<u>要再現的步驟</u>：

為了測試此修正，請排清快取並在店面開啟可設定的產品。 然後開啟終端機（主控台）並遵循以下步驟：

1. 執行命令： `redis-cli`。
1. 執行`KEYS "*PRICE"` （結果中應該只有一個索引鍵，例如`zc:ti:e54_PRICE`）。 複製金鑰。
1. 執行`SMEMBERS`，接著執行上一步驟中的金鑰（例如`SMEMBERS zc:ti:e54_PRICE`）。 從結果複製任何金鑰(例如，e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421)。
1. 使用上一個步驟的金鑰名稱執行`KEYS "*<key>"`以取得完整的金鑰名稱（例如，`KEYS "*e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421"`）。 結果中應該只有一個索引鍵（例如，`zc:k:e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421`）。 您可能會注意到，完整金鑰名稱只是前置詞為&quot;`zc:k:`&quot;的金鑰名稱。 現在複製完整金鑰名稱。
1. 執行`HGETALL`，接著執行步驟4中的完整金鑰名稱，以檢查值。 值應包含相關可設定產品之相關產品的序列化資料。
1. 執行`TTL`，接著執行步驟4中的完整金鑰名稱，以檢查金鑰是否到期。 結果應不同於&#x200B;**-1**&#x200B;和&#x200B;**-2**，並應約為2592000 （30天）。 雖然程式碼中設定的到期日為一年，但Adobe Commerce中使用的Redis程式庫具有2592000s的硬性最大到期限制。

<u>預期結果</u>：

到期限製為2592000s

<u>實際結果</u>：

到期限制設定為&#x200B;**-1**&#x200B;或&#x200B;**-2**。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解「品質修補程式」工具，請參閱：

* [已發行品質修補程式工具：支援知識庫中可自助提供品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的「品質修補工具」](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查是否有修補程式可用於您的Adobe Commerce問題。

如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
