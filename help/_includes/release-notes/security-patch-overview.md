---
source-git-commit: 52c330f62d722a4cae7f7f360ca61eca0f04b961
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---
# 關於Adobe Commerce安全性修補程式發行版本

**安全性錯誤修正**：解決已識別的安全性問題並在受影響的產品區域提供預期結果的軟體程式碼變更。 這些修正通常會回溯相容。

**安全性增強**：軟體改進或組態變更，以主動改善應用程式內的安全性。 這些安全性增強功能有助於解決安全性風險，這些風險會影響Adobe Commerce應用程式的安全狀態，但可能會與回溯不相容。

使用安全性修補程式發行版本，您無需套用完整修補程式發行版本中包含的其他品質修正和增強功能，即可保持網站更安全。 安全性修補程式發行版本會附加&#39;-pN&#39;，其中N是從1開始的增量修補程式版本（例如2.3.5-p1）。 安全性修補程式發行版本也可包含解決影響Adobe Commerce應用程式之重大問題所需的Hotfix。

安全性修補程式發行版本也可包含合規性相關變更，這些變更是確保Adobe Commerce應用程式符合合規性要求所必需的。 這些變更可能會引入與舊版不相容的變更，且為確保所有支援的發行版本都保持合規性而需進行。

每個安全性修補程式版本都是以之前的完整修補程式版本為基礎。 此版本包含先前修補程式版本的品質和安全修正，以及在先前完整修補程式版本和安全修補程式版本之間建立的安全性修正。

如需有關下載和套用安全性修補程式的說明，請參閱[Adobe Commerce知識庫](https://experienceleague.adobe.com/zh-hant/docs/commerce-knowledge-base/kb/how-to/how-to-obtain-and-apply-security-patches)中的&#x200B;_如何取得和套用安全性修補程式_。

>[!NOTE]
>
>延伸支援安全性修補程式僅適用於Adobe Commerce客戶，不適用於Magento Open Source程式碼基底。 請參閱[延伸支援](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/release/planning/lifecycle-policy#extended-support)。

## 隔離的安全性修補程式檔案

隔離的安全性修補程式檔案是非累積性的獨立修補程式檔案，僅包含一或多個安全性弱點的修正，不提供任何額外的功能更新或非安全性變更。 這些修補程式會獨立發行，以加快修正速度，並整合至下一個完整的安全性修補程式。 有關漏洞的詳細資訊可在相關安全性公告中提供，該公告連結至知識庫(KB)文章，其中包含套用修補程式的指示及其他資訊。

若要套用隔離的安全性修補程式檔案，客戶必須在其支援的發行版本行上使用最新的僅限安全性的修補程式發行版本（最新的 — p版本），因為隔離的安全性修補程式檔案是專門針對該版本進行測試的。

請參閱[安全性中心](https://helpx.adobe.com/tw/security/products/magento.html)以尋找Adobe Commerce的最新安全性更新。

