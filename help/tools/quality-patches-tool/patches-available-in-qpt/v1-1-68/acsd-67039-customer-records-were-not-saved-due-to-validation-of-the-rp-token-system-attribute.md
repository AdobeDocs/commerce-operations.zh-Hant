---
title: ACSD-67039：由於rp_token系統屬性驗證，未儲存客戶記錄
description: 套用ACSD-67039修補程式，修正Adobe Commerce編碼變數導致rp_token驗證中斷的問題。
feature: Customers, Admin Workspace
role: Admin, Developer
type: Troubleshooting
exl-id: e5995e28-b6b5-4955-a52a-895842c6b6e8
source-git-commit: 17c35f6da57440c2704879309a58c46b2c4eea25
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-67039：由於`rp_token`系統屬性驗證，未儲存客戶記錄

ACSD-67039修補程式修正了由於`rp_token`系統屬性驗證而未儲存客戶記錄的問題，且變音符號驗證僅套用至產生的客戶電子郵件。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68時，即可使用此修補程式。 修補程式ID為ACSD-67039。 請注意，此問題已在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6-p9

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.6-p9 - 2.4.6-p11

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

編碼變音符號導致`rp_token`上的驗證失敗，該錯誤已從驗證中排除。 如預期，只有電子郵件地址才允許變音符號。

<u>要再現的步驟</u>：

1. 安裝Adobe Commerce 2.4.4版。
1. 建立客戶。
1. 將Adobe Commerce從已建立客戶的2.4.4舊版升級至2.4.6版。
1. 設定加密金鑰為`env.php` =
   *d337b914e91ff703b1e94ba4156aadf0*
1. 在`customer_entity`資料表下的任何客戶中，將下列值設定到資料庫中：
*`rp_token` = *incr4869*
*`rp_token_created_at` = *2021-04-29 20:06:14*
1. 在[管理]面板中，移至&#x200B;**[!UICONTROL Customers]** > **[!UICONTROL All Customers]**。
1. 編輯您剛更新上述值的客戶。
1. 按一下&#x200B;**[!UICONTROL Save Customer]**&#x200B;或&#x200B;**[!UICONTROL Save and Continue Edit]**。

<u>預期結果</u>：

已成功儲存客戶值。

<u>實際結果</u>：

未儲存客戶記錄，且管理員使用者看到錯誤訊息： *儲存客戶時發生錯誤。*
`system.log`包含下列錯誤：

```
report.CRITICAL: Exception message: Notice: iconv(): Detected an incomplete multibyte character in input string in /vendor/magento/module-eav/Model/Attribute/Data/Text.php on line 190
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]： Tools指南中用於品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具
