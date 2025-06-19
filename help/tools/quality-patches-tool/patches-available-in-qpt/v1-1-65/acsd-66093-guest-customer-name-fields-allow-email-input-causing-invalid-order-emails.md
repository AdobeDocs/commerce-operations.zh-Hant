---
title: ACSD-66093：訪客客戶名稱欄位允許電子郵件輸入，導致無效的訂單電子郵件
description: 套用ACSD-66093修補程式以修正Adobe Commerce問題，該問題導致有可能在訪客客戶**[!UICONTROL First Name]**和**[!UICONTROL Last Name]**欄位中輸入電子郵件地址，並傳送無效的訂單確認電子郵件。
feature: Checkout
role: Admin, Developer
type: Troubleshooting
exl-id: 30790492-330e-4810-8069-fce87b40ebb2
source-git-commit: b1912bbc5aabd36067563326ee5c6bb84e14441d
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-66093：訪客客戶名稱欄位允許電子郵件輸入，導致無效的訂單電子郵件

ACSD-66093修補程式修正了電子郵件地址可能輸入到客體客戶的&#x200B;**[!UICONTROL First Name]**&#x200B;和&#x200B;**[!UICONTROL Last Name]**&#x200B;欄位中，導致訂單確認電子郵件無效的問題。 安裝[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65時，即可使用此修補程式。 修補程式ID為ACSD-66093。 請注意，問題已在Adobe Commerce 2.4.8中修正。

## 受影響的產品和版本

**已為Adobe Commerce版本建立修補程式：**

* Adobe Commerce （所有部署方法） 2.4.5-p11

**與Adobe Commerce版本相容：**

* Adobe Commerce （所有部署方法） 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>此修補程式可能適用於發行版本為[!DNL Quality Patches Tool]的其他版本。 若要檢查修補程式是否與您的Adobe Commerce版本相容，請將`magento/quality-patches`套件更新至最新版本，並在[[!DNL Quality Patches Tool]上檢查相容性：搜尋修補程式頁面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。 使用修補程式ID作為搜尋關鍵字，以尋找修補程式。

## 問題

電子郵件地址可輸入到客體客戶的&#x200B;**[!UICONTROL First Name]**&#x200B;和&#x200B;**[!UICONTROL Last Name]**&#x200B;欄位中，這會導致無效的訂單確認電子郵件。

<u>要再現的步驟</u>：

1. 以訪客客戶的身分將產品新增到購物車。
2. 前往結帳。
3. 將電子郵件地址填入「test1@gmail.co」。
4. 以&quot;<test2@gmail.co>&quot;填入&#x200B;**[!UICONTROL First Name]**。
5. 以&quot;<test3@gmail.co>&quot;填入&#x200B;**[!UICONTROL Last Name]**。
6. 填寫其他必填欄位。
7. 下單。

<u>預期結果</u>：

應該會顯示驗證訊息，指出&#x200B;**[!UICONTROL First Name]**&#x200B;和&#x200B;**[!UICONTROL Last Name]**&#x200B;欄位無效，例如&#x200B;*名字無效！ 和姓氏無效！*&#x200B;且不得下訂單。

<u>實際結果</u>：

已下訂單。
**[!UICONTROL First Name]**&#x200B;和&#x200B;**[!UICONTROL Last Name]**&#x200B;欄位已儲存為已輸入的內容。
訂單確認電子郵件會傳送至所有三封電子郵件：test1@gmail.co、test2@gmail.co及test3@gmail.co。

## 套用修補程式

若要套用個別修補程式，請根據您的部署方法使用下列連結：

* Adobe Commerce或Magento Open Source內部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用狀況](/help/tools/quality-patches-tool/usage.md)。
* 雲端基礎結構上的Adobe Commerce：雲端基礎結構上的Commerce指南中的[升級和修補程式>套用修補程式](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相關閱讀

若要進一步瞭解[!DNL Quality Patches Tool]，請參閱：

* [[!DNL Quality Patches Tool]：「工具」指南中，品質修補程式](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服務工具。
