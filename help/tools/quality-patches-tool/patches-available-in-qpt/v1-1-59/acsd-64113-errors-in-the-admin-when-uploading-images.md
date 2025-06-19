---
title: ACSD-64113：透過 [!DNL Media Gallery]上傳寬度小於高度的影像時發生管理員錯誤
description: 套用ACSD-64113修補程式來修正Adobe Commerce問題，其中透過 [!DNL Media Gallery]上傳寬度與其高度相比相對較小的影像（反之亦然）時，管理員會發生錯誤。
feature: Page Content, Media, Admin Workspace
role: Admin, Developer
exl-id: aba9d875-1d5d-49c2-8071-ba0ce679d7cd
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '359'
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
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

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

   ```
   report.CRITICAL: ValueError: imagecreatetruecolor(): Argument #1 ($width) must be greater than 0 in /home/lib/internal/Magento/Framework/Image/Adapter/Gd2.php:427
   ```

   或

   ```
   report.CRITICAL: ValueError: imagecreatetruecolor(): Argument #1 ($height) must be greater than 0 in /home/lib/internal/Magento/Framework/Image/Adapter/Gd2.php:427
   ```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。


## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
