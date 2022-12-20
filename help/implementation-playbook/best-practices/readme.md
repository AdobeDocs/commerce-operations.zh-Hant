---
source-git-commit: 8013e6339d42108dbefbbafa5db7f9ffc5288c4f
workflow-type: tm+mt
source-wordcount: '639'
ht-degree: 0%

---
# 最佳實務：內容建立工作流程

本文檔描述了請求更改或添加 *[最佳實務](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/phases.html)* 內容 *Adobe Commerce實施行動手冊*.

## 誰可以建立請求？

Adobe接受內部和外部持份者的請求，包括但不限於下列群組中的個人：

- Adobe合作夥伴
- AdobeCTAG（客戶技術顧問小組）、客戶支援、客戶成功、工程團隊

## 如何建立請求？

**內部利益相關方** 可在COMDOX專案中開啟Jira問題以提交請求。 **外部利益相關方** 可以透過開啟 [GitHub問題](https://github.com/AdobeDocs/commerce-operations.en/issues/new/choose) 儲存庫。

您可以提交下列類型的請求：

- 新內容的構想
- 已發佈內容的更新
- 發佈利益相關方或社群提供的新內容

## 整體流程是什麼？


**建立Jira票證或問題** — 內部利益相關方在COMDOX項目中建立Jira票證。 外部利害關係人提交GitHub問題。 在Jira或 [GitHub問題](https://github.com/AdobeDocs/commerce-operations.en/issues/new/choose) 協助團隊了解內容並排定請求的優先順序。

**Adobe專案團隊會評估請求，並排定請求的優先順序** — 團隊定期監控請求，以確定優先順序並評估請求的更改，以便納入實施行動手冊最佳做法。 例如，團隊可能會判斷，請求的內容應新增至Experience League或Adobe Developer網站上的現有產品檔案，而非建立新的最佳實務主題。

如果請求中提供的資訊不足，則團隊請求請求者提供的其他資訊。 如果要求者在14天內未回應，團隊會關閉要求。

**建立或更新內容** — 內容建立工作會依照 [Adobe Experience League貢獻者指南](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html). 視請求而定，工作可能包括將新內容轉換為Markdown、建立主題或更新現有主題。

**內容審核、核准和發佈** — 在主題建立或更新期間，使用 [GitHub提取請求](https://experienceleague.adobe.com/docs/contributor/contributor-guide/setup/git-fundamentals.html?lang=en#pull-requests). 所有內容都必須經過編輯審核。 技術審核是選填的，視內容而定。 如果不需要技術審查，該過程只會繼續進行編輯審查。 此程式需要數次反覆，直到內容獲核准為止。

文章核准後，提取請求即可合併至生產分支。 合併應由作者完成。 合併主題後，可使用手動程式立即發佈至生產環境，或在下次發佈工作執行時自動發佈。 發佈工作通常每兩小時執行一次。

**新內容通知**-Adobe將提供 *新增功能* 區段 [最佳實務概觀](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/phases.html?lang=en) 主題，讓使用者了解最近發佈或更新的主題。 Adobe也會使用現有的管道（例如行銷和內部通訊）來宣傳新的最佳實務內容。

## 積壓和看板板

為避免重複，已建立和排定優先順序的請求將在COMDOX項目的Jira積壓中顯示， [GitHub問題專案](https://github.com/orgs/AdobeDocs/projects/6/views/1). 鼓勵內部利益攸關者與吉拉的投票系統接觸，以支援他們認為必要或相關的請求。 投票也有助於最佳實務專案團隊了解利害關係人期望和重視的內容類型。 待定優先順序和審核的請求會顯示在積壓中，直到它們移至看板板中的活動通道。

看板板可由內部用戶訪問，以查看（和/或監視）正在處理的內容和已完成的進度。 此展示板上只會顯示作用中的請求。
