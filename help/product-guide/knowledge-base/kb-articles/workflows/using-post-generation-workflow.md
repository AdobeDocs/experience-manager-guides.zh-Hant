---
title: 貼文產生工作流程
description: 附範例的後生成工作流程概覽
exl-id: e19fdc0b-0ec6-46ce-81ed-e9490d12c029
feature: Workflow Configuration
role: User, Admin
TQID: https://experienceleague.adobe.com/GmpUvIwR5aDOIQ4RNUXoeOeQB3MrueRuxpvYBwYev4I
product_v2: id: fae5e35a-80c9-4b94-9352-1a060a6aab1did: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a3bd6397-2eb2-4908-a61c-226e26855dcaid: cb8c6a2a-3c38-4e40-867c-756f8c36bb0e
subfeature_v2: id: b455a250-64c4-4598-b015-7b6b6dc528b1id: fd6cc9e1-e5e5-494e-b7b1-a32f2d6cd7c9
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
source-git-commit: 8ed5c9cb07c56b84b36ef56a55af8738989a6d3f
workflow-type: tm+mt
source-wordcount: 327
ht-degree: 0%

---

# AEM Guides發佈 — 貼文產生工作流程

AEM Guides可讓您靈活指定輸出後產生工作流程。 您可以在使用AEM Guides產生的輸出上執行一些後續處理工作。
例如，您可能會想要在PDF輸出上設定某些屬性，或是在產生輸出後想要傳送電子郵件給一組使用者。


## 使用後產生工作流程需要哪些步驟

### 建立工作流程程式

建立以Java或ECMA為基礎的工作流程處理，以對產生的輸出執行作業。 例如，將部分中繼資料從來源複製到產生的內容，或操控產生的輸出的中繼資料。
- 我們將以使用ECMA指令碼建立此程式為例（您可以參考附加的套件）
- 如需以Java為基礎的工作流程程式，請參閱[安裝與設定指南](https://helpx.adobe.com/content/dam/help/en/xml-documentation-solution/4-2/Adobe-Experience-Manager-Guides_UUID_Installation-Configuration-Guide_EN.pdf#page=119)中的&lt;自訂輸出後產生工作流程&#x200B;*>一節*


### 建立工作流程模型

使用您在上一步建立的自訂工作流程程式，建立工作流程模型並將該程式步驟新增到其中。
- 您也必須新增強制的處理程式步驟&quot;*完成產生貼文*&quot;，作為工作流程的最後一個步驟。

請參閱下列範例工作流程模型：

![產生後工作流程模型](../assets/workflows/pgwf-workflow-model.png)


### 在地圖上使用此貼文產生工作流程

產生後工作流程是可設定在AEM Guides發佈機制中任何輸出預設集的屬性。 範例：

輸出預設集上的![產生後工作流程](../assets/workflows/pgwf-preset-settings.png)


假設已建立選取的模型。


### 測試

現在您可以使用此預設集執行發佈，並驗證程式步驟輸出


## 範例

您可以參考以下套件，並透過套件管理員進行安裝，以測試範例產生後工作流程（*，如上述熒幕擷取畫面所述*）

[基於ECMA的後生成工作流程模型範例](../assets/workflows/sample-pgwf-ecma-test-wfmetadata.zip)
