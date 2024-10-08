---
source-git-commit: cbb880010fa907592f87b42ecd4da8fdf06bc5fe
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 0%

---
# 2024年10月安全性修補程式重點說明

此版本包含下列重點專案：

* **TinyMCE升級** — 管理員中的[WYSIWYG編輯器](https://experienceleague.adobe.com/en/docs/commerce-admin/content-design/wysiwyg/editor)現在使用最新版本的TinyMCE相依性(7.3&#x200B;)。

   * TinyMCE 7.3提供更優異的使用者體驗、更出色的協同合作，以及更高的效率。 TinyMCE 5已在2.4.8版本行中移除&#x200B;。

   * 由於TinyMCE 5.10中報告安全性弱點([CVE-2024-38357](https://nvd.nist.gov/vuln/detail/CVE-2024-38357))，因此目前支援的所有發行版本系列也升級了相依性，並包含在所有的2024年10月安全性修補程式中：

      * 2.4.7 - p3
      * 2.4.6 - p8
      * 2.4.5-p10
      * 2.4.4-p11

* **Require.js升級**—Adobe Commerce現在使用最新版Require.js (2.3.7)。

   * 由於Require.js 2.3.6中報告有安全性弱點([CVE-2024-38999](https://nvd.nist.gov/vuln/detail/CVE-2024-38999))，因此目前支援的所有發行版本行也升級了相依性，並包含在所有2024年10月安全性修補程式中：

      * 2.4.7 - p3
      * 2.4.6 - p8
      * 2.4.5-p10
      * 2.4.4-p11

>[!NOTE]
>
>這些更新可回溯相容，且不會影響自訂專案和擴充功能&#x200B;。
