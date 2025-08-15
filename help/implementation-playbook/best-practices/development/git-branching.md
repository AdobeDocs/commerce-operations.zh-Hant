---
title: Git分支最佳實務
description: 瞭解用於原始程式碼管理的不同分支策略。
feature: Best Practices
role: Developer
exl-id: 7d7736e8-7023-4315-9965-71866b0be5c3
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# Git分支最佳實務

Source程式碼在開發過程中會經過多個穩定階段：

- 主動式開發
- 初始程式碼整合
- 品質保證(QA)的程式碼整合
- 用於最終使用者驗收測試(UAT)的程式碼整合
- 生產版本的最終程式碼整合

## 受影響的產品和版本

[所有支援的版本](../../../release/versions.md)：

- 雲端基礎結構上的Adobe Commerce
- Adobe Commerce內部部署

## 分支管理

每個開發階段都應該在Git中擁有對應的分支，以追蹤程式碼變更並簡化部署流程：

- **任務分支** — 開發人員在實作特定任務時，如功能和錯誤修正，提交其個別程式碼變更。
- **開發分支** — 多位開發人員將其個別工作分支的變更合併至單一開發分支，以進行自動化整合測試。 此分支會部署至開發環境。
- **QA分支** — 開發人員在開發完成之後合併變更，且程式碼已通過所有自動化整合測試和程式碼檢閱。 此分支會部署至QA環境，以進行手動QA測試。
- **穩定/UAT分支** — 程式碼通過手動QA測試後會合併的位置。 此分支會部署至UAT環境以進行使用者驗收測試。
- **生產/發行分支** — 在程式碼通過UAT後進行合併的位置。 此分支會部署至生產環境，以供發行版本使用。

>[!TIP]
>
>雲端基礎結構專案上的Adobe Commerce包含對應不同環境的特定分支。 請參閱[雲端指南](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow.html?lang=zh-Hant)中的[Pro專案工作流程](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/starter-develop-deploy-workflow.html?lang=zh-Hant)和&#x200B;_入門專案工作流程_。

## 分支策略

有幾種分支策略可供您使用。 選擇最適合開發團隊和專案複雜度的策略。

如需詳細資訊，請參閱下列外部資源：

- [分支工作流程](https://git-scm.com/book/en/v2/Git-Branching-Branching-Workflows)
- [分散式工作流程](https://git-scm.com/book/en/v2/Distributed-Git-Distributed-Workflows)
- 用於管理原始程式碼分支的[模式](https://martinfowler.com/articles/branching-patterns.html)
- [成功的Git分支模型](https://nvie.com/posts/a-successful-git-branching-model/)
- [GitHub流程](https://docs.github.com/en/get-started/quickstart/github-flow)
- [GitLab流程](https://about.gitlab.com/blog/2023/07/27/gitlab-flow-duo/)
