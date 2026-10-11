---
title: ACSD-47937：由於應用程式層級的快取，未傳送降價通知
description: 套用ACSD-47937修補程式，修正Adobe Commerce因應用程式層級的快取而不一定傳送降價通知的問題。
feature: Admin Workspace, Cache, Orders
role: Admin
exl-id: 91d8e677-c2bb-4230-bbe3-a2c5f9b82e16
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%
---
# ACSD-47937：由於應用程式層級的快取，未傳送降價通知

ACSD-47937修補程式修正了因應用程式層級的快取而未一定傳送降價通知的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.26時，即可使用此修補程式。 修補程式ID為ACSD-47937。 請注意，此問題已排程在Adobe Commerce 2.4.6中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.4和2.4.5-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4、2.4.5和2.4.5-p1

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

客戶不會因為後續產品價格變更而收到產品價格下降電子郵件。

<u>要再現的步驟</u>：

1. 在&#x200B;**[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Alert]**&#x200B;中同時啟用&#x200B;*[!UICONTROL Price Changes]*&#x200B;和&#x200B;*[!UICONTROL Back in Stock]*&#x200B;的&#x200B;**[!UICONTROL Product Alert]**。
1. 啟用&#x200B;**[!UICONTROL Display Out of Stock Products]**。
1. 建立數量= 0的簡單產品(ABC)。
1. 從店面建立客戶並訂閱上述產品，以取得價格下降的產品警示。
1. 開始向客戶發出產品警示。

   ```PHP
   bin/magento queue:consumers:start product_alert
   ```

1. 卸除ABC產品的價格。
1. 觸發產品警報確認。

   ```PHP
   php n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

1. 再次降低ABC產品的價格。
1. 觸發產品警報確認。

   ```PHP
   php n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

>[!NOTE]
>
>如果您不熟悉[!DNL n98]工具，則可照常執行`bin/magento cron:run command`並監視`cron_schedule`資料表，以確保`catalog_product_alert`工作取得成功狀態。

<u>預期結果</u>：

已傳送第二個降價電子郵件。

<u>實際結果</u>：

第二個降價電子郵件未傳送。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)

## 相關閱讀

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的新工具
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用
* [在Commerce實作行動手冊中修改資料庫表格的最佳實務](/help/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables.md#why-adobe-recommends-avoiding-modifications)


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
