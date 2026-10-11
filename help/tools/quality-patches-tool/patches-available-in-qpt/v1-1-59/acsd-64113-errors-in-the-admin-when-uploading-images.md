---
title: ACSD-64113：透過[!DNL Media Gallery]上傳寬度小於高度的影像時發生管理員錯誤
description: 套用ACSD-64113修補程式來修正Adobe Commerce問題，其中透過[!DNL Media Gallery]上傳寬度與其高度相比相對較小的影像（反之亦然）時，管理員會發生錯誤。
feature: Page Content, Media, Admin Workspace
role: Admin, Developer
exl-id: aba9d875-1d5d-49c2-8071-ba0ce679d7cd
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 17d326fa-534a-55a5-b46f-8ae1de1e2f75
    internal-label: Page Content
  - id: 4ca54350-01cb-5b22-8966-5f2873dc6d90
    internal-label: Media
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%
---
# ACSD-64113：透過[!DNL Media Gallery]上傳寬度小於高度的影像時發生管理員錯誤

ACSD-64113修補程式修正透過[!DNL Media Gallery]上傳寬度相對高度而言較小的影像（反之亦然）時，管理員中發生錯誤的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59時，即可使用此修補程式。 修補程式ID為ACSD-64113。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.4.7-p3

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.5 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

透過[!DNL Media Gallery]上傳寬度與其高度相比相對較小的影像（反之亦然）時，管理員會發生錯誤。

<u>要再現的步驟</u>：

1. 移至&#x200B;**[!UICONTROL Content]** > **[!UICONTROL Media]** > **[!UICONTROL Media Gallery]**&#x200B;並選取&#x200B;**[!UICONTROL wysiwyg]**&#x200B;目錄。
1. 上傳寬度和高度比較小的影像（反之亦然）。

<u>預期結果</u>：

上傳影像時沒有發生錯誤。

<u>實際結果</u>：

1. 擲回下列錯誤訊息：

   *伺服器的技術問題造成錯誤。 請再試一次，繼續您正在執行的動作。 如果問題仍然存在，請稍後再試。*
1. `var/log/exception.log`包含：

   ```yaml
   report.CRITICAL: ValueError: imagecreatetruecolor(): Argument #1 ($width) must be greater than 0 in /home/lib/internal/Magento/Framework/Image/Adapter/Gd2.php:427
   ```

   或

   ```yaml
   report.CRITICAL: ValueError: imagecreatetruecolor(): Argument #1 ($height) must be greater than 0 in /home/lib/internal/Magento/Framework/Image/Adapter/Gd2.php:427
   ```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。


## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
