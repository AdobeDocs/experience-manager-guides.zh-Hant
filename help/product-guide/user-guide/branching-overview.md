---
title: 在AEM Guides中分支 |Adobe Experience Manager Guides`
description: 瞭解如何在AEM Guides中建立和管理DITA map的分支，以支援平行撰寫、獨立發佈和合併檔案變更。
TQID: https://experienceleague.adobe.com/pg9zeEg8m3NeDbN-j945SqPbaMX0GgBmuquAsQcrjOM
product_v2:
  - id: fae5e35a-80c9-4b94-9352-1a060a6aab1d
    internal-label: Experience Manager Guides
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: ab01a588-7dea-43f2-a699-0b3f128465d6
    internal-label: Authoring
  - id: ec4263d9-bf7c-44c7-b3f1-3e664861c8f2
    internal-label: Generative AI
subfeature_v2:
  - id: ad602516-aca3-4247-9ae8-f393d958efa9
    internal-label: Editor
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: f5c2a4bb-71ca-4d7e-8efd-442250e6ba48
    internal-label: Content reuse
source-git-commit: 3f0d8e31537ade58a4eab5ddf73eb6d263d3dd96
workflow-type: tm+mt
source-wordcount: '747'
ht-degree: 0%
---
# 概觀

>[!NOTE]
>
> 分支和合併功能在2026.11.0版的Experience Manager Guides as a Cloud Service中引入，並預設為停用。 若要針對您的環境啟用此功能，請聯絡您的客戶成功團隊。

Adobe Experience Manager Guides中的分支可讓您從&#x200B;**主要**&#x200B;分支中建立和管理多個分支，讓DITA map可同時處理不同的檔案發行。 每個分支可讓作者獨立管理內容變更，而不會影響其他分支中的對應內容。

透過分支，多個專案團隊可同時處理同一DITA map相關的不同發行版本、功能或修正。 您可以在更新準備就緒時，將分支中的變更合併到預設分支(`main`)。

## 分支的運作

您可以從&#x200B;**主要**&#x200B;或任何現有DITA map分支建立分支。 建立分支後，您可以切換到該分支，並開始編輯地圖及其內容。 您也可以從選取的分支發佈內容，或在準備就緒時將變更合併至`main`。

例如，假設名為`install-the-lift.ditamap`的DITA map包含產品的安裝指示。 您的檔案團隊可以從`main`建立此對應的兩個分支：

- **版本1：** Team A會維護現有的安裝指示和位址修正。
- **版本2：** Team B開發新功能的安裝指示。

兩個團隊可以在各自的對應分支上獨立工作，而不會影響彼此的變更。

>[!NOTE]
>
>會根據DITA map建立分支。 您也可以新增和編輯所選分支中的對映未參考的主題。 如需詳細資訊，請檢視[開啟或編輯目前對映](./create-manage-branch.md#open-or-edit-topics-outside-the-current-map-context)之外的主題。

當您建立DITA map的分支時，Experience Manager Guides不會自動將對映的參考主題複製到新分支中。 未變更的主題會從來源分支或預設分支（主要）中讀取。 只有當您編輯主題並儲存在新分支中時，它才會複製到該分支中。

例如，一個DITA map參照100個主題，而存放庫包含50個其他主題，這些主題沒有被該map參照。 當您建立新分支（版本1.0）時，所有100個參照的主題都會自動成為1.0版的一部分，即使這些主題都未經過編輯。 這50個未參考的主題不會自動成為新分支的一部分。 如果您編輯其中10個，則只有這10個會成為1.0版的一部分。 其餘的40個未變更主題會繼續從預設分支（主要）使用。

>[!NOTE]
>
> 主題版本設定功能可繼續搭配分支使用。 您可以在DITA map的選定分支中建立和管理主題版本。 每個分支都會維護自己的版本記錄，獨立於其他分支。

## 主要優點

在Experience Manager Guides中使用分支可提供下列優點：

- **隔離編輯：**&#x200B;在選取的對應分支中進行變更，而不影響其他分支中的對應內容。
- **平行編寫：**&#x200B;讓多個團隊同時處理各自對應分支的不同版本、功能或修正。
- **獨立發佈：**&#x200B;從個別對應分支發佈檔案，而不等待其他分支中的變更完成。
- **控制合併：**&#x200B;將地圖分支的變更合併至預設分支(`main`)，並具備檢閱和解決衝突的能力。

## 分支與基準線

>[!NOTE]
>
> 基線和分支是互斥的特徵。 啟用分支時，基準線功能會變成無法使用。 但是，現有的基準線會維持不變，不會刪除。 如果稍後停用分支，則現有基準會再次可供使用。

**基準線**&#x200B;會識別DITA map的特定主題版本組合，可讓您使用這些選取的版本產生輸出。

**分支**&#x200B;為DITA map及其內容提供單獨的編輯環境，可讓作者進行變更，而不會影響相同對應的其他分支。

| 基準線 | 分支 |
|---|---|
| 在DITA map中選取特定版本的主題。 | 建立DITA map的個別分支以獨立管理變更。 |
| 用於發佈特定主題版本組合。 | 用於同時開發和發佈不同的版本。 |
| 不要提供隔離的編輯內容。 | 支援獨立編輯和合併。 |

## 即將推出的功能

下列功能目前僅於預設分支(`main`)中支援，並計畫在未來Experience Manager Guides版本中於DITA map的其他分支中支援：

- 搜尋
- 尋找並取代
- 稽核工作流程

