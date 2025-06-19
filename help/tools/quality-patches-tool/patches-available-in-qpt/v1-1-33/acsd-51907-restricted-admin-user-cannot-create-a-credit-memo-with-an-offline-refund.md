---
title: ACSD-51907：受限制的管理員使用者無法建立離線退款的銷退折讓單
description: 套用ACSD-51907修補程式以修正Adobe Commerce限制管理員使用者無法以離線退款建立銷退折讓單的問題。
exl-id: 1c44d99b-7633-4768-b7e7-332f3666a5d9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---

# ACSD-51907：受限制的管理員使用者無法建立離線退款的銷退折讓單

ACSD-51907修補程式修正受限管理員使用者無法以離線退款建立銷退折讓單的效能問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.33時，即可使用此修補程式。 修補程式ID為ACSD-51907。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.2-p2

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.2 &lt; 2.4.3-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

受限管理員使用者無法以離線退款建立銷退折讓單。

<u>要再現的步驟</u>：

1. 在預設網站上建立&#x200B;**客戶**。
1. 使用相關的&#x200B;*商店*&#x200B;和&#x200B;*商店檢視*&#x200B;建立&#x200B;**新網站**。
1. 將預設網站設定為新網站，清除快取。
1. 變更客戶設定： **管理員** > **商店** > **設定** > **客戶** > **客戶設定** > **共用客戶帳戶=全域**。
1. 在&#x200B;**管理員** > **系統** > **許可權**&#x200B;中，建立角色範圍設定為新建立網站&#x200B;*（僅存取銷售資料）*&#x200B;的新管理員使用者角色。
1. 使用此角色建立新的管理員帳戶。
1. 使用線上付款方式&#x200B;*(例如Auth.net或PayPal)*&#x200B;建立新訂單。
1. 以受限制的管理員使用者身分登入。
1. 移至&#x200B;**銷售** > **訂單** >然後&#x200B;**訂單檢視頁面**。
1. 建立發票。
1. 切換作業選項至「商業發票」頁標。
1. 按一下&#x200B;**發票**。
1. 按一下&#x200B;**[!UICONTROL Credit Memo]**。
1. 核取&#x200B;**[!UICONTROL Refund to Store Credit]**&#x200B;核取方塊，將旁邊文字欄位設定為&#x200B;*1*&#x200B;值。
1. 按一下&#x200B;**[!UICONTROL Refund Offline]**&#x200B;按鈕。

<u>預期結果</u>：

已建立銷退折讓單，且&#x200B;*$1*&#x200B;已退款至商店銷退折讓。

<u>實際結果</u>：

錯誤訊息顯示&#x200B;*需要更多許可權才能檢視此專案*。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
