---
title: ACSD-63244：解決管理面板JavaScript問題，包括 [!DNL Google Maps] 轉譯與主控台錯誤
description: ACSD-63244修補程式修正了管理面板中的多個JavaScript問題，包括 [!DNL Google Maps] 轉譯問題以及反複出現的「Uncaught TypeError」問題。瀏覽器主控台中的_each不是函式'錯誤。
feature: Admin Workspace
role: Admin, Developer
exl-id: 1985c845-219e-4af4-8f70-62dd57722494
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 0%

---

# ACSD-63244：解決管理面板JavaScript問題，包括[!DNL Google Maps]轉譯與主控台錯誤

ACSD-63244修補程式修正了管理面板中的多個JavaScript問題，包括[!DNL Google Maps]轉譯問題以及瀏覽器主控台中重複出現的`Uncaught TypeError: this._each is not a function`錯誤。 此修補程式可用於[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56。修補程式ID為ACSD-63244。 請注意，此問題已排程在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

Adobe Commerce （所有部署方法） 2.4.4、2.4.4-p9、2.4.6-p7、2.4.7

**與Adobe Commerce版本相容：**

Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hant)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

* `Uncaught TypeError: this._each is not a function`錯誤會顯示在瀏覽器主控台中，中斷管理UI功能。
* JavaScript錯誤導致[!DNL Google Maps]無法正確呈現。

<u>要再現的步驟</u>：

1. 載入Adobe Commerce管理UI。
1. 開啟瀏覽器主控台並執行下列指令碼：

   ```
   Object.values([] || {}).forEach((function(e) {  
   e("dd")  
   }));  
   ```

<u>預期結果</u>：

預設JS程式庫中可用的JavaScript功能可正確執行且沒有錯誤。

<u>實際結果</u>：

JavaScript錯誤會出現在瀏覽器主控台中：

```
Uncaught TypeError: this._each is not a function
```

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hant)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
