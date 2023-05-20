---
source-git-commit: 8013e6339d42108dbefbbafa5db7f9ffc5288c4f
workflow-type: tm+mt
source-wordcount: '639'
ht-degree: 0%

---
# 最佳做法：內容建立工作流

此文檔介紹要請求更改或添加到 *[最佳做法]https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/phases.html* 內容 *Adobe Commerce實施行動手冊*。

## 誰可以建立請求？

Adobe接受內部和外部利益相關方的請求，包括但不限於以下群體中的個人：

- Adobe合作夥伴
- AdobeCTAG（客戶技術咨詢組）、客戶支援、客戶成功、工程團隊

## 如何建立請求？

**內部利益相關方** 可以在COMDOX項目中開啟Jira問題來提交請求。 **外部利益相關方** 可以通過開啟 [GitHub問題](https://github.com/AdobeDocs/commerce-operations.en/issues/new/choose) 在此儲存庫中。

您可以提交以下類型的請求：

- 新內容的想法
- 對已發佈內容的更新
- 發佈利益相關者或社區提供的新內容

## 整個過程是什麼？


**建立Jira票證或問題** — 內部利益相關方在COMDOX項目中建立Jira票證。 外部利益相關方提交GitHub問題。 在Jira或 [GitHub問題](https://github.com/AdobeDocs/commerce-operations.en/issues/new/choose) 幫助團隊瞭解上下文並排定請求的優先順序。

**Adobe項目團隊評估請求並確定其優先順序** — 該團隊定期監控請求以確定優先順序並評估請求的更改，以便納入實施行動手冊最佳做法。 例如，團隊可能會確定，不應建立新的最佳做法主題，而應將請求的內容添加到Experience League或Adobe Developer站點上的現有產品文檔中。

如果在請求中沒有提供足夠的資訊，則團隊請求請求者提供的附加資訊。 如果請求方在14天內未響應，則團隊將關閉請求。

**建立或更新內容** — 內容建立工作在中記錄的過程之後完成 [Adobe Experience League撰稿人指南](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html)。 根據請求，工作可能包括將新內容轉換為標籤、建立主題或更新現有主題。

**內容審查、批准和發佈** — 內容在主題建立或更新過程中使用 [GitHub拉式請求](https://experienceleague.adobe.com/docs/contributor/contributor-guide/setup/git-fundamentals.html?lang=en#pull-requests)。 所有內容都必須經過編輯審核。 技術審查是可選的，取決於內容。 如果不需要進行技術審查，則該過程僅繼續進行編輯審查。 在批准內容之前，此過程可能需要多次迭代。

物品批准後，拉入請求可合併到生產分支。 合併應由作者完成。 合併主題後，可以立即使用手動流程將其發佈到生產環境中，或者在下次發佈作業運行時自動發佈。 發佈作業通常每兩小時運行一次。

**新內容通知**-Adobe將提供 *新增功能* 的 [最佳做法概述](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/phases.html?lang=en) 主題，讓用戶瞭解最近發佈或更新的主題。 Adobe還將利用現有渠道（如營銷和內部溝通）宣傳新的最佳做法內容。

## 積壓和看板板

為避免重複，已建立和排定優先順序的請求將在Jira積壓的COMDOX項目中可見， [GitHub問題項目](https://github.com/orgs/AdobeDocs/projects/6/views/1)。 鼓勵內部利益攸關者與吉拉的投票系統接觸，對他們認為必要或相關的請求進行投票。 投票還有助於最佳做法項目團隊瞭解利益相關方期望和重視的內容類型。 待定優先順序和審閱的請求將顯示在積壓工作中，直到它們被移至看板板中的活動通道。

內部用戶可以訪問看板板，以查看（和/或監視）正在處理的內容以及所取得的進展。 此主板上將只顯示活動請求。
