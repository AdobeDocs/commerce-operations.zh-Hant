---
title: ACSD-52041：頁面產生器演算不會解除鎖定
description: 套用ACSD-52041修補程式來修正Adobe Commerce問題，此問題導致頁面產生器呈現五秒鐘，且未釋放鎖定。
feature: Page Builder
role: Admin, Developer
exl-id: 48a7fc36-e98a-4a4e-bed3-248d7d73f6cb
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# ACSD-52041：頁面產生器演算不會解除鎖定

ACSD-52041修補程式修正了頁面產生器呈現五秒鐘，且未釋放鎖定的問題。 安裝[!DNL Quality Patches Tool (QPT)] 1.1.48時，即可使用此修補程式。 修補程式ID為ACSD-52041-v2。 請注意，此問題已排程在Adobe Commerce 2.4.7中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.6

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.4-p5、2.4.5 - 2.4.5-p4和2.4.6 - 2.4.6-p2。



>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。


## 問題

**[!DNL Page Builder]**&#x200B;轉譯&#x200B;*5*&#x200B;秒而不釋放鎖定。

<u>要再現的步驟</u>：

1. 編輯CMS頁面、產品頁面或任何具有&#x200B;**[!DNL Page Builder]**&#x200B;的內容。
1. 儲存變更。
1. 請注意頁面儲存時間。

<u>預期結果</u>

內容已儲存。 瀏覽器記錄檔中找不到錯誤。

<u>實際結果</u>

儲存作業需要比平常更久的時間才能完成。
主控台中的錯誤： ``Page Builder was rendering for 5 seconds without releasing locks``

## 套用修補程式

若要套用版本&#x200B;**2.4.4 - 2.4.4-p5、2.4.5 - 2.4.5-p4和2.4.6 - 2.4.6-p2**&#x200B;的個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用狀況[!DNL Quality Patches Tool]。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool] 已發行：支援知識庫中的自助式品質修補程式](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]，檢查您的Adobe Commerce問題是否有修補程式可用。


如需QPT中其他修補程式的詳細資訊，請參閱[[!DNL Quality Patches Tool]指南中的](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant>)：搜尋修補程式[!DNL Quality Patches Tool]。
