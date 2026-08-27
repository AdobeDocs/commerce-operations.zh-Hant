---
title: '[!DNL Adobe Commerce Patching Automation]疑難排解指南'
description: 疑難排解 [!DNL Adobe Commerce Patching Automation]中的常見問題和錯誤訊息
hide: true
source-git-commit: 1f92a1542c77954f10aa4c14de54f090581f9330
workflow-type: tm+mt
source-wordcount: '1710'
ht-degree: 0%

---

# [!DNL Adobe Commerce Patching Automation]疑難排解指南

使用[!DNL Patching Automation]進行修補程式操作時，您可能會遇到錯誤訊息和問題，這些訊息和問題可能會阻止修補程式應用程式成功或進行重新版本。 本指南提供最常見問題的解決方案。

## 快速疑難排解步驟

### 如果修補作業失敗

* 檢查操作狀態以瞭解哪個階段失敗
* 檢閱特定失敗原因的錯誤訊息
* 檢查錯誤記錄檔以取得技術詳細資訊
* 請遵循本指南中提供的解決方案

>[!TIP]
>
>在Cloud Console中，即使刪除了暫時的整合環境，您仍可從專案的活動摘要取得部署記錄。

### 修補作業持續時間

對於大多數環境，下列時間表說明修補作業需要多久時間，但視環境大小和複雜度而定，可能需要更長的時間：

* **預先處理：** 2-5分鐘
* **正在修補：** 5-15分鐘
* **後續處理：** 10-40分鐘
* **總計：** 15-60分鐘

>[!NOTE]
>
>後續處理時間是根據您環境的部署歷史記錄來估計，因此對於部署速度異常快或速度異常緩慢的環境，該時間可能會超出上述範圍。

### 取消進行中的修補程式

>[!WARNING]
>
>修補程式作業開始後，應允許其完成。 即使作業失敗，系統也會包含執行的清理程式。 中斷程式可能會讓您的環境處於不一致的狀態。

## 常見成功訊息

* **「工作已成功完成」** — 修補程式已成功套用/回覆，沒有任何問題。

* **「已套用修補程式」** — 您正在嘗試套用已套用的修補程式。 系統偵測到您的環境中已有此修補程式。 不需要採取任何動作。

* **「修補程式已還原」** — 您正在嘗試還原已還原的修補程式。 系統偵測到目前未套用修補程式。 不需要採取任何動作。

## 常見錯誤訊息與解決方案

>[!NOTE]
>
>並非所有可能的錯誤都列於下方。 初步檢查期間未列出的失敗顯示為一般「初步檢查期間發生錯誤」；驗證期間未列出的失敗顯示為一般「後期處理期間發生錯誤」 — 請以兩種方式連絡支援人員，並提供確切的錯誤文字。 修補期間，未預期的失敗會直接顯示原始的基本錯誤訊息，而非一般備援。

### 環境整備錯誤

#### 「上次部署不成功。 在套用或還原修補程式之前，請確定環境穩定。」

**發生時：**&#x200B;在初步檢查開始時，在任何修補程式特定驗證之前

**原因：**&#x200B;您目標環境的最新部署未成功完成

**解決方案：**&#x200B;重新部署您的目標環境，並確認部署已順利完成（在Cloud Console中檢查其部署記錄檔），然後再重試修補作業。

### 修補應用程式錯誤

#### 「無法套用修補程式，因為[!DNL Patching Automation]偵測到您的程式碼基底或修補程式檔案發生這些問題」

**發生時：**&#x200B;初步檢查期間

**原因：**&#x200B;修補程式與您目前的程式碼基底衝突，或是修補程式本身有問題

**解決方案：**

* 檢閱提供的詳細錯誤記錄檔，以識別是否為程式碼基底或修補程式問題
* 檢查您的程式碼中是否有衝突的自訂
* 確認修補程式與您的Adobe Commerce版本相容
* 請考慮手動解決衝突或聯絡支援人員

#### 「您正在嘗試還原未透過[!DNL Patching Automation]套用的修補程式。 修補程式可能是手動套用的。」

**發生時：**&#x200B;還原作業期間

**原因：**&#x200B;您正在嘗試還原未透過[!DNL Patching Automation]套用的修補程式

**解決方案：**&#x200B;使用與原來套用修補程式相同的方法，或連絡支援人員以取得手動協助

### 環境和驗證錯誤

#### 「環境與父系不同步」

