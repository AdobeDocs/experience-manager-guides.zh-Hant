---
title: 設定檔案狀態篩選器
description: 瞭解如何設定檔案狀態篩選器
feature: Web Editor Configuration
role: Admin
level: Experienced
source-git-commit: 4942b914ff278ebcf09d00da32d6f9c7cc4d7ff9
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---

# 設定檔案狀態篩選器

Adobe Experience Manager Guides提供依據檔案目前檔案狀態來搜尋檔案的功能。 您可以使用篩選器搜尋從儲存庫介面搜尋檔案，以瀏覽檔案。

執行以下步驟來設定檔案狀態篩選器：

1. 以管理員身分登入Adobe Experience Manager。
1. 選取頂端的Adobe Experience Manager連結，然後選擇&#x200B;**工具**。
1. 從工具清單中選取&#x200B;**指南**，然後選取&#x200B;**資料夾設定檔**。
1. 開啟&#x200B;**全域設定檔**&#x200B;圖磚。 如果您希望這些變更僅套用至該資料夾，而非全域，您也可以選取特定資料夾設定檔圖磚。
1. 瀏覽至&#x200B;**XML編輯器設定**。
1. 選取頂端的&#x200B;**編輯**&#x200B;圖示。
1. 選取「**下載**」圖示以在本機系統上下載`ui\_config.json`檔案。
在下載的`ui\_config.json`檔案中，請參閱下列章節：

       「
」       「repositoryFilters」： &lbrack;
       &lbrace;
       &quot;title&quot;： &quot;Document state&quot;，
       &quot;property&quot;： &quot;jcr：content/metadata/docstate&quot;，
       &quot;children&quot;： &lbrack;
       &lbrace;
       &quot;title&quot;： &quot;Draft&quot;，
       &quot;value&quot;： &quot;Draft&quot;
       ，
       &lbrace;
       &quot;title&quot;： &quot;Edit&quot;，
       &quot;value&quot;： &quot;Edit&quot;
       ，
       &lbrace;
       &quot;title&quot;： &quot;In-Review&quot;，
       &quot;value&quot;： &quot;In-Review&quot;
       ，
       &lbrace;
       &quot;title&quot;： &quot;Approved&quot;，
       &quot;value&quot;：&quot;Approved&quot;
       ，
       &lbrace;
       &quot;title&quot;： &quot;Reviewed&quot;，
       &quot;value&quot;： &quot;Reviewed&quot;
       ，
       &lbrace;
       &quot;title&quot;： &quot;Done&quot;，
       &quot;value&quot;： &quot;Done&quot;
       &rbrace;
       &rbrack;
       &rbrace;
       &rbrack;
       &quot;&#39;
   此程式碼片段代表Experience Manager Guides中可用的預設檔案狀態篩選器。

1. 您可以根據組織的工作流程來自訂篩選器值。 例如，若要新增自訂檔案狀態&#x200B;**擱置中**，請在`children`下插入下列專案：

   ```
   {
       "title": "Pending",
       "value": "Pending"
   }
   ```

1. 更新後，儲存檔案並上傳它。

設定的篩選器會顯示在首頁儲存庫的&#x200B;**篩選器**&#x200B;面板中。

**上層主題：**&#x200B;[&#x200B;自訂Web編輯器](conf-web-editor.md)
