---
title: 使用AI助理聰明地編寫檔案'
description: 瞭解如何使用AI助理聰明地在Adobe Experience Manager Guides中搜尋和編寫檔案。
exl-id: c18e8761-333e-40ef-9e16-e71a194a754a
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
source-git-commit: b3c2c68321080aa4dde16befe4bfd0022bf9f61c
workflow-type: tm+mt
source-wordcount: '757'
ht-degree: 0%
---
# AI 助理

>[!NOTE]
>
> AI助理功能目前可供Adobe Experience Manager Guides as a Cloud Service使用。

Adobe Experience Manager Guides中的AI Assistant是AI支援的工具，旨在透過簡化內容建立、管理和編寫工作流程來提升生產力。 它提供兩種模式：Agentic和Standard。 在&#x200B;**代理模式**&#x200B;中，AI Assistant可讓您透過自然語言互動來執行內容相關工作，並具備「匯入」、「建立」和「智慧標籤」等技能，以簡化內容建立、組織和中繼資料管理。 在&#x200B;**標準模式**&#x200B;中，AI助理可提供撰寫協助，協助您更有效率地建立、調整及管理內容。

## AI助理模式

AI助理有兩種模式可用： **Agentic**&#x200B;和&#x200B;**Standard**。 管理員可以從&#x200B;**Workspace設定**&#x200B;中&#x200B;**一般**&#x200B;標籤的&#x200B;**AI功能**&#x200B;區段選取模式。 兩種模式中，編輯器中的AI助理面板都維持不變，但可用的功能有所不同：

- **代理模式：**&#x200B;使用技能&#x200B;**匯入**、**建立**&#x200B;和&#x200B;**智慧標籤**，將檔案轉換為結構化主題、建立內容的第一個草稿，並根據您組織的分類法建議相關標籤。
- **標準模式：**&#x200B;透過內容重複使用、翻譯和內容品質改善等內容相關動作，提供AI支援的撰寫協助，以簡化撰寫工作流程。

## 代理模式

>[!NOTE]
>
> 若要以代理模式使用AI助理，您的組織需要上線到Adobe CX Enterprise Coworker並擁有可用的積分；上線後，請聯絡您的客戶成功團隊以啟用該功能。 如需設定詳細資料，請檢視[以代理模式設定AI小幫手](../install-conf-guide/configure-ai-assistant-agentic-mode-cs.md)。

AI Assistant中的代理程式模式可讓您透過自然語言互動來執行各種與內容相關的工作，例如建立和匯入內容、摘要主題、將主題新增至地圖以及管理中繼資料。 您可以在聊天面板中說明您的需求，AI助理規劃和執行任務，同時提供其進度的可見度。 代理模式可讓您快速存取以下技能：

- **匯入**：從裝置或內容存放庫將PDF、Word或Markdown檔案轉換為結構化主題。 如需詳細資訊，請檢視[使用AI助理匯入內容](./import-ai-assistant.md)。

- **建立**：從輸入資料（例如規格、白板影像、熒幕擷取畫面和其他參考內容）產生草稿主題和地圖，並可以選擇使用現有內容來設定色調和樣式。 如需更多詳細資料，請檢視[使用AI助理建立內容](./create-ai-assistant.md)。

- **智慧標籤**：根據您組織的分類法，建議主題的相關標籤，以改善中繼資料的一致性。 如需詳細資訊，請檢視[使用AI助理的智慧標籤](./ai-assistant-agentic.md)。

「AI輔助程式」面板的下列元件可協助您新增內容、輸入提示及啟動工作：

![ai助理智慧標籤](./images/panel-new-agentic.png)

- **(A)**&#x200B;交談記錄：檢視並重新開啟先前的交談，以檢視先前的要求與回應。
- **(B)**&#x200B;全熒幕：將AI助理面板展開至全熒幕。
- **(C)**&#x200B;提示空間：輸入提示要求，或輸入`/`以新增檔案並產生標籤。
- **(D)**&#x200B;附加檔案或新增內容：從您的本機系統新增主題、地圖或檔案，以提供AI助理處理的內容。
- **(E)**&#x200B;傳送：將您的提示和附加內容提交至AI小幫手。
- **(F)**&#x200B;快速動作：直接從下列捷徑之一開始工作： **匯入**、**建立**&#x200B;或&#x200B;**標籤**。

## 標準模式

標準模式可讓您的撰寫程式變得更聰明、更快。 當您在編輯器中選取文字時，「AI助理」會提供快速動作，例如產生內容重複使用的智慧型建議、轉譯內容、改善內容品質等等，所有這些都是根據您選取的內容。 如此可提升整體撰寫體驗及作者的生產力。

如需更多詳細資料，請檢視[使用AI助理撰寫檔案](./ai-assistant-right-panel.md)。

![ai助理](./images/ai-assistant-panel.png)


## 開始使用 AI 助理

第一次使用&#x200B;**AI小幫手**&#x200B;時，系統會提示您先提交同意，再使用Experience Manager Guides Generative AI功能。

執行以下步驟以啟動AI小幫手：

1. 登入Experience Manager Guides。
1. 在首頁上，從頂端選取&#x200B;**AI助理**。 確保您的管理員已在所需模式下啟用AI助理功能。
AI助理顯示主要功能、使用者指南連結和**開始使用**&#x200B;按鈕。
1. 請仔細閱讀使用者准則，然後選取&#x200B;**開始使用**&#x200B;以啟動AI小幫手。

>[!NOTE]
>
>如果您已同意使用「說明助理」功能的准則，則系統將不再提示您同意，您可以繼續使用「AI助理」功能。

**相關主題**

[AI Assistant安全性常見問題集](./ai-assistant-faq.md)

[Adobe Experience Manager Guides Generative AI披露](./adobe-generative-ai-disclosures.md)

[設定AI助理以提供智慧說明和編寫](../cs-install-guide/conf-smart-suggestions.md)