**發生時：**&#x200B;在驗證期間，在合併前同步檢查中 — 在整合環境合併到您的目標環境之前

**原因：**&#x200B;您的整合環境與上層環境不同，通常是因為測試修補程式時目標環境已變更

**解決方案：**

* 一旦目標環境穩定後，請重試修補程式操作
* 避免在修補作業進行時變更目標環境
* 如果同步問題仍然存在，請聯絡支援人員

#### 「合併後驗證失敗：環境在合併後未同步。」

**發生時：**&#x200B;驗證期間，整合環境已經合併至您的目標環境之後

**原因：**&#x200B;兩個環境的程式碼在合併後不相符，通常是暫時的Platform.sh API傳播延遲，而不是真正的衝突

**解決方案：**

* 請稍候幾分鐘，然後再次檢查環境狀態。 此問題通常會自行解決
* 如果數分鐘後環境仍不相符，請聯絡Adobe支援。

#### 「當cron啟用且維護模式停用時，無法在生產環境中建立修補工作。 請在套用修補程式之前啟用維護模式並停用cron工作。」

**發生時：**&#x200B;生產環境的初步檢查期間

**原因：**&#x200B;生產環境不符合必要的安全條件

**解決方案：**

* 為您的生產存放區啟用維護模式
* 在您的生產環境中停用cron工作
* 在重試之前，請確認兩個條件都符合
* 或者，在UI中選取覆寫核取方塊，以略過這些檢查並繼續進行。 只有在您瞭解修補生產環境而無這些防護措施時，才使用覆寫選項

>[!IMPORTANT]
>
> [!DNL Patching Automation]不會自動啟用維護模式或停用cron工作 — 這些工作必須由您從外部完成

#### 「修補程式操作已完成，但環境健康狀態檢查失敗。 這表示部署可能發生問題。 請檢閱環境狀態並考慮回覆變更。」

**發生時：**&#x200B;修補應用程式或還原後，驗證期間

**原因：**&#x200B;已成功套用或還原修補程式，但後續健康狀態檢查失敗

**解決方案：**

* 測試店面和關鍵結帳以及管理工作流程，確認客戶是否實際受到影響
* 在Cloud Console中，檢閱環境狀態並檢查專案&#x200B;**活動**&#x200B;摘要中的應用程式和部署記錄。 尋找與修補程式操作或部署相關的錯誤。
* 觸發手動重新部署，以判斷健康情況檢查失敗是由暫時性部署或基礎結構問題所造成。
* 如果問題仍然存在，請還原修補程式。 如果修補程式是由[!DNL Patching Automation]管理，而且作業可用，請選取[!UICONTROL Revert]。 如果修補程式是`m2-hotfixes`目錄中的自訂修補程式，請從專案存放庫中刪除修補程式檔案。 提交並推送變更，然後重新部署環境。
* 如果問題仍然存在，請聯絡Adobe支援。在您的支援要求中包含下列資訊：支援專案ID、環境ID，以及此確切訊息：上次的作業未完全完成，因此支援可能需要確認環境的狀態。

### 驗證和存取錯誤

#### 「存取遭拒」

**發生時：**&#x200B;當您的帳戶在環境建立或存取期間缺少必要的許可權時

**原因：**&#x200B;您的使用者帳戶缺少必要的許可權

**解決方案：**

* 檢查您的使用者角色和許可權
* 請連絡您的系統管理員
* 確認您擁有環境管理許可權
* 確保您擁有部署許可權

### GitHub整合錯誤

#### 沒有可用於提供者&quot;github&quot;的Git認證。 安裝此存放庫的Patching Automation GitHub應用程式」

**發生時：**&#x200B;在連線至GitHub的專案修補作業期間

**原因：**&#x200B;您的存放庫上未安裝[!DNL Patching Automation] GitHub應用程式

**解決方案：**&#x200B;請依照[中的步驟為 [!DNL Patching Automation]](github-integration.md)設定GitHub整合

#### 「GitHub API要求失敗」

**發生時：**&#x200B;在GitHub連線專案的修補程式操作期間

**原因：**&#x200B;暫時性問題導致服務無法連線至GitHub

**解決方案：**&#x200B;請稍候幾分鐘，然後再次嘗試操作。 如果錯誤持續發生，請連絡[Adobe Commerce雲端支援](https://experienceleague.adobe.com/home?lang=zh-Hant#support)

