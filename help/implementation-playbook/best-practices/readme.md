---
source-git-commit: 8013e6339d42108dbefbbafa5db7f9ffc5288c4f
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 0%

---
# 最佳做法：內容建立工作流程

本檔案說明在&#x200B;*Adobe Commerce實作行動手冊*&#x200B;中要求變更或新增&#x200B;*[最佳實務] (https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/phases.html?lang=zh-Hant*&#x200B;內容的使用者工作流程。

## 誰可以建立請求？

Adobe接受來自內部和外部利害關係人的請求，包括但不限於以下群組中的個人：

- Adobe合作夥伴
- AdobeCTAG （客戶技術顧問小組）、客戶支援、客戶成功、工程團隊

## 如何建立請求？

**內部利害關係人**&#x200B;可以透過在COMDOX專案中開啟Jira問題來提交請求。 **外部利害關係人**&#x200B;可以透過開啟此存放庫中的[GitHub問題](https://github.com/AdobeDocs/commerce-operations.en/issues/new/choose)來提交請求。

您可以提交下列型別的請求：

- 新內容的概念
- 已發佈內容的更新
- Publish利害關係人或社群提供的新內容

## 整體程式為何？


**建立Jira票證或問題** — 內部關係人在COMDOX專案中建立Jira票證。 外部利益關係人提交GitHub問題。 在Jira或[GitHub問題](https://github.com/AdobeDocs/commerce-operations.en/issues/new/choose)中包含完整的詳細資料，以協助團隊瞭解內容並排定請求的優先順序。

**Adobe專案團隊會評估請求並排定優先順序** — 團隊會定期監控請求以確定優先順序，並評估請求變更以納入Implementation Playbook最佳實務中。 例如，團隊可能會決定不建立新的最佳實務主題，而是將請求的內容新增至Experience League或Adobe Developer網站上的現有產品檔案。

如果請求中未提供足夠的資訊，團隊會向請求者要求其他資訊。 如果請求者未在14天內回應，專案團隊會關閉請求。

**建立或更新內容** — 內容建立工作已依照[Adobe Experience League貢獻者指南](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html?lang=zh-Hant)中記錄的程式完成。 根據請求，工作可能包括將新內容轉換為Markdown、建立主題或更新現有主題。

**內容檢閱、核准和發佈** — 內容在主題建立或更新期間使用[GitHub提取要求](https://experienceleague.adobe.com/docs/contributor/contributor-guide/setup/git-fundamentals.html?lang=zh-Hant#pull-requests)進行檢閱和編輯。 所有內容都必須經過編輯稽核。 技術審查是選用性的，取決於內容。 如果不需要技術審查，該流程將只繼續進行編輯審查。 在內容獲得核准之前，此過程可能需要多次反複操作。

文章獲得核准後，提取請求可以合併至生產分支。 合併應由作者完成。 主題合併後，可透過手動程式立即發佈至生產環境，或於下次發佈工作執行時自動發佈。 發佈工作通常每兩小時執行一次。

**新內容通知**-Adobe將提供[最佳實務概觀](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/phases.html?lang=zh-Hant)主題上的&#x200B;*新增功能*&#x200B;區段，以隨時通知使用者最近發佈或更新的主題。 Adobe也將利用現有管道（例如行銷和內部通訊）來推廣全新的最佳實務內容。

## 待處理專案與Kanban面板

為避免重複，已建立並排定優先順序的要求將顯示在COMDOX專案和[GitHub問題專案的Jira待辦專案中](https://github.com/orgs/AdobeDocs/projects/6/views/1)。 鼓勵內部利害關係人與Jira的投票系統互動，以投票表決他們認為必要或相關的請求。 投票也有助於最佳實務專案團隊瞭解利害關係人期望的內容型別和價值。 待定優先順序和稽核的請求會顯示在待處理專案中，直到它們移至Kanban展示板中的作用中通道為止。

內部使用者可以存取Kanban展示板以檢視（和/或監視）正在處理的內容以及進度。 此展示板上只會顯示作用中的請求。
