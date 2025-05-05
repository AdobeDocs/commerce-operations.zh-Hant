---
title: ACSD-50478：備份網格和資料庫復原命令中復原動作的JS問題
description: 套用ACSD-50478修正程式，修正備份網格中復原動作的JS問題，以及資料庫復原命令（針對DB傾印包含觸發程式和*分隔符號* SQL命令的情況）。
exl-id: 2f47fbf6-44fc-487c-91fe-6e2e52fcdb2b
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-50478：備份網格和資料庫復原命令中復原動作的JS問題

ACSD-50478修補程式修正了備份網格中復原動作的JS問題，以及資料庫復原命令中資料庫傾印包含觸發程式和&#x200B;*分隔符號* SQL命令的情況。 安裝[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.33時，即可使用此修補程式。 修補程式ID為ACSD-50478。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.3-p1

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.0 - 2.4.4-p4

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

JS問題，針對DB傾印包含觸發程式和&#x200B;*分隔符號* SQL命令的情況，在備份網格和資料庫回覆命令中執行回覆動作。

<u>要再現的步驟</u>：

1. 將索引子設定為[!UICONTROL Update on Schedule]模式，以便在資料庫中建立觸發程式。
1. 從命令列啟用備份功能：

   `bin/magento config:set system/backup/functionality_enabled 1`

1. 移至&#x200B;**系統** > **工具** > **備份**&#x200B;並產生DB備份。
1. 開啟瀏覽器主控台；您會看到下列錯誤：

   ```
   Uncaught SyntaxError: Unexpected token '&' (at (index):606:32)
   
   function eventListener8jtGaqtgG2 () {
   
           return backup.rollback(&#039;db&#039;, &#039;1678391644&#039;);
   ```

1. 嘗試從命令列匯入DB：

   `bin/magento setup:rollback --db-file="<filename>"`

1. 系統會顯示下列錯誤：

   ```
   Syntax error or access violation: 1064 You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near 'delimiter' at line 1, query was: delimiter ;;
   ```

<u>預期結果</u>：

從管理員和命令列都能成功還原資料庫。

<u>實際結果</u>：

您已觀察步驟4和步驟6中提到的錯誤。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* [!DNL Quality Patches Tool]指南中的Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜尋修補程式](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。