#### 「逾時內未建立環境」（GitHub連線的專案）

**發生時間：**&#x200B;整合環境建立期間

**原因：**&#x200B;專案的GitHub整合已停用`fetch-branches`選項。 因此，服務推送的暫時分支不會同步，且永遠不會建立整合環境。

**解決方案：**&#x200B;啟用整合的[`fetch-branches`選項](https://experienceleague.adobe.com/zh-hant/docs/commerce-on-cloud/user-guide/dev-tools/integrations/github#enable-the-github-integration)，然後重試作業。 請參閱[為 [!DNL Patching Automation]](github-integration.md)設定GitHub整合。

### 環境啟用錯誤

#### 「無法啟用整合環境。」

**發生時：**&#x200B;當[!DNL Patching Automation]無法啟動安全測試修補程式所需的暫時整合環境時。

**原因：**&#x200B;取決於錯誤旁邊顯示的其他詳細資料：

**如果詳細資料提及撰寫器或Adobe Commerce封裝：**

* 登入[https://account.magento.com/](https://account.magento.com/) （或讓您的帳戶擁有者登入），並確認您的帳戶可以存取Commerce Enterprise程式碼基底。
* 確認您專案的撰寫器公開/私密金鑰組是否正確 — 請參閱[驗證金鑰](https://experienceleague.adobe.com/zh-hant/docs/commerce-on-cloud/user-guide/develop/authentication-keys)。
* 登入[https://account.magento.com/](https://account.magento.com/) （或要求您的帳戶擁有者登入），並確認您的帳戶可以存取Commerce Enterprise程式碼基底。
* 驗證您專案的撰寫器公開和私用驗證金鑰是否正確。 請參閱[驗證金鑰](https://experienceleague.adobe.com/zh-hant/docs/commerce-on-cloud/user-guide/develop/authentication-keys)。
* 確認錯誤訊息中名為的套件適用於您的Commerce版本。 請參閱[Adobe Commerce套件](https://experienceleague.adobe.com/zh-hant/docs/commerce-operations/release/packages/adobe-commerce)。

**如果詳細資料提及環境位置或資源：**

* 在Cloud Console中，開啟專案概觀並檢閱環境及其狀態。 停用或刪除任何未使用的整合環境：選取環境。 前往&#x200B;**[!UICONTROL Settings]>[!UICONTROL General]**。 將環境狀態設定為非作用中。

  或者，使用CLI： `magento-cloud environment:list` / `magento-cloud environment:deactivate <environment-name>`
* 確認專案有足夠的資源，例如磁碟空間。
* 請確保作業時的父環境穩定（沒有作用中的部署）。
* 如果您需要提高環境上限，請聯絡Adobe支援。

**若為任何其他原因：**&#x200B;請檢閱[修補自動化] UI中的詳細錯誤記錄檔，或連絡支援人員並提供確切的錯誤文字。

## 取得協助

**何時連絡支援：**

若發生下列情況，請聯絡Adobe Commerce Cloud支援：

* 錯誤訊息不清楚或缺少足夠的詳細資訊
* 修補程式操作一致失敗
* 您需要手動衝突解決協助
* 健康情況檢查失敗，但原因不明
* 您需要有關環境同步問題的協助

**要提供的資訊：**

聯絡支援時，請提供：

* **專案識別碼** — 您的Adobe Commerce Cloud專案識別碼
* **環境ID** — 發生問題的特定環境
* **作業識別碼** - [!DNL Patching Automation]作業識別碼
* **錯誤詳細資料** — 完整的錯誤訊息和記錄
* **要再現的步驟** — 發生錯誤時您正在做什麼
* **先前嘗試** — 您已經嘗試解決的問題

### 其他資源

如需更詳細的技術資訊：

* 檢閱隨失敗操作提供的完整錯誤記錄檔
* 請檢視Adobe Commerce檔案以取得修補程式特定指南
* 請聯絡Adobe Commerce Cloud支援以取得特定於環境的問題

### 相關主題

* [Adobe Commerce Cloud檔案](https://experienceleague.adobe.com/zh-hant/docs/commerce-on-cloud/user-guide/overview)
* [Adobe Commerce安裝指南](/help/installation/overview.md)
* [修補自動化簡介](intro.md)
* [如何存取](access.md)
* [工作流程概觀](workflow.md)
* [GitHub整合](github-integration.md)
* [最佳實務](best-practices.md)
